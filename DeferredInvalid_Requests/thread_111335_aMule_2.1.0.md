---
title: "aMule 2.1.0"
date: 2006-01-02
forum: Deferred/Invalid Requests
---

### Post by Ferio on 2006-01-02
I've just seen that aMule 2.1.0 has been released, and it supports Kademlia network, among other improvements. It'll be great to see it backported ;) Thank you!

---

### Post by hav0x on 2006-01-02
It has my vote!
I'll be compiling the thing from src anyway, but it must be like totally backportable. :)

---

### Post by akurashy on 2006-01-02
eeeep, lol i compiled it yesterday
works great ;D

[http://akurashy.com/ubuntu/amule-2.1.0_2.1.0-1_i386.deb](http://akurashy.com/ubuntu/amule-2.1.0_2.1.0-1_i386.deb) (if somebody wants it ;D)

---

### Post by Ferio on 2006-01-02
It gives some kind of error when trying to install it, I think I'll wait for somebody to backport it, but thank you very much anyway.

---

### Post by jdong on 2006-01-02
Not  in Dapper yet.

---

### Post by Ferio on 2006-01-02
OK, I'm sorry. Such a pity... Thank you, anyway :smile:

---

### Post by noigeaR on 2006-01-02
> **akurashy]eeeep, lol i compiled it yesterday
works great  said:**
> http://akurashy.com/ubuntu/amule-2.1.0_2.1.0-1_i386.deb[/url] (if somebody wants it ;D)

if you want to use akurashy's package, you have to remove the original amule package (2.0.3) first, otherwise the installation will abort with an error (the amule package in breezy is called amule, akurashy's package is amule-2.1.0 so dpkg will try to install it in parallel to the existing package from breezy).
it works fine here, thanks for that akurashy!

---

### Post by Ferio on 2006-01-02
It worked like a charm! Thank you very much for your help! :p

---

### Post by akurashy on 2006-01-02
[quote=noigeaR]if you want to use akurashy's package, you have to remove the original amule package (2.0.3) first, otherwise the installation will abort with an error (the amule package in breezy is called amule, akurashy's package is amule-2.1.0 so dpkg will try to install it in parallel to the existing package from breezy).
it works fine here, thanks for that akurashy![/quote]

no problem! :D

---

### Post by Cagnulein on 2006-01-02
works great here too.

Thank u for your precious work

---

### Post by hav0x on 2006-01-03
It's easy to compile, it didn't give many problems here.
Lets hope it hits Dapper soon so we can have a backport.

---

### Post by gizm0 on 2006-01-04
Could someone compile amule 2.1.0 for AMD64? I can't compile it :/, it says something about Wxwidged and "no large file support".

Or even better, if there are backport for this :).

---

### Post by hav0x on 2006-01-04
You need the wxwidgets devel package.

---

### Post by voyageur_01 on 2006-01-04
If someone know where to get amule-utils package for this version of amule

[http://akurashy.com/ubuntu/amule-2.1.0_2.1.0-1_i386.deb](http://akurashy.com/ubuntu/amule-2.1.0_2.1.0-1_i386.deb) 

that I can remotly control my amule by http protocol from my work?? 
I will be very thankful:)

---

### Post by hav0x on 2006-01-04
compile the thing with "--enable-webserver --enable-webservergui"

---

### Post by gizm0 on 2006-01-04
[QUOTE=hav0x]You need the wxwidgets devel package.[/QUOTE]

Well i have that one installed.
(apt-get install g++ libwxbase2.4-dev libcurl3-dev libgtk1.2-dev libwxgtk2.4-dev gettext make)

I just tried again the following compile "manual", but it didn't work :(: 
[http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian)

---

### Post by GTvulse on 2006-01-04
[QUOTE=gizm0]Well i have that one installed.
(apt-get install g++ libwxbase2.4-dev libcurl3-dev libgtk1.2-dev libwxgtk2.4-dev gettext make)

I just tried again the following compile "manual", but it didn't work :(: 
[http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian)[/QUOTE]
You forgot to read the release notes: wxWidgets 2.6.x **only**.

---

### Post by Treviño on 2006-01-05
If you want.... I've mande another package of aMule... I've also all the instructions to compile it... Read it more at [http://italy.copybase.ch/blog/informatica/linux/compilare-amule-210-su-ubuntu-kubuntu/](http://italy.copybase.ch/blog/informatica/linux/compilare-amule-210-su-ubuntu-kubuntu/)
The article is written in Italian, but I think that commands are easy to undersand :P.

I hope it will be usefull... :)

My configuration has been launche with following parameters:

```
[FONT=courier new,courier]./configure &#8211;enable-optimize &#8211;enable-amule-daemon &#8211;enable-amulecmd &#8211;enable-webserver &#8211;enable-amule-gui &#8211;enable-wxcas &#8211;enable-alc[/FONT]
```

BYEEEEEEEE!!!

---

### Post by gizm0 on 2006-01-05
[QUOTE=dradul]You forgot to read the release notes: wxWidgets 2.6.x **only**.[/QUOTE]

Where can i get 2.6 version? apt-cache search can't find it. So i need to compile it?

------------EDIT-----------

Ok...now i got it, but now i have new problem. I cannot start the amule. I got "child process error "amule" cannot start (access denied)", when i try to start amule.

---

### Post by GTvulse on 2006-01-05
[QUOTE=gizm0]Where can i get 2.6 version? apt-cache search can't find it. So i need to compile it?

------------EDIT-----------

Ok...now i got it, but now i have new problem. I cannot start the amule. I got "child process error "amule" cannot start (access denied)", when i try to start amule.[/QUOTE]
It is there, you are just not looking in the right direction. Do this:

```

sudo apt-get remove  g++ libwxbase2.4-dev libcurl3-dev libgtk1.2-dev libwxgtk2.4-dev gettext make

```

to clean up the mess...

Then do this to set up things properly:

```

sudo apt-get install build-essential gnome-core-devel libwxgtk2.6-dev zlib1g-dev libgd2-dev fakeroot checkinstall

```

Acept all dependencies.

That'll set you in the right direction. Read both fakeroot and checkinstall man pages...

---

### Post by gizm0 on 2006-01-05
Ok i tried two ways...
FIRST TRY:
./configure --enable-amulecmd --enable-webserver --enable-cas --disable-monolithic --enable-amule-daemon --enable-amule-gui

sudo checkinstall make install

But that didn't work and it said that child process error again.

SECOND TRY (tried to use fakeroot):
./configure --enable-amulecmd --enable-webserver --enable-cas --disable-monolithic --enable-amule-daemon --enable-amule-gui

fakeroot checkinstall make install OR fakeroot AND checkinstall make install

This one didn't work either. It stopped at the point:
Copying documentation directory...
****  Installation failed. Aborting package creation.
Restoring overwritten files from backup... FAILED!


I'm doing something wrong, but what? I haven't ever used this fakeroot...i tried to check manuals, but can't figure out what i'm doing wrong.

---

### Post by mssm on 2006-01-05
Hi,

Thank akurashy for the deb package. It works for me after removing old copy of amule and xmule. However, CPU usage for amule alone shoots up to 92.9%. Did anybody else have this problem?

Thanx in advance

---

### Post by gizm0 on 2006-01-05
Ok now it's working. I didn't need to use fakeroot. I just needed to type " ./configure --enable-amule-daemon --enable-amulecmd --enable-amulecmdgui --enable-webserver --enable-amule-gui --enable-cas --enable-alcc --enable-kad-compile --prefix=/usr"

Anyways...thanks for the help :)

---

### Post by noigeaR on 2006-01-06
[QUOTE=mssm]However, CPU usage for amule alone shoots up to 92.9%.[/QUOTE]
mine is at about 2-5% minimized and 3-10% fullscreen with an athlon xp 2600

---

### Post by mssm on 2006-01-07
[QUOTE=noigeaR]mine is at about 2-5% minimized and 3-10% fullscreen with an athlon xp 2600[/QUOTE]

Okay, it might have been a temporary phase in may case. Now it is running with 2-4% CPU usage for last two days.

---

### Post by sbaush on 2006-01-08
In my opinion the best way is:

1) Download [http://italy.copybase.ch/linux/pkg/amule_2.1.0-0ubuntu1_i386.deb](http://italy.copybase.ch/linux/pkg/amule_2.1.0-0ubuntu1_i386.deb)
2) Type in terminal sudo dpkg -i amule_2.1.0-0ubuntu1_i386.deb
3) Run amule typing amule in terminal

---

### Post by infinito on 2006-01-09
[QUOTE=jdong]Not  in Dapper yet.[/QUOTE]
aMule 2.1.0 is since today (9 january) on Dapper, will it get backported now? I hope so...

Thanks in advance !

---

### Post by gizm0 on 2006-01-11
[QUOTE=sbaush]In my opinion the best way is:

1) Download [http://italy.copybase.ch/linux/pkg/amule_2.1.0-0ubuntu1_i386.deb](http://italy.copybase.ch/linux/pkg/amule_2.1.0-0ubuntu1_i386.deb)
2) Type in terminal sudo dpkg -i amule_2.1.0-0ubuntu1_i386.deb
3) Run amule typing amule in terminal[/QUOTE]


YEah...that is the easiest way, but it doesn't work on AMD64 ;) .

---

### Post by ariel on 2006-01-29
Akurashi site with the .deb is down.

You can find new .debs for ubuntu here:
[http://forum.amule.org/thread.php?threadid=8617&sid=0cf63bf215bc0993647936d04b670d00](http://forum.amule.org/thread.php?threadid=8617&sid=0cf63bf215bc0993647936d04b670d00)

The .deb by andy80 doesn't require you to unistall the previous version; works like a charm.
enjoy

---

### Post by bicchi on 2006-02-04
Any status of backporting aMule, version 2.1.0 has been on Dapper for almost a month now? Thanks. :)

---

### Post by vyruss on 2006-02-13
[QUOTE=Treviño]If you want.... I've mande another package of aMule... I've also all the instructions to compile it... Read it more at [http://italy.copybase.ch/blog/informatica/linux/compilare-amule-210-su-ubuntu-kubuntu/](http://italy.copybase.ch/blog/informatica/linux/compilare-amule-210-su-ubuntu-kubuntu/)
The article is written in Italian, but I think that commands are easy to undersand :P.

I hope it will be usefull... :)[/QUOTE]

Grazie! Your package came in very handy!!

---

