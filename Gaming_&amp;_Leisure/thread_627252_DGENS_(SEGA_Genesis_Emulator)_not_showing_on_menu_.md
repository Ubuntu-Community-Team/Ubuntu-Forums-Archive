---
title: "DGENS (SEGA Genesis Emulator) not showing on menu after installation."
date: 2007-11-29
forum: Gaming &amp; Leisure
---

### Post by braveerudite on 2007-11-29
DGENS (SEGA Genesis Emulator) not showing on menu after installation.  I installed DGens using "Synaptic Pakage Manager" but is no were to be found on the menus.  I'm trying to launch it but where is it?  Thank you all for your time.

---

### Post by acoustibop on 2007-11-30
Try entering dgen in a terminal, braveerudite.  If that works, you can create a launcher using that command.

Or you could try GENS: there are .debs in [this thread]("http://ubuntuforums.org/showthread.php?t=290008&highlight=gens").  If the latest 2.13 versions don't work for you, try the 2.12b.

---

### Post by braveerudite on 2007-12-01
> **acoustibop said:**
> Try entering dgen in a terminal, braveerudite.  If that works, you can create a launcher using that command.

Or you could try GENS: there are .debs in [this thread]("http://ubuntuforums.org/showthread.php?t=290008&highlight=gens").  If the latest 2.13 versions don't work for you, try the 2.12b.

But there is no GUI and I don't know how to load the Roms... text version is confusing. Help ](*,)

---

### Post by acoustibop on 2007-12-01
Well, if there isn't a gui, you're sort of stuck then, braveerudite.  If the documentation is confusing, you could try doing ```
dgen --help
``` or ```
dgen -h
``` in a terminal; you may get a list of switches and syntax that might be more informative.

Otherwise, see my comment above about GENS - that works, and has a gui.

---

### Post by braveerudite on 2007-12-01
> **acoustibop said:**
> Well, if there isn't a gui, you're sort of stuck then, braveerudite.  If the documentation is confusing, you could try doing ```
dgen --help
``` or ```
dgen -h
``` in a terminal; you may get a list of switches and syntax that might be more informative.

Otherwise, see my comment above about GENS - that works, and has a gui.

I'm still having trouble using the text mode.

If I want to start a rom what would the command look like in the terminal?

For example I type on terminal:

dgen 3 Ninjas Kick Back (U) [!] 

but I get this message:

bash: syntax error near unexpected token `('




Please help.

---

### Post by acoustibop on 2007-12-01
Post the output of dgen --help or dgen -h (whichever works) and we might be able to help you a bit more, braveerudite.  However, you don't have a path included to where your ROM is, and the format of your filename (i.e. with spaces - the emulator may not realise the entire phrase is the filename) may be producing problems, too.

---

### Post by disturbedite on 2007-12-01
yeah, gens is what i was gonna recommend too.  its much better imho.

---

### Post by Frem on 2007-12-03
> **braveerudite said:**
> 
For example I type on terminal:

dgen 3 Ninjas Kick Back (U) [!] 

but I get this message:

bash: syntax error near unexpected token `('

What you want actually want to run is [FONT="Courier New"]dgen "3 Ninjas Kick Back (U) [!].smd"[/FONT], or something like that.

Assuming you actually own the original cartage, of course.

---

### Post by Tanjer1588 on 2007-12-10
Hey dont know if you guys will see this or not :D seeing as how its like a week old now but Dgens got no GUI so the way you run the rom's is by right clicking on the rom file itself and click open with, at the bottom you can type in a command line so you type in dgen there... and it will start, if you type in dgen in your terminal it will give you a referance of what you can add with it if you type dgen -j the -j tells it to use a joypad (usb controler if you got it) so the best way to do it would be dgen -j -f, that will make it full screen or dgen -j -G ###x#### for a screen size. but you have to click right on the rom, since theres no GUI, thats the easyest way for me

---

