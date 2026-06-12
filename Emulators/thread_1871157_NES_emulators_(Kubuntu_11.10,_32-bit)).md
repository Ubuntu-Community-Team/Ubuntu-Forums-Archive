---
title: "NES emulators (Kubuntu 11.10, 32-bit))"
date: 2011-10-28
forum: Emulators
---

### Post by Kexolino on 2011-10-28
The first one I tried was GFCEU (which worked perfectly with Xubuntu), but the games are very choppy. Disabling sound doesn't help. Here's what the terminal shows (I'm guessing the first error doesn't have anything to do with it):

```
noel@kubuntu:~$ gfceu
# # # #
gfceu ERROR code 5:
The gnomevfs libraries cannot be found.
  To enable ROM loading over the network, ensure that gnomevfs is installed on  this system.
  On Debian based systems (like Ubuntu), try this command:
  sudo apt-get install python-gtk2 libgnomevfs2-0
# # # #
gfceu message:  Using: /usr/games/fceu
/usr/bin/gfceu:510: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.widgets = gtk.glade.XML(glade_file)
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 1 -opengl 1 -xres 1280 -yres 1024  "/home/noel/Super Mario Bros./Super Mario Bros. (PC10).nes"

Starting FCE Ultra 0.98.12...
Loading /home/noel/Super Mario Bros./Super Mario Bros. (PC10).nes...

Error opening "/home/noel/Super Mario Bros./Super Mario Bros. (PC10).nes"!
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 1 -opengl 0  "/home/noel/Games/Super Mario Bros. (PC10).nes"

Starting FCE Ultra 0.98.12...
Loading /home/noel/Games/Super Mario Bros. (PC10).nes...

 PRG ROM:    2 x 16KiB
 CHR ROM:    1 x  8KiB
 ROM CRC32:  0xd445f698
 ROM MD5:  0x8e3630186e35d477231bf8fd50e54cdd
 Mapper:  0
 Mirroring: Vertical

Initializing video... Video Mode: 1280 x 1024 x 8 bpp full screen

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1024 sample frames(21.333333 ms)
```Then I tried FCEUX which is even worse, because I don't even get to the playing part. I just started configuring the controller and I got this:

```
noel@kubuntu:~$ fceux

Starting FCEUX 2.1.3...
A (1)
A (2)
B (1)
B (2)
Select (1)
Select (2)
Start (1)
Start (2)
Segmentation fault

```FCEUX looks hopeless, but I'm hoping GFCEU can be fixed... :-k

---

### Post by DoktorSeven on 2011-10-28
I've found mednafen works the best for NES, every other emulator I get choppy performance as you are.

---

### Post by Kexolino on 2011-10-28
I've tried mednafen, but everything looks like it's in slow motion. I've also tried nestopia, but it's the same, plus the colors aren't right...

---

### Post by Kexolino on 2011-10-29
Bump ):P

---

### Post by DoktorSeven on 2011-10-29
Slow motion?  Everything runs exactly right here in mednafen.  Were you using another emulator that ran things too fast, or maybe you're trying to run a different region ROM that originally ran at a different speed on the actual hardware because of the refresh differences of European vs. US/Japan televisions?

Or maybe you have a really old and slow computer?  I don't know, I'm just guessing here.

---

### Post by Kexolino on 2011-10-29
No, as I said, Mednafen is slow (maybe there's a way to speed it up?) and GFCEU is choppy. It would be funny if I could run Kubuntu fine, but not an NES game :P

---

### Post by DoktorSeven on 2011-10-29
Using desktop effects?  That might be slowing things down.  No idea why desktop effects are so popular when all it does is slow things down across the board.  (And if you're using AMD/ATi or Nvidia, make sure you're using the binary graphics drivers.)

---

### Post by Kexolino on 2011-10-30
I am, but I've already tried it with desktop effects turned off, no difference.

---

