---
title: "Is Kubuntu more buggy than Ubuntu?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Navyblue on 2005-10-13
Hi,

As a KDE person, I have been using 32 bit Kubuntu Hoary and apt-getted to Breezy. However I notice somethings like media autodetection refused to work. I'm not sure if a fresh install would help.

But others here who are doing fresh install seems to have some problem that I did not see.

As I am running a AMD64 box, I am considering to plunge into 64 bit version of the OS  (hopefully I can make Java and Flash work!), so I am wondering should I get Ubuntu which seems to be less buggy instead of Kubuntu at this point of time. As mentioned I prefer KDE over GNOME. But am a little dissapointed that somethings are still not ironed out depite it is officially released.

For those who had done a fresh install on Breezy please share your experience (especially if you are using 64 bit version). Other advice are appreciated too.

Thanks in advance. :)

---

### Post by pistoli on 2005-10-13
I installed the Kubuntu pre-release a week ago (fresh install) and I am having no problems with autodetection.  With Hoary I could never get this feature to work.  I did upgrade to KDE 3.5 and now get a pop-up window that asks what I want to do when I insert a CD/DVD/USB Drive.

---

### Post by Navyblue on 2005-10-13
[QUOTE=pistoli]I installed the Kubuntu pre-release a week ago (fresh install) and I am having no problems with autodetection.  With Hoary I could never get this feature to work.  I did upgrade to KDE 3.5 and now get a pop-up window that asks what I want to do when I insert a CD/DVD/USB Drive.[/QUOTE]

That's great to hear. A side question, how does KDE 3.5 work for you? Is there anything that is broken?

---

### Post by pistoli on 2005-10-13
So far it is very stable and is IMO faster.  I am very happy with 3.5.

---

### Post by mlomker on 2005-10-13
> For those who had done a fresh install on Breezy please share your experience (especially if you are using 64 bit version). Other advice are appreciated too.


I've been running amd64 since I moved to (k)ubuntu.  You won't get flash or java (browser-wise) to work well unless you want to run a 32-bit chroot environment.  There are definite application downsides to 64-bit.  You also won't get the latest goodies, like KDE 3.5 on amd64.

I haven't had any problems with hotplug...never have, but I know other people do report that.  I only have two usb drives and a camera, though.  Using the command-line also isn't very difficult once you've learned a few of the commands, so I guess it wouldn't matter to me if it didn't automount.

---

### Post by Protostar on 2005-10-13
I tried to install Kubuntu on my system but the GUI would always failed. I tried the "Startx" command but it said something about Fatal Error 4 or something. Anyway, Gnome works just fine. I am wondering why KDE doesn't.

---

### Post by mlomker on 2005-10-13
> I am wondering why KDE doesn't.

I'd suggest posting a new thread with exact error messages...perhaps in the Installation forum.

---

### Post by SilverTab on 2005-10-14
for me, kubuntu was definitly more buggy :(

which sucks because I definitly need KDE apps and so far, installing kubuntu-desktop from ubuntu doesnt seem to work (on breezy)....

I decided to go the kubuntu way, did a clean install, and had random problems....kate wouldnt run, the package manager was working half of the time etc etc...and some loooooong delay when I opened some apps...I went back to ubuntu..much more stable for me...

I still need kftpgrabber, kopete and amarok though :(

---

### Post by HermanAB on 2005-10-14
You can run those KDE apps on Gnome.  Just install them and add them to the menu.  You don't need the whole KDE for that.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by SilverTab on 2005-10-14
[QUOTE=HermanAB]You can run those KDE apps on Gnome.  Just install them and add them to the menu.  You don't need the whole KDE for that.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]


I was able to do it with amarok and kopete...

however, the kftpgrabber package from the backports wont install (saying I need kdelibs and qt3lib-mt etc etc...which I have)....

---

### Post by Navyblue on 2005-10-14
I appreciate your inputs guys.

Hmmm... 2 good and 2 not so good experience. I guess I need a coin toss. :p

---

### Post by SilverTab on 2005-10-14
np!
also: dont base your opinion on my words only hehe, I have some weird problems with breezy, both with kde and gnome...but gnome just seems to have less problem on my machine...

If both would be working well, I'd probably installed both KDE and gnome like I did in hoary since I love both of them...

oh and about the kate problem: I could only run it as kdesu, and even then it was working like 50% of the time...

but it might just be my lack of knowledge in KDE, I don't know...gedit is always working so well and is quite fast, I was expecting the same from kate, but it was extremely slow, and could only be ran as root (even when opening a file created by me (i.e. not root)...)

---

### Post by GeneralZod on 2005-10-14
For some reason, kate couldn't be run as root in Hoary, either - however, kwrite did, which is cool as it is much lighter-weight anyway :)

[QUOTE=SilverTab]I was able to do it with amarok and kopete...

however, the kftpgrabber package from the backports wont install (saying I need kdelibs and qt3lib-mt etc etc...which I have)....[/QUOTE]


Did you try out what Kassetra suggested? That really should solve the problem.

---

### Post by SilverTab on 2005-10-14
[QUOTE=GeneralZod]For some reason, kate couldn't be run as root in Hoary, either - however, kwrite did, which is cool as it is much lighter-weight anyway :)




Did you try out what Kassetra suggested? That really should solve the problem.[/QUOTE]


yes yes! that worked!...(that was for installing a kde theme...)

but with KFTPGrabber, nothing to do...

---

### Post by GeneralZod on 2005-10-14
[QUOTE=SilverTab]yes yes! that worked!...(that was for installing a kde theme...)

but with KFTPGrabber, nothing to do...[/QUOTE]

Post the exact errors, and we'll take a look - if something doesn't go right, don't spend hours being frustrated - just ask!

I'm fairly surprised it's not in the repos, actually; do you have universe and multi-verse enabled?

---

### Post by abhidg on 2005-10-15
Kubuntu is working fine here with KDE 3.5 but I had to disable HAL, otherwise media:// shows only my floppy drive.
I have a problem with installing styles. I installed the linspireclear and qtcurve styles from the deb repo in kde-look.org ([http://mirror.pusling.com/debian/unstable)](http://mirror.pusling.com/debian/unstable)), but none of them show up in the style list. The files are properly installed:
after "locate qtcurve":
/usr/lib/kde3/plugins/styles/qtcurve.la
/usr/lib/kde3/plugins/styles/qtcurve.so
/usr/lib/kde3/kstyle_qtcurve_config.la
/usr/lib/kde3/kstyle_qtcurve_config.so

---

### Post by deeek on 2005-10-15
I am running kubuntu also (fresh install) and I am having no problems (except for  amarok!! :???: ) .  I seemed to have more problems with  GNOME than with KDE.  Just my $0.02.

---

### Post by Segovia on 2005-10-15
I first tried Breezy when the RC came out.  I was pleasantly surprised that everything worked perfectly for me.  My experience with Kubuntu Hoary was not good, so for the time being, my faith has been restored with respect to Kubuntu's devs.  :smile:

---

### Post by Navyblue on 2005-10-15
Btw I actually have lesser problem with the RC earlier on, its the recent updates that causes some problem.

---

### Post by der_joachim on 2005-10-16
[QUOTE=Navyblue]That's great to hear. A side question, how does KDE 3.5 work for you? Is there anything that is broken?[/QUOTE]

[off-topic]I tried 3.5 a few weeks ago. Looks really nice. There was one strange thing though: I had some major (non-KDE related) crashes, which utterly borked two of my partitions. Anyhoo, after reinstalling Kubuntu and accidentally (ok, it was on purpose :)) installing 3.5, I wanted to reactivate my girlfriend's account. I opened Kuser and after filling in all the goodies, her account was saved as a root account. I had to edit her userid manually, after which she was just a mortal user again.
AFAIK, this is a known issue, and the bug has already been submitted by someone else. 
[/off-topic]

---

