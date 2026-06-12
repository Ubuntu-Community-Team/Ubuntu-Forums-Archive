---
title: "Installing Unreal Tournament on Kubuntu 64 bit??"
date: 2006-09-06
forum: Gaming &amp; Leisure
---

### Post by Shantanu80 on 2006-09-06
Hey guys,
need some help here..
I cant seem to install Unreal Tournament GOTY with the installer i found on another thread here.
I have a 64 bit AMD machine with Kubuntu 6.06 LTS for 64 bit PC running on it.
It gives me the following error when i try to run the installer


shantanu@Shantanu:~/Desktop$ sh ut-install-436-GOTY.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436-GOTY Linux install.........................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
The program returned an error code (1)


:S

---

### Post by crane on 2006-09-06
Have you searched for a 64 bit installer? This is the reason I am still running 32bit on my AMD64. There are still a lot of programs that are not able to run.

---

### Post by Shantanu80 on 2006-09-10
I think i might have to switch to 32 bit too..
dont think there is a 64 bit installer

---

### Post by crane on 2006-09-10
I did find this[ UT2004 64 support]("http://www.linux-gamers.net/modules/news/article.php?storyid=183") But it appears to be just a demo install. Not real sure.

---

### Post by handy on 2006-09-11
UT2k4 installs just as easily on 64bit as it does on 32bit...

You may find [help here]("http://gaming.gwos.org/"), as far  as it being a GOTY problem or not.

---

### Post by msch on 2008-05-01
It's ancient, but still comes up high on google.  The fix is to run the installer using linux32.

```
linux32 sh installer.run
```

If you run into the error about checksums try:

```
export _POSIX2_VERSION=199209
```

and run it again.

---

### Post by Luke has no name on 2008-05-02
I installed the ECE from DVD ISO and it worked fine. I don't know why you're having trouble... I do know I had to edit the launcher so it could recognize 64 bit.

---

### Post by doorknob60 on 2008-08-01
> **msch said:**
> It's ancient, but still comes up high on google.  The fix is to run the installer using linux32.

```
linux32 sh installer.run
```

If you run into the error about checksums try:

```
export _POSIX2_VERSION=199209
```

and run it again.

Holy crap it worked :-D I tried getlibs and everything but it kept complaining about not finding libgtk-1.2.so.0 even though I looked and it was where it should be (the 32 bit version installed with getlibs). The installation is running ATM on my Debian Lenny AMD64 :)

---

