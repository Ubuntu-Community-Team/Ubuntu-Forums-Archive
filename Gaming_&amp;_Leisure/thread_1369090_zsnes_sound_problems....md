---
title: "zsnes sound problems..."
date: 2009-12-31
forum: Gaming &amp; Leisure
---

### Post by switch10 on 2009-12-31
zsnes sound worked great in 8.10.  after installing 9.10 the sound is all scrambled.  I tried many of the different settings, none really make a difference..

any ideas??

Thanks

Dave

---

### Post by farrell2k on 2009-12-31
Check the docs.  There is a switch you can use when running zsnes to switch between alsa, sdl, and oss sound.  One of them will likely wqork for you.

---

### Post by Catboy~ on 2009-12-31
Zsnes is pretty old, you'd be better off using bsnes. ;)

[http://byuu.org/bsnes/](http://byuu.org/bsnes/)

---

### Post by switch10 on 2010-01-01
> **Catboy~ said:**
> Zsnes is pretty old, you'd be better off using bsnes. ;)

[http://byuu.org/bsnes/](http://byuu.org/bsnes/)

hmm bsnes runs extremely slow...

---

### Post by hypert on 2010-01-01
WEll if ur sound is not working then this will help: go into the terminal and type in alsamixer. It help for my problem which was just like urs.

---

### Post by benmoran on 2010-01-01
Take my advice. I was a loooooong time Zsnes user, but experienced similar problems as you. I also didn't care for the snes9x versions in the repos. 

Then I found Snes9x-gtk. It's much better than I expected. It supports all the options you could hope for, and it actually fits into the Ubuntu desktop and behaves like you would expect. 

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

I guarantee you won't be disappointed.

---

### Post by byuu on 2010-01-01
> hmm bsnes runs extremely slow...

For Linux, you'd need to set the video driver to either OpenGL or X-Video, otherwise it will crawl. But a Turion is pushing it, especially for SuperFX / SA-1 games.

I would also recommend Snes9X-GTK, but I would suggest waiting for v1.52. It should hopefully be out soon, it'll integrate in Snes9X-GTK as part of the official codebase, and it will have an all-new sound core that's much, much better.

---

### Post by switch10 on 2010-01-01
> **benmoran said:**
> Take my advice. I was a loooooong time Zsnes user, but experienced similar problems as you. I also didn't care for the snes9x versions in the repos. 

Then I found Snes9x-gtk. It's much better than I expected. It supports all the options you could hope for, and it actually fits into the Ubuntu desktop and behaves like you would expect. 

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

I guarantee you won't be disappointed.

I tried snes9x-gtk.  it said my gamepad drivers were too old...  I am happy as could be with zsnes, no problems with it other than the sound issue.  But i guess i can just deal with it, or shut the sound off completely...  I have many saved games with zsnes as well.

---

### Post by farrell2k on 2010-01-02
Have you tried using a different audio switch other than the default SDL?

You can do zsnes -ad then do sdl, alsa, oss, etc.    

try zsnes -ad alsa

Otherwise, use XE from xe-emulator.com   It doesn't play FX games, as far as I know, but it has played everything else I have tried with it.

---

### Post by KIAaze on 2010-01-03
```
zsnes -ad oss
```
worked best for me.
Thanks. :)

---

