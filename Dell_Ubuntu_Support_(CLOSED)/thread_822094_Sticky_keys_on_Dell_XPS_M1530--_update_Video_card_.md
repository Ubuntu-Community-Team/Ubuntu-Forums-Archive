---
title: "Sticky keys on Dell XPS M1530-- update Video card drivers??"
date: 2008-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stevieP on 2008-06-07
I have a Dell XPS M1530, running Ubuntu 7.10 - Gutsy Gibbon. 

I amm having a problem with sticky keys on my notebook computer, as you can see in this message whichh I've left unedited. I have called Dell custommer servvice and spoke with sommeone who insisted that the reason letters were being double-typed on my keyboard was that my graphics driver needed to be updated. He would not consider sending me a replacement keyboard because "I was not using the original operating system that the computer came with-- Windows Vista". He claimmed that he had seen this problemm resolved in the past by updatinngg the graphics card drivers. 

I have a 256MB NVIDIA GeForce 8600M GT Graphics card. 
I am currently running the open-source nv Driver. 
Here is the section inn my /etc/X11/xorg.conf file:

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nv"
	Busid		"PCI:1:0:0"
EndSection

So should I update the driver? and if so, to what? I've tried to update drivers before for this laptop to solve hibernation problems, but without success. I'm willinng to try again howevver because this repeatting key problem is driving me crazy. 

Any help or advice would be greatly appreciated,
StevieP

---

### Post by stevieP on 2008-06-08
Further to my question about whether this is a driver issue rather than a hardware (keyboard) issue: if this problem was due to the 'old' nv graphics driver, wouldn't all keys be equally likely to repeat? Why is it primarily the m's, n's, h's, g's that are repeating?

---

### Post by stevieP on 2008-06-13
Well I suppose I just tried the obvious thing which was to get another external keyboard, plug it in and try it. No repeating keys whatsoever. So I suppose this means it is not the graphics driver that is the problem?... seems that the keyboard that came with my laptop is defective.

---

### Post by zcwalker on 2009-04-04
Hi,
 Dont know if you ever got this probem sorted out ... but I have a M1530 and have keyboard problems too ... but mine are that some chars dont get typed when i am pressing the keys ... it started with the 's' key and has now moved on to other keys too.

 It seems to only happen when I type at full speed (I am an experienced user and type without looking at the keyboard however dont use all my fingers).

 I am running Windows Vista Enterprise with all updates on.

 Problem is that I bought the laptop in the UK and have now moved to Norway ... will see what the tec support say.

Ths is an exampl when i atypin at full seed.
This is an example when i am typing at full speed.

Odd !!

Chris

---

