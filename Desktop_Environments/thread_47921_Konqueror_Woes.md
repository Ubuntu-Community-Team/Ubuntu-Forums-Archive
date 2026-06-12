---
title: "Konqueror Woes"
date: 2005-07-10
forum: Desktop Environments
---

### Post by davidgypsy on 2005-07-10
.

---

### Post by JPatrick on 2005-07-10
> I already have Ubuntu installed, how can I get Kubuntu?

   1. Make sure you are using hoary in your /etc/apt/sources.list
   2. apt-get install kubuntu-desktop

See InstallingKDE for a full explanation.

Why didn't you do that instead of an install from a CD?

---

### Post by davidgypsy on 2005-07-10
[QUOTE=JPatrick]Why didn't you do that instead of an install from a CD?[/QUOTE]

The curse of a very slow dialup connection. But should it make a difference?

---

### Post by ltmon on 2005-07-10
[QUOTE=davidgypsy]I have been using Ubuntu for some time now, but I really like KDE and decided to try to install Kubuntu on top of Ubuntu. I added the Kubuntu disc to my repository and installed it, and it ran well for about one day. Now Konqueror has become totally unstable and crashes every few minutes. Is this a "normal" problem? Can I fix it? All help would be appreciated![/QUOTE]

This sounds like an unfortunate bug in kubuntu 5.0.4 that some (but not all) users are reporting. 

To fix it, either search this thread: [http://ubuntuforums.org/showthread.php?t=26043](http://ubuntuforums.org/showthread.php?t=26043)

or upgrade to kde 3.4.1

Cheers,

L.

---

### Post by Terracotta on 2005-07-11
[QUOTE=davidgypsy]The curse of a very slow dialup connection. But should it make a difference?[/QUOTE]

It makes a difference, since the kubuntu release on the cd is quite (*euheum*) buggy, if you do a kubuntu-desktop install, or a full update it should be A LOT less buggy

---

### Post by SysFail on 2005-07-11
Upgrading to kde 3.4.1 will not guarantee a fix.  Upgrading did NOT fix mine.

---

### Post by davidgypsy on 2005-07-11
[QUOTE=Terracotta]It makes a difference, since the kubuntu release on the cd is quite (*euheum*) buggy, if you do a kubuntu-desktop install, or a full update it should be A LOT less buggy[/QUOTE]

Nope, didn't work.:-? Still buggy, but it seems there is a general problem with Konq at the moment. :roll:

Back to Gnome! Fast, stable, reliable! ;-)

---

### Post by McQuaid on 2005-07-11
This might not actually solve it for you but it might be worth a try.  I am having a problem with khotkeys always crashing.  Now, I haven't actually solved it but I realized that an account that never ran kde before has no problems with khotkeys.  So it seems like a transition bug going from 3.4 to 3.4.1.  

Try creating a new dummy account just to see if the problem disappears.  If it does, you can tackle it one way by deleting your ~.kde dir (back it up first) and login and kde will create a new .kde dir.  Then you can copy over stuff from the previous .kde dir so you can restore your bookmarks etc.

---

### Post by SysFail on 2005-07-12
That was a good idea...I thought that might fix it...but it didn't  ](*,) 
same exact problems with new user etc...

---

### Post by davidgypsy on 2005-07-24
Hooray! Problem solved!! \\:D/ I uninstalled the kde desktop, including Konqueror etc. and then installed KDE 3.4.1 from the repositories listed at the Kubuntu site, and voila! IT WORKED! Stability at last!:):):)

---

