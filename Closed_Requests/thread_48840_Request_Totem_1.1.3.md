---
title: "Request: Totem 1.1.3"
date: 2005-07-14
forum: Closed Requests
---

### Post by Majlo on 2005-07-14
Hi .
Is possible backport Totem 1.1.3 ? Its in Breezy [http://lists.ubuntu.com/archives/breezy-changes/2005-July/007935.html](http://lists.ubuntu.com/archives/breezy-changes/2005-July/007935.html)

Thanks

---

### Post by ubuntp on 2005-07-19
[http://www-public.rz.uni-duesseldorf.de/~thpod001/totem_1.1.3-0ubuntu3_all.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/totem_1.1.3-0ubuntu3_all.deb)
[http://www-public.rz.uni-duesseldorf.de/~thpod001/totem-xine_1.1.3-0ubuntu3_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/totem-xine_1.1.3-0ubuntu3_i386.deb)
[http://www-public.rz.uni-duesseldorf.de/~thpod001/libtotem-plparser0_1.1.3-0ubuntu3_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/libtotem-plparser0_1.1.3-0ubuntu3_i386.deb)
[http://www-public.rz.uni-duesseldorf.de/~thpod001/totem-gstreamer_1.1.3-0ubuntu3_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/totem-gstreamer_1.1.3-0ubuntu3_i386.deb)
[http://www-public.rz.uni-duesseldorf.de/~thpod001/libxine1c2_1.0.1-1ubuntu5_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/libxine1c2_1.0.1-1ubuntu5_i386.deb)

packages updated, i forgot to compile ogg support in.

---

### Post by Majlo on 2005-07-20
Thanks :-)

Work for me yet ..

---

### Post by jdong on 2005-07-20
If you're making custom packages, please be responsible and add a "~something" version trailer to it. Otherwise, you're setting up users for an upgrade DISASTER with the Breezy transition.

This is a valid Backports request, accepted.

---

### Post by Kyral on 2005-07-20
I can't get it to compile...

Build Deps can't be satisfied...

---

### Post by Seth on 2005-07-21
[QUOTE=Kyral]I can't get it to compile...

Build Deps can't be satisfied...[/QUOTE]
 That's why you have to fix them :)
```
totem (1.1.3-0ubuntu3~5.04ubp1) hoary; urgency=low

  * Backport to Ubuntu Hoary
  * Change build-dep in control.in on firefox-dev => mozilla-firefox-dev

 -- Seth Kinast <seth@sethkinast.com>  Thu, 21 Jul 2005 03:59:57 +0000
```
[http://sethkinast.com/ubuntu/hoary/backports/totem/](http://sethkinast.com/ubuntu/hoary/backports/totem/)

---

### Post by Kyral on 2005-07-21
I don't know how to do that. Looks like I have a lot to learn :D

---

### Post by Seth on 2005-07-21
[QUOTE=Kyral]I don't know how to do that. Looks like I have a lot to learn :D[/QUOTE]
 Well, for this particular one, pbuilder-satisfydepends said that **firefox-dev** couldn't be installed.

So I went to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and looked up **firefox-dev**. It is a new package in Breezy; as you can see it has only a Breezy version. The Hoary version is called **mozilla-firefox-dev**.

So I went into the source tree of totem, into the **debian** directory, and edited the file **control.in** to change the Build-Depends from **firefox-dev** to **mozilla-firefox-dev**. Cake :)

---

### Post by Kyral on 2005-07-21
what is pbuilder-satisflydepends?

Oh, I tried that with my copy, but my depends still aren't satisfied

---

### Post by Seth on 2005-07-21
[QUOTE=Kyral]what is pbuilder-satisflydepends?

Oh, I tried that with my copy, but my depends still aren't satisfied[/QUOTE]
 Pbuilder rocks for making backports, because even though I run Breezy, I can backport in a clean-room Hoary environment. See [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) for more details.

Did you change **control.in** and not **control**? If you're not using Pbuilder, you'll need to run **sudo apt-get build-dep totem** as well.

---

### Post by Majlo on 2005-07-21
> **Seth]That's why you have to fix them :)
```
totem (1.1.3-0ubuntu3~5.04ubp1) hoary said:**
> http://sethkinast.com/ubuntu/hoary/backports/totem/[/url]

I have problem with this backport.I have same problem when trying backport Totem 1.1.3 .I install totem , totem-xine and libtotem-plparser0 .Then run Totem click Help --> About .

Totem 1.1.3

**Movie Player using GStreamer version 0.8.9 **

I not install totem-gstreamer.In hoary is gstreamer version 0.8.8 in breezy 0.8.9 

Maybe problem with libxine .In hoary is libxine0 and in breezy libxine1c2

---

### Post by Kyral on 2005-07-21
[QUOTE=Seth]Pbuilder rocks for making backports, because even though I run Breezy, I can backport in a clean-room Hoary environment. See [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) for more details.

Did you change **control.in** and not **control**? If you're not using Pbuilder, you'll need to run **sudo apt-get build-dep totem** as well.[/QUOTE]


Yah I changed control.in

```
Source: totem
Section: gnome
Priority: optional
Maintainer: Sebastien Bacher <seb128@debian.org>
Uploaders: @GNOME_TEAM@
Build-Depends: debhelper (>= 4.2.21), dpatch, libgtk2.0-dev (>= 2.6.0), libglib2.0-dev (>= 2.6.3), libgnomeui-dev (>= 2.6.1.1-4), libglade2-dev (>= 2.4.0), libgnomevfs2-dev (>= 2.8.4), libxine-dev (>= 1-rc5-1), liblircclient-dev (>= 0.6.6), libirman-dev (>= 0.4.2), libgnome-desktop-dev (>= 2.6.1-2), gnome-pkg-tools, scrollkeeper (>= 0.3.14-5), mozilla-firefox-dev, libxml-parser-perl, libgstreamer-gconf0.8-dev (>= 0.8.4.1), libgstreamer0.8-dev (>= 0.8.6.1), libnautilus-burn-dev (>= 2.9.0), libgstreamer-plugins0.8-dev (>= 0.8.4.1), libnautilus-extension-dev, iso-codes, libmusicbrainz4-dev, gnome-icon-theme
Standards-Version: 3.6.1.1
```

Thats at the top of mine. Yet when I do a sudo apt-get build-dep totem

```
sudo apt-get build-dep totem
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for totem could not be satisfied.

```

---

### Post by ubuntp on 2005-07-21
[QUOTE=jdong]If you're making custom packages, please be responsible and add a "~something" version trailer to it.[/QUOTE]
How would i go about doing this? I've always made the packages just for myself primarily so i never gave it much thought.

---

### Post by Seth on 2005-07-21
[QUOTE=ubuntp]How would i go about doing this? I've always made the packages just for myself primarily so i never gave it much thought.[/QUOTE]
 To add a custom version string, cd into the root of your source tree after extracting.


Then, run the command **dch -i** (Debian changelog: insert)

Change the version string to be identical to the version string below yours. Add **~5.04ubp1** Change the target to **hoary**.
[color=red]Note: if the package you're backporting is not Backports-compliant (not in Ubuntu Breezy, for example), you might add your initials to the version string instead of **ubp**.

Add a changelog entry, something like ** * Backport to Ubuntu Hoary**.

Change the e-mail address to the one specified in your GPG keyring. CTRL - X exits.

You can then run a build and a deb will be created with your new version string :)

---

### Post by Kyral on 2005-07-21
What if you don't HAVE a GPG Keyring?

---

### Post by jdong on 2005-07-21
now a bit OT, but built and uploaded :)

---

### Post by ubuntp on 2005-07-21
I neither have a GPG keyring nor am i sure that i want one ;) Actually i don't even know exaxctly what it is.

---

### Post by rpgcyco on 2005-07-22
> I have problem with this backport.I have same problem when trying backport Totem 1.1.3 .I install totem , totem-xine and libtotem-plparser0 .Then run Totem click Help --> About .

Totem 1.1.3

Movie Player using GStreamer version 0.8.9

I not install totem-gstreamer.In hoary is gstreamer version 0.8.8 in breezy 0.8.9

Maybe problem with libxine .In hoary is libxine0 and in breezy libxine1c2

Same problem here. The totem-xine package was accidently built against gstreamer. ;)

- Rpg Cyco

---

### Post by Remix_88 on 2005-07-22
Yep, I noticed that totem-xine is build against gstreamer too :-(

---

### Post by stoffe on 2005-07-24
[QUOTE=Remix_88]Yep, I noticed that totem-xine is build against gstreamer too :-([/QUOTE]
 Me too. Actually was a bit interesting to note that Totem-Gstreamer now handles quite a lot of what I need - it was quite a while since I tried it last. I suspect it never will handle it all though, if I've understood the policys correctly.

Any news on a correct rebuild?

---

