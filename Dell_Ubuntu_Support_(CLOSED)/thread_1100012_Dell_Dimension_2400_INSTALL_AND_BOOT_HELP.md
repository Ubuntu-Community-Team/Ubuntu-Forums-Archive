---
title: "Dell Dimension 2400 INSTALL AND BOOT HELP"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by terrorhawk on 2009-03-18
Okay... problem.

I'm a novice, at best, with this Ubuntu thing. By novice I mean I've managed to get used to the workings of Linux by doing the user-friendly thing. I'm no pro - and I rarely ever open Terminal.

That being said, I'm confused by something that I've never seen before... literally.

A while back I had installed Ubuntu (Hardy Heron) on this Dell Dimension 2400, but deleted the partition a while ago because I didn't feel it was right with this slower computer... then I upgraded the computer with some nicer things. Right now I've got Windows XP with SP3. I downloaded the WUBI Installer after I'd decided to try Ubuntu again, this time with Intrepid Ibex...

I go to install it, and all goes well - after the nearly hour and 20 minutes it took for the installer to get everything set up - and then at the boot screen (with that bongo tapping noise, to tell you to sign in) I wrote my name correctly, typed my password correctly and then... NOTHING.

I wait around for maybe 2 minutes, cause the screen seemed to have blacked out but then it comes back and I see nothing but my mouse. No menu bar, no desktop, no anything. I even heard that weird Ubuntu chant thing when the OS loads fully and everything is supposed to show.

So my question is: who can help me diagnose this? I know there are very experienced users, and I'm willing to give it another go because to me, Ubuntu is a great distro for beginner-level folks like me that're new to Linux.

I've uninstalled it again because if someone can help me, I'll start fresh going by their directions.

Is it maybe a bad video driver? If so, why can I see my mouse but not my desktop and everything? I have an integrated Intel 82845G graphics controller, and like I said, a while back with Hardy Heron everything worked and showed up perfectly.

Here's some specs for those that may be able to help:

Dell Dimension 2400 Desktop
Intel Pentium 4 @ 2.8GHz
Windows XP Home Edition (SP3)
1.25GB DDR RAM
40GB IDE Hard Drive
Intel 82845G/GL/GE/PE/GV Graphics Controller

---

### Post by ugm6hr on 2009-03-18
When you see the mouse pointer, is the background brown?

---

### Post by terrorhawk on 2009-03-18
> **ugm6hr said:**
> When you see the mouse pointer, is the background brown?



No, it's actually just black. The only way I can explain it is that at the bongo noise (typing your username and password) I can see the brown Ubuntu stuff and the login and all that, and then I hit Enter after I sign in.

The screen looks faded black (as if your screensaver with no logo were on, ya know?) and then it seems to like... turn off (dark black)... then it's back on but still that faded black-ish screen but I can see and move my mouse around.

---

### Post by ugm6hr on 2009-03-18
Hmmm...

That means it is unlikely to be a RAM issue (and you have more than 1GB, which would be bizarre).

Boot into the Recovery Terminal, and remove compiz, then reboot and try that.

```
apt-get remove compiz-core
```

EDIT: I suspect this is in fact the problem:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833)

---

### Post by terrorhawk on 2009-03-18
> **ugm6hr said:**
> Hmmm...

That means it is unlikely to be a RAM issue (and you have more than 1GB, which would be bizarre).

Boot into the Recovery Terminal, and remove compiz, then reboot and try that.

```
apt-get remove compiz-core
```

EDIT: I suspect this is in fact the problem:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833)



I'll have to re-install Ubuntu yet again. I uninstalled it after a few failed attempts at this, and plus I don't really know how to do the boot option thing like in Windows (where on my Dell I hit F2 and F12 for Boot Options, Help, etc)

Should I likely give that a go?

I need to know how to do that, btw... I dont know how to boot into the Recovery Terminal

---

### Post by ugm6hr on 2009-03-18
I have never installed with Wubi, so I am not 100% certain how the boot manager works.

Even if you can't get into recovery terminal, you can just press Ctrl+Alt+F1 from the login screen, and then login as yourself from Terminal.

Then add **sudo** to the start of the command given, and it should have the same effect.

Exit with:
```
sudo shutdown -r
```

---

### Post by terrorhawk on 2009-03-18
> **ugm6hr said:**
> I have never installed with Wubi, so I am not 100% certain how the boot manager works.

Even if you can't get into recovery terminal, you can just press Ctrl+Alt+F1 from the login screen, and then login as yourself from Terminal.

Then add **sudo** to the start of the command given, and it should have the same effect.

Exit with:
```
sudo shutdown -r
```



So then you're saying I oughtta re-install Ubuntu, go through the Setup as usual and then try to log in through Terminal? If that works, does that mean something's wrong and I'll have to do that EVERY time til that is fixed?

Should I try another distro like Xu- or Kubuntu? Would that have anything to do with it?

---

### Post by ugm6hr on 2009-03-18
> **terrorhawk said:**
> So then you're saying I oughtta re-install Ubuntu, go through the Setup as usual and then try to log in through Terminal? If that works, does that mean something's wrong and I'll have to do that EVERY time til that is fixed?

Should I try another distro like Xu- or Kubuntu? Would that have anything to do with it?

No.  It looks like it is a problem with Compiz.  All the standard -buntus default with Compiz enabled.

If you remove it, the next (and subsequent) reboots should work fine (assuming I am right about Compiz being the problem).

---

### Post by terrorhawk on 2009-03-18
> **ugm6hr said:**
> No.  It looks like it is a problem with Compiz.  All the standard -buntus default with Compiz enabled.

If you remove it, the next (and subsequent) reboots should work fine (assuming I am right about Compiz being the problem).



Okay I'm gonna give it a go, after I re-download and install. I'm going to try Kubuntu this time, cause I've wanted to try out the KDE interface a long time anyway.

After I disable it though through the Terminal, and log in - if this all works, that is - will I be able to re-install Compiz and what not so that I can have the desktop effects, etc? I assume that's what it does by default (not Fusion effects).

---

### Post by abn91c on 2009-03-18
your dell has as intel845 video card, Compiz will not work in Ubuntu 8.10 only solution is ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```
or install a separate PCI video card.

---

### Post by ugm6hr on 2009-03-18
> **terrorhawk said:**
> will I be able to re-install Compiz and what not so that I can have the desktop effects, etc? I assume that's what it does by default (not Fusion effects).

Maybe?  But it doesn't look that hopeful.

An apparent solution:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8)

---

### Post by terrorhawk on 2009-03-18
> **abn91c said:**
> your dell has as intel845 video card, Compiz will not work in Ubuntu 8.10 only solution is ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```
or install a separate PCI video card.



Damn... that's not good news. Is it simply cause it's just an older computer and there's no need to really keep up with that stuff?

I don't get why Hardy Heron worked but not Intrepid Ibex... hmm.

I'll remove the compiz thing, though... hopefully that'll work.

---

### Post by abn91c on 2009-03-18
> **terrorhawk said:**
> Damn... that's not good news. Is it simply cause it's just an older computer and there's no need to really keep up with that stuff?

I don't get why Hardy Heron worked but not Intrepid Ibex... hmm.

I'll remove the compiz thing, though... hopefully that'll work.
if you want compiz it will work with 8.04 normally, it is just ubuntu 8.10 that has some as of yet unresolved Bug in the driver for i845 cards and removing compiz will let you in the OS. With Kubuntu you can get some eye candy.

---

### Post by abn91c on 2009-03-18
By the way  I have a Dell 2400 also, max out the RAM for some serious Speed!!

---

### Post by Brixton on 2009-04-27
I can testify that the sudo removal of compiz does the trick.

 I have a Dell 2400 with an upgraded 1 gig of RAM from the 512mb shipped stock. I got fed up with the integrated graphics compiz bug, so I inserted a PNY GeForce 8400 GS 512MB video card that I got for $50. I know that is gross overkill, but I can run Steam and Half-Life 2 and related Source engine games like Team Fortress 2 at 35 FPS at 1650x1080 at full graphics on  my Windows XP partition. Previously, those games would not run at all higher than 20 fps on low.

On Ubuntu 9.04, I have no issues graphically anymore. Compiz is not an issue, and for $50, (price of card) I got a brand new computer in my opinion. I generally never leave Ubuntu unless I want to hop on Steam.

Other thoughts, PCI cards are really, really cheap now. Any PCI card will get you around this boot up bug. Just make sure you disable the integrated chip in Windows when you're using XP.

Also, Ubuntu auto detects the drivers needed for the card I listed, works perfectly.

---

### Post by billyboy1995 on 2009-06-20
i have not added any changes to my 2400 and i can run 9.04 "out of the box" with no problems other than speed.

---

