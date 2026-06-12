---
title: "Rhythmbox Crashing 0.11.2 Gusty"
date: 2007-12-01
forum: Desktop Environments
---

### Post by Ongaku86 on 2007-12-01
Hi, first time poster, long time looker 

I have Rhythmbox v. 0.11.2 and I have been having some odd problems as of late...I´m running on Gusty 

I can open one song and play it all the way through, but the minute  I either manually switch to a different song or let it switch itself, it completely freezes....it´s not the files, they are .mp3s...they work fine on my other Windows PC.

I put the gdb in pastebin here:

[http://pastebin.com/m4447cad1](http://pastebin.com/m4447cad1)

anyone know what´s going on?

---

### Post by Nano Geek on 2007-12-01
Firstly, Welcome to Ubuntu!
Can you run it in the terminal and tell us what it says?

---

### Post by Ongaku86 on 2007-12-01
I run it in the terminal, play a song until it ends...then when it switches to a new song, the program completely freezes and I have to force quit it or ctrl+c it...it doesn´t say I have to file a bug report or anything or say anything in the terminal.

---

### Post by Nano Geek on 2007-12-01
> **Ongaku86 said:**
> I run it in the terminal, play a song until it ends...then when it switches to a new song, the program completely freezes and I have to force quit it or ctrl+c it...it doesn´t say I have to file a bug report or anything or say anything in the terminal.But we might find something that would give us a hint as to what your problem is. If you don't mind, could you post what it says?

---

### Post by Ongaku86 on 2007-12-02
I´ve told you what the problem is...I play a song, if I either switch manually to a new song or let it select the next song or even hit next in the program, the program completely freezes and doesn´t do  anything and I have to force quit it....

now running it.....

:shock:

It works now...

So, If anyone else is having this problem, this may solve it.

I was on Xchat discussing this problem with the community and someone told me to find a verbose option in Rhythmbox. I didn´t know what it was really, but I looked for it and it is located here...

katy@ubuntu:~$ rhythmbox --help-gst
Usage:
  rhythmbox [OPTION...] [URI...]

GStreamer Options
  --gst-version                   Print the GStreamer version
  --gst-fatal-warnings            Make all warnings fatal
  --gst-debug-help                Print available debug categories and exit
  --gst-debug-level=LEVEL         Default debug level from 1 (only error) to 5 (anything) or 0 for no output
  --gst-debug=LIST                Comma-separated list of category_name:level pairs to set specific levels for the individual categories. Example: GST_AUTOPLUG:5,GST_ELEMENT_*:3
  --gst-debug-no-color            Disable colored debugging output
  --gst-debug-disable             Disable debugging
  --gst-plugin-spew               Enable verbose plugin loading diagnostics
  --gst-plugin-path=PATHS         Colon-separated paths containing plugins
  --gst-plugin-load=PLUGINS       Comma-separated list of plugins to preload in addition to the list stored in environment variable GST_PLUGIN_PATH
  --gst-disable-segtrap           Disable trapping of segmentation faults during plugin loading
  --gst-disable-registry-fork     Disable the use of fork() while scanning the registry

katy@ubuntu:~$ rhythmbox --gst-plugin-spew

I tried it after I did that and it still didn´t work...and I gave up for the night and just listened to CDs lol. But I started up my computer this morning, and did what you told me to do in the terminal, and it worked! I believe it was because I enabled the verbose plugin. I just forgot to restart :P

---

