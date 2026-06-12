---
title: "Debian DELETES everything if I do apt-get type stuff."
date: 2016-06-29
forum: Debian
---

### Post by guymanforget on 2016-06-29
I was using Debian on my computer and I love the game supertuxkart. So since I previously reinstalled Debian, I was downloading supertuxkart off the ubuntu package site(packages.ubuntu.com). I was installing the dependency libstdc++6 from the ubuntu version and it gave a broken dependency. If I try to fix it says it will remove everything. If I try to fix that, it can't because there is a broken dependency. I usually have to reinstall at least once a week but this was the time I almost got everything to work perfectly. Other then my wi-fi. :biggrin: But seriously it is annoying please help.

I'm on Debian 8 Jessie running gnome and the default apps.:confused:

Oh, I did install the multimedia codecs and ALL the game apps(games-GENRE) except for racing.

I'm in a rush.

---

### Post by ian-weisser on 2016-06-29
For beginners: Frequent breakage and reinstalls are expected behavior when you use binary packages compiled for a different distro or release. Don't do it. It's advanced stuff.

For the OP: Okay, you're advanced. Have you tried compiling the problem dependency yourself? What's the exact problem you need help with: Removing the package (use dpkg) or something else?

---

### Post by arochester on 2016-06-29
Supertuxkart is available from Debian.

[https://wiki.debian.org/DontBreakDebian/](https://wiki.debian.org/DontBreakDebian/)

You should not have to re-install at that frequency. Debian Jessie is STABLE. You are doing it wrong, 

Can you copy and paste your sources list here so we can look at it?

---

### Post by guymanforget on 2016-06-29
arochester:
I did it for the newest version. Not the most stable. 
Sources:
```
# deb cdrom:[Debian GNU/Linux 8.5.0 _Jessie_ - Official i386 NETINST Binary-1 20160604-14:07]/ jessie main 

# deb cdrom:[Debian GNU/Linux 8.5.0 _Jessie_ - Official i386 NETINST Binary-1 20160604-14:07]/ jessie main 

deb http://ftp.us.debian.org/debian/ jessie main contrib non-free 
deb-src http://ftp.us.debian.org/debian/ jessie main contrib 

deb http://security.debian.org/ jessie/updates main 
deb-src http://security.debian.org/ jessie/updates main 

# jessie-updates, previously known as 'volatile'
deb http://ftp.us.debian.org/debian/ jessie-updates main 
deb-src http://ftp.us.debian.org/debian/ jessie-updates main 

deb http://www.deb-multimedia.org jessie main non-free
```
Might be a problem i'm running x32 on a x64 machine but i doubt it.

ian-weisser:

The exact problem is I can not fix or download anything as it either tries to delete everything or can't continue because of the broken dependency.  I already have the dependency but I installed the ubuntu version alongside. I thought the change in code and location would be enough.

---

### Post by arochester on 2016-06-29
Try
(As Root)
apt-get purge supertuxkart
apt-get purge libstdc++6
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install supertuxcart

You might have 8.5 but it is still Jessie and it is still Stable

It should be no problem that you are running 32 bit on a 64 bit machine.

Your sources.list is lacking, particularly in terms of main contrib non-free. Have a look at the Debian Sources List Generator >>> [https://debgen.simplylinux.ch/index.php](https://debgen.simplylinux.ch/index.php)

Look at things like [https://linuxgeekar.blogspot.co.uk/2015/05/things-to-do-after-installing-debian.html](https://linuxgeekar.blogspot.co.uk/2015/05/things-to-do-after-installing-debian.html) and [https://elias.praciano.com/2016/05/o-que-fazer-depois-de-instalar-o-debian/](https://elias.praciano.com/2016/05/o-que-fazer-depois-de-instalar-o-debian/) DO NOT follow all the steps  and DO NOT follow blindly because they might not apply to you, but have a look. 

If you are still experiencing problems do try Debian Users Forum >>> [http://forums.debian.net/index.php](http://forums.debian.net/index.php)

---

### Post by guymanforget on 2016-06-29
ok it said unmet dependencies and -f trys to uninstall everthing.

---

### Post by ian-weisser on 2016-06-30
Use dpkg for low-level install/uninstall. Apt assumes you want to use repositories. Dpkg doesn't.

Please show the complete terminal output of a failure (using dpkg). The error messages contain a lot of useful data about your specific problem, and that data is lost when you summarize. 'unmet dependencies' is expected. Exactly which unmet dependencies helps determine the way forward.

Have you considered what you will do differently next time?

---

