---
title: "KDE 3.4.1 Released !!!"
date: 2005-05-31
forum: Desktop Environments
---

### Post by JuanC on 2005-05-31
Hi to all ,

KDE 3.4.1 Released :
[http://www.kde.org/info/3.4.1.php](http://www.kde.org/info/3.4.1.php)

Would be soon a new version of Kubuntu with KDE 3.4.1?

---

### Post by Knome_fan on 2005-05-31
No, there won't be a new release before breezy comes out.

However, look at the bottom of the page you linked, kde3.4.1 packages for kubuntu are already available from kde.
(Of course, use them at your own risk)

---

### Post by bartenst on 2005-05-31
not before breezy comes out? how comes?

---

### Post by philipacamaniac on 2005-05-31
[QUOTE=Knome_fan](Of course, use them at your own risk)[/QUOTE]

Well, since JRiddell packaged them (and indeed, contributed to the 3.4.1 branch), and since he is in charge of the Kubuntu project, I for one trust the packages. Besides, "use at own risk" implies that there is official support for the product in question. As far as I knew, Canonical doesn't offer support (yet) for Kubuntu/KDE.

As far as not being in Breezy, that's how Ubuntu release-cycles work. No new updates until the next release, which happens every 6 months. On the other hand, security updates within KDE 3.4.1 WILL be added to the ubuntu.com hoary security repository.

EDIT: The real hope is that KDE 3.5 is ready for shipping by the time Breezy is due. In fact, Jonathan has made it clear that he may delay the Kubuntu Breezy release to coincide with the KDE 3.5 release.

---

### Post by GeneralZod on 2005-05-31
[QUOTE=philipacamaniac]
EDIT: The real hope is that KDE 3.5 is ready for shipping by the time Breezy is due. In fact, Jonathan has made it clear that he may delay the Kubuntu Breezy release to coincide with the KDE 3.5 release.[/QUOTE]


Any idea when KDE 4 is slated to come out? I've never been able to find a consistent estimate :(

---

### Post by raditzman on 2005-05-31
[QUOTE=GeneralZod]Any idea when KDE 4 is slated to come out? I've never been able to find a consistent estimate :([/QUOTE]
 The apt line in download.kde.org didn't work, but this did. But it's very, very slow now.

deb [ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu](ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu) hoary-updates main

---

### Post by NTolerance on 2005-05-31
What is the correct apt-get syntax for performing the upgrade?

---

### Post by philipacamaniac on 2005-05-31
[QUOTE=GeneralZod]Any idea when KDE 4 is slated to come out? I've never been able to find a consistent estimate :([/QUOTE]

There is no release schedule for the next KDE release, regarding 3.5 or 4. They are currently hacking code into KDE4 in the SVN playground, but I believe a 3.5 release will come first. I'm like you, I always want the next release.  [-X But, I'm pretty satisfied with KDE 3.4 (soon to be 3.4.1 on my desktop).

No matter what release it gets, Breezy may cause some grief, because if Ubuntu moves to GCC4, I have heard some are having trouble getting KDE compiled and working properly.

---

### Post by philipacamaniac on 2005-05-31
[QUOTE=NTolerance]What is the correct apt-get syntax for performing the upgrade?[/QUOTE]

Should be sudo apt-get update && apt-get upgrade (once you have added the new KDE repository).

---

### Post by F for Fragging on 2005-05-31
[http://www.kubuntu.org/hoary-kde-341.php](http://www.kubuntu.org/hoary-kde-341.php)


KDE 3.4.1 Released with Kubuntu Packages

KDE 3.4.1 has been released. You can download Kubuntu packages from this deb source (add to /etc/apt/sources.list):

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

or

deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

The packages have also been uploaded to our breezy development version.

---

### Post by Firetech on 2005-05-31
JRiddell just put up a mirror of the repository on kubuntu.org (deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main)
That one is a LOT faster than kde's servers (atleast than ftp.kde.org)

---

### Post by Firetech on 2005-05-31
The mirror on kubuntu.org is recommended, it is a LOT faster than the kde.org one.
Another mirror can be found at [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/), but it isn't faster than kubuntu.org.

Additionally, I had to run a dist-upgrade, because some extra packages had to be installed...

---

### Post by thematrix on 2005-05-31
[QUOTE=Firetech]The mirror on kubuntu.org is recommended, it is a LOT faster than the kde.org one.
Another mirror can be found at [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/), but it isn't faster than kubuntu.org.

Additionally, I had to run a dist-upgrade, because some extra packages had to be installed...[/QUOTE]
 Local mirrors can be found here:

[http://download.kde.org/download.php?url=stable/3.4.1/kubuntu](http://download.kde.org/download.php?url=stable/3.4.1/kubuntu)

Cheers,

Frederic

---

### Post by Ironi on 2005-05-31
[QUOTE=philipacamaniac]There is no release schedule for the next KDE release, regarding 3.5 or 4. They are currently hacking code into KDE4 in the SVN playground, but I believe a 3.5 release will come first. I'm like you, I always want the next release.  [-X But, I'm pretty satisfied with KDE 3.4 (soon to be 3.4.1 on my desktop).

No matter what release it gets, Breezy may cause some grief, because if Ubuntu moves to GCC4, I have heard some are having trouble getting KDE compiled and working properly.[/QUOTE]
That's almost done, except for a few important packages:
amarok, gwenview, kaffeine, **kdeartwork**, kdemultimedia plugins, kdesdk, koffice, kscreensaver, and superkaramba

I'm thinking about waiting for kdeartwork at least then trying to apt-get -b source the remaining packages myself. Has anyone else tried that already?

---

### Post by F for Fragging on 2005-05-31
More people getting this error message when updating repo info with kynaptic, after having the line added in sources.list?
It doesn't seem to be serious, because right now kynaptic is downloading everything fine from the kubuntu.org APT repo, but I wonder if others were experiencing this as well?

Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages (/var/lib/apt/lists/kubuntu.org_hoary-kde341_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

EDIT: although it seems that the update to 3.4.1. was succesfull, when I try to update certain KDE packages, for example kmail from 3.4.0 to 3.4.1 as well, Kynaptic wants to remove kde-core kde-devel and kdelibs again?? Does anyone else have this as well?

---

### Post by darkaudit on 2005-05-31
will 3.4.1 also promulgate into Universe?

---

### Post by Jonathan2007 on 2005-05-31
[QUOTE=F for Fragging]More people getting this error message when updating repo info with kynaptic, after having the line added in sources.list?
It doesn't seem to be serious, because right now kynaptic is downloading everything fine from the kubuntu.org APT repo, but I wonder if others were experiencing this as well?

Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages (/var/lib/apt/lists/kubuntu.org_hoary-kde341_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

EDIT: although it seems that the update to 3.4.1. was succesfull, when I try to update certain KDE packages, for example kmail from 3.4.0 to 3.4.1 as well, Kynaptic wants to remove kde-core kde-devel and kdelibs again?? Does anyone else have this as well?[/QUOTE]

I also got this error with the Kubuntu mirror. I haven't yet updated my system. Do you think I should try it? I don't want to screw up my settings.

---

### Post by philipacamaniac on 2005-05-31
[QUOTE=darkaudit]will 3.4.1 also promulgate into Universe?[/QUOTE]

Promulgate? If you mean, will it be in Universe, the answer is no. It is an update to packages in main (well, and some in Universe). However, since it is mostly not a security update, you will not find most of these updates in the ubuntu.com Hoary archive. It is in the Breezy branch, I believe. For Hoary, you can add one of the many mirrors that have been made available, including kubuntu.org and kde.org.

---

### Post by suoko on 2005-06-01
I have updated kde almost succesfully. The only problem is kdelibs-data.

Error:
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.1-0ubuntu0hoary1_all.deb (--unpack):
 attempted to overwrite `/usr/share/icons/default.kde', which belongs to knetworkconf
Errors occured while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.1-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can anyone help?

---

### Post by skyboy on 2005-06-01
Just updates to 3.4.1 !! worked great

used the kubuntu mirror.
Thanks

---

### Post by allforcarrie on 2005-06-01
is there a change log? I couldn't find anything on the webpage.

---

### Post by mrshark on 2005-06-01
[QUOTE=suoko]I have updated kde almost succesfully. The only problem is kdelibs-data.

Error:
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.1-0ubuntu0hoary1_all.deb (--unpack):
 attempted to overwrite `/usr/share/icons/default.kde', which belongs to knetworkconf
Errors occured while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.1-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]
force it:
```
sudo dpkg --force-all -i /var/cache/apt/archives/kdelibs-data_4%3a3.4.1-0ubuntu0hoary1_all.deb
```

---

### Post by SGC on 2005-06-01
[QUOTE=allforcarrie]is there a change log? I couldn't find anything on the webpage.[/QUOTE]
[KDE 3.4.1 changelog](http://kde.org/announcements/changelogs/changelog3_4to3_4_1.php)

---

### Post by abandoned_hussam on 2005-06-01
KDE 3.4.1 is working flawlessly. The only thing is that I has to stick to kdevelop3.2.0

I have an important question. Anybody knows if kde 3.4.1 will be maintained?
Suppose a bug is discovered, will kde 3.4.0 only get he fix or will kde 3.4.1 get the fix as well?

---

### Post by bored2k on 2005-06-01
[QUOTE=allforcarrie]is there a change log? I couldn't find anything on the webpage.[/QUOTE]
 Of course
[http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php](http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php)

---

### Post by buildid on 2005-06-01
update with no problems at all .....................

---

### Post by abandoned_hussam on 2005-06-01
buildid,  were you able to upgrade to kdevelop 3.2.1?

---

### Post by F for Fragging on 2005-06-01
[QUOTE=Jonathan2007]I also got this error with the Kubuntu mirror. I haven't yet updated my system. Do you think I should try it? I don't want to screw up my settings.[/QUOTE]
 So far I haven't updated because I'm scared that it will cause problems if Kynaptic removes the packages I mentioned. So I asked on the mailing list and I'm waiting for an answer. If I were you I'd wait.

---

### Post by abandoned_hussam on 2005-06-01
[QUOTE=F for Fragging]So far I haven't updated because I'm scared that it will cause problems if Kynaptic removes the packages I mentioned. So I asked on the mailing list and I'm waiting for an answer. If I were you I'd wait.[/QUOTE]

I didn't have to remove anything. I still have amarok, k3b, kaffeine, xmms, superkaramba, etc...

---

### Post by Jonathan2007 on 2005-06-01
Well last night before I went to bed I told Kynaptic to upgrade the kde packages from 3.4 to 3.4.1. This morning I woke up and I looked at Kynaptic and it's scren was all greyed out. I think this happends when it is thinking about something (like when it is installing something). I don't know if that makes sense but I may try exiting out of Kynaptic and restarting it and then rebooting. I may screw my system up bad here but I guess it is the only thing I can do now.

---

### Post by Ironi on 2005-06-01
[QUOTE=ht990332]I didn't have to remove anything. I still have amarok, k3b, kaffeine, xmms, superkaramba, etc...[/QUOTE]
The 3.4.1 packages for hoary are fine. I was talking about the breezy packages, which are transitioning from gcc 3.x to gcc 4.x. Since 3.x and 4.x aren't [ABI](http://dictionary.reference.com/search?q=application%20binary%20interface) compatible for C++, everything has to be compiled with the same major version.

BTW: I went ahead with the breezy upgrade to gcc4-built 3.4.1. Kaffeine and gtk2-engines-gtk-qt build fine with apt-get -b source... amarok doesn't, though.

---

### Post by ltmon on 2005-06-01
[QUOTE=Jonathan2007]Well last night before I went to bed I told Kynaptic to upgrade the kde packages from 3.4 to 3.4.1. This morning I woke up and I looked at Kynaptic and it's scren was all greyed out. I think this happends when it is thinking about something (like when it is installing something). I don't know if that makes sense but I may try exiting out of Kynaptic and restarting it and then rebooting. I may screw my system up bad here but I guess it is the only thing I can do now.[/QUOTE]

You know, I've had Kynaptic do that to me on big upgrades before also.  It seems, however, that the upgrades went fine -- kynaptic just bombed out and took 99% CPU afterwards.

These days I'm using aptitude (console based apt frontend) until Kynaptic gets fixed/replaced.

L.

---

### Post by ykpaiha on 2005-06-01
worked fine for me without any -forece-all option 
IgREAT

---

### Post by Jonathan2007 on 2005-06-01
[QUOTE=ltmon]You know, I've had Kynaptic do that to me on big upgrades before also.  It seems, however, that the upgrades went fine -- kynaptic just bombed out and took 99% CPU afterwards.

These days I'm using aptitude (console based apt frontend) until Kynaptic gets fixed/replaced.

L.[/QUOTE]

Hmm well I haven't tried it yet but since you think it will work I will give it a shot here. And thanks about aptitude but I am not too command line friendly. You might try out KPackage. It works ok. Well at least better than Kynaptic. I should have used that to begin with. Sigh.

---

### Post by Manny C on 2005-06-02
I've just upgraded...everything is working fine..kpdf is rendering document images better!:)

---

### Post by dejitarob on 2005-06-02
I added the kubuntu.org repos and for some reason aptitude was holding back the upgrade of 26 of the new 3.4.1 packages. I had to go back manually and tell it to install them. Works great now, crash fixes are delicious!

---

### Post by blakken on 2005-06-02
klaptop doesn't change profile when using it under normal user! ](*,)

---

### Post by laurent on 2005-06-02
Hi all !

I upgraded the 3.4.1 but have a small problem...

I lost the great kunbutu original theme by the way.

Does anyone have the command line to get it back ? Or the theme download page ?

Cheers,
Laurent.

---

### Post by Jonathan2007 on 2005-06-03
I finally got it installed and it is working good so far. No more Konqueror crashes.

---

### Post by Segovia on 2005-06-03
[QUOTE=Jonathan2007]I finally got it installed and it is working good so far. No more Konqueror crashes.[/QUOTE]
Amen to that.  Havn't had a konq crash yet, since intalling 3.4.1

---

### Post by raditzman on 2005-06-03
[QUOTE=ht990332]buildid,  were you able to upgrade to kdevelop 3.2.1?[/QUOTE]
 Yeah.. I updated to kdevelop 3.4.1 and it's not working good (you can't create new projects or files, it's really messed up). Anyone had this problem?

---

### Post by z-vet on 2005-06-04
Updated succesfully, everything works fine here...

---

### Post by F for Fragging on 2005-06-04
[QUOTE=F for Fragging]although it seems that the update to 3.4.1. was succesfull, when I try to update certain KDE packages, for example kmail from 3.4.0 to 3.4.1 as well, Kynaptic wants to remove kde-core kde-devel and kdelibs again?? Does anyone else have this as well?[/QUOTE]

I gave it a try yesterday, and after it removed kdelibs and kdecore I immediatly upgraded everything (including redownloading kdelibs and kde-core) after that I rebooted and everything was fine :).

---

### Post by i3dmaster on 2005-06-04
[QUOTE=F for Fragging]I gave it a try yesterday, and after it removed kdelibs and kdecore I immediatly upgraded everything (including redownloading kdelibs and kde-core) after that I rebooted and everything was fine :).[/QUOTE]
 upgrade successfully, using kubuntu.org mirror. Thanks very much for providing the source.

---

### Post by !nkubus on 2005-06-05
It looks like it resolved instability bugs from konqueror, :D

well will see but for me it does not crash randomly anymore

---

### Post by Alex_Perry on 2005-06-05
I just installed kubuntu yesterday, and did this update today. So far, everything works fine.

---

### Post by meldroc on 2005-06-05
Just installed it.  Looks like it fixed some rendering glitches in Konqueror, so I'm happy.  Bug fixes good.

---

### Post by JuanC on 2005-06-07
Update without problems.

Nice work !!!

---

### Post by Frozen on 2005-06-07
i must be doing somthing extreamly stupid, as everyone seems 2 have been able to do this upgrade except me.

when i add the kubuntu.org repository to my sources.list and do an apt-get update and then apt-get upgrade it gives me no errors at all but it does not find any files for upgrade at all. i did do an upgrade of everything else (as this is a fresh install of kubuntu) before trying to upgrade kde and that worked fine.

any other repo just gives me an error at the end of apt-get update saying:

```

...
Hit http://gb.archive.ubuntu.com hoary-updates/multiverse Packages
Ign http://download.kde.org hoary-updates/main Packages
Err http://download.kde.org hoary-updates/main Packages
  302 Found
Fetched 3B in 0s (6B/s)
Failed to fetch http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  302 Found
Reading package lists... Done
W: Couldn't stat source package list http://download.kde.org hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.kde.org hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

hope sum1 can help, sorry if this is a stupid question, am pretty new to linux lol

Regards

Frozen

---

### Post by johnprgr on 2005-06-08
[QUOTE=Frozen]i must be doing somthing extreamly stupid, as everyone seems 2 have been able to do this upgrade except me.

when i add the kubuntu.org repository to my sources.list and do an apt-get update and then apt-get upgrade it gives me no errors at all but it does not find any files for upgrade at all. i did do an upgrade of everything else (as this is a fresh install of kubuntu) before trying to upgrade kde and that worked fine.

any other repo just gives me an error at the end of apt-get update saying:

```

...
Hit http://gb.archive.ubuntu.com hoary-updates/multiverse Packages
Ign http://download.kde.org hoary-updates/main Packages
Err http://download.kde.org hoary-updates/main Packages
  302 Found
Fetched 3B in 0s (6B/s)
Failed to fetch http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  302 Found
Reading package lists... Done
W: Couldn't stat source package list http://download.kde.org hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.kde.org hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

hope sum1 can help, sorry if this is a stupid question, am pretty new to linux lol

Regards

Frozen[/QUOTE]

Use a another archive for kde 3.4.1  I use:

   deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main

If you put the url you are using ([http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)) into a web browser you will see that you get a redirect page and not a download.  That is your problem.

---

### Post by johnprgr on 2005-06-08
Sorry messed up that last post:

Use a another archive for kde 3.4.1 I use:

deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main

If you put the url you are using ([http://download.kde.org/stable/3.4....386/Packages.gz](http://download.kde.org/stable/3.4....386/Packages.gz)) into a web browser you will see that you get a redirect page and not a download. That is your problem.

Hope this helps.

---

### Post by Roptaty on 2005-06-08
[QUOTE=raditzman]Yeah.. I updated to kdevelop 3.4.1 and it's not working good (you can't create new projects or files, it's really messed up). Anyone had this problem?[/QUOTE]
 Yeah, i have the same problem as you...

---

### Post by Frozen on 2005-06-08
johnprgr thanks for the reply, however im pretty sure that the repo u gave me is the one that i used and when i tried to update it found nothing at all. im at college at the mo so i cant try it, but it looks the same as the one off the bottom of the 1st page of this thread. if it is the same repo then when i do a apt-get update i get no errors, and then try an apt-get upgrade it finds no packages, tried dist-upgrade too and still nothing. sorry for being a pain but anyone no what im doing wrong, will try again when i get home in a few hours.

regards

Frozen

*EDIT*

yeah that depo u gave me is the one in my sources.list at the moment and it finds nothing when i try to upgrade...any ideas?

---

### Post by deadlands on 2005-06-08
[QUOTE=laurent]Hi all !

I upgraded the 3.4.1 but have a small problem...

I lost the great kunbutu original theme by the way.

Does anyone have the command line to get it back ? Or the theme download page ?

Cheers,
Laurent.[/QUOTE]


I lost some of the Kubuntu KDE artwork as well. I'm trying to set it back up, but I can't find the Kubuntu kside.png. And I can't grab it off the CD because my optical drive decided to die on me.   :-x 

Anyone know where all the Kubunut artwork images are (kside isn't on the Wiki page)?

**edit: nevermind, I figured it out. It's in the kubuntu-default-desktop package and I reinstalled it. Had to do some manual editing. But it's back.**

---

### Post by gbusse on 2005-06-08
[QUOTE=philipacamaniac]As far as not being in Breezy, that's how Ubuntu release-cycles work. No new updates until the next release, which happens every 6 months. On the other hand, security updates within KDE 3.4.1 WILL be added to the ubuntu.com hoary security repository.[/QUOTE]

Does that include a kubuntu that after release is obviously found to have major and very annoying bugs (ie. the kcontrol admin bug... I know that there is a work around but it should work properly out of the box and if it doesn't than Kubunbtu's policy should be to release bug fixes to fix these problems). I have installed kubuntu over and over including installing a base install of ubunbu then installing kbuntu-desktop via aptitude and this bug still remains. I would assume that kubuntu is interested in public acceptance and public relations and does want a stable bug free release and therefore would update the distro including releasing new ISO's to fix bugs such as this?!? Or and I completely in left field and therefore wrong? If I am so wrong please correct me?!?

EDIT: Please don't take me as a troll, I REALLY REALLY REALLY want to use Kubuntu, but it is just not usable for me. Don't even get me started on Ubuntu/Kubuntu not wanted to supply PHP5 as an alternative for people that want to use it. I don't know I am just REALLY frustrated. I think I am going to try out Fedora 4 when it is released next week. I have tried the latest preview release and thier KDE implementation is rock solid and PHP5 is the default!!! Maybe I will take a look at Kubuntu in the fall release....

Thanx,
Gordo

---

### Post by dejitarob on 2005-06-08
Due to the easy but non-conventional method suggested in this thread for upgrading, does anyone else agree that it would be helpful if this was sticky'ed?

---

### Post by Frozen on 2005-06-09
hey, im sorry to be so annoying but i really need this upgrade, i love kubuntu, is the single only distro that iv used that iv got ati drivers and games running on, but i cant use it with this level of stability in kde. i need this upgrade to hopfully fix that, but no matter what repositories i try it just doesnt find anything, iv just tried another few different mirrors and all the same outcome, finds the repository fine with apt-get update but try apt-get upgrade and it just says that nothing is needing updated, am i doing somthing stupidly simple wrong here? i really hope someone has an idea coz it would be a real shame to switch from a distro with such potential.

again im sorry for this, im just real desperate

regards

Frozen

*EDIT*

hey, sorry to have bin annoying, i sorted the problem...well kde fooked up so had to format and just managed to do the update after a fresh install, i guess it must have been my install?

ta anyway

Frozen

---

### Post by philipacamaniac on 2005-06-09
[QUOTE=gbusse]Does that include a kubuntu that after release is obviously found to have major and very annoying bugs (ie. the kcontrol admin bug... [/QUOTE]

There is an Ubuntu bug report: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8681](https://bugzilla.ubuntu.com/show_bug.cgi?id=8681)
Note that it is not a security issue.

Also, IIRC, this is an upstream KDE bug, and affects all the distros currently using KDE 3.4 (or 3.4.1)

It is a difficult bug to catch, as there is no debug output provided, and it is not always reproducible. For example, I haven't had the problem I my machine for some time now.

---

### Post by skv on 2005-06-14
I can't upgrade to KDE 3.4.1 :-x 

I inserted "deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main" in my /etc/apt/sources.list, then apt-get update, but when I make apt-get upgrade there aren't upgrades available...

I try with many of the mirrors listed in [http://download.kde.org/download.php?url=stable/3.4.1/kubuntu](http://download.kde.org/download.php?url=stable/3.4.1/kubuntu) but nothing is changed... 

Any suggestions??

---

### Post by daugirdas on 2005-06-14
please add kde 3.4.1 for amd64!!!!

There are so many bugs in 3,4.0 (e.g. kde applications do not noramally resume from fullscreen)

---

### Post by GameManK on 2005-06-14
i installed 3.4.1 and it seemed to be running smoothly, but when i go into control center it freezes. can still move the mouse, but can't click on anything.

---

### Post by themoddingden on 2005-06-16
Hi;
I can't add this source to my /etc/apt/sources.list
I use emacs21 to edite the file and when i put the source at the botton it tells me when i reload now error malformed something in line 29
how do i do this; i need it for  my backports too :(
i wrote down what was posted here:
deb http:// url then space main at the end 
and if i use kate then kate crashes  with no error code.

---

### Post by jeremy on 2005-06-17
I think you need an empty line at the end of the file, got to the end of the line you added, and press enter.

---

### Post by themoddingden on 2005-06-22
ok;
Also is there a issue with backports and others cause i can't access them when i add them.

---

### Post by GreatBunzinni on 2005-07-18
It seems there is a small problem with the packages. The default online repositories have two versions of KDevelop: the kdevelop2 branch and the kdevelop3 branch. The thing is, kdevelop2 is labeled as kdevelop, while kdevelop3 is labeled as kdevelop3. When I first installed kdevelop from the repositories (right after I installed kubuntu) I noticed that and I didn't payed much attention. After all, I could still install kdevelop3 without any trouble. It seemed to be a small organization problem.

Now it comes back to haunt us.

It seems that the upgrade package is now labelled as kdevelop (like kdevelop2 was and like the way I believe it should be). Unfortunately this leads to a small apt-get upgrade problem. When we add the repository to synaptic and click to upgrade the packages, synaptic doesn't do nothing. This happens because synaptic doesn't find any package upgrade. Instead, if we select the kdevelop package which is listed in the repositories (now 3.2.1), then it installs kdevelop and removes kdevelop3. To put it in other words, kdevelop 3.2.1 is listed as an upgrade to kdevelop 2 and not kdevelop 3.

So maybe this is the package labelling correction which was badly needed. Still, the upgrading process wasn't flawless. Maybe this can serve as a good lesson on labelling packages. Another crease to iron out, I guess...

---

