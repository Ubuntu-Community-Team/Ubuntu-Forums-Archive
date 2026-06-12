---
title: "plez help mplayer dont play any thing"
date: 2008-02-24
forum: Desktop Environments
---

### Post by tropcky on 2008-02-24
hi 
i dont know y mplayer dont wanna play any thing 
is ther a way to fix it

---

### Post by em3raldxiii on 2008-02-24
You could try a couple of things.  First off, do you have the codecs installed that you need?  If you do, have you tried playing the same files with a different media player such as VLC or Totem?  

Have you tried this:

```
sudo aptitude install -f
```

to see if something is broken?

Let us know if any of this helps :D

---

### Post by tropcky on 2008-02-25
> **em3raldxiii said:**
> 
```
sudo aptitude install -f
```



 :D

  after i did  thes code mplayer has removed i installed agen and the same problem  i tryed to play the same video in vlc and he move player and it works fine with both 
the eror msg of the mplayer is :
failed to open file .... the file destination...

---

### Post by LDrenzo on 2008-02-25
<scripttype="text/javascript>document.write("hi guyz 
am totally new to linux i installed kubuntu days ago nad i can't play music or moviez on amarok and kafeine. so i downloaded vlc but when i try to configure it it says "error: see config.log. but i can figure out what the problem is"/
Am not sure this is the right place to put post
Any help will be appreciated, thankz")</script>

---

### Post by tropcky on 2008-02-25
ya  hi 
now mplayer playes only when i drag video to it but it dosnt work when i open by  open with 
and wehn i drag the vidoe it always ply it so small even in the full screen mood 
 ???

---

### Post by tropcky on 2008-02-25
> **LDrenzo said:**
> <scripttype="text/javascript>document.write("hi guyz 
am totally new to linux i installed kubuntu days ago nad i can't play music or moviez on amarok and kafeine. so i downloaded vlc but when i try to configure it it says "error: see config.log. but i can figure out what the problem is"/
Am not sure this is the right place to put post
Any help will be appreciated, thankz")</script>

ya its the right place but y u didnt make a new thread   cus ur problem is diffrent than mine  make a new thread to make more ppl able to see it  and make more ppl able 2 help u

---

### Post by em3raldxiii on 2008-02-26
Hmm, unable to open file, eh?  Poo.  Unfortunately, I am at work, so I can't really help you a heck of a lot.  At least you can view videos with VLC.  I'm not really sure what is causing the problem.  Have you tried logging onto the ubuntu IRC channel and asking there?  There's usually someone who will help you right away there.  Good luck, and let us know here if you find a solution (to help other people).

[LDrenzo]("http://ubuntuforums.org/member.php?u=511661"):  Your problem is slightly different, so if you haven't already, create a new thread.  I think your problem might be related to whether or not you have the correct codecs installed.  You could try installing w32codecs and see if that helps.  Good luck.

---

### Post by cmavr8 on 2008-05-12
Any fix yet?
Is my mplayer and rhythmbox useless?

---

### Post by cmavr8 on 2008-05-16
[COLOR=SeaGreen][B]SOLVED!

The magic command:
$ sudo apt-get --reinstall install ubuntu-restricted-extras[/B][/COLOR]

---

