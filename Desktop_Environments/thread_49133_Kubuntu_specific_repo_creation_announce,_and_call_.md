---
title: "Kubuntu specific repo creation announce, and call for contributions ;)"
date: 2005-07-15
forum: Desktop Environments
---

### Post by Altmenorg on 2005-07-15
Hi everyone

Kubuntu is an excellent distro, but does't actually have enough kde packages compared to ubuntu...

Looking at kde-apps.org, I saw that many of the most popular applications didn't have any package at the moment (backports included)...
To give my part of contribution to the community, I decided to create a repo on my webserver and to package as much of those applications waiting for them to be officially supported..
Bandwidth : 80 mb/sec - 12mb used
Disk Space : 120 GB avail.
Should be quite okay ;-) 

At the moment, I already packaged the following 10 applications :
- Kaffeine : The original Kaffeine package is bugged, is using 100% processor when stopped and is very unstable, after beeing mailed, the maintener didn't answer, so I've packaged this working version...)
- Kat : file indexer à la Google Desktop Search.
- Katalog : CD/DVD collection manager.
- Kdocker : very nice little tools that enables to put in the systray any application (very usefull for Thunderbird...)
- Kftpgrabber : The best ftp client for KDE (not stable enough to me but...).
- Klibido : The best Newsgrabber for Linux.
- Kshutdown : A shutdown manager.
- Ktorrent : A BitTorrent client with search engine.
- KxStitch : A cross stitch patterns editor (Grandmama, if you read this :razz: !)
- Pwmanager : A great password manager (à la Pim or Keepass for those who know)

I hope to maintain about 20 apps in a few days.

For those who might be interessted to contribute (most of you have certainly had to compile a KDE app for their needs) contact me by PM, I will give you the ftp parameters.
For those who won't, well, I hope this repo could be of any help !

Packaging a little app is really an easy job (not more complicated that compilation in any case...), and I will certainly write a little documentation for this, so don't hesitate to contact me if you could be interessed, but don't know how to package an app...

Waiting for your positive or negative criticism, or your PM, I wish you a very nice day (whether is marvellous here in France !  \\:D/ 

Here are the repo params :
```
deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
```

---

### Post by skyboy on 2005-07-15
good idea, 
 and a HOW TO "create .deb file" would be a very good use to

---

### Post by Altmenorg on 2005-07-15
[QUOTE=skyboy]good idea, 
 and a HOW TO "create .deb file" would be a very good use to[/QUOTE]
As said, because debian documentations on that point is a pain in the "you know what", I'm gonna write this afternoon an easy guide for that...
It is really as simple as compiling, and can be done with 3 commands for little applications ;)

---

### Post by GeneralZod on 2005-07-15
This sounds great; I (and I'm sure, many others on these forums) wish you the best of luck! :)

---

### Post by Altmenorg on 2005-07-15
Added :
- Konverter : Video convertion tool
- Gwenrename : Mass renamer

---

### Post by skyboy on 2005-07-15
I've just finnish to compile the latest Transcode and latest ffmpeg with shared-libavcodec enable, was a real fight :) ( also latest libmpeg2)
I dunno how to creat .deb but I would be glad to add those to your rep.

---

### Post by Altmenorg on 2005-07-15
Well, thanks a lot for that proposal, but in fact the aim of that repo is not to become another backport, but to package applications that are not already packaged until they get a real official support (exception is done with Kaffeine whose official package is crappy...)
In any case, packaging those apps might be usefull, but certainly better to submit them the the backports maintainers don't you think ?
I'll finish (I hope...) the little documentation today and will send it to you if you want ;)

---

### Post by skyboy on 2005-07-15
Yes you are right, anyway, I just made a HowTo for those package.

I'm waiting for the HowTo .deb  :)

---

### Post by Aikurn on 2005-07-15
Good idea. I always package my apps in .deb format for easy un/install. I could contribute with QComicBook, KRename ,KBandwidth and a few more.
 :grin:

---

### Post by Altmenorg on 2005-07-15
[QUOTE=Aikurn]Good idea. I always package my apps in .deb format for easy un/install. I could contribute with QComicBook, KRename ,KBandwidth and a few more.
 :grin:[/QUOTE]
 Nice, very nice ;)
But in order to put the debs in a repo, you should put correct informations for the deb file.
I don't know for you, but I sure wouldn't do that for my own usage ;)
I just takes 2 minutes more by package...
I wrote a little HOWTO on the same board, to prepare the packages correctly, with the good infos, way to write a desc etc...

Here is the link : [http://www.ubuntuforums.org/showthread.php?t=49216](http://www.ubuntuforums.org/showthread.php?t=49216)

Once you're ready, let me know, I will open you the ftp for the repo and give you instruction on where to put the files ;)

---

### Post by void_false on 2005-07-15
Excelent idea! THX for your effort.  :)

---

### Post by Aikurn on 2005-07-15
Ok, I have read your How-To and it's basically the same as I use to do. The only difference is that I add some options to dpkg-builpackage because I don't need .diff's and other extra files for "home" use. Anyway, I'll rebuild the packages to generate those.
Which files are needed? .dsc .deb and .tar.gz?  :? 

I could send you a PM when I'm ready if you want to.

---

### Post by Altmenorg on 2005-07-15
[QUOTE=Aikurn]Ok, I have read your How-To and it's basically the same as I use to do. The only difference is that I add some options to dpkg-builpackage because I don't need .diff's and other extra files for "home" use. Anyway, I'll rebuild the packages to generate those.
Which files are needed? .dsc .deb and .tar.gz?  :? 

I could send you a PM when I'm ready if you want to.[/QUOTE]
 .dsc and .deb are necessary for the deb repo, and .dsc, .diff.gz and .orig.tar.gz are necessary for the deb-src repo.

This is the reason putting no options to dpkg-buildpackage is better, you will have all the files needed.
Let me know when done by PM yes, I'll send you the ftp access.
Thanks for your contrib !!

Edit : Added kchm, chm file viewer for KDE, composed of a kio for konqueror and a viewer. (Can be usefull)

---

### Post by Feanor on 2005-07-15
This seems a very good idea... But is possible to add the repo to the sources.list yet? Cool!  \\:D/

---

### Post by Altmenorg on 2005-07-15
[QUOTE=Feanor]This seems a very good idea... But is possible to add the repo to the sources.list yet? Cool!  \\:D/[/QUOTE]
 Of course it is ;)

---

### Post by rlklee on 2005-07-16
I think the repo is  a great idea, but I'm coming across a dependency issue that I'm not sure how to resolve, this happens for kaffeine as well as ktorrent and I'm assuming the others in this repo, but haven't checked:

kaffeine:
  Depends: kdelibs4 (>=4:3.4.1) but 4:3.4.0-0ubuntu3.2 is to be installed


I don't seem to have these libs available... what to do?

---

### Post by t2kburl on 2005-07-16
it appears you have not yet update to kde 3.4.1

add this line to your sources.list

deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main

update and upgrade

---

### Post by Aikurn on 2005-07-16
Added 2 programs:
 - QComicBook: A comic book archives viewer.
 - KRename : Batch renamer.

---

### Post by z-vet on 2005-07-16
I try to upgrade kaffeine, but get this:

```
kaffeine:
  Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
```

What's wrong here and where can i get this libgcc package?

---

### Post by Aikurn on 2005-07-16
I guess Altmenorg is using the libgcc version that you can find in the ubuntu backports. You could just install it or wait until Altmenorg is back.

---

### Post by Altmenorg on 2005-07-17
[QUOTE=Aikurn]I guess Altmenorg is using the libgcc version that you can find in the ubuntu backports. You could just install it or wait until Altmenorg is back.[/QUOTE]
 Yes, here is the problem....
I have a very up to date system, and that can cause a little issue with the packages I create.
Damn, I didn't think of that before...
I'll try to repackage everything (gasp !!), with a more "standard" system.
Unless I find a way to manually modify those dependancies, because the gcc version might not be of any useonce the binaries are built.

---

### Post by rn0dal on 2005-07-18
Altmenorg pls PM me( I sent you a PM) I would like to help :)

-r

---

### Post by Altmenorg on 2005-07-18
[QUOTE=rn0dal]Altmenorg pls PM me( I sent you a PM) I would like to help :)

-r[/QUOTE]
 I replied ;)

For those who may know this, do you have a way to modify dependancies without having to repackage on another system, not as up to date as mine ?
I really don't want to have a dual boot for this....

---

### Post by Altmenorg on 2005-07-20
Added FTP Monitor :
[http://de.kde-apps.org/content/show.php?content=11918](http://de.kde-apps.org/content/show.php?content=11918)
Simple KDE applet but that can be of any use ;)
Usefull to me in any case.

Added KcmPureftpd :
[http://kde-apps.org/content/show.php?content=10437](http://kde-apps.org/content/show.php?content=10437)
KDE Control Center module for the PureFTPd server daemon, which includes .

Added Kpum :
[http://kde-apps.org/content/show.php?content=10081](http://kde-apps.org/content/show.php?content=10081)
KDE PureFTPd User Manager  

Still a problem with the dependancies, I tried with qemu, and that worked, but I get errors during compilation I don't get normaly (strange, but I didn't found the solution).

This repo will maybe have to be used in addition to the backports if I don't find a way to get clean deps without maintainning a dualboot that I don't want...

---

### Post by Aikurn on 2005-07-21
Maybe you could downgrade your libgcc version to the official one. You could even lock the package so it doesn't get updated when you upgrade or dist-upgrade.
Another idea, you could try to add options to ./configure so that it uses a specific version of libgcc. And last idea, try editting the control file inside the .deb and changing any dependency reference to libgcc version number. I don't know if this would work, but you could just try it.

---

### Post by ceti on 2005-07-21
Have you read this?

[http://www.ubuntuforums.org/showthread.php?t=50641](http://www.ubuntuforums.org/showthread.php?t=50641)

---

### Post by Altmenorg on 2005-07-22
Thanks for the information ;)
I wasn't aware for the "~" problem...

Next to that, because there is apparently no easy way to package with manually set deps, I decided to do what I didn't want to do (lack of time...), I mean manually modify all dependencies via a script...
The problem is that this is requirering many, many specific cases I didn't want to consider.

The script is over, codec with PHP.
You may ask me why not sh or perl, the response is simple ; BECAUSE !!!

I put it with this message, in case it might help people.
The compilation is completly automated, from dh_make to dpkg-buildpackage, the "~" problem is considered, and the dependencies are correct at the end, by replacing all necessary depds by the default hoary ones.

To use it, first install "php-cli", put the script it to /usr/bin, and chmod it to 755.
Unpack a .tar.gz source file (be sure the unpacked folder is name "<package>-<version>"), go in the folder in shell and launch "sudo pkg-build".

Follow the steps and that's it, you should get a valid, clean deps and version package at the end.

I am just repackaging all the repo apps using it, and that works very well (and is 3 time faster that manually perform all the steps).

IMPORTANT : At it's current state, the script is NOT design to package something else that a "single binary" package...

---

### Post by Altmenorg on 2005-07-22
I repackaged all applications, you shouldn't have dependencies problems now....
Also added Klamav, a kde frontend to Clamav (antivirus), and ksystemlog, a log viewer.

---

### Post by Feanor on 2005-07-30
Will be possible to have a version of firefox optimized for kde in this repository?

It's so bad to have firefox uses gtk...  :?

---

### Post by GeneralZod on 2005-07-30
[QUOTE=Feanor]Will be possible to have a version of firefox optimized for kde in this repository?

It's so bad to have firefox uses gtk...  :?[/QUOTE]

I thought Zack's port of Firefox to KDE was abandoned and never finished...? I'd love to hear otherwise, though - especially if I could use KDE's awesome file dialogues in Firefox!

Edit:

This is the closest I could find, and it doesn't work too well :(

[http://www.polinux.upv.es/mozilla/](http://www.polinux.upv.es/mozilla/)

---

### Post by z-vet on 2005-07-30
[QUOTE=GeneralZod]I thought Zack's port of Firefox to KDE was abandoned and never finished...? I'd love to hear otherwise, though - especially if I could use KDE's awesome file dialogues in Firefox!

Edit:

This is the closest I could find, and it doesn't work too well :(

[http://www.polinux.upv.es/mozilla/](http://www.polinux.upv.es/mozilla/)[/QUOTE]
 GeneralZod:
I use Plastikfox Nuvola theme for FF and can't see any problem. Yes, it don't "integrates" FF into KDE, but at least make it looks like KDE app as much as possible. By the way, there is an [improvement](http://www.polinux.upv.es/mozilla/mejoras.php?idioma=en) for Mozilla and FF that make a browser to use a KDE standard dialogs.

---

### Post by Feanor on 2005-07-30
Plastikfox is a fake solution... Try to download something! The dialog boxes are too ugly!

And using plastikfox is good only if you have a plastik look in your kde theme... I spent some time to configure my kde's theme (see here if you want [http://ubuntuforums.org/gallery/showimage.php?i=557&c=3](http://ubuntuforums.org/gallery/showimage.php?i=557&c=3) ) and firefox with plastikfox doesn't fit it  :?

---

### Post by angrykeyboarder on 2005-07-30
[QUOTE=Feanor]Plastikfox is a fake solution... Try to download something! The dialog boxes are too ugly!

And using plastikfox is good only if you have a plastik look in your kde theme... I spent some time to configure my kde's theme (see here if you want [http://ubuntuforums.org/gallery/showimage.php?i=557&c=3]("http://ubuntuforums.org/gallery/showimage.php?i=557&c=3") ) and firefox with plastikfox doesn't fit it  :?[/QUOTE]

I had a very similar desktop.  What I  did for firefox was to use this theme:

[http://www.spuler.us/themes/apollo/index.html]("http://www.spuler.us/themes/apollo/index.html")

I also followed instructions there to customize it.

---

### Post by z-vet on 2005-07-30
Feanor, it was just **my** opinion. For full integration with KDE we need something like Open Office port of FF for KDE. I understand that nobody interested to do it... :(

---

### Post by Feanor on 2005-07-30
You're right... It's a very very bad thing, firefox is a great browser.  :-?

---

### Post by yongyi on 2005-08-01
Can use this source ?
> deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main

I can't connet it.

---

### Post by abandoned_hussam on 2005-08-09
Kaffeine 0.7 is out, can it be added to this repository?

---

### Post by Altmenorg on 2005-08-10
[QUOTE=hussam]Kaffeine 0.7 is out, can it be added to this repository?[/QUOTE]
 I have been contacted by J Riddell, from the ubuntu team, and I'm actually packaging directly for the Universe branch of ubuntu, and will continue for the next versions for sure.
It is much more interesting to me due to the technical perfection required for the sources packages (argh!!!), and that will certainly be better for the users instead of having to manage with hoary/breezy unofficial repos while upgrading.
I will let that repo open until breezy is out, but will close it after.
Most of the available packages in that repo will (maybe) go in breezy when approved.

Concerning Kaffeine, breezy is not planned in many, many month, so you'd better wait, or try to create a paclage by yourself using the little HOWTO I've written.
It is not that much complicated, even if the given technique isn't at the top for "repo packaging" ;)

---

### Post by zAo on 2005-08-15
Wow! Great! Needed Ktorrent and Klibido!

---

### Post by joshuai on 2005-10-07
Out of curiosity, will these packages be updated once Breezy is out?  I've updated to the preview release, but I'm having dependency problems when I try to install PwManager.

I tried compiling it myself, and it runs, but every time I try to save it crashes.

---

### Post by f1dave on 2005-10-08
[QUOTE=Feanor]Plastikfox is a fake solution... Try to download something! The dialog boxes are too ugly!

And using plastikfox is good only if you have a plastik look in your kde theme... I spent some time to configure my kde's theme (see here if you want [http://ubuntuforums.org/gallery/showimage.php?i=557&c=3](http://ubuntuforums.org/gallery/showimage.php?i=557&c=3) ) and firefox with plastikfox doesn't fit it  :?[/QUOTE]

Ah, but that's when you use /this/
[http://www.kde-look.org/content/show.php?content=25478](http://www.kde-look.org/content/show.php?content=25478)

---

