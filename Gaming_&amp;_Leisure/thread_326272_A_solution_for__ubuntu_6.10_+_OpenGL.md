---
title: "A solution for : ubuntu 6.10 + OpenGL"
date: 2006-12-27
forum: Gaming &amp; Leisure
---

### Post by cleardays on 2006-12-27
the stroy happens @
**DATE**: several days ago - till yesterday
**SYSTEM**: ubuntu 6.10 
**computer**: DELL Latitude D620 with a) video card of Intel Corporation Mobile 945GM;
b) wide screen 1400x900

I install the new system on the laptop, It runs well, of cause after apply the patch of 
**915resolution**. However, when I run IDL to plot something, the problem happens.
Give me this information:
[INDENT][COLOR="RoyalBlue"]libGL warning: 3D driver claims to not support visual 0x5b[/COLOR][/INDENT]
so I think this problem happens with the openGL, so I use dpg-reconfigure xserver-xorg
to reconfigure the card, and [COLOR="Red"]**delete the option of "glx"**[/COLOR] when you are asking if you load
this glx module by default, THen, restart X-window, IDL works, I can open window, and
plot somthing. BUT later I realize (of course) my openGL cannot run anymore. So I try 
to re-configure the Xwindow with glx module, try to find the solutions (you may possible 
have read them all as me did). 

By chance, I remove the drive of nvidia, and notice that  some of restricted kernel 
was remove at the same time, (I don't restar computer!) I try to re-intall the kernel back.
But finally it stall a new kernel: **[COLOR="Red"]Ubuntu, kernel 2.6.17-10-386[/COLOR]**, the old one is
**Ubuntu, kernel 2.6.17-10-generic**, 

OK, start with new kernel, my openGL don't wrok any more even I have load the module
of glx when I reconfigure the Xorg. when I run :glxgears , glxinfo, I always got some
information of:
**[INDENT]Xlib: extension "GLX" missing on display ":0.0".[/INDENT]**

I was crizy! I try to find the solution by google, it says this problem possbile is related to
mesa, openGL, nv, nvidia driver (but my video care is not nv) , And somebody say I shoud
install nvidia-glx-legacy, I tried, don't work! and say I should add something more in xorg.conf. Don't work also!

finally, I think, ok, I will install all things related to openGL, I start synaptic Package manager
, and the search for mesa, and installed something, THen I find openGL works, even 
without restart the Xwindow. I don't remember which I choose, but I can list what in  my
computer now:
[COLOR="MediumTurquoise"]libgl1-mesa-swx11
libgl1-mesa-swx11-dbg
libgl1-mesa-swx11-dev
libglu1-mesa
mesa-common-dev
mesademos (I think this is not necesarry)
mesa-utils[/COLOR]

And search by glx, the list of installed are:
[COLOR="MediumTurquoise"]libglitz-glx1
rss-glx
[/COLOR]

Sorry to reader: I'm not good at Linux, I just fight for my the software I use, so I just can 
write what I remember, write the process I ever passed, hope it is helpful to somebody!


[COLOR="Red"]All my thank to who share the problem, share the possible solutions![/COLOR]

good luck! even it will comes to you at some time!
:)

if anyone need more information, pls write to me, I'm glad to do that:)

---

### Post by ltk5 on 2006-12-28
hm.. I have the same problem, and maybe even the same error; which is the reason I can't use Blender, and play Planeshift. On planeshift forums there was suggested to recompile mesa, which I don't know how..
Anyway, I've looked some of your packages, and couldn't find half of them in Synaptic, :) but ok, that's my problem:o I'll try to find a solution (or to recompile mesa), and if I do, I'll let you know.

Here's the link to ps forums: [http://hydlaa.com/smf/index.php?topic=26927.0](http://hydlaa.com/smf/index.php?topic=26927.0). At the bottom there's a link to launchpad. On launchpad there's a link to a nice looking solution-- for debian.:mrgreen:

---

### Post by cleardays on 2006-12-28
> **ltk5 said:**
> 
...
Anyway, I've looked some of your packages, and couldn't find half of them in Synaptic, :) but ok, that's my problem:o I'll try to find a solution (or to recompile mesa), and if I do, I'll let you know.
...


Maybe your source.list is different from mine. Here is mine:

[FONT="Courier New"][COLOR="RoyalBlue"]
(/etc/apt) > more sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restrict
ed

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer
se multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un
iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
[/COLOR][/FONT]

---

### Post by Thenotsowyzewun on 2006-12-28
I get the same error, but it hasn't messed anything up (that I've noticed...).
I've got a Toshiba Satellite A100-207 (standard specification), and it comes with the same Intel Express 945GM Chipset.
Going to try and find a solution now (now that I know its a proper problem that is!), I'll report back if I do :)

---

### Post by ltk5 on 2007-01-06
In Synaptic I selected 'Proprietary drivers for devices' and 'Canonical supported Open Source..'.
Then it gave me the options to install 'libgl1-mesa-swx11'.
After installation my 3d graphics work; Blender also. Thanks:D 
Planeshift is showing, it's just painuflly slow. I'll try to find a way about that.

---

