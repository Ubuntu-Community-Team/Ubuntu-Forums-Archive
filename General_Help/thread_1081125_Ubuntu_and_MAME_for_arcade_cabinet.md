---
title: "Ubuntu and MAME for arcade cabinet"
date: 2009-02-26
forum: General Help
---

### Post by tonyzpony on 2009-02-26
I'm building an arcade cabinet and am going to run the MAME emulator. I'd like to avoid running a full Windows system just to run the emulator and the gui front end. I found a MAME port for Ubuntu and thought this might be a better solution.

I was hoping to run the computer with no hard drive at all.
My question is, is it possible to load a minimal version of the OS with the emulator and the ROM games on to a USB stick, boot off the USB stick, and load the entire thing into memory when powering up?

This seems like it may work, I know there are USB drive installs of Ubuntu. Would this possible? Can you load the whole OS into RAM from the drive? More importantly would it be fast? and would it boot fast? The thought of having a Windows bootup just to play a game of Donkey Kong is not really appealing nor is having a hard drive in the cabinet.

Any thoughts would be appreciated!
Thanks

---

### Post by DagMan on 2009-02-26
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
I don't know if that still works, however I have used it for Feisty Fawn if I remember right.

The easiest thing would be to set things up on a machine, then installing remastersys to make an image file, [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Then using unetbootin for older releases or the built in liveusb creater in the newer release, to get it on a stick. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

May as well look at other machines like mednafen, which can do quite a few including NES (my favorite).
There's even a Playstation emulator in the tips and tutorial section around somewhere but I don't know what hardware you'de need to run it.

The first link is what you want.  I got ahead of myself.

---

