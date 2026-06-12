---
title: "Konqueror a Crash Machine in 5.04"
date: 2005-06-18
forum: Desktop Environments
---

### Post by polo_step on 2005-06-18
Don't have any idea why, but in both the Live and now the Install version of Kubuntu 5.04, Konqueror crashes a lot on pages like portals and webmail where there's apparently a lot of complex stuff going on as you're doing mail and soforth.  Bam!, it just *vanishes*.

The error message is "signal 11 SIGSEGV"

I'd like to replace Konqueror with FireFox, but as a new user, I'm not absolutely sure how to go about it.

If Konqueror can be fixed, I might stick with it a bit.

I need one solution of the other.

As always, thanks for any help.

(let's see if I can post this and keep the browser up...)

---

### Post by altorus on 2005-06-18
As far as installing firefox goes, grab a terminal and type:

sudo apt-get install mozilla-firefox gtk2-engines-gtk-qt

mozilla-firefox is the browser.  gtk-engines-gtk-qt is a little app that makes gtk apps look native under kde.  They are seriously fugly otherwise.

---

### Post by deadlands on 2005-06-18
[QUOTE=altorus]As far as installing firefox goes, grab a terminal and type:

sudo apt-get install mozilla-firefox gtk2-engines-gtk-qt

mozilla-firefox is the browser.  gtk-engines-gtk-qt is a little app that makes gtk apps look native under kde.  They are seriously fugly otherwise.[/QUOTE]
 Have you upgraded to KDE 3.4.1?

---

### Post by polo_step on 2005-06-18
[QUOTE=deadlands]Have you upgraded to KDE 3.4.1?[/QUOTE]
No.  I just installed this thing last night.  I assumed that the version would be the latest.  I'm pretty bugged with what I see of Konqueror so far, just in the way it does stuff compared to FireFox, which is a lot more intuitive for a former IE user and manages to deal with all the cookies and popups and other garbage more intuitively.  I also have it on my XP machine.

I've stopped it crashing (for now), but there are a lot of things I'd rather have different anyway.

---

### Post by polo_step on 2005-06-18
[QUOTE=altorus]As far as installing firefox goes, grab a terminal and type:

sudo apt-get install mozilla-firefox gtk2-engines-gtk-qt
[/QUOTE]
Will try it later.

Never done this sort of thing before, so is that upgrade pretty foolproof?

Thanks...

---

### Post by polo_step on 2005-06-18
[QUOTE=altorus]As far as installing firefox goes, grab a terminal and type:

sudo apt-get install mozilla-firefox gtk2-engines-gtk-qt[/quote]

I get an error:

E: Couldn't find package gtk2-engines-gtk-qt

---

### Post by deadlands on 2005-06-19
[QUOTE=polo_step]I get an error:

E: Couldn't find package gtk2-engines-gtk-qt[/QUOTE]

You need to enable all the repositories.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Embajador on 2005-06-20
[QUOTE=polo_step]No.  I just installed this thing last night.  I assumed that the version would be the latest.  I'm pretty bugged with what I see of Konqueror so far, just in the way it does stuff compared to FireFox, which is a lot more intuitive for a former IE user and manages to deal with all the cookies and popups and other garbage more intuitively.  I also have it on my XP machine.

I've stopped it crashing (for now), but there are a lot of things I'd rather have different anyway.[/QUOTE]
Just use Opera!  ;-) 
I think anyway that it would be a good idea to update to KDE 3.4.1

---

### Post by ykpaiha on 2005-06-20
I did n't expected to be so desapointed by Kubuntu, even installed over the main Ubuntu

A lot of crashes
Konqueror,Kaffeine...
Wrong translations (kaffeine, amarock....)
k3b unstable sometime even not burning ( empty dvds or cds)
wrong mime-types and menus
Hal working once in a time
dma not included, sometime and at random X refuses to open....
Even Mozilla in crashing and cannot even get its themes and extentions unless you download the moz-install!!!

I didn't have those issues on a Mepis box

Tell me if I am wrong but, I think, the whole team is working on the next version and didn't realy looked  carefully deep on this distro....

The worse is that even you upload the 3.41 version the prob remain and some more appears

If someone have some clues you are welcomed.
 [-X  [-X  [-X  [-X  [-X

---

### Post by dejitarob on 2005-06-20
It's very difficult to try to help when you are that broad about your problems. It would immensely help us if you were more specific. Please describe the problems you are having in the greatest detail possible with the exact errors you are receiving.

---

