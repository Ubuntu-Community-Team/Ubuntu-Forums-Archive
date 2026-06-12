---
title: "Upgrading a server installation"
date: 2005-06-11
forum: Desktop Environments
---

### Post by Krogen on 2005-06-11
Hey everyone!

Since I kept getting corrupted copies of Ubuntu (downloaded 3 or four of them and they all had some corrupted packages... Had a lot of problems with it) I decided to do a standard so-called server installation.

Now... Is there anyway to upgrade that installation from the shell one  to one that has a nice gui? (kde or some other ones?)

Sorry... I'm a Linux newbie looking for a decent distro.

Thanks for help!

---

### Post by digby on 2005-06-11
Yes, there is.  For KDE (my favorite) run ```
sudo apt-get install kubuntu-desktop
```
For Gnome:```
sudo apt-get install ubuntu-desktop
```

---

### Post by Krogen on 2005-06-11
Thanks so much. I'll try it and post back the results.

One more thing. If I do an apt-get install, how do I display the packages that I can download/install?

*EDIT*

OMG, so annoying. When I did "sudo apt-get install kubuntu-desktop" it prompted me to put in the ubuntu cd. It downloaded all the needed files but it still kept doing something from the cd drive! Then I got error messages that open office and other crap is corrupted.

Grh... This is the third downloaded image and the third one burned!!!

---

### Post by az on 2005-06-11
I thin you mean

apt-cache search (thing)
to look for packages that include the word thing in the description or name.

---

### Post by Krogen on 2005-06-11
All right. I reinstalled ubuntu server again, and now when I try doing "sudo apt-get install kubuntu-desktop" it downloads some files (the first time it downloaded a lot of them) but then, it says "Failed to fetch ---url---here" -a lot of them like that.  At the end of each one of them, it says "MD5Sum mismatch".  All the way at the end "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?" I tried doing so but no luck. 

This sucks.

---

### Post by FLeiXiuS on 2005-06-11
[QUOTE=Krogen]All right. I reinstalled ubuntu server again, and now when I try doing "sudo apt-get install kubuntu-desktop" it downloads some files (the first time it downloaded a lot of them) but then, it says "Failed to fetch ---url---here" -a lot of them like that.  At the end of each one of them, it says "MD5Sum mismatch".  All the way at the end "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?" I tried doing so but no luck. 

This sucks.[/QUOTE]


You cold either apt-get update or apt-get install -f kubuntu-desktop. "-f" = force.

---

### Post by Krogen on 2005-06-11
[QUOTE=FLeiXiuS]You cold either apt-get update or apt-get install -f kubuntu-desktop. "-f" = force.[/QUOTE]

Thanks but I still get the same MD5sum mismatch/unable to fetch error.

---

### Post by digby on 2005-06-11
It just isn't your day, is it?  A couple of things:  the reason you're getting those md5 sum errors is because us.archive.ubuntu.org is flaky today... several people have posted on here today about getting the same errors from those severs.

You can change to a different server by editing /etc/apt/sources.list.  There is a guide in the howto section that will explain all that if you need it.


About your bad downloads (the cd iso files) did you check the md5 sum before you burned them?  With that many, it makes me suspicious of your burner or (more likely) the media.

---

### Post by Krogen on 2005-06-11
[QUOTE=digby]It just isn't your day, is it?  A couple of things:  the reason you're getting those md5 sum errors is because us.archive.ubuntu.org is flaky today... several people have posted on here today about getting the same errors from those severs.

You can change to a different server by editing /etc/apt/sources.list.  There is a guide in the howto section that will explain all that if you need it.


About your bad downloads (the cd iso files) did you check the md5 sum before you burned them?  With that many, it makes me suspicious of your burner or (more likely) the media.[/QUOTE]

Yes, I checked them before burning them (and I did burn them thinking it won't matter).

I was wrong.

I tried doing the "sudo apt-get install ubuntu-desktop" (not kubuntu) and everything was all right up to the point when... MY KEYBOARD STOPPED WORKING!!! It was when xserver-xorg configuration came up. All I could do was to reboot my PC. 

I rebooted and now my Ubuntu freezes after I log in... A minute or two later.

I'm so sick of this  ](*,) 

How do I get a GOOD Ubuntu image? I downloaded one with Firefox, corrupted. I downloaded one with FlashGet, corrupted. Finally, I went to torrentspy.com and found a working ubuntu torrent, ran Azureus and checked my Firefox-downloaded image. It made changes to it and started sharing it. I forced checked it again, fine.

I checked sumed it and there were two corrupted files.  ](*,)  ](*,)  ](*,) 

It is not my day.

Thanks for the replies. Any suggestions? Right now I'm typying from my Windows XP which might crap out soon, unfortunetely.

---

### Post by az on 2005-06-11
Need a hug?



*hug*

---

### Post by Krogen on 2005-06-11
[QUOTE=azz]Need a hug?



*hug*[/QUOTE]

Thanks. I feel much better now.

I downloaded ubuntu again (with FlashGet) and the iso had 5 corrupted entries/files/packges.

---

### Post by afonic on 2005-06-11
[QUOTE=Krogen]Thanks. I feel much better now.

I downloaded ubuntu again (with FlashGet) and the iso had 5 corrupted entries/files/packges.[/QUOTE]
 I *think* there is something wrong with your ISP.

I downloaded Ubuntu like 3 times the past 6 months and never had any problem. If you use Flashget do not cut the file in 2-5 pieces as the default settings are.

Last time I downloaded correctly was from this mirror:
[http://source.rfc822.org/pub/mirror/releases.ubuntu.com/hoary/](http://source.rfc822.org/pub/mirror/releases.ubuntu.com/hoary/)

---

### Post by Krogen on 2005-06-11
I never get any lost packets, my line quality is good, and I get about 160KB/s all the time (45KB/s upload).

I'll try downloading Ubuntu for the last time using Azureus. If it won't work, I'll either go back to Kanotix or I'll *try* installing Gentoo  ;-) 

Oh, yeah, my Kanotix and Gentoo cds are corrupted, too, but they work fine. ROFLMAO

Thanks again!

---

### Post by digby on 2005-06-11
<conspiracy theory>Maybe windows is messing up your linux cds as a way of maintaining dominance?</conspiracy theory>

I have no idea what could be wrong... I'm tempted to burn and mail you a cd...

---

### Post by Krogen on 2005-06-11
No no no...

I know what's wrong. Someone started seeding a corrupted copy with bittorent and people started downloading it. Now they put in on the official ubuntu servers and everyones getting corrupted copies.

I mean, look at this!

[[IMG]http://img138.echo.cx/img138/7389/screen1by.th.jpg[/IMG]](http://img138.echo.cx/my.php?image=screen1by.jpg)

Normal Azureus bittorrent screen? Right. The file is downloaded and is being checked. After a minute or two, it will stop checking and it will put it onto the "DOWNLOAD" list. Corrupted. It will try to redownload some parts of the file. And when it's finished, it will put it onto the "SEED" (bottom) upload list. Then, since the file is corrupted, it will redownload it. The same thing will keep happening. Or if it won't, it will be.... "OK", but if I checksum it... There WILL be some errors. 

See my other topic:

[http://www.ubuntuforums.org/showthread.php?t=41107](http://www.ubuntuforums.org/showthread.php?t=41107)

It can't be only me.

---

### Post by afonic on 2005-06-12
[QUOTE=Krogen]No no no...

I know what's wrong. Someone started seeding a corrupted copy with bittorent and people started downloading it. Now they put in on the official ubuntu servers and everyones getting corrupted copies.

I mean, look at this!

[[IMG]http://img138.echo.cx/img138/7389/screen1by.th.jpg[/IMG]](http://img138.echo.cx/my.php?image=screen1by.jpg)

Normal Azureus bittorrent screen? Right. The file is downloaded and is being checked. After a minute or two, it will stop checking and it will put it onto the "DOWNLOAD" list. Corrupted. It will try to redownload some parts of the file. And when it's finished, it will put it onto the "SEED" (bottom) upload list. Then, since the file is corrupted, it will redownload it. The same thing will keep happening. Or if it won't, it will be.... "OK", but if I checksum it... There WILL be some errors. 

See my other topic:

[http://www.ubuntuforums.org/showthread.php?t=41107](http://www.ubuntuforums.org/showthread.php?t=41107)

It can't be only me.[/QUOTE]
 Did you try that mirror I gave you?

The ISO from there works fine, I just tried it once more.

Bittorrent shouldn't allow someone with a corrupted file to seed, but some crap clients have removed the hash check before seeding. Shame on them.

I don't think the official mirror get their ISOs from torrents, they probably wget them and then check them right away. And then you tell me that you got 2 more distro ISOs and they where corrupted too, there is obviously something wrong there...

However the best solution would be to install all packages that are not corrupted and then get the rest using apt-get.

---

### Post by Krogen on 2005-06-12
Now, this is creeping me out.

The iso I downloaded from Azureus/Bit Comet/Bittorrent was 586 MB. It was the 5.04 version. I got the iso from TorrentSpy.com. The tracker can be found at: [http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce) .

The mirror image you posted (i386 5.04) has 600.9 MB. Hm...   ](*,)

---

### Post by afonic on 2005-06-12
Try the mirror I gave you, with your speed it will be down in an hour.

Do not use a download manager.

Good luck.

---

### Post by Krogen on 2005-06-12
Yes... I'm downloading it right now from there [no download manager] with IE.

---

### Post by nocturn on 2005-06-13
[QUOTE=Krogen]Hey everyone!

Since I kept getting corrupted copies of Ubuntu (downloaded 3 or four of them and they all had some corrupted packages... Had a lot of problems with it) I decided to do a standard so-called server installation.

Now... Is there anyway to upgrade that installation from the shell one  to one that has a nice gui? (kde or some other ones?)

Sorry... I'm a Linux newbie looking for a decent distro.

Thanks for help![/QUOTE]

If you have this kind of corruption, it is very well possible that either your CD Writer of CD ROM are broken.

You could also order a CD from shipit (for free).

---

### Post by Krogen on 2005-06-13
[QUOTE=nocturn]If you have this kind of corruption, it is very well possible that either your CD Writer of CD ROM are broken.

You could also order a CD from shipit (for free).[/QUOTE]

It might be. I'll try burning a new Kanotix with it (03) and I'll see if it works... Or not.

Anyways, since I'm using Windows right now, which program should I burn it with? Alcohol 120% (Everyone probably heard about this wonderful piece of software :)) or Nero Xpress?

Does it really matter? Both burn isos...

---

### Post by GTvulse on 2005-06-13
[QUOTE=Krogen]
Anyways, since I'm using Windows right now, which program should I burn it with? Alcohol 120% (Everyone probably heard about this wonderful piece of software :)) or Nero Xpress?

Does it really matter? Both burn isos...[/QUOTE]

Both are good; use what makes you feel comfortable.

The trick is to burn the ISO at low speed. There is something with filesystem complexity in the ubuntu ISOs that will destroy your CD if burned at too high a speed. I got several coasters until I decided to burn it at half the max speed of my burner (following advice given here at the forums, somewhere...).

There is another alternative to downloading the installer ISO: jigdo-file. It worked for me because I already had Cygwin installed in my windows partition (jigdo-file is written for POSIXy OSs) and is was a matter of downloading the source code, compiling, installing and pointing it to the .jigdo file in the download listing at ubuntulinux.org.

---

### Post by Krogen on 2005-06-13
I went on my sisters PC and downloaded the latest Ubuntu image with Firefox.

And, holy shit!, I almost thaught everything's going to be fine when, on 99%, the cd integrity test failed! (Something with NVIDIA drivers  ](*,) )

I decided to install it anyways. 

We'll see what happens next in tommorows episode!

---

### Post by Krogen on 2005-06-13
HOLY CRAP!!! EVERYTHING WORKS!!!

see my other topic :)

---

### Post by afonic on 2005-06-14
Heh, glad it works after all!

With all these problems you should thank god ubuntu is not one of these 3 - 5 CDs distro! :-)

---

### Post by demosdemon on 2006-05-31
Just as a suggestion, even though your problem is allready solved...

remove the CD from the apt-get list anyways...

either using synaptic...

or manually
```
sudo nano /etc/apt/sources.list
```

the CD will be the first one on the list

---

