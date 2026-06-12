---
title: "Atari800 emualtor question"
date: 2022-08-17
forum: Emulators
---

### Post by jonfisher on 2022-08-17
I've found the built in OS Version set to AltirrOS is probably the culprit of only about half my game roms working.
I've located actual Atari OS roms, but need some guidance on how to install it into the emulator...

---

### Post by Dennis N on 2022-08-17
> **jonfisher said:**
> I've found the built in OS Version set to AltirrOS is probably the culprit of only about half my game roms working.
I've located actual Atari OS roms, but need some guidance on how to install it into the emulator...

How did you install atari800?

atari800 version 4.2 is available in the Ubuntu Repository.
atari800 version 3.1 is available as a Snap package called atari800-jz.

The Snap package includes the emulator ROMS you need. Ubuntu Repository versions 4.1 or later come with an alternate ROM to the Atari ROM.
The best solution is to install the Snap package. All games I have run correctly. It's what I would recommend.
No game files are included with either of these.

I've tried the 4.2 and had problems with it, and there is a bug in configuring the keyboard for directional control. It might be OK if you have a joystick. Also one game we like does not work quite right in 4.2, but does in version 3.1. So again, I would recommend the 3.1 over 4.2. [update: the directional control problems happened only when installed in a virtual machine.]

Further answers would depend on what you have installed.

---

### Post by jonfisher on 2022-08-19
> **Dennis N said:**
> How did you install atari800?

atari800 version 4.2 is available in the Ubuntu Repository.
atari800 version 3.1 is available as a Snap package called atari800-jz.

The Snap package includes the emulator ROMS you need. The Repository version does not, so you have to find the ROMs elsewhere.
The best solution is to install the Snap package. All games I have run correctly. It's what I would recommend. 
No game files are included with either of these.

I've tried the 4.2 and had problems with it, and there is a bug in configuring the keyboard for directional control. It might be OK if you have a joystick. Also one game we like does not work quite right in 4.2, but does in version 3.1. So again, I would recommend the 3.1 over 4.2.

ADDENDUM:  I installed from Synaptic and it now is also 4.2 version...


Addendum:  I see an atari800-jz emulator in the Ubuntu repository.  I'm very curious how it works...


Further answers would depend on what you have installed.

It is version 4.2.0 so it's from the Ubuntu Software Repository...
I will uninstall my version and install from Synaptic package manager...

update:  I installed from Synaptic and it is currently version 4.2 also...

---

### Post by Dennis N on 2022-08-19
> update: I installed from Synaptic and it is currently version 4.2 also... 
It's a Snap package, so you can use **Ubuntu Software** to install it. Search for **atari800-jz** as shown in my attachment of post #2.
OR
You can install with a terminal command:
**snap install atari800-jz**

Comment: 

I have had this running on Ubuntu 20.04 for a long time, and it works fine. I just tried installing the snap version on Ubuntu 22.04 and encountered lots of problems starting with the configuration dialogs (press F1). Many things seemed unresponsive. I did get a game to run after some effort, but then there was no sound. That's unacceptable.  

If you are using Ubuntu 22.04, you may have a better result, but I really can only recommend using this program with Ubuntu 20.04.

---

### Post by jonfisher on 2022-08-19
Hmm, I installed that version.
I seem to have less success with it - concerning my logitech gamepad...
hmmm....

---

### Post by Dennis N on 2022-08-20
I've not used any controller device with my atari800 emulator. I figured the actions are just left, right, up, down, and fire, and that the keyboard would suffice. I use a desktop keyboard with separate number keys, so it made sense to just use those keys plus another for fire.

I notice there is a man page for atari800. You may find something useful in this:
[https://manpages.ubuntu.com/manpages/trusty/man1/atari800.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/atari800.1.html)
or just type **man atari800** in the terminal. This may get you a newer version as well.

I've managed to get by with the F1 configuration dialog, although using it can be very frustrating.  

If you ever venture outside of Ubuntu Land, version 5.0.0 of atari800 is now offered by Fedora, Arch, Manjaro and possibly other Linux distros I am not aware of. I have the 5.0.0 version on Fedora and it works well. And it's not a snap package.

---

### Post by jonfisher on 2022-08-21
> **Dennis N said:**
> I've not used any controller device with my atari800 emulator. I figured the actions are just left, right, up, down, and fire, and that the keyboard would suffice. I use a desktop keyboard with separate number keys, so it made sense to just use those keys plus another for fire.

I notice there is a man page for atari800. You may find something useful in this:
[https://manpages.ubuntu.com/manpages/trusty/man1/atari800.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/atari800.1.html)
or just type **man atari800** in the terminal. This may get you a newer version as well.

I've managed to get by with the F1 configuration dialog, although using it can be very frustrating.  

If you ever venture outside of Ubuntu Land, version 5.0.0 of atari800 is now offered by Fedora, Arch, Manjaro and possibly other Linux distros I am not aware of. I have the 5.0.0 version on Fedora and it works well. And it's not a snap package.

Thanks for the information, especially the link to the page.
I'm going to install version 5.0.0 now and give it a try...
As far as my logitech gamepad goes, it works on some games (like Donkey Kong) then won't work at all for others.  I suspect it may be if I ran a better Atari rom OS it may straighten a lot out (but still don't know how to insert the os roms into the emulator - oh well)...

Thanks again!

---

### Post by Dennis N on 2022-08-24
> **jonfisher said:**
> Thanks for the information, especially the link to the page.
I'm going to install version 5.0.0 now and give it a try...
As far as my logitech gamepad goes, it works on some games (like Donkey Kong) then won't work at all for others.  I suspect it may be if I ran a better Atari rom OS it may straighten a lot out (but still don't know how to insert the os roms into the emulator - oh well)...
Thanks again!

As to the ROM files, you can put them where you like. There are settings in the F1 configuration dialog to set the location of the emulator ROMs as well as game ROMS, files for cassette games and for disk games.

A possible arrangement: I would have a **games** folder in my home folder. I would then have an **atari** folder and sub-folders with any related files. For example:

```
atari
&#9500;&#9472;&#9472; Atari-cassette-games
&#9500;&#9472;&#9472; Atari-disk-games
&#9500;&#9472;&#9472; Atari-game-roms
&#9500;&#9472;&#9472; Atari-save-state
&#9500;&#9472;&#9472; emulator-roms
&#9500;&#9472;&#9472; game-directions
&#9492;&#9472;&#9472; my-atari-magazine

```
My understanding is that if you supply a path to your own emulator ROMs, those are used instead of any supplied with the snap package.

In addition, the configuration file** .atari800.cfg** (for non-snap version) is in your home folder. The F1 dialog just sets values in this file. You could change the file yourself if you know what you are doing. Note: If you change some settings using the F1 configuration dialog, be sure to save emulator settings it before you quit atari800 or the changes are discarded.

---

