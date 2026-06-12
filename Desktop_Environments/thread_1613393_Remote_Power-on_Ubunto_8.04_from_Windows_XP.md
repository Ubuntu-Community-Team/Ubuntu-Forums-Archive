---
title: "Remote Power-on Ubunto 8.04 from Windows XP"
date: 2010-11-04
forum: Desktop Environments
---

### Post by xp_newbie on 2010-11-04
I found a nice tutorial on "[how to power on remotely with WakeOnLan (WOL)]("http://ubuntuforums.org/showthread.php?t=360901")"

Problem is... it's for a Linux-to-Linux setup.

I need to be able to achieve exactly the same but turn on Ubuntu 8.04 (64-bit) from a Windows XP laptop.

I can't really do "sudo apt-get install wakeonlan" on Windows XP.

Can you recommend a way to do that?

Thanks.

---

### Post by tlroche on 2010-11-04
> **xp_newbie said:**
> I need to [wake-on-lan] Ubuntu 8.04 (64-bit) from a Windows XP laptop.

I can't really do "sudo apt-get install wakeonlan" on Windows XP.

Whenever you must use Windows, you should first get [Cygwin]("http://cygwin.com/"). I haven't used it for this specific task, but Cygwin adds lots linuxy goodness to Windows, and should enable you to do one of the following (et al):
[LIST=1]
[*]compile WOL from source as mentioned [here]("http://hepunx.rl.ac.uk/~adye/software/cygwin/cygwin.html") (or use his binaries)
[*]install [python]("http://cygwin.com/packages/python/"), and do [this]("http://www.sgvulcan.com/wake-on-lan-a-machine-using-python-wol/")
[/LIST]
Similar to item=2, you could also install Java and do [this]("http://www.jibble.org/wake-on-lan/").

---

### Post by xp_newbie on 2010-11-04
> **tlroche said:**
> 
[LIST=1]
[*]compile WOL from source as mentioned [here]("http://hepunx.rl.ac.uk/~adye/software/cygwin/cygwin.html") (or use his binaries)
[*]install [python]("http://cygwin.com/packages/python/"), and do [this]("http://www.sgvulcan.com/wake-on-lan-a-machine-using-python-wol/")
[/LIST]
Similar to item=2, you could also install Java and do [this]("http://www.jibble.org/wake-on-lan/").


Ouch... I was hoping to get away with much less than compiling, building and installing several packages.

Is there a simple, tiny downloadable .exe for Windows XP that is equivalent to Ubuntu's **wakeonlan**?

Thanks.

---

