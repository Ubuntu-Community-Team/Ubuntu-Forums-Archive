---
title: "Freeciv 2.1.0-beta2 sound and theme help"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by User_Program on 2006-08-28
I've built freeciv and it looks amazing but I'm having a problem with sound this is the error that I get

2: No real audio plugin present, proceeding with sound support disabled
2: For sound support, install SDL_mixer

I have SDL_mixer intalled is the problem with the way I built it?  Do I need a sdl_mixer prefix when compiling ? 

Under sound options would I enter the plugin path ? and where is the plugin located.

I would also like to install a theme how would I do this?

Thanks

---

### Post by Toxicity999 on 2006-08-28
I'm not so sure about that... but if you don't mind... could you list all the Deps for building? I've just been using the new tileset in the stable version. I noticed the new client looks way smoother... any other major notable features?

---

### Post by ShirishAg75 on 2006-08-29
Any screenshots anyone from the newest beta, thnx in advance.

---

### Post by Toxicity999 on 2006-08-29
[www.freeciv.org](www.freeciv.org)
Screenshots of most major versions kicking around there on the wiki. Still curious about the Deps for building though On dialup don't want to download 15mb without knowing for sure heh.

---

### Post by Alpha1Dash1 on 2006-10-06
Hi all, 

User_Program:
 I've just come across the exact same prob. Don't know if this is significant, but looking at the dependencies of sld_mixer in Synatic Pkt Mngr there is one lib which is in italics - libsmpeg0c2 (not sure if that's ...<o>c2 or ...<zero>c2). Outdated? Superceeded? Unavailable? Not Compatible? Being a nOOb, I really don't know. Did you manage to solve this?

Toxicity999:
 Paraphrasing from the "install" doc ('cos I don'd know how to import a text file into one of those cool scrolly boxes!):

note: square brackets [] denote versions specified, round () = guesses! 

general: 
gettext   [>=0.10.36]
automake  [>=1.6] 
autoconf  [>=2.55]
gcc (I used the one from Synatic Pkt Mngr)
g++ (note: not specified but "make" used it when compiling)

"1a. Prerequisites for the Gtk+ 2.0 client"
...
The "pkg-config" (I'm assumimg = 0.14.0 from the ver # in the ftp call)
The "Glib" utility library. [version >= 2.4.0.]
The "Atk" accessibility library. (assume =1.8.0)
The "Pango" text layout and rendering library. (assume = 1.4.1)
The "Gtk+" widget library.  [version >= 2.4.0.]

as far as their install doc goes, that it. Additionally, I had to install the Gtk+ dev package.
Given the time since your last post on this, I guess you know all the above already. But since I've just done it all, thought I should post it just in case! I don't suppose you know how to get the sdl_mixer thing working do you?

---

### Post by KhaaL on 2006-10-06
If anyone manages to squeeze a deb together with this baby, do share :)

---

### Post by mac.ryan on 2007-10-06
[Launchpad says]("https://bugs.launchpad.net/ubuntu/+source/freeciv/+bug/33721") that there is an issue with the copyrights of the sounds, so I don't think this will be fixed in the immediate future.

I might be wrong, but for the moment this is how I got the sound to work:
[LIST=1]
[*]Download the sound files at [ftp://ftp.freeciv.org/freeciv/contrib/sounds/sets](ftp://ftp.freeciv.org/freeciv/contrib/sounds/sets)
[*]Decompress the archive in the directory /usr/share/games/freeciv (so to have the file stsounds.soundspec and the directory stdsounds directly here, and not in a "data" subdir)
[*]Start the game with the command:[/LIST]```
civclient -P sdl -S stdsounds
```

(for me the sdl is the only plugin that worked).

Best luck!

---

### Post by himasaram on 2007-10-23
> **mac.ryan said:**
> 
(for me the sdl is the only plugin that worked).

Best luck!

FYI: as of 2.1, sdl *is* the only plugin available.

---

