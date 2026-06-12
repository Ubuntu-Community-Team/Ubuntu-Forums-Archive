---
title: "Turning Ubuntu Box Into MAME \ Boxee Appliance"
date: 2011-03-04
forum: Gaming &amp; Leisure
---

### Post by garybiscuit on 2011-03-04
[FONT="Verdana"]Hi,

I'd like to turn a semi-dated PC into an Ubuntu-powered "appliance" that's sole purpose is to run either...

a) Wah!Cade    OR
b) Boxee

... once Ubuntu finishes booting up. The idea would be to hook this box up to my TV (through HDMI) and have it permanently setup so it can just be powered up anytime I want to get my entertainment on. I'd really like to configure it in such a way so that you just get an über-simple menu like this once bootup completes...

      +-----------------------------+
      | [*]  Wah!Cade          
      | [ ]  Boxee             
      +-----------------------------+

... and to be able to make the selection with a gamepad instead of a keyboard. I'm picturing something that *looks* like GRUB - with the real point of it being that you visually can't see anything else *but* the selection menu. Cleanliness is key.

I'm not worried about getting Wah!Cade, SDLMame or Boxee going - those should be okay. The only things I don't know where to start with are the selection menu (above) - and the gamepad to control it with. 

For what it's worth, though I doubt it matters, my hardware specs are:

* Intel Pentium 2.8GHz Processor
* 2G of RAM
* 2 IDE Hard Disks
  - 1 for the OS
  - 1 for data \ ROMs
* (some to-be-determined graphics card w/ an HDMI output)


So, my questions:

1) Is there a program that can layout a simple selection menu like I described? That is, you get 2 choices displayed and those are the only things you can visually see on the screen.

2) I'd like to use the [Logitech F710 Wireless Gamepad ]("http://bit.ly/9W1MoM")to both a) make the selection and b) actually play MAME ROMs. Has anyone successfully used this particular gamepad in Ubuntu?

3) Would Ubuntu be able to natively convert gamepad movement into movement detectable by the selection program?


Any help is greatly appreciated.

Thanks,
Gary[/FONT]

---

### Post by mips on 2011-03-05
Google seems to indicate the F710 works fine in linux/Ubuntu. Some people even use it to control XBMC.

[http://forums.logitech.com/t5/PC-Gaming/Cannot-connect-F710/td-p/513080](http://forums.logitech.com/t5/PC-Gaming/Cannot-connect-F710/td-p/513080) See post#5
[http://superuser.com/questions/223137/media-player-windows-or-linux-thats-easy-to-control-with-a-gamepad](http://superuser.com/questions/223137/media-player-windows-or-linux-thats-easy-to-control-with-a-gamepad)

---

### Post by garybiscuit on 2011-03-05
Any word on the selection menu - and having it detect movement from the gamepad?

- Gary

---

### Post by mips on 2011-03-05
> **garybiscuit said:**
> Any word on the selection menu...

Selection menu of what?

---

### Post by garybiscuit on 2011-03-05
To select either Boxee or Wah!Cade to launch - as in, those are the only 2 visible options - once Ubuntu finishes booting up.

- Gary

---

### Post by mips on 2011-03-06
Sure it's doable but you will have to scratch around a bit. I have zero knowledge of this.

---

### Post by frostwork on 2011-03-06
Imho it's not the perfect solution to always boot into some tiny menu just to select either wahcade or boxee, when you also could directly boot in to one of them instead.

as boxee is a xbmc fork it should be possible to also use one of the xbmc emulator launcher addons.
or you start some tiny program launcher script from within boxee to launch wahcade.

no idea if wahcade can launch standalone programs, but if so you could also start boxee from there.

alternatively you could use my mighty ;)  opengl
emulator launcher "typhon"
( [http://www.frostworx.de/?p=1](http://www.frostworx.de/?p=1) ).
up to 21 different emulators, 140 programs, 3d, wysiwyg, native unleashx and ps3 theme (p3t) support to name just a few features :)
good luck and have fun!

---

### Post by garybiscuit on 2011-03-06
Frostwork,

You might be right. And actually, to keep things even simpler I might just buy an actual Boxee Box and leave the PC to do all the game emulation. But! Now since I'm thinking down that avenue...

1) What's the simplest way to get Ubuntu (latest out-of-the-box version) to start Wah!Cade immediately after bootup? 

2) What's the easiest way to make Ubuntu skip past the login window... so that no typing is necessary after bootup?

3) Is there a simple way to force Ubuntu to start the bare minimum of startup programs and services? The idea being to save all possible CPU and RAM for game emulation.

Thanks for the help.

- Gary

---

### Post by mips on 2011-03-07
> **garybiscuit said:**
> 
1) What's the simplest way to get Ubuntu (latest out-of-the-box version) to start Wah!Cade immediately after bootup? 

System-->Preferences-->Startup Applications


> **garybiscuit said:**
> 
2) What's the easiest way to make Ubuntu skip past the login window... so that no typing is necessary after bootup?

System-->Administration-->Login Screen


> **garybiscuit said:**
> 
3) Is there a simple way to force Ubuntu to start the bare minimum of startup programs and services? The idea being to save all possible CPU and RAM for game emulation.


Install **sysv-rc-conf** & **bum**

[http://www.liberiangeek.net/2010/05/how-to-stop-programs-from-automatically-starting-in-ubuntu-and-improve-performance/](http://www.liberiangeek.net/2010/05/how-to-stop-programs-from-automatically-starting-in-ubuntu-and-improve-performance/)
[http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/](http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/)




.

---

### Post by garybiscuit on 2011-03-07
Cool, I'll try those out. Thanks.

- Gary

---

### Post by mips on 2011-03-08
Hope you come right, let us know how it goes.

---

### Post by daniel_w93 on 2011-03-10
Well

you can use a tool like the "Ubuntu Customization Kit" to throw out all the unnecessary stuff from the install image and maybe add some functions (plugins, codecs, etc.) and create a custom ubuntu image for your needs.

Then you could use a program from the 
Ubuntu Software Center -> Developer Tools -> Graphical Interface Design like for example "Gazpacho" or "Glade Interface Designer" to design this 2 option interface you talked about.

Then you'd need to write a short program or script that responds to the the output given by the interface you designed.

In the Start-Up Application Manager you'd have to add that little program or script to make it appear on start-up.

and finally set ubuntu to auto-login in order to not have to type any passwords after turning it on.

All that is highly theoretical..never tried it myself (not combined in the above mentioned way at least) and I'm sure there are other ways....but I could imagine this one to work

---

