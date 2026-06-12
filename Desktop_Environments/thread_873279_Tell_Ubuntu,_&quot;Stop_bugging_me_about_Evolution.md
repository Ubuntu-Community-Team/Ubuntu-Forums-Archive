---
title: "Tell Ubuntu, &quot;Stop bugging me about Evolution&quot;"
date: 2008-07-28
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2008-07-28
I don't want to ever use Evolution.  It's not that there's anything wrong with it.  It's just that I'm not using my Linux PC for e-mail, at least not yet.  If I do decide to start using it for e-mail, I'll use Thunderbird because it's what's on my Windows PC.  It's what I'm used to; plus, there's a chance I could transfer my e-mails over from my Windows PC.  

However, every time Ubuntu tells me about available updates, there's Evolution.  How do I tell it to quit offering it?

---

### Post by jay019 on 2008-07-28
Uninstall it?

---

### Post by p_quarles on 2008-07-28
You can remove Evolution using the Add/Remove Programs tool. The only consequence of this is that it will also remove the "ubuntu-desktop" metapackage. This doesn't harm your system, since that package is only a list of dependencies (including Evolution), but it *may* require you to reinstall a few things you thought you already had. 

It also may present minor and fixable difficulties when and if you upgrade to the next Ubuntu release.

---

### Post by Tom_ZeCat on 2008-07-28
I want to be really careful about uninstalling Evolution.  On my other Linux PC, I went through the Synaptec Package Manager and told it to uninstall everything I could find that said Evolution in it.  The result was that I all of a sudden had no more menus on my desktop.  

What I really should do is find and install some kind of equivalent to Acronis True Image or Norton Ghost so that I can try things knowing I can just do a system rollback if I @#$% up my system.  

Acronis True Image is supposed to work on my Linux PC via a bootable CD.  In fact, that bootable CD is even Linux based.  However, I've not been able to get it to work.  It's a shame because Acronis has been my friggin' savior many times on my Windows PC.  I had a total hard drive crash on that PC and didn't lose so much as an e-mail.

---

### Post by p_quarles on 2008-07-28
Removing Evolution will not automatically remove everything else in the ubuntu-desktop package unless you tell it to. The only core component of Gnome that is part of the Evolution is the calendar. Unfortunately, that will go away if you remove Evolution.

The other packages will only go away if you run the "autoremove" option in Synaptic. They can then be reinstalled. You may find it helpful to make a note of everything that is removed by Synaptic.

You can restore everything by installing the "ubuntu-desktop" metapackage in Synaptic. 

For a restorable system image, take a look at Clonezilla.

---

### Post by Tom_ZeCat on 2008-07-29
Your help is very appreciated.  Those are excellent suggestions.  And I can't wait to try Clonezilla.

---

### Post by chinasteve2000 on 2008-08-25
There's a more recent post about this--

So for additional advise on uninstalling Evolution, with what seems to be important warnings, please also note this thread:
[URL="http://ubuntuforums.org/showthread.php?t=891058"]
[COLOR="Blue"][ubuntu]   Remove Evolution Mail?[/COLOR][/URL]

---

