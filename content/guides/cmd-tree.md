---
title: "Having fun with the tree command"
summary: tree command essentials
date: 2021-10-30T19:19:49-07:00
draft: false
toc: true
tags:
  - terminal
  - tree
---

## Overview

The `tree` utility can be very handy to quickly see the contents of a directory.

## Install

```shell
brew install tree
```

## Examples

### Sample Directory Structure

For the following examples, assume we have the following directory structure:

```shell
cmd-tree-material
├── baked-goods
│   ├── cakes
│   │   ├── carrot.md
│   │   └── chocolate.md
│   └── cookies
│       ├── chocolate-chip.md
│       └── sugar.md
└── beer
    ├── blonde-ale.md
    ├── ipa.md
    └── stout.md
```


*Yes, this was generated with `tree`*

### Basic tree view

No options, show me the default.

```shell
tree ./cmd-tree-material
```

Output

```shell
cmd-tree-material
├── baked-goods
│   ├── cakes
│   │   ├── carrot.md
│   │   └── chocolate.md
│   └── cookies
│       ├── chocolate-chip.md
│       └── sugar.md
└── beer
    ├── blonde-ale.md
    ├── ipa.md
    └── stout.md

4 directories, 7 files
```

### Only show first 2 levels

Maybe you're only interested in seeing the first two levels of the directory:

```shell
tree -L 2 cmd-tree-material/
```

Output
```shell
cmd-tree-material
├── baked-goods
│   ├── cakes
│   └── cookies
└── beer
    ├── blonde-ale.md
    ├── ipa.md
    └── stout.md
```

### Show Date Modified

How about displaying the date the files were modified? Add the `-D` option.

```shell
tree -D cmd-tree-material/
```

Output

```shell
cmd-tree-material
├── [Oct 31 18:06]  baked-goods
│   ├── [Oct 31 18:06]  cakes
│   │   ├── [Oct 31 18:06]  carrot.md
│   │   └── [Oct 31 18:06]  chocolate.md
│   └── [Oct 31 18:06]  cookies
│       ├── [Oct 31 18:06]  chocolate-chip.md
│       └── [Oct 31 18:06]  sugar.md
└── [Oct 31 18:06]  beer
    ├── [Oct 31 18:06]  blonde-ale.md
    ├── [Oct 31 18:06]  ipa.md
    └── [Oct 31 18:06]  stout.md

4 directories, 7 files
```

### Show the full path for each file

What's the full path? `-f`

```shell
tree -f cmd-tree-material/beer
```

Output:

```shell

cmd-tree-material/beer
├── cmd-tree-material/beer/blonde-ale.md
├── cmd-tree-material/beer/ipa.md
└── cmd-tree-material/beer/stout.md

0 directories, 3 files
```

### Just show me directories


Screw the files, just me show the directories. Hello `-d` option.

```shell
tree -d ./cmd-tree-material'
```

Output:

```shell
cmd-tree-material
├── baked-goods
│   ├── cakes
│   └── cookies
└── beer

4 directories
```

### Output tree in JSON

Yep, that's easy too

```shell
tree -J ./cmd-tree-material/
```

Output:

```json
[
   {
      "type":"directory",
      "name":"cmd-tree-material",
      "contents":[
         {
            "type":"directory",
            "name":"baked-goods",
            "contents":[
               {
                  "type":"directory",
                  "name":"cakes",
                  "contents":[
                     {
                        "type":"file",
                        "name":"carrot.md"
                     },
                     {
                        "type":"file",
                        "name":"chocolate.md"
                     }
                  ]
               },
               {
                  "type":"directory",
                  "name":"cookies",
                  "contents":[
                     {
                        "type":"file",
                        "name":"chocolate-chip.md"
                     },
                     {
                        "type":"file",
                        "name":"sugar.md"
                     }
                  ]
               }
            ]
         },
         {
            "type":"directory",
            "name":"beer",
            "contents":[
               {
                  "type":"file",
                  "name":"blonde-ale.md"
               },
               {
                  "type":"file",
                  "name":"ipa.md"
               },
               {
                  "type":"file",
                  "name":"stout.md"
               }
            ]
         }
      ]
   },
   {
      "type":"report",
      "directories":4,
      "files":7
   }
]
```

And don't forget, you can also add the other `options` to get additional information

```shell
tree -JDf ./cmd-tree-material/beer
```

Output:

```shell
[
   {
      "type":"directory",
      "name":"cmd-tree-material/beer",
      "contents":[
         {
            "type":"file",
            "name":"cmd-tree-material/beer/blonde-ale.md",
            "time":"Oct 31 18:06"
         },
         {
            "type":"file",
            "name":"cmd-tree-material/beer/ipa.md",
            "time":"Oct 31 18:06"
         },
         {
            "type":"file",
            "name":"cmd-tree-material/beer/stout.md",
            "time":"Oct 31 18:06"
         }
      ]
   },
   {
      "type":"report",
      "directories":0,
      "files":3
   }
]
```
### More output formats

Add the `-C` flag to get colors to make output nice and pretty

```shell
tree -C md-tree-material/
```

Use the `-H` option to output the contents in `HTML`

```shell
tree -H ./cmd-tree-material/baked-goods/cookies
```

Include hidden files in your results by adding the `-a` option

```shell
tree -a ./cmd-tree-material/beer/blonde-ale.md
```
