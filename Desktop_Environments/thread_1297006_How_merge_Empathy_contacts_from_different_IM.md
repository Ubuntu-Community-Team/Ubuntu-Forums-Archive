---
title: "How merge Empathy contacts from different IM?"
date: 2009-10-21
forum: Desktop Environments
---

### Post by frankabel on 2009-10-21
Hi all,

How merge Empathy contacts from different IMs?

Example, I have a friend with an account on yahoo, other on hotmail and other on gmail. I need merge those three contact, so in the contact list windows just appear one contact with those three contacts inside and then I can chat with those compose contact and the first IM available is picked to send the message, just like Pidgin do.

Cheers
Frank Abel

---

### Post by CoolGoose on 2009-10-29
+1, is it possible ?

---

### Post by justleen on 2009-10-29
+1.. Dont think you can... Which really sucks if that is the case!

---

### Post by jjmatt on 2009-11-08
Weak sauce. This needs to be added. Anybody know if it's in the works?

I like some of the features of empathy, but it (STILL) needs a lot of work. Kind of upset that it replaced pidgin in Karmic.

btw, using 2.28.1.1

---

### Post by zasf on 2009-11-14
looking at bugs on bugzilla.gnome.org, it seems that there is not one open about this subject. Moreover in the list it is not possible to recognize which im a friend is using.

Should we open one?

---

### Post by phjr on 2009-11-15
this is the last feature I need in empathy to switch from pidgin; until then, it's a no-go for me :-( if anyone feels up to it, please do open a feature request somewhere (closest to the developers)

---

### Post by networkspeedy on 2010-04-03
+1

This problem with empathy is extremely annoying.  I consider it a significant step backward from functionality in pidgin that I've come to consider as standard for several years.  Several years!  Empathy fails on this one.

Ubuntu was wrong to move so quickly to empathy when it isn't ready for prime time.

---

### Post by priegog on 2010-04-30
In case anyone is still interested there is a bug [here.]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/256478") Let's all subscribe and comment (ie: make some noise) so that this can be taken up upstream for them to add it. In the meantime (and it due to me finding a couple of more bugs in empathy) I'm going to be switching pack to pidgin for this release at least.

---

### Post by dannymichel on 2010-04-30
It's beyond my comprehension as to why ubuntu would chose empathy as a default. It's obviously not ready

---

### Post by Linfreak on 2010-09-26
+1.. Would love to see this feature in future Empathy versions..

---

### Post by Linfreak on 2010-09-26
To all those badly waiting for this feature!! Maverick's got it!!

Ref : [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/256478](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/256478)

This bug was fixed in the package empathy - 2.31.91.1-0ubuntu1

---------------
empathy (2.31.91.1-0ubuntu1) maverick; urgency=low

  * New upstream release
  * debian/control:
    - add libgcr-dev build-dep
  * debian/patches/91_git_unref_empathyindividualview_later.patch:
    - additional fix from git requested by upstream

empathy (2.31.91-0ubuntu1) maverick; urgency=low

  * New upstream release:
    - Support metacontacts (Travis Treitter, Philip Treitter) (LP: #256478)
    - Initial empathy account wizard (Welcome Screen) does not offer IRC as an
      account (Guillaume Desmottes) (LP: #433714)
    - Dragging and dropping a chat tab hides the original window (Guillaume
      Desmottes) (LP: #512746)
    - After upgrade to 2.31.90 (from 2.31.6) empathy does not list users of irc
      chat (Guillaume Desmottes) (LP: #622684)
  * debian/control:
    - Bump build-depends on libgnome-keyring-dev, libfolks-dev,
      libfolks-telepathy-dev, libnautilus-sendto-dev
    - Add build-depends on libgnutls-dev
    - Drop build-depends on libebook1.2-dev
 -- Didier Roche <didrocks@ubuntu.com> Thu, 02 Sep 2010 12:40:03 +0200


This bug was fixed in the package empathy - 2.31.91.1-0ubuntu1

---------------
empathy (2.31.91.1-0ubuntu1) maverick; urgency=low

  * New upstream release
  * debian/control:
    - add libgcr-dev build-dep
  * debian/patches/91_git_unref_empathyindividualview_later.patch:
    - additional fix from git requested by upstream

empathy (2.31.91-0ubuntu1) maverick; urgency=low

  * New upstream release:
    - Support metacontacts (Travis Treitter, Philip Treitter) (LP: #256478)
    - Initial empathy account wizard (Welcome Screen) does not offer IRC as an
      account (Guillaume Desmottes) (LP: #433714)
    - Dragging and dropping a chat tab hides the original window (Guillaume
      Desmottes) (LP: #512746)
    - After upgrade to 2.31.90 (from 2.31.6) empathy does not list users of irc
      chat (Guillaume Desmottes) (LP: #622684)
  * debian/control:
    - Bump build-depends on libgnome-keyring-dev, libfolks-dev,
      libfolks-telepathy-dev, libnautilus-sendto-dev
    - Add build-depends on libgnutls-dev
    - Drop build-depends on libebook1.2-dev
 -- Didier Roche <didrocks@ubuntu.com> Thu, 02 Sep 2010 12:40:03 +0200

This bug was fixed in the package empathy - 2.31.91.1-0ubuntu1

---------------
empathy (2.31.91.1-0ubuntu1) maverick; urgency=low

  * New upstream release
  * debian/control:
    - add libgcr-dev build-dep
  * debian/patches/91_git_unref_empathyindividualview_later.patch:
    - additional fix from git requested by upstream

empathy (2.31.91-0ubuntu1) maverick; urgency=low

  * New upstream release:
    - Support metacontacts (Travis Treitter, Philip Treitter) (LP: #256478)
    - Initial empathy account wizard (Welcome Screen) does not offer IRC as an
      account (Guillaume Desmottes) (LP: #433714)
    - Dragging and dropping a chat tab hides the original window (Guillaume
      Desmottes) (LP: #512746)
    - After upgrade to 2.31.90 (from 2.31.6) empathy does not list users of irc
      chat (Guillaume Desmottes) (LP: #622684)
  * debian/control:
    - Bump build-depends on libgnome-keyring-dev, libfolks-dev,
      libfolks-telepathy-dev, libnautilus-sendto-dev
    - Add build-depends on libgnutls-dev
    - Drop build-depends on libebook1.2-dev
 -- Didier Roche <didrocks@ubuntu.com> Thu, 02 Sep 2010 12:40:03 +0200


Yet to see if its available for lucid.

Cheers,
Siva

---

### Post by jarreboum on 2010-10-26
How do I install this version when I'm using 10.4? I tried to add the official depot but I'm still on 2.30.2.

---

