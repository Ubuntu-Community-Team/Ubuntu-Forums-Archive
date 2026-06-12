---
title: "Trouble with installing"
date: 2008-12-31
forum: General Help
---

### Post by froggyone on 2008-12-31
Hello,

This is the first time I am trying a Linux OS with no luck. I can install Ubuntu just fine in seems, I am able to get the Ubuntu logo and the progress bar under it, but after that all I seem to get is a command line. I have read a few post, tried typing startx, but it tells me that it cannot find any screens. I am lost any help would be great.
Thanks

My system:

Motherboard:Biostar TPower Nvidia NForce 750a SLI
CPU: AMD Phenom 9950 Quad-Core @ 2.6 
Memory: 2, 2 gigs sticks OCZ (DDR2 800) 
Video: 2, Nvidia GeForce 8600 GT setup for SLI
DVD Burner: Pioneer DVD-RW
Hard Drive: WD 500 gigs

---

### Post by SonnHalter on 2008-12-31
I had that problem. It wouldn't stop until i switched my connection to a VGA cord and not the DVI that i was using. maybe you can try other connections?

---

### Post by froggyone on 2008-12-31
Thanks for the input but that did not work.

thanks

---

### Post by bradthewanderer on 2008-12-31
Did you try the Live CD first, this allows you to see how your system works with it first before you install.

---

### Post by froggyone on 2008-12-31
I did not try the live CD first but later I gave it a go and nothing still gave me a command line

---

### Post by donkyhotay on 2008-12-31
Sounds like it's a graphics card problem. Whats the contents of your /etc/X11/xorg.conf file?

---

### Post by froggyone on 2008-12-31
how would I list the contents of that file, please keep in mind that I am really new at this so it is ok to talk to me like I was 5 years old.... minus the baby talk :D

---

### Post by An6oon on 2008-12-31
Hey guys,
I am having the same problem as well. Every time I try to install Ubuntu or run it live, I get a gray flashy screen until I restart my system. Can anyone please help.

My system:

Asus M50sa
CPU: Intel(R) Core(TM)2 Duo CPU T9300 @ 2.5 
Memory(RAM): 4 GB 
Video: ATI Radeon HD 3650 Graphics
System Type: 64-bit Operating System
Hard Drive: WD 500 gigs

---

### Post by donkyhotay on 2008-12-31
> **froggyone said:**
> how would I list the contents of that file, please keep in mind that I am really new at this so it is ok to talk to me like I was 5 years old.... minus the baby talk :D

Sorry, sometimes it's hard to tell what people do/don't know. 
```
less /etc/X11/xorg.conf
```
will display the file for you. When your done looking at it just press 'q' to get back to the command prompt.

---

### Post by froggyone on 2008-12-31
> **donkyhotay said:**
> Sorry, sometimes it's hard to tell what people do/don't know. 
```
less /etc/X11/xorg.conf
```
will display the file for you. When your done looking at it just press 'q' to get back to the command prompt.


from what I can tell there is nothing their, it is telling me about editing files and automatic updates. Then it goes on with this at the bottom

[B][I]Section "Device"
         Identifer      "Configured Video Device"
EndSection

Section "Monitor"
:[/I][/B]

---

### Post by froggyone on 2008-12-31
I also forgot to add when I type startx this comes up

xinit: Connection refused (errno 111): unable to connect to X Server

xinit: No such process (errno 3): server error

---

### Post by froggyone on 2008-12-31
> **froggyone said:**
> from what I can tell there is nothing their, it is telling me about editing files and automatic updates. Then it goes on with this at the bottom

[B][I]Section "Device"
         Identifer      "Configured Video Device"
EndSection

Section "Monitor"
:[/I][/B]



ok

---

### Post by froggyone on 2009-01-02
I would like to thank you for your help, but the battle has not been won. If you anymore ideas I am all ears.

---

### Post by donkyhotay on 2009-01-06
Try this:
```
sudo rm /tmp.x0-lock
```
and then try launching the X server after that. If that doesn't work it has to be a driver problem. In that case take a look at this howto
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

