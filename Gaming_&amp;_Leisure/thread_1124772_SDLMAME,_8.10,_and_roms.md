---
title: "SDLMAME, 8.10, and roms"
date: 2009-04-13
forum: Gaming &amp; Leisure
---

### Post by rppp01a on 2009-04-13
Ok. I am running Intrepid Ibix on my HP DV5170us laptop. All hardware works out of the box. 

I installed SDLMAME from ubuntu repositories, found it didn't work, followed a few links I found (this one first [http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138&page=2](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138&page=2)). I uninstalled the package.

So I downloaded the SDLMAME .130 sources and compiled. No problems. I set up the $HOME/.mame directory, I set up the ROMS directory. I manually set the symlink to /usr/local/bin/mame so it would work in my $PATH.

When I run MAME, up comes the full screen menu with my games. I only have 6 or 7. Of those, I can run Spy Hunter. No sound. That's ok for now. Gameplay is good, though I have to fiddle with the controls. But that's ok.

Whenever I try to play any other ROM, however, I get an error that says:

'The selected game is missing one or more required ROM or CHD images. Please select a different game'

These same roms ran just fine when I was running Windows. Does anyone know if I need to make any modifications to make this work?

---

### Post by KingHanco on 2009-04-13
Might want to ask over here at: [http://www.bannister.org/forums/ubbthreads.php?Board=8&page=1&ubb=postlist](http://www.bannister.org/forums/ubbthreads.php?Board=8&page=1&ubb=postlist)

R. Belmont did that port.

Ubuntu have nothing to do with the SDLMAME sounds.

---

### Post by wingnux on 2009-04-13
Not that I know of. You should notice that a lot of romsets changed on mame 0.130 and maybe you need to update them. Have you tried running "sdlmame 'romname'" (without quotes) on the terminal?

---

### Post by rppp01a on 2009-04-13
> **KingHanco said:**
> Might want to ask over here at: [http://www.bannister.org/forums/ubbthreads.php?Board=8&page=1&ubb=postlist](http://www.bannister.org/forums/ubbthreads.php?Board=8&page=1&ubb=postlist)

R. Belmont did that port.

Ubuntu have nothing to do with the SDLMAME sounds.

That's ... where I went to get the initial compilation. It compiled fine.


> **wingnux said:**
> Not that I know of. You should notice that a lot of romsets changed on mame 0.130 and maybe you need to update them. Have you tried running "sdlmame 'romname'" (without quotes) on the terminal?

Thanks. I had the same error.

---

### Post by rppp01a on 2009-04-13
Ah. That was strange. I renamed all the files to lowercase and they worked. Great. Thanks!

---

