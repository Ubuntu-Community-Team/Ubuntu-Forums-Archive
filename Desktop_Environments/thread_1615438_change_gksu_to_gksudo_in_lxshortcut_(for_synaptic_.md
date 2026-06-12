---
title: "change gksu to gksudo in lxshortcut (for synaptic package manager)"
date: 2010-11-07
forum: Desktop Environments
---

### Post by prolefeedprocessor on 2010-11-07
I installed lubuntu 10.10 from a minimal netinstall.  For some reason, the main menu entry for synaptic package manager uses gksu instead of gksudo at the beginning of the command, as revealed by right-clicking the entry, then clicking "properties".  This, of course, precludes the ability to access the program unless you're among the few who have activated the root user account.  That's a problem in and of itself, but it's been recognized elsewhere.

However, after I fixed the command and clicked "ok", nothing changed.  I opened up the little properties menu again and it was gksu, as though I hadn't fixed the command.

The properties window is a mysterious little program called lxshortcut.  I suspect that if I run lxshortcut using sudo, then the changes I make will actually stick.  Problem is, I don't know how to find the actual location of the main menu's SPM shortcut/launcher-thingy.  Nor are there any clear instructions on how to use lxshortcut in terminal.  I flailed about with my best interpretation of vague instructions, but to no avail.

I downloaded alacarte (which is, of course, intended for gnome), and I got the software sources entry to show up in the list, but nothing else in the program responded when I clicked.  The whole experience in alacarte was weird and unhelpful and somehow I've outright removed the menu entry for synaptic.  And that's fine, I barely use it anyway, but Software Sources also has the same gksu problem, and I actually use that one.

So how do I change the command associated with one of the preferences in the lxde/lubuntu main menu?

---

### Post by kerry_s on 2010-11-07
you don't need to, lubuntu is based on ubuntu & ubuntu is a sudo system so gksu would be linked to gksudo.

run **gksu-properties** in a terminal & see what the setting is.

running gksu is the same as running gksudo on ubuntu based distros.

---

### Post by prolefeedprocessor on 2010-11-07
Thank you! I was looking at the problem in the completely wrong way! I'm still curious to know how to make changes stick when editing lxde menu shortcuts, but now I can tackle the synaptic problem just fine.

Update: The gksu problem was exponentially easier than I was making it.  I just switched the authentication mode from "su" to "sudo" and everything was all better.

---

### Post by Vryko Lakas on 2010-11-09
I *was* having the same problem with Xfce after a minimal install and wondering how to fix it. This fix worked for me too. 

Strangely, a similar min. install with LXDE had Synaptic working correctly from the menu. Maybe it was because in the first install I only added Synaptic after the desktop, but in other system I added both the DE and package manager in the same apt-get line?

---

### Post by Kiori on 2011-07-07
Thanks kerry_s this post saved my day today.
cheers

---

