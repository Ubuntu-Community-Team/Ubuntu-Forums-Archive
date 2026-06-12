---
title: "will a better graphics card speed up ubuntu/gnome?"
date: 2006-03-22
forum: Desktop Environments
---

### Post by techrush on 2006-03-22
i currently have a slightly older pc which ive installed ubuntu 5.10 onto successfully. everything works great! the specs of the machine are as follows:

celeron 1.3ghz 256k onboard cache
512mb ram 
SiS 6329 crap pci vga adapter or "video card"  :)

the box has no AGP slot so i ordered a cheap nvidia pci card for it (EVGA MX4000 PCI). im wondering if it will improve the following aspects of the ubuntu/gnome experience:

 its very slow and choppy while minimizing and maximizing windows. it seems like it struggles to "draw" the black outline fade out thingy on minimizing and takes a second or two to "redraw" the contents of the screen when i maximize a window.

resizing and moving windows is very cumbersome because of how choppy it is.

opinions on if you think the new video card i ordered will help out are appreciated.
was also considering doing a dist-upgrade to dapper to give XGL/compiz a try if you guys think the system could run it. thanks!

---

### Post by OffHand on 2006-03-22
I have the exact same machine with a GeForce FX 5200 VS and I don't experience the problems you have.

What are the specs of your new card?

---

### Post by dragonfyre13 on 2006-03-22
The MX4000 is a decent card for the specs you have. However, I would look at repartitioning, and installing dapper all by it's lonesome. dist-Upgrades are only for when you are sure, since you can never go back.

Dapper is also still in testing, and has quite a few bugs. You could easyly screw things up if you are not careful with it.

As for video card speeding things up, absolutely. Gnome/KDE live on video cards. not to the extent that windows does, but much more so than XFCE, or the terminal. The issues you are having are mainly from lack of video memory it sounds like. Just make sure you install the drivers for the card as suggested here on the forums.

---

### Post by az on 2006-03-22
[QUOTE=techrush]
 its very slow and choppy while minimizing and maximizing windows. it seems like it struggles to "draw" the black outline fade out thingy on minimizing and takes a second or two to "redraw" the contents of the screen when i maximize a window.

resizing and moving windows is very cumbersome because of how choppy it is.

opinions on if you think the new video card i ordered will help out are appreciated.^[QUOTE]

A better graphics card will not improve your desktop responsiveness. It's all 2D and your card can either handle the resolution or not.  

There must be a reason why this is so choppy.  You have a decent processor and ram.  Are you short on disk space (like 90 percent full?)  Can you find out if you have dma enabled on your hard drive?

I run Ubuntu on a 500MHz pIII with 256 megs of ram and don't suffer the pain you are describing....

---

### Post by techrush on 2006-03-22
i do have dma enabled on my HD and it is no where near being full its about %75 free in fact. im also confused by the two contridicting responses heheh. geuss i will just have to try it out and see ?

---

### Post by Deepsyx on 2006-03-22
there is a possibility that the CPU may have been taxed/loaded when you were trying to open/close windows. that would definately cause things to be choppy. I doubt that it would be the case as your specs are decent. It very well could be Bugs/Glitches that are still trying to be worked out. Or, in fact if you had a 3d application running and were closing other 2D apps that may cause it as well as the 3D app will be using your Video Ram which is very limited with your present card .

Just a few options,

~D~

P.S. Definately upgrading Hardware is a good thing (BUT) not always necessary and may not fix the problem if the wrong hardware is being upgraded.

---

### Post by NeghVar on 2006-03-22
I have a "relativly" similar system with a duron 1.3 Ghz and the agp mx4000 and have had no problems at all with it. same ram, and my hd is still more than half empty.

---

### Post by adamkane on 2006-03-23
Gnome uses poor memory management, and it makes everything sluggish on machines like yours (mine):

Kubuntu and Xubuntu are faster, if you don't make any significant changes to the desktop like adding file previewing and fancy eyecandy.

The way to speed up Gnome is to turn off some services and tweak disc performance:
[http://www.ubuntuforums.org/showthread.php?t=89491]("http://www.ubuntuforums.org/showthread.php?t=89491")

My personal experience was that I had to keep the hotplug service enabled, and I also kept a few other favorite services enabled like CUPS. It was a huge improvement though. I can run amaroK in the background with almost no problem.

---

### Post by MichaelZ on 2006-03-23
[quote=adamkane]Gnome uses poor memory management, and it makes everything sluggish on machines like yours (mine):

Kubuntu and Xubuntu are faster, if you don't make any significant changes to the desktop like adding file previewing and fancy eyecandy.
[/quote] 
Are you sure that kde (kubuntu) is faster than gnome :???:. AFAIK it is the opposite.

Best wishes,
Michael

---

### Post by adamkane on 2006-03-23
[quote=MichaelZ]Are you sure that kde (kubuntu) is faster than gnome :???:. AFAIK it is the opposite.

Best wishes,
Michael[/quote]

Kubuntu has more eyecandy, so it should be slower, but I've confirmed with other posts that a fresh Kubuntu install is faster. Just my experience. I haven't seen anyone do a comparative benchmark yet.

---

### Post by MichaelZ on 2006-03-23
[quote=adamkane]Kubuntu has more eyecandy, so it should be slower, but I've confirmed with other posts that a fresh Kubuntu install is faster. Just my experience. I haven't seen anyone do a comparative benchmark yet.[/quote] 
Hello,

Sometimes ago I have found this post which is interesting:

[http://www.ubuntuforums.org/showthread.php?t=142147]("http://www.ubuntuforums.org/showthread.php?t=142147")

Personally, I use gnome in my Pentium III 500 MHz (516 MB RAM), because it seems to work faster and without font problems.

Anyway, I also appreciate kde and use it sometimes.

Best wishes,
Michael

---

### Post by techrush on 2006-03-23
i got the gefore mx4000 from UPS today installed it and............
everything is MUCH MUCH better its almost as quick as my 3ghz penitum 4 laptop.


i think i might try out the xgl/compiz stuff since this is just a box i have to mess around with anyways. :)

---

### Post by akiro.yamamoto on 2006-03-24
People tend to forget that a built in card not only uses a part of main memory but
shares the entire system as well including the CPU. You have to take into consideration how much of Main memory is being allocated to the video card.
A seperate Video Card relieves the system of all those calculations needed to
enable 2D rendering as well as relieves the need to use the MCC to access a time
share of main memory.

---

