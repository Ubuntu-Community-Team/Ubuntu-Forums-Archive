---
title: "Video card not working after update"
date: 2009-04-28
forum: Desktop Environments
---

### Post by sn0m on 2009-04-28
Hi guys, I updated today to Jaunty from Intrepid and to my surprise the video card cannot enable desktop effect, so I can't get my beloved AWN working.
I have a dell inspiron 1525 and the video card is Intel Corporation Mobile GM965.
Does any of you have the same experience and how did you sort it out, ?:( downgrade....
Thanks in advance
Sokol

---

### Post by Roger E Critchlow Jr on 2009-04-28
Yes, there was a Jaunty testing thread about problems with intel video which recommended some fairly dire fixes.  I was just looking for it.  Here's a newer one:

  [http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

and here's the one I followed, using amd64 packages:

  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

It's not for the faint-hearted, stick with Hardy or Intrepid if you're not sure.

-- rec --

---

### Post by sn0m on 2009-04-29
I just find the whole thing quite bizarre. Is there a linux driver for Intel Corporation Mobile GM965 that I could try and install myself. I had a similar problem with an ATI driver a while ago and all I needed to do was install the driver from ati website rather then the one from Ubuntu repos and worked fine.
So if any of you knows the link to download the driver, please post it here and I will try and experimen with it. It so frustrating as I was looking forward to ext4 file system and need to downgrade now..

---

### Post by sn0m on 2009-04-29
This is what I found from Amaranth

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
I'll try it and keep you guys posted.
Ta Sokol

---

### Post by sn0m on 2009-04-29
Can someone help me out here:
this is what i get from my output
sn0m@sn0m-laptop:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >>~/.config/compiz/compiz-manager
bash: /home/sn0m/.config/compiz/compiz-manager: Permission denied
sn0m@sn0m-laptop:~$ sudo mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >>~/.config/compiz/compiz-manager
[sudo] password for sn0m: 
bash: /home/sn0m/.config/compiz/compiz-manager: Permission denied
sn0m@sn0m-laptop:~$

---

