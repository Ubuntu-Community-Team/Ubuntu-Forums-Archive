---
title: "Differences between server and Ubuntu and Xubuntu"
date: 2006-07-06
forum: Desktop Environments
---

### Post by Elim on 2006-07-06
I recently tried (and failed) to upgrade to Dapper (unless someone can help me [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=210450")).
So this got me thinking about installing from CD, and of course I've got a question.

Right now I'm running Ubuntu with an added Xfce session.  Is there a difference between the server install with ubuntu-desktop and xubuntu-desktop, Ubuntu desktop install with xubuntu-desktop, and Xubuntu desktop install with ubuntu-desktop?  Also, is there a difference between updating an old version and installing a fresh version (e.g. with Windows it's best to install a fresh install of XP)?

---

### Post by atoponce on 2006-07-06
> **Elim said:**
> I recently tried (and failed) to upgrade to Dapper (unless someone can help me [here]("http://ubuntuforums.org/showthread.php?t=210450")).
So this got me thinking about installing from CD, and of course I've got a question.

Right now I'm running Ubuntu with an added Xfce session.  Is there a difference between the server install with ubuntu-desktop and xubuntu-desktop, Ubuntu desktop install with xubuntu-desktop, and Xubuntu desktop install with ubuntu-desktop?

Nope.  Not that I am aware.

>  Also, is there a difference between updating an old version and installing a fresh version (e.g. with Windows it's best to install a fresh install of XP)?

Yes.  Different config files will be written to the OS during an upgrade versus what you may currently have.  This could keep software from being updated, and thus, running a "hacked" version of your OS versus new.

---

### Post by Elim on 2006-07-07
> **atoponce said:**
> 
Yes.  Different config files will be written to the OS during an upgrade versus what you may currently have.  This could keep software from being updated, and thus, running a "hacked" version of your OS versus new.

I take it, then, that it would be best to just burn an ISO each time a new release comes out, rather than attempting the dist-upgrade?

---

### Post by i_m_meen on 2006-07-07
Basically, dist-upgrade shoule be easier. And it asks you if you want to keep the old config files. Practically, things can go wrong, and you must be able to fix them, should they arise.

---

### Post by atoponce on 2006-07-07
> **Elim said:**
> I take it, then, that it would be best to just burn an ISO each time a new release comes out, rather than attempting the dist-upgrade? Just do a dist-upgrade unless you are like a typical Gentoo user, and hack every config file in your system.  I have done dist-upgrades since Warty, and I am running Ubuntu just fine.  I have had some hiccups along the way, that I know a clean install would not have otherwise given me, but at least I learned new things.  Generally, it has been asprin-free.

---

