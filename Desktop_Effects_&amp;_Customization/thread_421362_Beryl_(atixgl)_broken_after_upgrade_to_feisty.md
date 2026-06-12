---
title: "Beryl (ati/xgl) broken after upgrade to feisty"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by mwob on 2007-04-24
Hi,

I'm sure I'm not the only one in this position - hopefully someone can shed some light on this

Scenario: I had Beryl working perfectly in Edgy - XGL / ATI card, using the instructions in the beryl wiki.
Now I have upgraded to Feisty (rather than a fresh install), Beryl doesn't work any more. During the upgrade Beryl-manager was removed. I have tried to add it again, using Trevino's tuxfamily repository, but it doesn't work when I try to start it, I get a eror saying "Failed to manage screen 0".

I know there are "howto's" dotted around for feisty/beryl/ati, but I'm confused as to which one I should use for my situation... 

Please can anyone help?

Thanks

Matt

---

### Post by mts-fi on 2007-04-24
Hi mwob!

I had similar problem ("Failed to manage screen 0") with my nvidia card, the GLX-thing didn't work. I got it working by reinstalling latest nvidia drivers. Envy doesn't work with Feisty but I found the latest nvidia driver in synaptic.

I cant't help you with Beryl-manager, sorry!

---

### Post by greymongrey on 2007-04-24
Envy worked fine on Feisty for me. I just had to run it twice.

---

### Post by mwob on 2007-04-24
Thanks all. I don't think its the gfx drivers (I'm ATI not nvidea), although its hard to say for sure. I'll try messing about some more and see what I can find out

---

### Post by mwob on 2007-04-24
Hi all,

Its not having it :( Feisty and beryl just don't seem to want to work on an ATI card!

I tried using AIGLX instead, as documented here : [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
But that just doesn't work, no errors but I don't get any effects and no window decorators. I have a rv350 based card though so its not classed as one that will definately work.

In XGL, it just moans about failing to manage screen 0!

It worked fine in Edgy!!! Grrr :(

---

### Post by edfromballarat on 2007-04-24
Yeah, I have Radeon 9600, Beryl was working well with Edgy then when I upgraded I got the same problem.  Another instance of being a second class ATI graphics card citizen!

Going back to life without Beryl is like going back to radio from TV!

Incidently, while trying to fix it when I log into Xgl session it goes straight to a gnome session.  When I start Xgl from the command line a get a black screen and can't ctrl+altFx or restart the window manager.  If any body could help (have  I broken gdm.conf or xorg.conf?) that would be greatly appreciated.

---

### Post by mwob on 2007-04-25
I'm very close to selling my ATI card on ebay and getting a nvidea! Especially since I saw my mates similar spe'd PC with an nvidea running beryl really quickly!

can anyone help?!

---

### Post by mwob on 2007-04-25
Aha! Sorted it :)

I'll create a "howto" and post anyone interested to it!

---

### Post by cornish on 2007-04-25
Yes please mate

---

### Post by mwob on 2007-04-25
OK, heres what I did to fix:

First I removed all the existing Beryl related stuff I had left fro my edgy installation (I did this with "sudo apt-get remove beryl"). Once this was done I removed the beryl repo's I had in my sources.list file from edgy (although they should be commented out during the upgrade).

Once done, I followed this guide here: [http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

It all works fine now, Beryl is happy and working just like it was in edgy.

---

### Post by all2ez on 2007-05-05
I got beryl in feisty working on my laptop. I have a thinkpad T60 with ATI Radeon Mobility X1400. I have a triple boot system with XP, Vista and Feisty... I had Edgy and beryl working, then I upgraded to Feisty and beryl was still starting when I logged in, but it wasn't working.

The link posted by mwob seems to be for a specific compyter, so I didn't really want to try it.  But I followed the advice about removing beryl, except I just went into System>Administration>Synaptic Package Manager.  I searched for beryl and marked everything that was installed for complete removal.

After that, I basically followed the guide here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

and it works!!!

It seems the key was editing the startxgl.sh that I already had. Also I had to disable the universe repository and add the correct repository to install beryl from (deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main). Oh and the ATI restricted driver has to be checked enabled.

Hope this helps!

:guitar:

---

