---
title: "Newbie questions"
date: 2009-05-24
forum: General Help
---

### Post by nietzschez on 2009-05-24
Hi,
I'm a new guy here, so I'll just say it.
I got the Ubuntu CD 2 days ago, tried it, installed it and liked it. This system boots in less than 8 seconds! XP was like, 5 minutes...
All the controls are pretty obvious.
Now, these are my questions.
1) Is there a full, detailed list of all the Terminal commands with descriptions somewhere?
2) How can I input other languages? I am Chinese and I need to write to my family in Chinese.
3) Is it possible to make a tarball into a .deb file?
4) Are there any antivirus programs / firewalls for Ubuntu?
5) With this being an entirely free system, where do the developers get their money? Also, why isn't Windows eradicated by Linux?
Thanks!

---

### Post by Girl™ on 2009-05-24
> **nietzschez said:**
> 
1) Is there a full, detailed list of all the Terminal commands with descriptions somewhere?


Here is a list of all (at least almost) terminal commands, or so called bash commands: [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

> **nietzschez said:**
> 
3) Is it possible to make a tarball into a .deb file?


The short answer here is yes. Are you looking for a way to make an official ubuntu package or just a quick-and-dirty way of making a .deb out of a tarball?

> **nietzschez said:**
> 
4) Are there any antivirus programs / firewalls for Ubuntu?


You can take a closer look at ClamAV and Shorewall. I've only used ClamAV myself, though.

---

### Post by madmaxou on 2009-05-24
2) System-> preferences -> Keyboard -> Add; then you'll see

---

### Post by Super TWiT on 2009-05-24
Clam av and such detect windows viruses. Viruses aren't normally written for the linux platform, as it doesn't control much market share.  As far as a firewall, I believe Linux (atleast Ubuntu) comes with one. You shouldn't really need any extra security software.  The developers, aren't normally paid except if developing software for commercial linux distros.  This code may or may not be contributed as open source.  Sometimes however, bounties are put on certain bugs.  Windows isn't eradicated by linux because most people are fine with what's on their machine in the first place. They may not even know Linux exists!

---

### Post by nietzschez on 2009-05-24
So if the developers are not paid, why is Linux developed?

---

### Post by Super TWiT on 2009-05-24
I guess people do things out of the goodness of their heart. Linux started out as a hobby project, and a lot has streamed out of it. Many people do things for the good of the community and open source movement. I tend to think of open source people as kind of the hippies of the 21st century (no offense to anyone)

---

### Post by clhsharky on 2009-05-24
None taken.

---

### Post by nietzschez on 2009-05-24
Oh, and another question...hope I'm not bugging too much.
Using FireFox (came with the OS), videos were played by Swfdec 0.8.2. They actually will never play, just a spinner spinning in the middle of the screen. I disabled it via the plugin manager and installed Adobe Flash Player 10. Now videos can actually play, but are quite choppy; flash-based games, too, are sluggish. There's nothing wrong with my internet and this did not happen back in XP (when I was also using FireFox). Why is this happening?

---

### Post by fillintheblanks on 2009-05-24
if possible update graphics card driver and disable sync to Vblank. 

should fix with the choppy video

---

### Post by Aped on 2009-05-24
> **fillintheblanks said:**
> if possible update graphics card driver and disable sync to Vblank. 

should fix with the choppy video

haha helpful, "disable sync to Vblank" - don't worry, it's intuitive!

If you're looking for this option, I believe it can be found under System -> Preferences (maybe Administration?) -> "Nvidia Xserver Settings" and there should be a tab called "xserver xvid settings" or something - sorry about lack of specifics, no nvidia on this laptop to verify - and here you can tick or untick the vblank option. 

Lot of other stuff can be done to improve video card performance in ubuntu, which comes packaged to 'just work' and not 'squeeze every ounce of GPU power from your machine' - but the ability to do so is there. 

There's another subforum for that though ;) good luck.

---

### Post by miegiel on 2009-05-24
> **nietzschez said:**
> Oh, and another question...hope I'm not bugging too much.
Using FireFox (came with the OS), videos were played by Swfdec 0.8.2. They actually will never play, just a spinner spinning in the middle of the screen. I disabled it via the plugin manager and installed Adobe Flash Player 10. Now videos can actually play, but are quite choppy; flash-based games, too, are sluggish. There's nothing wrong with my internet and this did not happen back in XP (when I was also using FireFox). Why is this happening?

If you're using 64bit ubuntu try the 64bit flash player, it's still in the alpha phase but it works fine for me. The "normal" flash player is 32bit and on 64bit ubuntu runs in a 32bit emulation, this has a bad effect on the player's performance


see more : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by nietzschez on 2009-05-25
nVidia? I have an Intel 945GM chipset...
I actually never game with it, just some occasional flash games...
Thanks, still.

---

### Post by miegiel on 2009-05-25
> **nietzschez said:**
> nVidia? I have an Intel 945GM chipset...
I actually never game with it, just some occasional flash games...
Thanks, still.

In that case check the forums for problems with intel graphics in jaunty. A lot of people are having problems with that combination. Some people could fix it, while others neded to install ubuntu 8.10.

---

