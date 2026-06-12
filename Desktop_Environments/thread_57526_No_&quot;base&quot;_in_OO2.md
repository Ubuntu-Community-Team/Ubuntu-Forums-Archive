---
title: "No &quot;base&quot; in OO2?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by veritas366 on 2005-08-16
I am wanting to try the new OpenOffice Base so that I have a gui database to work with.  On the site, it says it's in Open Office version 2 but if you install OO 2 from synaptic it doesn't install it and it's not listed like the others.  I could do a manual install, but you have to install the entire OO not just base.  Will it be in apt/synaptic soon?

---

### Post by matthew on 2005-08-16
The newest version possible should be in Breezy when it releases (hopefully the full 2.0, not 1.9.xxx). For now the repositories have 1.9.79 but there is a far newer release available that DOES include Base. 

Try [this thread](http://www.ubuntuforums.org/showthread.php?t=30866) for more info.

I'm using 1.9.113 with good results, but I know there is a newer version out.

---

### Post by veritas366 on 2005-08-17
Thanks Matthew,

I can't find it in the repos via synaptic....I have everything enabled: universe, multiverse and the marillat  it lists openoffice.org2 and lists all the apps: calc, scribus, etc but it does not show Base of any flavor.  

I didn't read the whole thread you offered as I assumed that it was the install program that you were referring me to , or the how to.  Both of these are no longer available via the links in that thread, unfortunately.  I suppose I can simply do a full install of the newest version...I just really prefer doing via debian files.

---

### Post by matthew on 2005-08-17
Sorry for the misunderstanding. I was referring you to a thread where I first found an easy way to install the latest beta. I didn't know/realize their method wasn't working any more. 

You won't find anything newer than 1.9.79 in the repos until Breezy, I'm afraid. I fyou really want the latest Ooo with Base you will have to install manually. I believe the reason you can't install just Base is that all of the programs in the suite are very interrelated so they all need to updated at the same time.

---

### Post by veritas366 on 2005-08-20
ack...what a nightmare.  I went and found the latest version, 1.9.122 and installed.  This itself was no easy task.  They come as rpms, but luckily they have some "hints" on converting to deb files which I followed.  However, after succesfully doing most of the installation, the hints contained several commands to do and none of those worked.  Oh well, I tried anyway, and I ran the program.  It opened fine and everything, but when trying to use a wizard in base, it said "no java".  I have java, of course, as I use it to play yahoo chess all the time.  I looked more on the site and it said "see release notes to see what version of java you need".  I looked in all the release notes I could find and saw no such information.  I looked in synaptic to see what version I actually had, and I guess that must not have been how I installed Java, because it showed nothing java related on my system.  Even if I did know what version I have and where it is located, no instructions could be found about telling OO where to find it, since obviously it wasn't where it expected!

I really wanted to start setting up client files via base, but I will have to wait until Breezy.  I just wish they had "base" in their "stable" release.

Thanks for the help though.

---

### Post by raven on 2005-08-21
did you try "ooffice2 - base" from terminal 
if it work create a menu
hope that help

---

### Post by stig on 2005-08-21
[QUOTE=matthew]The newest version possible should be in Breezy when it releases (hopefully the full 2.0, not 1.9.xxx). For now the repositories have 1.9.79 but there is a far newer release available that DOES include Base. 
[/QUOTE]

I read in a magazine (perhaps LinuxFormat?) that there was some doubt about whether Ubuntu would include OO with Base in its repositories. Some problem with proprietary bits in Base, I think was the reason given.

---

### Post by veritas366 on 2005-08-21
Well, OO uses Java for certain things.  Evidently, for example, the Wizard for creating a new database uses Java, as when I tried to do it, it couldn't find Java, even though I have java on my system.  I assume it's a matter of pointing OO to the path for Java but I found no explanation of how to do this.

Hopefully, if they don't include Base in Breezy, it will be easily downloaded in universe.

---

### Post by raven on 2005-09-02
I stumbled on this last night

[QUOTE=manicka]I can't find the thread again, but someone posted a link to the latest 125 relase that is now available as debs.

They installed perfectly for me :) and the best part is that we finally we have some debs that take away the need for installing via scripts.

Install notes: You must remove the latest beta that you have from your system.
For me I did it through synaptic, then went to /opt and deleted the openoffice 1.9 folder. (apt doesn't completely remove it because the script moves it from where apt installed it at the final step.)
You also need to delete the icons that are created by the script (zerohalo's) in /usr/share/applications. 
I did all these jobs with 'sudo nautilus' but I'm sure command line people will know a better way.

Once ready I just untared the deb install file. Changed to the created folder and ran:

sudo dpkg -i *.deb

Much thanks to whoever it was that posted this link
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)[/QUOTE]

I tried it and works fine for me and it is a DEB file

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/OOo_SRC680_m125_en-US_native_LinuxIntel_install_deb.tar.gz](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/OOo_SRC680_m125_en-US_native_LinuxIntel_install_deb.tar.gz)


and this is the thread 
[http://www.ubuntuforums.org/showthread.php?t=30866&page=27&pp=10](http://www.ubuntuforums.org/showthread.php?t=30866&page=27&pp=10)

hope this one help

---

