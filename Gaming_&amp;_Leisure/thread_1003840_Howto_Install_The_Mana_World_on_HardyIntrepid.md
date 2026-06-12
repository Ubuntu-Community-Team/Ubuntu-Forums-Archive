---
title: "Howto: Install The Mana World on Hardy/Intrepid"
date: 2008-12-06
forum: Gaming &amp; Leisure
---

### Post by Grant A. on 2008-12-06
As you know, there is an Open Source MMORPG in the Hardy Heron and Intrepid Ibex repositories known as The Mana World. The current version is 0.0.27, but sadly Hardy only has 0.0.24, which is currently incompatible with the game server, and Ibex has the out of date 0.0.26. To address this issue I have created this install script to help users who don't know how to compile software, and due to the fact that guichan and The Mana World are extremely difficult to compile in (K)(X)Ubuntu.

[http://forums.themanaworld.org/viewtopic.php?f=7&t=5498]("http://forums.themanaworld.org/viewtopic.php?f=7&t=5498")

Check that topic on the support forums for the scripts! Cheers! :KS

EDIT- Support for Intrepid Ibex now built-in!

---

### Post by Vadi on 2008-12-06
Despite your good intentions, this is not the way to go. Your script does no error checking, litters the home directory with 2 folders, and does no cleanup.

It's better to ask getdeb.net to make a new package: [http://wiki.getdeb.net/Software%20scouting](http://wiki.getdeb.net/Software%20scouting)

---

### Post by Grant A. on 2008-12-06
It does not need error checking, as everything required for install is installed at the beginning of the script, therefore, no problems. On top of that, ./configure will hender the script from continuing if it finds errors, AFAIK. And the two dirs are needed for non-root installation. Also, the cleanup is not required either, as the source files need to be kept unclean so that you don't have to rerun the script to remove it. I would not prefer debs, as they would require x64 and x32 debs, which would just complicate things further. If you are interested in helping out by making a deb, be my guest. Otherwise, don't complain when you don't even attempt to fix it.

BTW- A .deb is being worked on currently for the sf.net page. Also, the uninstall script is coming shortly.

---

### Post by Vadi on 2008-12-06
No, it won't stop if ./configure failed in your script.

So I'll say this outright - _do not use this script_.

---

### Post by Grant A. on 2008-12-06
> **Vadi said:**
> No, it won't stop if ./configure failed in your script.

So I'll say this outright - _do not use this script_.

Why not? Back up your accusations.

And even if it doesn't, let me state this again:

**_ALL PREREQUISITES FOR COMPILING AND THE SCRIPT ARE INSTALLED PREVIOUS TO THE PACKAGES BEING COMPILED**_

this line in the script prevents failure:

```

sudo apt-get build-dep tmw
sudo apt-get install build-essential
sudo apt-get remove libguichan2 libguichan2-dev

```

Stick that in your pipe and smoke it.

---

### Post by jdong on 2008-12-06
Vadi has some valid points. Shell scripts do **not** terminate on abnormal return codes (ie. if some part of the procedure failed) unless the **-e** option is set on the shell for Bourne shells.

As the author of the script, it's entirely reasonable for others to make suggestions on issues in your implementation without submitting a patch :)

---

### Post by Grant A. on 2008-12-06
Yes, but blatantly saying 'do not use this script' is rather offensive, especially when the creator has no intent but to help newer users.

---

### Post by jdong on 2008-12-06
Kids, you both have good intentions but are grasping at straws to express them.


(1) When criticizing, please provide constructive criticism that gets towards the way of a resolution.

(2) When evaluating criticism, try to understand what is being pointed out and ask for clarifications if you are not clear what is meant.

---

### Post by Grant A. on 2008-12-06
I suppose you have a point there. I was acting in a non-open source spirit. I realize this now and I am sorry Vadi, and to you too jdong. Now what was this error checking you were talking about? Could you show me a way to implement it? My knowledge of BASH is quite limited.

BTW, according to Bjorn and Jaxad version 0.0.27 is coming out tomorrow, this means I need to make install scripts for both Hardy and Intrepid.

---

### Post by Vadi on 2008-12-06
> **Grant A. said:**
> Why not? Back up your accusations.

And even if it doesn't, let me state this again:

**_ALL PREREQUISITES FOR COMPILING AND THE SCRIPT ARE INSTALLED PREVIOUS TO THE PACKAGES BEING COMPILED**_

this line in the script prevents failure:

```

sudo apt-get build-dep tmw
sudo apt-get install build-essential
sudo apt-get remove libguichan2 libguichan2-dev

```

Stick that in your pipe and smoke it.

You assume in your script. Assuming is bad.

You assume the packages will get installed. What if they won't? What if the person is offline and has no CD in? They won't get installed. Your assumption fails.

---

### Post by Grant A. on 2008-12-06
> **Vadi said:**
> You assume in your script. Assuming is bad.

You assume the packages will get installed. What if they won't? What if the person is offline and has no CD in? They won't get installed. Your assumption fails.


Did you not read my above post? Btw, the script won't work period if they are offline, because it requires wget to grab files, therefore, the script will fail in its entirety. On top of that, they wouldn't obtain this script in the first place if they were offline.

---

### Post by jdong on 2008-12-06
[http://www.davidpashley.com/articles/writing-robust-shell-scripts.html](http://www.davidpashley.com/articles/writing-robust-shell-scripts.html)

This article provides some good ideas on writing bash scripts that correctly handle error conditions.


Note that "apt-get build-dep foo" requires deb-src lines too; you may want to instead list all the packages that need to be installed. It's fairly common for people to remove deb-src lines to save on apt-get update time.

---

### Post by Grant A. on 2008-12-06
> **jdong said:**
> [http://www.davidpashley.com/articles/writing-robust-shell-scripts.html](http://www.davidpashley.com/articles/writing-robust-shell-scripts.html)

This article provides some good ideas on writing bash scripts that correctly handle error conditions.


Note that "apt-get build-dep foo" requires deb-src lines too; you may want to instead list all the packages that need to be installed. It's fairly common for people to remove deb-src lines to save on apt-get update time.

Thanks :)

Would "apt-get install x" require deb-src lines aswell?

---

### Post by jdong on 2008-12-06
No, apt-get install X would work as long as 

(1) Another package manager isn't currently working
(2) The install goes smoothly as planned.

Of course, neither one of those things tends to always be true. It's probably *most* reliable if you simply ask the user to install all of the given packages by giving them the apt-get command, or list of packages to find in Synaptic.


The rest of your script looks fairly reasonable in keeping to safe places (I'd recommend building things somewhere in /tmp rather than ~/ though)

---

### Post by Grant A. on 2008-12-06
> **jdong said:**
> No, apt-get install X would work as long as 

(1) Another package manager isn't currently working
(2) The install goes smoothly as planned.

Of course, neither one of those things tends to always be true. It's probably *most* reliable if you simply ask the user to install all of the given packages by giving them the apt-get command, or list of packages to find in Synaptic.


The rest of your script looks fairly reasonable in keeping to safe places (I'd recommend building things somewhere in /tmp rather than ~/ though)

Ok, does /tmp require root access? Btw, what about making the files hidden? ~/.programs & ~/.src

---

### Post by jdong on 2008-12-06
No, any user is welcome to use /tmp and /var/tmp for temporary work. I would recommend not using ~/src as a temporary location to build things -- personally I actually store quite a bit of my development work in ~/src and don't like scripts messing with there.

I don't think it's important between ~/program or ~/.program -- I'd recommend making it clear to users exactly what it is, i.e. by putting a ~/program/README file explaining it came from this install script. you'd be surprised how much one forgets in a couple month's time!

---

### Post by Grant A. on 2008-12-06
Ok, I'll keep that in mind :)

But if any user can go there, wouldn't that mean that any remote users/attackers could modify it as well?

---

### Post by jdong on 2008-12-06
> **Grant A. said:**
> Ok, I'll keep that in mind :)

But if any user can go there, wouldn't that mean that any remote users/attackers could modify it as well?

Once you create a file in /tmp, it'll be owned by you, and no other users are allowed to change or delete it.


But in general, yes, there are several areas of the system that are free for any users to create files in. These include /tmp and /var/tmp off the top of my head. If an attacker or malicious local user wishes, he can fill up the filesystem to the brim by putting junk in /tmp or /var/tmp. This is one of the many reasons administrators of multiuser serious UNIX/LINUX machines will make as many as 5-7 separate filesystems to keep runaway activity in /tmp, /home, /var/, and so on from affecting other parts of the system.

---

### Post by Grant A. on 2008-12-06
> **jdong said:**
> But in general, yes, there are several areas of the system that are free for any users to create files in. These include /tmp and /var/tmp off the top of my head. If an attacker or malicious local user wishes, he can fill up the filesystem to the brim by putting junk in /tmp or /var/tmp. This is one of the many reasons administrators of multiuser serious UNIX/LINUX machines will make as many as 5-7 separate filesystems to keep runaway activity in /tmp, /home, /var/, and so on from affecting other parts of the system.

Ouch, that sounds like a blaring vulnerability in Linux, why has no one bothered to chown that file, or atleast make it only available to users?

EDIT- Ah, nvm, I saw the word 'local' in there. So I am assuming that attackers from somewhere else in the world are out of the question?

---

### Post by jdong on 2008-12-06
> **Grant A. said:**
> Ouch, that sounds like a blaring vulnerability in Linux, why has no one bothered to chown that file, or atleast make it only available to users?

Well, the user needs a place to store temporary files. All users need that capability. On a lot of systems, /home is a network filesystem that's costly to access compared to local filesystems like /tmp. Generally if you have a local user that's not clamped down he can do a lot of disruptive things by utilizing system resources. It's not really a "vulnerability" as much as the system giving the user his fair share of resources in an undesirable manner.

What I didn't mention before is that there's ways to limit all of this -- you can set quotas on filesystems per-user, you can set limits on CPU usage or RAM consumption using the "limits" system (manpage: ulimit and limit, limits.conf) . However, by default a distribution assumes that the system allows the user to use all available resources on the system. This is a reasonable assumption that's correct 99% of the time except for the case where you are dealing with untrusted users playing around.

---

### Post by Vadi on 2008-12-08
So that's why a .deb made by people who know what are they doing is generally a much better, and easier (for the end-user).

---

### Post by Grant A. on 2008-12-08
> **Vadi said:**
> So that's why a .deb made by people who know what are they doing is generally a much better, and easier (for the end-user).

.debs are platform dependent. Shell scripts are not, and are a lot more customizable to boot. If you would actually like to make constructive discussion please, but please do not go off-topic again.

---

### Post by jdong on 2008-12-08
Hi Grant, I noticed the .26 version is in Intrepid and Jaunty; would you be interested in an official backport of this to Hardy so that people can get the updated version directly out of the repositories?

---

### Post by Grant A. on 2008-12-08
Ah, a backport would be lovely :)

The backported package of tmw 0.0.26 would require a backport of Intrepid and Jaunty's Guichan 0.8.1 as well.

---

### Post by jdong on 2008-12-08
> **Grant A. said:**
> Ah, a backport would be lovely :)

The backported package of tmw 0.0.26 would require a backport of Intrepid and Jaunty's Guichan 0.8.1 as well.

Alright, understood. I will put this on my TODO list :)

---

### Post by Grant A. on 2008-12-08
Guichan isn't backwards compatible, would this break any other packages in the repositories?

---

### Post by jdong on 2008-12-08
Upon closer inspection, yes you're right. That would be a good reason why a deb for this is not a practical solution or any "cleaner" than a compile into a local prefix in the home directory.

---

### Post by Grant A. on 2008-12-09
Uninstall scripts for 0.0.26, and install/uninstall scripts for 0.0.27 have been added check the topic at the link in the OP to see! I will add Intrepid Ibex support as soon as I can. Cheers! :KS

---

### Post by Grant A. on 2008-12-24
Intrepid Ibex is now supported.

---

