---
title: "CD Ripping HELP"
date: 2005-02-04
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-02-04
Okay so I want to make a Audio CD I drag and droped the files onto the window that poped up when I inserted a blank cd wrote to disk I put it in my cd player did not work. I try to use K3b but it does not let me burn audio cd's. Anyone have an idea I can borow? :confused:

---

### Post by ilari on 2005-02-04
First you have to convert mp-files to wav, and then you are able to copy them to an audio-CD. Both can be done from command line using ie. mpg123 and cdrecord. You can check [this site](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/MP3-CD-Burning.html#AUDIO)  for more details...

---

### Post by jdodson on 2005-02-04
[QUOTE=Chrisb319]Okay so I want to make a Audio CD I drag and droped the files onto the window that poped up when I inserted a blank cd wrote to disk I put it in my cd player did not work. I try to use K3b but it does not let me burn audio cd's. Anyone have an idea I can borow? :confused:[/QUOTE]

it looks like what you did (if you were using nautilus) was write a cd with your audio files on it.  this puts the files on the cd, however does not make it an audio cd, or a cd playable on most cd players(unless your cd player supports mp3s or oggs or flac).  

what you need to do is use k3b.  it is the best way to get an audio cd in warty(as far as i can tell).  you can install k3b from universe.  make sure when you run it to use "gksudo k3b" and enter your root password.  you need to do this because k3b is picky about somethings and this is a cheesy workaround to get it to run.  they might have some other more "gnomish" options for the next release of ubuntu, though k3b works really well for me, i have no complaints.

---

