---
title: "Gaim 1.5.0"
date: 2005-08-12
forum: Deferred/Invalid Requests
---

### Post by acascianelli on 2005-08-12
gaim.sourceforge.net

I know it just came out, but Ubuntu has been pretty good about upgrading to the latest version quickly.

---

### Post by veratyr on 2005-08-12
I'd really like it since it says in the changes that they fixed file transfers when both users are behind a NAT firewall/router.

---

### Post by Kyral on 2005-08-12
1.5.0 isn't in Breezy yet, so I don't think it can be backported ATM.

Wait a couple days :D

---

### Post by Kimm on 2005-08-12
Wow... gaim 1.5.0 is out? great! ^^

*downloads sources*

---

### Post by earobinson on 2005-08-15
[QUOTE=Kimm]Wow... gaim 1.5.0 is out? great! ^^

*downloads sources*[/QUOTE]
 can ne one compile it?

---

### Post by lotusleaf on 2005-08-18
If no one backports it, consider [downloading](http://gaim.sourceforge.net/downloads.php) the [Gaim 1.5.0 autopackage](http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download). It's [very](http://autopackage.org/), [very](http://autopackage.org/using.html) [simple](http://autopackage.org/docs/howto-install/) to use. :)

---

### Post by earobinson on 2005-08-18
[QUOTE=lotusleaf]If no one backports it, consider [downloading](http://gaim.sourceforge.net/downloads.php) the [Gaim 1.5.0 autopackage](http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download). It's [very](http://autopackage.org/), [very](http://autopackage.org/using.html) [simple](http://autopackage.org/docs/howto-install/) to use. :)[/QUOTE]
 ya i am, maybe i will.

---

### Post by veratyr on 2005-08-18
I was able to compile and install it from source easily enough. Give it a try. Still can't get AIM file transfers to work though :(.

---

### Post by jamo on 2005-08-18
You have to open TCP port 5190 in your firewall to get this working.
Maybe this is the problem?

---

### Post by ZephyrXero on 2005-08-24
The Autopackage worked great for me! ;)

---

### Post by jamo on 2005-08-26
I compiled 1.5.0 from Breezie for Hoary.
The packages can be found [here](http://user.cs.tu-berlin.de/~jadero/ubuntu).
Though they work for me, I give no guaranty at all. 

Anyway, try them and post comments  :) 

Cheers,
jamo

---

### Post by GoA on 2005-08-26
I tryed to first install the gaim data which worked and after that the gaim 1.5 but I got an error saying I don't have liblaunchpad-integration0 package. Synapatic didn't  find that. Any help?

---

### Post by jamo on 2005-08-26
You're right. The missing deps are launchpad-integration and liblaunchpad-integration0, both backported from breezy.
I uploaded them as well.

Hope everything runs fine now.

---

### Post by Kyral on 2005-08-26
I can't Apt-Source it 'cause it needs the -dev package of the launchpad integration. WTF is up with this launchpad stuff anyway... I can't compile XChat 2.4.4 because of it

---

### Post by jamo on 2005-08-26
I removed launchpad from gaim. It's not a necessary feature imho. 
You can find updated (1ubuntu2) packages [here](http://user.cs.tu-berlin.de/~jadero/ubuntu).
If you still need launchpad for other software (or want to install 
version 1ubuntu1 with launchpad-integration),  all packages spawned 
from the source-package can be found under the same link.

---

### Post by GoA on 2005-08-27
Works fine now. Thank you for helping. :)

---

### Post by stas on 2005-08-28
[QUOTE=][/QUOTE]
 Works good.
Thanx.

---

### Post by duffman25 on 2005-08-29
Bump!

I would prefere to install backports from the official proyect, so, Can the backports people backport gaim please.

Is this proyect stalled? I've haven't seen any backports in a few weeks. :(

---

### Post by tom-ubuntu on 2005-08-29
The new release of Ubuntu is coming closer; I guess, most of the devs are working on this. Really don't hope, that Backports is dead. This is a really important part of the distribution!

---

### Post by duffman25 on 2005-08-29
[QUOTE=joeuser]The new release of Ubuntu is coming closer; I guess, most of the devs are working on this. Really don't hope, that Backports is dead. This is a really important part of the distribution![/QUOTE]

Then I hope something will be done so that backports aren't dead. :(

---

### Post by Kyral on 2005-08-29
I would think that as Breezy gets closer and closer to being complete, and as a side effect more libs and stuff that CAN'T be Backported safely come into it and enter the depends of packages, that Backports will slow down. By the time that Breezy comes out, there won't be an immeadiate need for the Backports, seeing as Backports exists for bringing packages from Ubuntu Unstable (Breezy right now) to Ubuntu Stable (Hoary right now). However I think within a month of Breezy going stable that Backports will come back as development of the next version starts.

And besides, jdong and co. could use a break, don'tcha think? :razz:

---

### Post by jdong on 2005-08-29
IIRC, I've tried this backport and it didn't work out. I'll take another look.

---

### Post by aledie on 2005-08-30
Can somebody check this repository for Ubuntu 5.04: it contents besides Gaim 1.5, Inkscape 0.42, vym, gnome-doc-utils 0.3.2, evince 0.4.1 ...
Full list of packages: [http://kitty.in.th/index.php?room=blog](http://kitty.in.th/index.php?room=blog)

Add in sources.list:
# Kitty Repositoy
deb [ftp://ftp.kitty.in.th/pub/ubuntu/](ftp://ftp.kitty.in.th/pub/ubuntu/) kitty unstable

Download gpg-key:
[ftp://ftp.kitty.in.th/pub/ubuntu/kitty.in.th.gpg](ftp://ftp.kitty.in.th/pub/ubuntu/kitty.in.th.gpg)

Authentification:
$ sudo apt-key add /path/to/kitty.in.th.gpg

---

### Post by manicka on 2005-08-30
Well, it's probably the riskiest thing I've done since using Ubuntu, but I bit the bullet and gave this repo a whirl. Main updates I wanted were Gaim and Evince.
The only issue I had was that the icon for Evince disappears from the menu with this package. Quickly fixed by adding back in manually with smeg. 

As a precautionary measure I've kept a record of all the changes in case I need to go back.Everything seems fine though at this stage, only time will tell.

Main site is a Thai one, so it's difficult to know where the owners are from are from or what they do. Maybe someone out there could translate for us.

---

### Post by Kyral on 2005-08-30
Using Repos outside the main Ubuntu or Debian ones? (Or Official KDE Repos or Smoon's E17 Repo) 

Don't come crying to us if you break your system.....

---

### Post by manicka on 2005-08-30
[QUOTE=Kyral]Using Repos outside the main Ubuntu or Debian ones? (Or Official KDE Repos or Smoon's E17 Repo) 

Don't come crying to us if you break your system.....[/QUOTE]
 OK, I'm a big boy, I can handle it.

I  wasn't recommending that everyone do this. Just giving feedback to a request

---

### Post by donar73 on 2005-09-01
How about an official backport for Gaim 1.5.0? I don't like to use an unknown repository...  :???:

---

### Post by veratyr on 2005-09-01
Hey donar73, you wouldn't happen to be a fan of Menhir would you?

---

### Post by jdong on 2005-09-01
No, doesn't resolve cleanly from Breezy sources... Not a candidate for Backports.

---

### Post by m0ther on 2005-09-01
autopackage seems to be the best bet so far for Hoary.. worked fine first time for me.. my first ever autopkg install :]

(i removed the previous ("official") version via synaptic just to be safe but i'm not sure if this is necessary)

---

### Post by donar73 on 2005-09-02
[QUOTE=veratyr]Hey donar73, you wouldn't happen to be a fan of Menhir would you?[/QUOTE]

Menhir?

---

### Post by veratyr on 2005-09-02
I guess not then.

---

### Post by n1x0r on 2005-09-05
Hi all,

I'm installing from autopackage and so far everybody seems to have accomplished this flawlessly except for me :-(

somewhat strange problem...

this is my errout when run as normal user (I usualy do this first for the feedback)

:```
root@ganymede:~/downloads/gaim# ./gaim-1.5.0.x86.package
# Preparing: Gaim Internet Messenger
# Checking for required C library versions ... failed
# FAIL:
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
#
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
#
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL:  Unable to prepare package Gaim Internet Messenger.
root@ganymede:~/downloads/gaim#
``` 

thoughts? Now felt like a good time to take a step back and ask for advice...

I use kubuntu hoary 5.04 on amd64 - need any other info?

Thx!

---

### Post by pizzach on 2005-09-05
n1x0r, I would just install 1.5 from source.  It's really not all that hard.  I did it will no weird problems if I remember.  Just make sure you install the build essentials before hand.  (just search build essentials on the forums or go to ubuntuguide.org)

Hope this helps.

---

### Post by n1x0r on 2005-09-06
i tried that earlier and had difficulty, but on your advice i'll try again. I'm very confused about why the autopackage would work for so many other people but not in my case. The only sig difference that i can think of is that i use amd64....

but if that means i can't use autopackage then i would be very dissapointed because it seems like such a good and natural solution from what i read (?)

If i run into trouble installing from source I'll demonstrate / describe the problem alot better than i am now :-P

---

### Post by n1x0r on 2005-09-06
[QUOTE=pizzach]n1x0r, I would just install 1.5 from source.  It's really not all that hard.  I did it will no weird problems if I remember.  Just make sure you install the build essentials before hand.  (just search build essentials on the forums or go to ubuntuguide.org)

Hope this helps.[/QUOTE]

ya, you were right. Stupid mistake on my part. I had GTK+2 installed but not the devel version of the libs, I grabbed them from synaptic iin seconds and ran

```
root@ganymede:~/downloads/gaim/gaim-1.5.0# ./configure && make && make check && make install & make clean
``` 

happy ending :-)

---

### Post by ktulu1115 on 2005-09-09
[QUOTE=n1x0r]ya, you were right. Stupid mistake on my part. I had GTK+2 installed but not the devel version of the libs, I grabbed them from synaptic iin seconds and ran

```
root@ganymede:~/downloads/gaim/gaim-1.5.0# ./configure && make && make check && make install & make clean
``` 

happy ending :-)[/QUOTE]

I'm running AMD64 as well, getting same error.   Could you inform me which package exactly is needed (I use apt-get, don't touch Synaptic).  Thanks.

---

### Post by n1x0r on 2005-09-10
> I'm running AMD64 as well, getting same error. Could you inform me which package exactly is needed (I use apt-get, don't touch Synaptic). Thanks. 

i'm curious why you don't use snaptic. Its a powerul and stable tool. You shouldn't neglec it as an option, because it is a good one. 

I don't typically use apt but i'll attempt to answer your question...

**libgtk2.0-dev** is the name of the package abstraction. If you install this it will install the latest stable version of this library available for your archetecture. In my case that was version 2.6.4-ubuntu3 . 

*the following section should be verified by someone smarter than me before accepted as true* :-) ---
dev lib files are generally not platform specific (i think) because they are mostly just header and other interface files and not binaries. Unless the interface changes (major/minor update) you will probably get the same version. --- *is this correct?*

at any rate your /etc/apt/sources.list file will by default direct you only to packages appropriate for your platform. If you edited this, someone should have told you it was at your own risk. However if you didn't- it's possible that your worrying to much b/c this detail is taken care of for you

So then i think your specifically looking for this
```
# apt-get install libgtk2.0-dev
```    :grin:

---

### Post by ZephyrXero on 2005-09-12
The current version of Autopackage doesn't work so well on KDE/Qt machines...and you'd need a x86-64 specific autopackage if youre running 64bit linux I believe. If your running a 32bit x86 - Gnome/GTK based system it works flawlessly.

Do remember Autopackage is still very new. The next version of Autopackage (1.2) will be out soon, and it should fix all the problems with KDE/Qt stuff ;)

---

### Post by domstyledesign on 2005-09-23
I installed gaim 1.5 from the autopackage and 1.5 is what runs, but apt still shows 1.4 as the installed version.  i don't really know too much about autopackage.  is this what i should expect?

---

### Post by Technoviking on 2005-09-23
Sorry, tried to get a backport built, but it is kicking my butt.

Mike

---

### Post by manicka on 2005-09-23
[QUOTE=domstyledesign]I installed gaim 1.5 from the autopackage and 1.5 is what runs, but apt still shows 1.4 as the installed version.  i don't really know too much about autopackage.  is this what i should expect?[/QUOTE]
 Yes it is. I think you'd find it safe to remove 1.4 with apt, as you have two versions on your system.

---

### Post by cyrixware on 2005-12-21
how do i compile gaim 1.5.0.. i downl0ad it already..
tnx.....
:D

---

### Post by Zotova on 2005-12-21
[QUOTE=cyrixware]how do i compile gaim 1.5.0.. i downl0ad it already..
tnx.....
:D[/QUOTE]

You will have to make sure you have all the gtk developer files installed first.

To compile gaim open a terminal then type the following commands once in the gaim directory:

```
./configure
```

^If you get errors note them and then install the required package from apt-get.

Once done:

```
make
```

Then...

```
make install
```

However it would be easier sticking to the gaim available in apt-get.

---

### Post by manicka on 2005-12-21
[QUOTE=Zotova]
However it would be easier sticking to the gaim available in apt-get.[/QUOTE]

or use the deb that akurashy has already made

[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb](http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb)

---

### Post by cyrixware on 2005-12-22
I have already gtk+-2.0.0 i downloaded last day... but i dnt have any idea how to use it... anybody? do i need some softwares for testing? i save it in C:\ then after that i tried type on the command prompt but ther was an  error occur.... (./configure...etc.....)

Downloaded:
- gaim 1.5.0 
- gtk+-2.0.0
- libao-0.8.6
- audiofile-0.2.6
- gtkspell-2.0.11

Pls mail me  for more info about gaim 1.5.0 at [email]fv_comscie@yahoo.com[/email]

FEEDBACK IS HIGHLY APPRECIATED.... tnx

---

### Post by manicka on 2005-12-22
[QUOTE=cyrixware]Wow... gaim 1.5.0 is out? great! 

how do i compile gaim 1.5.0? ur answer is highly apreciated.......

pls mail me at : [email]fv_comscie@yahoo.com[/email]  

tnx[/QUOTE]

Gaim 1.5 is in the repos

---

### Post by cyrixware on 2005-12-22
[QUOTE=manicka]Gaim 1.5 is in the repos[/QUOTE]

Sir In windows? because my OS is XP...

---

### Post by cutOff on 2005-12-22
[QUOTE=cyrixware]Sir In windows? because my OS is XP...[/QUOTE]
:shock:

---

### Post by cyrixware on 2005-12-22
[QUOTE=cutOff]:shock:[/QUOTE]
 i have 2 OS... i tried to compile in LInux its ok... But i dont knw how to configure in windows..hehehehehe

---

### Post by veloct on 2005-12-22
[QUOTE=cyrixware]i have 2 OS... i tried to compile in LInux its ok... But i dont knw how to configure in windows..hehehehehe[/QUOTE]

You may be on your own on that one.

---

### Post by manicka on 2005-12-22
[QUOTE=cyrixware]Sir In windows? because my OS is XP...[/QUOTE]

ah, why didn't you say? :)

[http://gaim.sourceforge.net/win32/index.php](http://gaim.sourceforge.net/win32/index.php)

---

### Post by cyrixware on 2006-01-12
what editor that i will use... should i use VS.NET? or VC6 ? tnx

---

### Post by cyrixware on 2006-06-22
hi! i just wanna ask if Gaim 1.5.0 can be integrate to other open source program like for example VOIP like YM coz yahoo uses chat system and at the same time call using Voip..?

---

