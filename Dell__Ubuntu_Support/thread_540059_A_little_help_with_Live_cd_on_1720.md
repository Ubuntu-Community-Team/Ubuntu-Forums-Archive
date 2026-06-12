---
title: "A little help with Live cd on 1720?"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by Hope for Chaos on 2007-09-01
Hello all.  I'm trying to run the Live cd on my inspirion 1720 and have had some problems but I'm pretty sure I've figured it out I'm just not sure how to exactly do it.  I'm brand new to Linux/Ubuntu but am a cs major so I know some coding.  I think my problem is with the video card and all that.  I could just use some more detail on the third section of [this post]("http://ubuntuforums.org/showthread.php?t=512576&highlight=1720").  I get the F6 part and the modprobe piix ( do I literally enter 'exit' after that?) but changing the xorg.conf is something I'm not too sure on.  Thanks for any help!

---

### Post by AndyQ on 2007-09-01
after the modprobe piix entry
literally type 'exit' (no quotes) and press enter. this will continue the boot sequence up to starting X.

At this point, your screen will flash black, a few times and then you will get an error saying that X has failed to start. You can view the log files IF you really want however the reason is the drivers don't support your video card.

So, to temporarily fix this, select OK to all the messages and whe you get to a command prompt, type sudo vi /etc/X11/xorg.conf. (Make sure you read up on the basics of how to use vi!).

search for "nv" and replace it with "vesa".

Save and exit vi and then type startx 

This will start X and allow you to play around.

I would suggest that you play with the live CD for a while BEFORE installing Linux to get an understanding of how it works, an dalso, be prepared for lots of tweaking and searching too get everything working.

---

### Post by Hope for Chaos on 2007-09-01
Thanks a lot!  I've used vi very little but think I know how to save (:wq right?) and by search I think you mean find where "nv" occurs and replace that occurance with "vesa" right?  Running this off the live cd won't mess my computer up will it?  I don't think it can but man I'm a little uneasy.  I guess I will give this a try and see how it goes.  Thanks a lot for the help.

---

### Post by Hope for Chaos on 2007-09-01
Well it worked and wasn't nearly that bad.  I was a little scared just because the environment was really different.  I didn't say bad I just wasn't use to it plus I was worried I might mess something up. But the live cd wasn't nearly as slow as some gave the impression it might be.

I was just curious where to go from here.  I know that might sound like a very noob thing to say, but what is safe to explore and what should I look for in linux? Again thanks for your help.

Let me ask you one more thing.  Have you done anything with a second hard drive in the 1720.  That was my initial plan, to add a second hdd and install Ubuntu on that but after a little looking it looks like Dell doesn't like it and it can be a rather pain.  Just curious.  Thanks.

---

### Post by AndyQ on 2007-09-02
When using the live CD, you can pretty do anything you want (install lsoftware, muck with settings, etc), without it affecting anything, and when you reboot, it will be as if you hadn't done anything at all.

The only time you would affect something was if you mounted an existing partition and played around in that filesystem, or repartitioned your drives or something, but you have to explicitly do that.

As to where to start. The best place is to start up syaptic (the package manager), and spend a little time looking through the packages, installing stuff and having a little play. Then, either buy a good book on Linux (if you think you're going to use it and learn how to use it), or do some googling on linux and admnistration.

I've not even looked into the 2nd hard disk yet, and probably won't will use external disks if I need to expand disk space (so I can access them from other machines on my network).

---

### Post by thomasdersozpaed on 2007-09-26
Hello, 
thanks a lot for this help. But when I enter Vi and search for nv it tells me "E486: pattern not found: nv"   after the ....xorg.conf I tried following things:  :s/nv/vesa    this doesnt work, so I tried      /nv
It never found "nv" I have got an inspiron 1720 as well. What can I do?
Thanks for your help!

---

### Post by Aonxe on 2007-09-26
Did you get the Nvidia graphics card? If not look for something else.

---

### Post by thomasdersozpaed on 2007-09-26
I have the nvidia 8600 but no idea how to install. my post:

[http://ubuntuforums.org/showthread.php?p=3432235#post3432235](http://ubuntuforums.org/showthread.php?p=3432235#post3432235)

any idea?
thomas

---

