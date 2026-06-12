---
title: "get two files when using bchunk to convert bin/cue to iso"
date: 2009-03-03
forum: General Help
---

### Post by shva on 2009-03-03
I have a bin/cue image. It was originally a VCD disc. Now I want to convert it into iso format. I use bchunk, but after I type:

bchunk -v vcd.bin vcd.cue vcd

it just gives me two iso files instead of one. One file is only less than 1M but the other is around 700M. I then try bin2iso, but it just stops at 200M. How can I get one iso image instead of two by using bchunk? Thank you a lot~! The content of cue file is:

FILE "vcd.bin" BINARY

  TRACK 01 MODE2/2352

    INDEX 01 00:00:00

  TRACK 02 MODE2/2352

    INDEX 00 00:04:00

    INDEX 01 00:06:00

---

### Post by Perducci on 2009-06-07
A while ago, I know, but in case you never got to the bottom of this, I found your question while searching for the same answer ;)

I also found [this page]("http://answers.yahoo.com/question/index?qid=20080717035940AADgCxj") that basically points out that a very simple ".cue" file will generate an accessible ISO file.  So create your own, e.g.:

```

FILE "your-bin-file.bin" BINARY
  TRACK 01 MODE2/2352
    INDEX 01 00:00:00

```I still haven't worked out why so many of these cue files have these extra entries, but I'm guessing that if you use CD burning software (like Nero) it has the smarts to interpret these correctly, whereas bchunk takes a pretty simple approach, hence the need for the tweak (if that makes any sense).

Be interested to know if you came to any (other) conclusions yourself.

---

