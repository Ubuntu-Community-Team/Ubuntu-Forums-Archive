---
title: "Do I need any BIOS with XMESS emulator ?"
date: 2006-03-16
forum: Gaming &amp; Leisure
---

### Post by Biased turkey on 2006-03-16
I would like to try the Sega Genesis ( Mega Drive ) with Linux.
I first tried the WGENS emu with Windows 2000 and it worked nicely.I just had to install the executable , copy a ROM game in the ROM directory and ... voila, no BIOS to install
I found the XMESS emulator on the Ubuntu repository, do I need any Mega Drive BIOS in order to run that emulator ? If yes, which one ?
tia for any info.

---

### Post by DoktorSeven on 2006-03-17
I just tried it and doesn't seem like you do for Genesis/Megadrive:

xmess gen_usa -cart ./sonic.zip

(Disclaimer: I own the actual Sonic cart for my US Genesis system...)

---

### Post by Dullin on 2006-03-17
[QUOTE=Biased turkey]I would like to try the Sega Genesis ( Mega Drive ) with Linux.
I first tried the WGENS emu with Windows 2000 and it worked nicely.I just had to install the executable , copy a ROM game in the ROM directory and ... voila, no BIOS to install
I found the XMESS emulator on the Ubuntu repository, do I need any Mega Drive BIOS in order to run that emulator ? If yes, which one ?
tia for any info.[/QUOTE]
XMESS is not a really good emulator to play roms with. It's more of a technical demo of emulation. You should head on too [http://www.zophar.net/](http://www.zophar.net/) and research in the Unix section to see wich are the good emulators for genesis.

---

### Post by DoktorSeven on 2006-03-17
True, and there is a version of Gens for Linux, though it's slow.

There's been a hack done that renders the screen using OpenGL which speeds things up a bit (it's not 3d, it just renders the screen using an OpenGL  plane which is faster on 3d-enabled cards), and can be found at [http://users.vialink.com.br/denilson/gens/](http://users.vialink.com.br/denilson/gens/) (source only).

---

### Post by Biased turkey on 2006-03-17
First, thanks to both of you for taking some of your time to reply.

To DoktorSeven:

the syntax you posted for using the xmess command helped me a lot.
I tried it for seggalaga and it worked OK.I didn't have any sound, but maybe I didn't specify the right sound option.At least I have the demo running.
I was confused because when i type "man xmess", it listed the man page for ... the xmame command.

On the other hand running "xmess --help" listed the correct options.

To Dullin:
I tried xmess because ... it was available in the Ubuntu repository.
I checked the Linux Format june 2005 issue ( special emulator ) and they recommend using gens as the best Sega genesis emulator. On the other hand, they warned the user that installing gens might be a real pain in the neck.

I tried the Sega Genesis emu just out of curiosity to see how the Sega Genesis looks, I own the Sega Saturn ( it was the 1st video console I ever owned because I was hooked on Sega Rally ) and the Dreamcast but never saw the Genesis in action.
I have to admit, the Sega genesis looks good ... for its age.

---

