---
title: "kubuntu packages for koffice 1.4"
date: 2005-06-21
forum: Desktop Environments
---

### Post by SGC on 2005-06-21
The people whom responsible for kubuntu amazes me each time. They offer an update for koffice 1.4 atthe same release  day from here:
[http://kubuntu.org/hoary-koffice-14.php](http://kubuntu.org/hoary-koffice-14.php)

Also on the same page there is a livecd of kubuntu with kde 3.4.1 + koffice 1.4 with **experimental install feature**.

* [Koffice realse announcement](http://www.koffice.org/announcements/announce-1.4.php) 
* [Koffice changlog](http://www.koffice.org/announcements/changelog-1.4.php)

---

### Post by Zeddicus on 2005-06-22
Installed it on a whim, having never tried KOffice before -- I'm rather impressed!  Starts much quicker than OO.o for me, while retaining most of the functionality (in more than a few cases, surpassing it...) and the KDE look.

Very nice!

*uninstalls OO.o* ;)

---

### Post by SGC on 2005-06-22
I also uninstalled OOo today.

---

### Post by philipacamaniac on 2005-06-22
I'm liking the KDE look & feel, but what is bugging me is the frame paradigm (rather than page paradigm) in KWord.

You try giving KWord to someone who is proficient in Microsoft Word. It just doesn't work. On the other hand, OOo2 has very similar functionality to Microsoft Word. Any user can pick it up right away.

I really want to use KOffice. I really do. I just wish it wasn't so darn different. Yes, I'm willing to learn, but my wife isn't. :(

---

### Post by SGC on 2005-06-22
The frame's border can be hidden from (View -> Frame Borders) and you can customize the lookof the frames from "frames" menu.

See these screenshots for Kword and Microsoft word , I think there are no difference. If you used to work in Microsoft Word or even OOo then you will have no problem in using Kword:

---

### Post by tristian on 2005-06-22
Has any one compiled OpenOffice? It took 7 hours under Gentoo on AMD Sempron 3100+ (1.8Ghz, 256 L2 Cache...)

I think Koffice might take longer since its bigger group ware but I don't want to try it.

---

### Post by SGC on 2005-06-22
[QUOTE=tristian]Has any one compiled OpenOffice? It took 7 hours under Gentoo on AMD Sempron 3100+ (1.8Ghz, 256 L2 Cache...)

I think Koffice might take longer since its bigger group ware but I don't want to try it.[/QUOTE]
 There is no need to compile it there is a binary packages (see the first post) and even if you want to compile it ,  I'dont think it will take as long as openoffice since its 150 mb less in size.

Removing openoffice is great way to save 199 mb of hard disk space.

---

### Post by elsewhere on 2005-06-22
Anyone have any experience with realistic MS-Office compatibility with KOffice ?  Nothing too fancy, just the ability to use standard Word/Excel files ?

Just curious, wouldn't mind letting go of OOO and I like what I see so far in KOffice.

Cheers,
KV

---

### Post by ltmon on 2005-06-22
[QUOTE=elsewhere]Anyone have any experience with realistic MS-Office compatibility with KOffice ?  Nothing too fancy, just the ability to use standard Word/Excel files ?

Just curious, wouldn't mind letting go of OOO and I like what I see so far in KOffice.

Cheers,
KV[/QUOTE]

I do know that the release notes for KSpread were touting a much improved Excel import filter.  Haven't tried it myself yet.

L.

---

### Post by deadlands on 2005-06-22
[QUOTE=ltmon]I do know that the release notes for KSpread were touting a much improved Excel import filter.  Haven't tried it myself yet.

L.[/QUOTE]
 Kword can read .doc files, but cannot write them. You can save docs in Rich Text Format that can be opened in MS Word.

---

### Post by !nkubus on 2005-06-23
Wow awesome job, I really like the fact Kubuntu is realeasing all new stuff sooooooooooooooooo fast :)

---

### Post by !nkubus on 2005-06-23
well it might be to fast on that one here the error i get :

with the first repo:
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main
```

Get:1 http://kubuntu.org hoary-updates/main koffice-data 1:1.4.0-0ubuntu0hoary2 [956kB]
Get:2 http://kubuntu.org hoary-updates/main kivio-data 1:1.4.0-0ubuntu0hoary2 [633kB]
Get:3 http://kubuntu.org hoary-updates/main koffice 1:1.4.0-0ubuntu0hoary2 [21.5kB]
Fetched 1588kB in 3s (452kB/s)
Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice-data_1.4.0-0ubuntu0hoary2_all.deb  Size mismatch
Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/kivio-data_1.4.0-0ubuntu0hoary2_all.deb  Size mismatch
Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice_1.4.0-0ubuntu0hoary2_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

i did the update and the --fetch-missing but , same error.

and with the second repo:
```

Failed to fetch http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  302 Found
Reading package lists... Done
W: Couldn't stat source package list http://download.kde.org hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_pub_kde_stable_koffice-1.4_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


```
anyone had the same errors?

thanks

---

### Post by tristian on 2005-06-23
hmm

---

### Post by Bob D. on 2005-06-23
[QUOTE=!nkubus]
anyone had the same errors?
[/QUOTE]

Yep. See [http://ubuntuforums.org/showthread.php?t=43720]("http://ubuntuforums.org/showthread.php?t=43720") but no answer yet.

Filed bug here [https://bugzilla.ubuntu.com/show_bug.cgi?id=12116]("https://bugzilla.ubuntu.com/show_bug.cgi?id=12116") for what it's worth.

UPDATE: Talked to Jonathan Riddell on IRC and he just fixed the KOffice repo. I just downloaded and installed KOffice. Wow, is KWord FAST!

Bob

---

### Post by SGC on 2005-06-23
Does any body know why koffice packages has been updated from 1.4.0-0ubuntu0hoary1  to 1.4.0-0ubuntu0hoary2

---

### Post by ltmon on 2005-06-24
[QUOTE=SGC]Does any body know why koffice packages has been updated from 1.4.0-0ubuntu0hoary1  to 1.4.0-0ubuntu0hoary2[/QUOTE]

The probably had to be repackaged due to errors the first time.  I don't think there is any difference in the software, just the packaging.

L.

---

### Post by blackboxxx on 2005-07-06
Have anyone tried this "experimental install feature"?
I downloaded kubuntu-5.04.3-i386-live.iso, burned and booted with "install" option.
[left]After selecting language and keyboard and a couple of progress screens, debconf priority selection appears. Console #3 shows a couple of errors (see attached image).
[/left]
    The CD in live mode works fine though.
](*,)

---

### Post by djensen47 on 2005-07-24
I have Ubuntu installed with KDE installed as the "kubuntu-desktop"

I've added one of the sources from ([http://kubuntu.org/hoary-koffice-14.php](http://kubuntu.org/hoary-koffice-14.php)) to my sources.list file. Then I issue the following commands

```
apt-get update
apt-get install koffice
```

And i get the following error ...
```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  koffice: Depends: karbon (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kchart (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kformula (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kivio (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: koshell (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kpresenter (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kspread (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kugar (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kword (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: krita (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
E: Broken packages
```

I'm new to Ubuntu/Debian (but not Linux in general) so any detailed help would be appreciated.

---

### Post by SGC on 2005-07-25
[QUOTE=djensen47]
...
I'm new to Ubuntu/Debian (but not Linux in general) so any detailed help would be appreciated.[/QUOTE]
 See this post:
[http://ubuntuforums.org/showpost.php?p=233219&postcount=6](http://ubuntuforums.org/showpost.php?p=233219&postcount=6)

---

### Post by Terracotta on 2005-07-25
it's actually more a question about MS-office, but will MS-office be able to read the OASIS-format, and even write to it? Since it's been called the standard, and well, compatability is something that goes both ways :s, it's not fun when you create an .odt file and send it to a friend you're working on a paper with who has only ms-office that he can't read it.

---

