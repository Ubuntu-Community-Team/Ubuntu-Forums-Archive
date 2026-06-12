---
title: "Global Copy/Paste"
date: 2005-12-05
forum: Desktop Environments
---

### Post by aspr1n on 2005-12-05
One thing I discovered recently is there is no global copy/paste setup on Ubuntu.

Eg. If the app I've copied from isn't still running the paste fails.

In WIndows I used to be able to shut that app down, and still paste the content into another app as it was available at the OS level.

How can I enable this in Ubuntu?

Cheers,

asp

---

### Post by doitashimashite on 2005-12-05
Anything you select with the mouse is automatically in your clipboard.
You can paste that anytime, in any application, by pressing your mouse wheel, or -in case you have no mouse wheel- by pressing the left and right mouse button simultaneously.

---

### Post by Jonne on 2005-12-05
That's not an answer to his question.

I find the copy-paste stuff in Ubuntu confusing too (coming from Windows). The two seperate clipboards don't help things either. 

The select>middle click is useless in most cases: Say i find an url somewhere in a text document, and I want to go to the website. I could highlight it and fire up firefox, but since the address bar is already filled in, I can't clear the address bar easily without selecting something.

---

### Post by GeneralZod on 2005-12-05
Doesn't GNOME have some kind of clipboard daemon running? I know KDE has "klipper" which is designed to eliminate this precise issue.

---

### Post by aspr1n on 2005-12-05
Hi all,

doitashimashite, Jonne is right, but I didn't know about the middle click.

Playing with it though, it isn't copy/paste it's copy/insert, it concatenates from where the curser is when you middle click, it doesn't replace what you've highlighted, which means to copy/paste with it now requires 3 actions rather than 2!

One place I regularly use the global copy/paste is with webmail. CTRL+A, CTRL+C to store the current message in the clipboard. If Firefox or the webmail dies I don't loose my message.

I confess I am somewhat dismayed that cross app copy/paste on Linux is considered an "issue".  Surely the Gnome libraries implement proper copy/paste routines.  Am I missing something here? Is Ubuntu suggesting I do it another way?

Cheers,

asp

---

### Post by linuxNewb on 2005-12-05
There is a clipboard daemon that used to work (just like windows clipboard -- copy/paste) in warty and hoary BUT DOES NOT WORK IN BREEZY!

I used to follow the instructions here to install it...
[http://ubuntuguide.org/#clipboard-daemon](http://ubuntuguide.org/#clipboard-daemon)

But it DOES NOT WORK IN BREEZY. WHY? Does anyone know why this doesn't work anymore?

---

### Post by tanari on 2005-12-16
Is there any app like klipper for GNOME?
copy/paste in breezy doesn't work well :(

---

### Post by psychicdragon on 2005-12-16
This is copied from the Gnome 2.12 release notes:
> GNOME now remembers data that you copy, even when you close the window from which it was copied. This long-standing problem has finally been solved without the performance problems usually associated with clipboard daemons, by allowing applications to explicitly request the use of this feature.
So this means that only GNOME apps will remember clipboard data? Sounds like an incredibly stupid solution to me.

---

### Post by sethmahoney on 2005-12-16
[QUOTE=psychicdragon]This is copied from the Gnome 2.12 release notes:

So this means that only GNOME apps will remember clipboard data? Sounds like an incredibly stupid solution to me.[/QUOTE]

Probably not Gnome apps only, but freedesktop.org compliant apps only (which would include KDE apps, I think).

---

### Post by psychicdragon on 2005-12-16
Why would KDE apps support this? KDE uses klipper.

There is definately nothing about this in the freedesktop.org specs:
> A remaining somewhat odd thing about X selections is that exiting the app you did a cut/copy from removes the cut/copied data from the clipboard, since the selection protocol is asynchronous and requires the source app to provide the data at paste time. The solution here would be a standardized protocol for a "clipboard daemon" so that apps could hand off their data to a daemon when they exit. Or alternatively, you can run an application such as xclipboard which constantly "harvests" clipboard selections.

---

### Post by linkunderscore on 2005-12-16
haha wow...I always wondered why I would sometimes have something I copied hours before show up in gaim window I clicked on (must have him the scroll wheel in the middle).

---

