---
title: "Uninstalling gnome?"
date: 2005-03-23
forum: Desktop Environments
---

### Post by Stephen-I-M on 2005-03-23
Is it possible and safe to uninstall gnome? Bonus points for how to use dpkg/apt to uninstall everything with 'gnome' in the title.

Stephen

---

### Post by az on 2005-03-23
remove libgnome-2.0


Is it safe?  What do you mean?  What do you expect there to be?  You will be losing a lot of stuff.  You will still be able to boot, though.

---

### Post by Stephen-I-M on 2005-03-23
[QUOTE=azz]remove libgnome-2.0
Is it safe?  What do you mean?  What do you expect there to be?  You will be losing a lot of stuff.  You will still be able to boot, though.[/QUOTE]
Thanks for the reply. I can see how most gnomish packages would need libgnome. I can always reinstall it if an app that I want to keep needs it.

I was just worried that, since ubuntu was based first on the gnome desktop that I could break something needed by the distribution.

Stephen

---

### Post by dawynn on 2005-03-23
Generally, I would keep ubuntu-base installed, and keep *either* ubuntu-desktop or kubuntu-desktop installed.  Since this is the KDE forum, you're probably looking at keeping kubuntu-desktop.  As far as I can tell, they've tried with the kubuntu-desktop to replicate the same functionality as you have with ubuntu-desktop.

As long as you have ubuntu-base and [ubuntu-desktop | kubuntu-desktop] installed, your system should be "safe" -- as in bootable.  Note: depending on the hardware installed in your system, this may not include everything that you need.   (This would not include such things as support for Nvidia cards, Reiser drives, DVD burning software, etc)

Good luck!

---

### Post by Stephen-I-M on 2005-03-23
[QUOTE=dawynn]
As long as you have ubuntu-base and [ubuntu-desktop | kubuntu-desktop] installed, your system should be "safe" -- as in bootable.[/QUOTE]

I tried uninstalling kynaptic (there's an example of where I liked the gtk+ app more) and it wanted to uninstall kubuntu-desktop too. I let it go ahead, since it didn't actually try to uninstall other kde pieces. Hope this won't bite me later.

Stephen

---

### Post by Stephen-I-M on 2005-03-23
I was able to uninstall most things gnome. One issue is that the package for firefox wants to pull in lots of gnome stuff. I'm thinking that it can't be that way for debian.

The installer at mozilla.org works fine, though.

Stephen

---

