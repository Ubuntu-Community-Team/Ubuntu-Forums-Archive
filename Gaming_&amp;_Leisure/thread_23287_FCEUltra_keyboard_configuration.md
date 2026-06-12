---
title: "FCEUltra keyboard configuration"
date: 2005-04-01
forum: Gaming &amp; Leisure
---

### Post by SolidAndShade on 2005-04-01
Hey everyone,

I just installed the fceu NES emulator and it works well, but I want to remap the control keys but can't figure out how.  Does anyone know how to do this?  Thanks.

SolidAndShade

---

### Post by SolidAndShade on 2005-04-02
Well, I just found out a way to reconfigure the keys in fceu, although anyone who knows an easier method is welcome to speak up.  In your home directory, there should be a hidden directory called .fceultra.  Go in there and hex edit the file fceu98.cfg.  The configuration data is stored in here.  As of yet, I've only figured out how to change the directional buttons.  Find part of the file that says "GamePadConfig."  After this label, you should see the four letters whose keys are used to control the D-pad.  My default keys are w, z, a and s, for up, down, left and right.  I changed these to the easier-to-use w, s, a, and d.  I'm still trying to find where the A and B button keys are defined.  Hope this helps someone.

SolidAndShade

---

### Post by Jujimufu on 2005-04-03
I can't FCEUltra to work at all.  I tried starting it through run application by typing fceu - but nothing happens cept a system sound (like the click).  

Then I tried running it in terminal and it gives me options.  I typed fceu followed by the location of a game it says:

Starting FCE Ultra 0.98.12...
Loading /home/user/Crap/Megaman.nes...

Error opening "/home/user/Crap/Megaman.nes"!
--------------------

Megaman as an example game / I know this has nothing to do with keyboard configuring: But thought I'd just bring the problem to this thread instead of starting a new one.  What do I need to do to get this working?  ZSNES works great, but not this emulator...  Thanks guys!

---

### Post by nukethewhale on 2005-04-12
You can remap the control keys for the player 1 controller in FCEUltra by starting it up with the command
```
fceu -inputcfg gamepad1 romfile.nes
```
where romfile.nes is some ROM you want to play. You are then prompted to enter keys for the A, B and directional buttons and rapid fire A and B. To configure the player 2 control keys substitude gamepad2 for gamepad1 in the command above. When you do this, the keys you choose become default for FCEUltra and you don't have to repeat this every time you run it.

I have, however, only tried this on FCEUltra compiled from source on Fedora.

---

### Post by Synt4x_3rr0r on 2005-07-03
[QUOTE=nukethewhale]You can remap the control keys for the player 1 controller in FCEUltra by starting it up with the command
```
fceu -inputcfg gamepad1 romfile.nes
```
where romfile.nes is some ROM you want to play. You are then prompted to enter keys for the A, B and directional buttons and rapid fire A and B. To configure the player 2 control keys substitude gamepad2 for gamepad1 in the command above. When you do this, the keys you choose become default for FCEUltra and you don't have to repeat this every time you run it.

I have, however, only tried this on FCEUltra compiled from source on Fedora.[/QUOTE]

Thank you SOOO much. I've been looking for a solution for quite a while now :D and it totally works on Ubuntu too.

---

### Post by BoyOfDestiny on 2005-07-03
Has an easier input cfg (actually it's a little funny since u can do multiple devices at the same time, but easy), you'll have to compile and make debs though.

[http://nintencer.fobby.net/](http://nintencer.fobby.net/)

---

### Post by eddie303 on 2006-01-28
Hi!
Somebody knows why fceu ignores -xres, -yres and any other resolution-modifying commands?

---

### Post by punkrockguy318 on 2006-06-12
[QUOTE=SolidAndShade]Well, I just found out a way to reconfigure the keys in fceu, although anyone who knows an easier method is welcome to speak up.  In your home directory, there should be a hidden directory called .fceultra.  Go in there and hex edit the file fceu98.cfg.  The configuration data is stored in here.  As of yet, I've only figured out how to change the directional buttons.  Find part of the file that says "GamePadConfig."  After this label, you should see the four letters whose keys are used to control the D-pad.  My default keys are w, z, a and s, for up, down, left and right.  I changed these to the easier-to-use w, s, a, and d.  I'm still trying to find where the A and B button keys are defined.  Hope this helps someone.

SolidAndShade[/QUOTE]
For an easier way to configure FCEU, you can use the new graphical frontend.  For more info, check out this post: [http://ubuntuforums.org/showthread.php?t=195413](http://ubuntuforums.org/showthread.php?t=195413)

---

### Post by RealG187 on 2008-08-18
> **nukethewhale said:**
> You can remap the control keys for the player 1 controller in FCEUltra by starting it up with the command
```
fceu -inputcfg gamepad1 romfile.nes
```
where romfile.nes is some ROM you want to play. You are then prompted to enter keys for the A, B and directional buttons and rapid fire A and B. To configure the player 2 control keys substitude gamepad2 for gamepad1 in the command above. When you do this, the keys you choose become default for FCEUltra and you don't have to repeat this every time you run it.

I have, however, only tried this on FCEUltra compiled from source on Fedora.

How do I configure the keys for ALL roms?

---

### Post by punkrockguy318 on 2008-08-19
> **RealG187 said:**
> How do I configure the keys for ALL roms?

firstly you should use double dashes

but if you configure it for one it will configure it for all

all users and recommended to upgrade to 2.0.2; major overhaul [http://fceux.com](http://fceux.com)

---

### Post by RealG187 on 2008-08-20
> **punkrockguy318 said:**
> but if you configure it for one it will configure it for all

Isnt that redundant? Why would it have an option to configure for one ROM if it configures for all?

I dont follow...

---

### Post by punkrockguy318 on 2008-08-20
> **RealG187 said:**
> Isnt that redundant? Why would it have an option to configure for one ROM if it configures for all?

I dont follow...

your not setting a config to a rom, your just setting the config.  the romname can me /dev/null for all the emu cares it just needs a romname to parse

---

### Post by RealG187 on 2008-08-20
why does it need a rom name? What's it mean to parse?

---

### Post by punkrockguy318 on 2008-08-20
> **RealG187 said:**
> why does it need a rom name? What's it mean to parse?

it just needs one okay? plain and simple it needs a rom name or the emulator will **** out

use gfceu(x) if the command-line is over your head

---

### Post by RealG187 on 2008-08-20
I have kamefu as the gui

I know how to use the command line to so stuff like open files
I dont get why it would need a rom name

> it just needs one okay? plain and simple it needs a rom name or the emulator will **** out
But why?

---

### Post by RealG187 on 2008-08-20
I have kamefu as the gui

I know how to use the command line to so stuff like open files
I dont get why it would need a rom name

> it just needs one okay? plain and simple it needs a rom name or the emulator will **** out
But why?

---

### Post by punkrockguy318 on 2008-08-20
> **RealG187 said:**
> I have kamefu as the gui

I know how to use the command line to so stuff like open files
I dont get why it would need a rom name


But why?

what the hell fceu has another gui? 

but the code is just written so a rom name is required because 9 times out of 10 your going starting fceu to play a rom file

---

### Post by RealG187 on 2008-08-20
> **punkrockguy318 said:**
> what the hell fceu has another gui?
Kamefu is a frontend for all emulators. You get it to scan a folder for ROMs then enter in the emualtor command, for example under NES "fceu"

---

