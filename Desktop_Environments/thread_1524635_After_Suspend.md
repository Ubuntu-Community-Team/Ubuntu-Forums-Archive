---
title: "After Suspend"
date: 2010-07-05
forum: Desktop Environments
---

### Post by m.e.danko on 2010-07-05
Hello all, I have a really frustrating problem, whenever my machine goes on standby, or I manually invoke the suspend feature, when I attempt to log back in, the computer just sits there for ages, I mean it doesn't actually log me back in. It doesn't goes past the login screen where I enter my password.

I've never experienced this before in a previous version of ubuntu, there is just one thing that I've done different with my installation of 10.04, and that was I changed my login password and I believe, don't quote me on this, I believe it only happened after I changed my login password, any help would be greatly appreciated.

Many thanks, Martin. 

PS I really can't be bothered to do a re-install, as I have everything setup how I like it, I have VIM and a load of other apps configured just as I like.

---

### Post by SaintDanBert on 2010-07-05
I have a similar problem, different symptoms, but neither suspend-to-ram (sleep) or suspend-to-disk (hibernate) work for me.

Ubuntu Lucid 64-bit, Lenovo ThinkPad X61-tablet

---

### Post by m.e.danko on 2010-07-06
> **SaintDanBert said:**
> I have a similar problem, different symptoms, but neither suspend-to-ram (sleep) or suspend-to-disk (hibernate) work for me.

Ubuntu Lucid 64-bit, Lenovo ThinkPad X61-tablet

My one suspends and/or hibernates fine, wakes up properly and asks me to enter a password (once I move the mouse or touch the keyboard), it's just it never accepts the passwords and "thinks" about for eternity and never actually logs me back in. I then have to do the 'old CTRL-ALT-BACKSPACE to get GDM to restart which looses my session which is very, very annoying! It also happens if my screen locks so I would assume it has nothing to do with the actually suspend/hibernate function.

Anyone have any advice? please help! Thanks. :D

---

### Post by rayray519 on 2010-08-19
I too am seeing the same thing - the one thing I noticed is that the scroll and cap lock lights will be blinking on the keyboard.

I can't bring it back unless I do a complete manual power off, and unplug/replug at the back of the PC.  Windows 7 was previously on the box without any power issues.

Thoughts??

---

### Post by ChrisBuchholz on 2010-08-20
Have you guys tried using the s2ram and s2disk features found in the uswsusp package in the universal ubuntu repository?

Although I'm not using any of the same computers as you, I could not get suspend and hibernate to work with Ubuntu on my laptop either. So I found the uswsusp package, and tried the s2ram and s2disk, and they not only work really well. They also seem to work better and faster than what bundles with ubuntu, from what I hear from others.

You should try it out -- just install the uswsusp package and then try *sudo s2ram* (if it says you machine is unknown, use the *--force* argument) and *sudo s2disk* in a terminal and see if it works.
If it does, I have written an article about how to get ubuntu to use that as the default suspend and hibernation mechanism: [http://chrisbuchholz.name/journal/fixing-suspend-and-hibernation-on-macbook-pro-running-ubuntu](http://chrisbuchholz.name/journal/fixing-suspend-and-hibernation-on-macbook-pro-running-ubuntu)
The article is targeted for Macs, but it would be the same on your computers too.

---

