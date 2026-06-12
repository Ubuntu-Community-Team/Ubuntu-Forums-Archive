---
title: "Desktop Effects don't work."
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by KingFoo on 2007-08-25
I went into System>Preferences>Desktop Effects.

[IMG]http://i137.photobucket.com/albums/q220/Shane_Orin_OConnor/Screenshot-DesktopEffects.png?t=1188088657[/IMG]

But when I click on the "Enable Desktop Effects" button I get this message.

[IMG]http://i137.photobucket.com/albums/q220/Shane_Orin_OConnor/Screenshot-desktop-effects.png?t=1188088306[/IMG]

That's the only message I get. It doesn't say why or how I can fix it.
I'm a new Linux user and don't know my way around the OS very well.
So if you know what might be the problem and will help me, then could you give me step by step dirrections? Thanks

---

### Post by ArtF10 on 2007-08-25
Post your system configuration, including graphic card.

---

### Post by KingFoo on 2007-08-25
Um... Ubuntu just crashed on me and I can't get back on... I was using wubi on my Compaq Desktop. I have 512mb of memory... I don't have a graphics card. :(

That's probally the problem. :|

I'll get one and see if it'll work. Anything that would work better than others? I'd like to use beryl also.

Oh yeah, my processor is AMD Athlon XP. I don't know if that helps.

---

### Post by psyopper on 2007-08-25
Again, post your system specs if you know them. Specifically does your computer/motherboard use PCI Express or AGP for video, and at what speed. 

Take a look at [www.tigerdirect.com](www.tigerdirect.com) for Nvidia 6200 series cards, they are in the $30 to $50 range and VERY capable of running Beryl/Compiz/Compiz-Fusion.

I will make one suggestion though - do NOT use Wubi for you Linux installation, especially your Ubuntu installation. A Wubi install takes as much space as a real Ubuntu install and it could very easily break either you Ubuntu install or your Windows install.

I would recommend installing Ubuntu directly into it's own partition.

---

### Post by ArtF10 on 2007-08-25
> **psyopper said:**
> ....I will make one suggestion though - do NOT use Wubi for you Linux installation, especially your Ubuntu installation. A Wubi install takes as much space as a real Ubuntu install and it could very easily break either you Ubuntu install or your Windows install.

I would recommend installing Ubuntu directly into it's own partition.

+1

Agreed with everything there.  Plus Wubi runs slower than the Live CD.

---

### Post by KingFoo on 2007-08-26
> **psyopper said:**
> Again, post your system specs if you know them. Specifically does your computer/motherboard use PCI Express or AGP for video, and at what speed. 

Take a look at [www.tigerdirect.com](www.tigerdirect.com) for Nvidia 6200 series cards, they are in the $30 to $50 range and VERY capable of running Beryl/Compiz/Compiz-Fusion.

I will make one suggestion though - do NOT use Wubi for you Linux installation, especially your Ubuntu installation. A Wubi install takes as much space as a real Ubuntu install and it could very easily break either you Ubuntu install or your Windows install.

I would recommend installing Ubuntu directly into it's own partition.

So can I install Ubuntu (or any version of linux) and still have my Windows XP OS?
Or do I have to chose Linux or Windows?


I do know that I have atleast one of my PCI and AGP slots open, maybe two. But I need help on how to find what the speed is.

---

### Post by Rupertronco on 2007-08-26
Yes, you can do what is called a dual boot. You can use a bootloader (grub) to give you the option of what operating system you will boot into.  

When did you get the motherboard? My guess would be the AGP is 4x or 8x (which is what i would recommend going with given the choice of AGP vs PCI)

---

### Post by KingFoo on 2007-08-26
> **Rupertronco said:**
> Yes, you can do what is called a dual boot. You can use a bootloader (grub) to give you the option of what operating system you will boot into.  

When did you get the motherboard? My guess would be the AGP is 4x or 8x (which is what i would recommend going with given the choice of AGP vs PCI)

I downloaded "grub-1.95", what do I do with it? Do I have to put it somewhere special? Or does it work automatically?

And how can I install Ubuntu using a dual boot?

I bought my PC about... maybe... 3-4 years ago...

---

### Post by ArtF10 on 2007-08-27
This might help(**[COLOR="Red"]DO THIS AT YOUR OWN RISK[/COLOR]**):
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

I'd recommend reading through ALL the instructions first and asking questions about something you don't understand.  Only then would I consider attempting anything.  And backup all important data BEFORE attempting anything.

---

### Post by pmkhoa on 2007-08-27
I have the same error that's desktop effect doesnot work, So I wonder, at the beginning I Install Ubuntu I run desktop effect very well, but after I installed some softwares such as SCIM, Xvnkb, the desktop effect no longer run, 

I did try to install Beryl and Compiz, but nothing happened. The same errors, cannot run desktop effect. 
Anybody can help me now? Thax ....

--------------------
My computer's devices is : CPU: Dual 2.8Ghz, Ram: DDR2 512MB,  Graphic Card: Onboard : Intel Corperation 82945 G/GZ Intergrated Graphics controller. (I updated my Graphic card and in addition, my graphic card when I run on XP OS is 128MB)

---

