---
title: "new: mednafen 0.8.a"
date: 2008-10-28
forum: Gaming &amp; Leisure
---

### Post by FranMichaels on 2008-10-28
Just a heads up, new [mednafen]("http://mednafen.sourceforge.net/") release. Notably, some support for mapper 163 on nes added.

This allows some odd roms to work... ;)
For example, this unofficial ff7 clone:

---

### Post by Disreali on 2008-10-29
Sweet!

Thanks again, FranMichaels. Your knowledge of the various game emulators has been a great help to me and my retro game obsession.

Did you build the new mednafen yourself, or is there a deb somewhere?

I absolutely love the pics you included, but I believe I'm not allowed to ask about the game. Oh well... Google is is fun

---

### Post by FranMichaels on 2008-10-29
Thanks, I'm very glad. :D

Anyway, just built it from the tarball.


This should do it, (but not sure if something is missing as I installed the dependencies long ago.)

```
sudo apt-get install build-essential
sudo apt-get build-dep mednafen

```

then just extract the tar.bz2, (let's assume in your home folder)
```
 
cd mednafen 
./autogen.sh
./configure
make
sudo make install
```

---

### Post by BigSilly on 2008-10-29
Thanks very much for this. I absolutely love Mednafen. A new release is always a good excuse for some cheering. So with that in mind - **Huzzah**!

:biggrin:

---

### Post by Disreali on 2008-11-09
I've finally succeeded in building a deb of mednefen.  :KS

Now, I am searching for info on loading save states.  Any help would be appreciated.  I had previously been using Kega Fusion on WinXP to play a couple sms games.  Can I load the Kega save states into mednafen?  Am I out of luck?  I really want to completely dump M$, but I'm well into Phantasy Star and really don't want to start over.

Thanks in advance

---

### Post by Dodongo Dislikes Smoke on 2008-11-10
How is everyone configuring sound in Mednafen?  Every since PulseAudio was added things have been really laggy.  The SDL driver worked best for me in Hardy.  Now in Intrepid, OSS with the -sounddevice /dev/dsp/ option works best, which is to say not very well.

I'd love to see native PulseAudio support in Mednafen soon.

---

### Post by Disreali on 2008-11-11
> **Dodongo Dislikes Smoke said:**
> How is everyone configuring sound in Mednafen?  Every since PulseAudio was added things have been really laggy.  The SDL driver worked best for me in Hardy.  Now in Intrepid, OSS with the -sounddevice /dev/dsp/ option works best, which is to say not very well.

I'd love to see native PulseAudio support in Mednafen soon.


I've adopted a 'wait and see' stance on 8.10 because of these types of situations.

I suggest asking your question on the Mednafen forums, as the devs don't read posts here.  [http://forum.fobby.net/](http://forum.fobby.net/)

---

### Post by Dodongo Dislikes Smoke on 2008-11-11
> **Disreali said:**
> I've adopted a 'wait and see' stance on 8.10 because of these types of situations.

I suggest asking your question on the Mednafen forums, as the devs don't read posts here.  [http://forum.fobby.net/](http://forum.fobby.net/)

I wish I had done the same.  I've been using Ubuntu for nearly four years now, and it wasn't until the last two releases that I lost functionality after an upgrade.

There was a thread about it on Mednafen's boards a couple months ago, but it quickly died after the dude requesting it switched to OSS4.  I hate to pester open source developers and seem ungrateful, but I might try picking up that torch.

---

### Post by Mega_Mike on 2008-11-22
When I run Dracula X under Mednafen though the gameplay is dead on, the music is too fast.  Has anyone else experienced this (in Ubuntu Intrepid 8.10)?

---

