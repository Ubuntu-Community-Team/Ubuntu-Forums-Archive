---
title: "Macromedia Flash Freezing Firefox"
date: 2005-10-16
forum: Desktop Environments
---

### Post by cwaldbieser on 2005-10-16
I just upgraded to Breezy from Hoary, and I noticed that I am having a couple problems with web pages with Flash in them.  The animations seem to work, but I do not hear any sound.  Also, when I try to leave the page, Firefox freezes.  If I simply close the browser (rather than attempt to navigate away), the window closes, but the process "firefox-bin" is still hanging out there and needs to be manually killed before the browser can be opened again.

Happens under Kubuntu and Ubuntu.  Anyone else experiencing this?  I have noticed that others have been having trouble with the sound, but I didn't see where anyone was reporting the freezing.

Any ideas are welcome.

---

### Post by Knome_fan on 2005-10-16
As any ideas are welcome, here's a wild guess:

Did you by any chance install flash with firefox (you now, using the download missing plugin stuff?). If so, uninstall it and install the flash from synaptic (I think it is in multiverse) and see if the problem goes away.

---

### Post by bionnaki on 2005-10-16
how do you uninstall a plugin?

---

### Post by adis on 2005-10-16
I had this problem some time ago. It can be fixed with:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Cheers.

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=Knome_fan]As any ideas are welcome, here's a wild guess:

Did you by any chance install flash with firefox (you now, using the download missing plugin stuff?). If so, uninstall it and install the flash from synaptic (I think it is in multiverse) and see if the problem goes away.[/QUOTE]
I tried removing all the flash plugins from both system and home directories, and I tried reinstalling the plugins from breezy multiverse (free and non-free) as well as from Macromedia's site.  The problem persists.

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=bionnaki]how do you uninstall a plugin?[/QUOTE]
You can uninstall them through synaptic if that is how you originally installed it.  Otherwise you go to the plugins directory and just remove the files.  You might have a couple plugins directories (usually under /usr/lib/mozilla/plugins and ~/.mozilla/plugins).

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=adis]I had this problem some time ago. It can be fixed with:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Cheers.[/QUOTE]
I tried doing this.  It doesn't really seem to make a difference.

I also noticed that not all animations seem to be working.  For example, [http://www.transformers.com]("http://www.transformers.com") shows the animations without a problem.  However, [http://www.badgerx3.com]("http://www.badgerx3.com") does not seem to play-- the badger just doesn't move.  If right click and toggle the play button, a single badger will bounce, but it doesn't seem to get further than that.

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=cwaldbieser]I tried doing this.  It doesn't really seem to make a difference.

I also noticed that not all animations seem to be working.  For example, [http://www.transformers.com]("http://www.transformers.com") shows the animations without a problem.  However, [http://www.badgerx3.com]("http://www.badgerx3.com") does not seem to play-- the badger just doesn't move.  If right click and toggle the play button, a single badger will bounce, but it doesn't seem to get further than that.[/QUOTE]
After a little more experimentation, I found out that a setting in my /etc/mozilla-firefox/mozilla-firefoxrc was the problem.  FIREFOX_DSP is normally set to "auto".  I set it to artsdsp (since I am using aRts with Kubuntu) and that seemed to do the trick.  I now have sound and the flash animations play without freezing.

Thanks to everyone who gave me ideas!

---

### Post by leonardoo on 2006-04-10
hello, in my file i've got "none", i've set it to "auto", the problem persists :( Amically.

i've got the gnome.

---

### Post by mistypotato on 2007-02-11
> **adis said:**
> I had this problem some time ago. It can be fixed with:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Cheers.


ADIS.....
I was just thumbing through looking for a solution to my flash web pages closing abruply and I just copied the sudo line above, pasted it into a terminal, ran it and VIOLA!....fixed !!!!:KS 

Thanks !!   I've been fuddling with this for a couple months and this fixed it!

---

