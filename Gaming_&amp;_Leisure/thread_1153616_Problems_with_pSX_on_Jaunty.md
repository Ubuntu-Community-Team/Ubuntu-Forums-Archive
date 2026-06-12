---
title: "Problems with pSX on Jaunty"
date: 2009-05-08
forum: Gaming &amp; Leisure
---

### Post by Mandala 13 on 2009-05-08
[SIZE=2]Basically, my problem is that when I try opening the pSX, it prompts the whole "Bio file thing", I select it, and nothing happens. When I was using Hardy, that same problem was solved installing the libgltext1-dev that is needed and everything was solved. Now, in Jaunty, I have installed all the libraries I could think of, and nothing is working.

So, like the last time, here's the link to what it says while trying to open pSX with the terminal. It say way too much things about not recognizing or finding devices and more. Compiz is deactivated, in case that might be another option. [http://www.openpaste.org/14023/. ]("http://www.openpaste.org/14023/")

Hope that you could help me with anything at all, considering how much I love pSX working on Linux.

Thanks![/SIZE]

---

### Post by disturbedite on 2009-05-09
if you compiled pSX before i HIGHLY recommend you recompile it now.

---

### Post by zero777zero on 2009-05-09
i stopped using pSX after annoying problems that the dev didn't care to fix.

i started using PCSX in the add/remove and it works fine for me.

pSX for linux always has and probably always will be a second class citizen to the windows version

---

### Post by disturbedite on 2009-05-09
> **zero777zero said:**
> pSX for linux always has and probably always will be a second class citizen to the windows version

i've never had a problem with it and i don't know what that means, it is practically identical to the windows port in my experience.

---

### Post by Mandala 13 on 2009-05-09
> **disturbedite said:**
> i've never had a problem with it and i don't know what that means, it is practically identical to the windows port in my experience.

Kinda had problems to get back to this forum for awhile. But I should say that I totally agree with you. I mean, I loved using pSX on Hardy, and to be honest with you, it was 100 times better than the same version on Guindous. 

That's why I have been so into getting this work, although I'm going to give pscx a try as well, just to know what might end up happening. As long as I can use my Logitech controller, don't need to complicate myself too much and can save states, I would be happy, hehe.

---

### Post by Mandala 13 on 2009-05-09
> **disturbedite said:**
> if you compiled pSX before i HIGHLY recommend you recompile it now.

Ok, just to be sure about it. So re-compile, you think, might be the thing that would fix my problems? And just for the records, how would you advice me doing it exactly? Let's say that I might have Ubuntu for some time now, but I have quite a reputation doing the wrong thing in the worst moment, hehe.

---

### Post by Mandala 13 on 2009-05-09
> **zero777zero said:**
> i stopped using pSX after annoying problems that the dev didn't care to fix.

i started using PCSX in the add/remove and it works fine for me.

pSX for linux always has and probably always will be a second class citizen to the windows version

Ok, tried to used that PCSX and well, the only problem would be that I can't seem to load a game from an actual CD, because it keep asking me for the ISO file. So, I can't even try if it's working fine, because the only thing that I got is PS1 games that I actually bought in some moment, (irony?) Hehe...

So, is there a way to load CD's without so much problems? See, that's what I miss about pSX, hehe. :(

---

### Post by dfreer on 2009-05-10
You can't recompile pSX, as the author has not released the source code. And have you tried killing pulseaudio prior to running pSX?

---

### Post by Mandala 13 on 2009-05-10
> **dfreer said:**
> You can't recompile pSX, as the author has not released the source code. And have you tried killing pulseaudio prior to running pSX?

Actually, there's nothing that I would really be able to kill, because PA is not even working, after a disable it with a script I found in another website; had way too much sound problems on Jaunty, until I did that. Sorry for not mentioning it before, knowing that there are way too much PA issues with pSX, kinda forgotten about it.

So, that wouldn't be exactly the solution.

But hey, thanks to keep on offering ideas! :)

---

### Post by zero777zero on 2009-05-10
in PCSX go to configure and choose the CD ROM plugin instead of the ISO plugin

---

### Post by Mandala 13 on 2009-05-10
> **zero777zero said:**
> in PCSX go to configure and choose the CD ROM plugin instead of the ISO plugin

Ok, basically the PS1 Emulator did work, with a few problems, of course. And guess what was the main problem? A Sound one, just like in pSX. So I suppose that if I could get PCSX to sound, that would means that I could try using pSX as well.

Here's the code of terminal: [http://www.openpaste.org/en/14050/](http://www.openpaste.org/en/14050/)

As you can see, it has the whole "can't find device" thing, just like in pSX. Is that a problem that for the time being, couldn't be solved?

---

### Post by disturbedite on 2009-05-10
> **dfreer said:**
> You can't recompile pSX, as the author has not released the source code.

oops. i forgot about that...#-o

---

### Post by zero777zero on 2009-05-10
some games which have redbook audio cannot be played by current emulators, however this should only effect music and not soundFX

---

### Post by Mandala 13 on 2009-05-11
> **zero777zero said:**
> some games which have redbook audio cannot be played by current emulators, however this should only effect music and not soundFX

The basic problem would be that we would be talking about games that had sound before, in any case. So, I think that I just have (like some Jaunty users) serious sound problems that, even if they let me watch movies and all (for a while, in any case), can't let me play... Bad, bad computer, don't letting me be a Gamer.

:(

---

