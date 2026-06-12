---
title: "Xgl CVS: faster &amp; better"
date: 2006-03-22
forum: Desktop Environments
---

### Post by DeeZiD on 2006-03-22
Advantages: 
- looks really nice
- No more slowdowns with NVIDIA-cards
- No more glitches with ATi radeons (solved some of my X700mobile problems)
- Fbos and Xv are working flawlessly with the latest fglrx and some modifications :)

Disadvantages:
- might be unstable
- bad support of opengl games and programs
- video issues (like tearing, problems with zoom etc.)


**[SIZE="4"]1. Download and install packages[/SIZE]**

**[COLOR="Red"]*i386 & amd64*[/COLOR]**
It has become very easy for dapper users. All packages are now available through apt. (Thanks to reggaemanu & quinnstorm)
You can use a graphical frontend like synaptic or adept *or use a terminal...*
```
sudo nano /etc/apt/sources.list
```
add the following lines...
```
deb http://www.beerorkid.com/compiz dapper main
deb-src http://www.beerorkid.com/compiz dapper main
or
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```
press CTRL+X and Enter. Then download the key for this repository (in your homefolder). [http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510]("http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510") 
Now install the key.
```
gunzip quinn.key.asc.gz
cat quinn.key.asc | sudo apt-key add -
```
install the new packages...
```
sudo apt-get update
sudo apt-get dist-upgrade 
(or if they're not installed yet)
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd
```


**[SIZE="4"]2. Configure Xgl[/SIZE]**

**[COLOR="Sienna"][SIZE="3"]Xgl with gdm for ubuntu-users[/SIZE][/COLOR]**

Open gdm.conf-custom
```
sudo gedit /etc/gdm/gdm.conf-custom
```
and add the following lines at the bottom.
**NVIDIA proprietary driver & ATi fglrx**
```
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

Then open gdm.conf
```
sudo gedit /etc/gdm/gdm.conf
```
and set the GdmXserverTimeout to 50. Uncomment the line before.
```
GdmXserverTimeout=50
```

**[SIZE="3"][COLOR="Navy"]Xgl with kdm for kubuntu-users[/COLOR][/SIZE]**

Open kdmrc
```
sudo kate /etc/kde3/kdm/kdmrc
```
and edit the ServerCmd to look like that...
**NVIDIA proprietary driver & ATi fglrx**
```
ServerCmd=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
```
And set servertimeout from 15 to 50. Uncomment the line before.
```
ServerTimeout=50
```

**don't forget!**
open displayconfig-restore
```
sudo kate /usr/bin/displayconfig-restore
```
and let the last line look like that placing a comment before main()
```
#main()
```


**[SIZE="4"]3. Configure Compiz and prevent Shift+Backslash bug[/SIZE]**

*[COLOR="Red"]**compiz i386 & amd64**[/COLOR]*
create and open the thefuture script
```
sudo nano /usr/bin/thefuture
```
now add the following lines...
```
#!/bin/bash
cgwd & compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```
press CTRL+X and Enter
make the script executeable
```
sudo chmod 755 /usr/bin/thefuture
```


**[COLOR="Sienna"][SIZE="3"]Compiz for ubuntu-users[/SIZE][/COLOR]**
Open sessions>prereferences>sessions
add "/usr/bin/thefuture" and "xmodmap /usr/share/xmodmap/xmodmap.<language>" (for me it is xmodmap.de) to your additional programs. 

**[SIZE="3"][COLOR="Navy"]Compiz for kubuntu-users[/COLOR][/SIZE]**
Put compiz.desktop in your /home/<user>/.kde/Autostart folder
[http://ubuntuforums.org/attachment.php?attachmentid=7960&d=1144093200](http://ubuntuforums.org/attachment.php?attachmentid=7960&d=1144093200)
Don't forget to edit the setxkbmap <language> line in it. It was setxkbmap de for me.


**[SIZE="4"]4. Now restart your (k)ubuntu :)[/SIZE]**


**[SIZE="4"]5. If it doesn't work...[/SIZE]**

Many people (me included) have the problem they don't have any window-decoration after that and they get no error message.

If that happens to you, try that:

kill compiz
```
killall compiz.real cgwd -9
```

then open metacity or kwin
```
metacity &
kwin &
```

open gconf-editor then
```
G_SLICE=always-malloc gconf-editor
```
go to /apps/compiz/general/allscreens/options/ and remove the active plugins line by  clicking with right mouse on the item and selecting "remove key" or something like that (sry, german version of gconf-editor ;) )

then restart compiz```
cgwd & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
```

---

### Post by vendetta red on 2006-03-22
Is there any way you could post the sources (or the links to them) for those as well. I am maintaining Xgl/Compiz on a Dapper install as well as a Gentoo install.

---

### Post by Bandit on 2006-03-22
If this kills my desktop its pownding time :D

The AMD64 XGL link seem sto be broken..

---

### Post by DeeZiD on 2006-03-22
@ vandetta red:
the sources from mesa are about 500MB big and sudo dpkg-buildpackage doesn't work with it. :mad: 

When I find the dpkg-buildpackage error, I will upload the sources :)

---

### Post by vendetta red on 2006-03-22
[QUOTE=DeeZiD]@ vandetta red:
the sources from mesa are about 500MB big and sudo dpkg-buildpackage doesn't work with it. :mad: 

When I find the dpkg-buildpackage error, I will upload the sources :)[/QUOTE]

ok, thanks. :)

---

### Post by eeclark on 2006-03-22
I don't use "thefuture"...and everything works for me...should I be using it?

---

### Post by DeeZiD on 2006-03-22
You don't need to, but you have to make sure to use LD_LIBRARY_PATH=/opt/mesa for compiz and gnome-window-decorator.

---

### Post by DeeZiD on 2006-03-22
@vandetta red:
I followed this howto:
[http://ubuntuforums.org/showthread.php?t=131659&highlight=AMD64+Xgl](http://ubuntuforums.org/showthread.php?t=131659&highlight=AMD64+Xgl)

You need to do following, to (the howto is a bit outdated)
patch Mesa with this patch:
[http://www.freedesktop.org/~davidr/m...buffer-1.patch](http://www.freedesktop.org/~davidr/m...buffer-1.patch)

and you need to install latest macros:
first go into xserver/xorg
```
cvs co util cd util/macros/ ./autogen.sh --prefix=/usr make sudo make install
```



then everything should work fine


it works very nice :)

---

### Post by jaymode on 2006-03-22
i have the following problem when doing:
sudo dpkg -i xorg_1.0.1_cvs-1_i386.deb
(Reading database ... 106538 files and directories currently installed.)
Unpacking xorg (from xorg_1.0.1_cvs-1_i386.deb) ...
dpkg: error processing xorg_1.0.1_cvs-1_i386.deb (--install):
 trying to overwrite `/usr/bin/Xgl', which is also in package xserver-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 xorg_1.0.1_cvs-1_i386.deb


Any ideas?

---

### Post by DeeZiD on 2006-03-22
uninstall old xgl first ;)
added in howto

---

### Post by krusbjorn on 2006-03-22
Isnt it supposed to ge "sudo chmod 755 /usr/bin/thefuture2"?

Anyways, I mean, look at the smooooooothness!! Thanks!!

---

### Post by vendetta red on 2006-03-22
[QUOTE=DeeZiD]@vandetta red:
I followed this howto:
[http://ubuntuforums.org/showthread.php?t=131659&highlight=AMD64+Xgl](http://ubuntuforums.org/showthread.php?t=131659&highlight=AMD64+Xgl)

You need to do following, to (the howto is a bit outdated)
patch Mesa with this patch:
[http://www.freedesktop.org/~davidr/m...buffer-1.patch](http://www.freedesktop.org/~davidr/m...buffer-1.patch)

and you need to install latest macros:
first go into xserver/xorg
```
cvs co util cd util/macros/ ./autogen.sh --prefix=/usr make sudo make install
```



then everything should work fine


it works very nice :)[/QUOTE]

the link to the patch is a 404 not found.

---

### Post by DeeZiD on 2006-03-22
@krusbjorn: fixed it ;)
@vendetta red: try the attached file-

regards Dennis

---

### Post by krusbjorn on 2006-03-22
DeeZiD:

Quinn mentioned that it's better to only use "compiz --replace gconf" instead of listing all the plugins. I wouldnt know why, but gconf should take care of loading the plugins. I edited the thefuture2 script according to this and it works like a charm. Of course, it worked before i changed it too ;)

---

### Post by jaymode on 2006-03-22
Sweet got it working.

Dont mean to hijack the thread but with my old setup and this one, whenever i do the xmodmap thing I lose my keyboard shortcuts for xgl like the built it ones. I cant rotate the cube with ctrl +alt + left/right. Anyone know why?

---

### Post by DeeZiD on 2006-03-22
@krusbjorn:
mhh, did you ever try this installing from scratch ;) ](*,) 


regards Dennis

---

### Post by DeeZiD on 2006-03-22
@jaymode:

no problem here...

---

### Post by krusbjorn on 2006-03-22
> **DeeZiD]@krusbjorn:
mhh, did you ever try this installing from scratch  said:**
> (*,) 


regards Dennis

Nope, I'm shamelessly letting you guys do the work. ;)

---

### Post by danmagicman7 on 2006-03-22
Websense blocks the rapidshare.de

I'm at college so I can't do anything about it.

Can anyone host an alternate mirror?  I would be very grateful!

---

### Post by mstlyevil on 2006-03-22
Success on my part. Thanks for your help in getting this s*** installed. :mrgreen:

---

### Post by vendetta red on 2006-03-22
[QUOTE=DeeZiD]@krusbjorn: fixed it ;)
@vendetta red: try the attached file-

regards Dennis[/QUOTE]

ok, I got the patch and have the howto bookmarked. I will check out the sources from CVS and build it on my Gentoo system as soon as its finished updating (probably about 2-3 hours from now, having to compile everything and all). I will post back here if/when I am successful in getting it working.....actually I'll post here if something goes wrong too. :)

---

### Post by mfarley on 2006-03-22
This thread should be prefixed with HowTo: and stickied.  I can't wait to try it in the morning.

---

### Post by Shikai on 2006-03-22
Finally! I can run beagle without those annoying as hell cpu spikes killing my machine!

---

### Post by Bandit on 2006-03-22
[QUOTE=Shikai]Finally! I can run beagle without those annoying as hell cpu spikes killing my machine![/QUOTE]
Sorry to ask a off topic question.
What did you have to do to get the graphic on top of the cube?
Thanks,
Joey

---

### Post by scpike on 2006-03-22
and the good old ati mobility x300 64mb ram card hardlocks again
bleh

i get just enough to get to use all the effects and see how cool they are, and then it dies randomly in hard lock, the begining of this thread was making me way to optomistic

---

### Post by Shikai on 2006-03-22
[QUOTE=Bandit]Sorry to ask a off topic question.
What did you have to do to get the graphic on top of the cube?
Thanks,
Joey[/QUOTE]
gconf-editor
apps --> compiz --> plugins --> cube --> screen0 --> options

For the svgs key, enter the path to the svg image you want to use. For me, that image is /home/shikai/.bamboo.svg

---

### Post by krusbjorn on 2006-03-22
[QUOTE=Shikai]gconf-editor
apps --> compiz --> plugins --> cube --> screen0 --> options

For the svgs key, enter the path to the svg image you want to use. For me, that image is /home/shikai/.bamboo.svg[/QUOTE]

Care to share that svg-image? :)

---

### Post by Shikai on 2006-03-22
lol...you want one with my screen name plastered on it? ;)

Umm...I'll see about removing that, and hosting up the panda later. Right now, gotta spend some time with the gf before she leaves for work.

---

### Post by Bandit on 2006-03-22
[QUOTE=Shikai]gconf-editor
apps --> compiz --> plugins --> cube --> screen0 --> options

For the svgs key, enter the path to the svg image you want to use. For me, that image is /home/shikai/.bamboo.svg[/QUOTE]

You know I was looking at that. But I really wanted to hear it from someone else.
I been taking online UNIX courses this week and I didnt want to break my desktop trying something out.
Thanks,
Joey

---

### Post by mstlyevil on 2006-03-22
Anyone else noticing that Firefox opens faster and seems to render pages faster also with this new build?

---

### Post by krusbjorn on 2006-03-22
[QUOTE=mstlyevil]Anyone else noticing that Firefox opens faster and seems to render pages faster also with this new build?[/QUOTE]

Yeah, I noticed. Swiftness. Everything seems to be faster.

---

### Post by Bandit on 2006-03-23
[QUOTE=Shikai]gconf-editor
apps --> compiz --> plugins --> cube --> screen0 --> options

For the svgs key, enter the path to the svg image you want to use. For me, that image is /home/shikai/.bamboo.svg[/QUOTE]
I cant seem to get it to work. ](*,)  It stays white. ????
Any suggestions?
Thanks,
Joey

---

### Post by WiLLiE on 2006-03-23
Smooth as a babys butt! :mrgreen:

---

### Post by WiLLiE on 2006-03-23
[QUOTE=Bandit]I cant seem to get it to work. ](*,)  It stays white. ????
Any suggestions?
Thanks,
Joey[/QUOTE]
Check the path to the svg.
Press space to see if that refreshes it.

---

### Post by matid on 2006-03-23
Could you please use something different from rapidshare to store this files? I could even host them, but I rapidshare is preventing me from downloading...

---

### Post by reggaemanu on 2006-03-23
I've made all needed packages for the new xgl in the proper ubuntu way, so if you want it instead of the checkinstall packages there are here :

Just needed packages for running xgl (for most users):
[http://www.reggaemanu.info/new-xgl.tar.gz]("http://www.reggaemanu.info/new-xgl.tar.gz") (14Mb)

Or all packages going with xgl (so all "-dev" packages and packages needed for compile the new xgl) :
[http://www.reggaemanu.info/new-xgl-all.tar.gz]("http://www.reggaemanu.info/new-xgl-all.tar.gz") (25Mb)

All packages are tested and works fine for me.

_**Attention**_: thoses packages replace ubuntu's universe ones for mesa/cairo/glitz/xserver-xgl, they are not using /opt/fdo for installing stuff. So don't forget to edit your scripts for launching Xgl and compiz. Both are now in /usr/bin and mesa is in /usr/lib

---

### Post by Bandit on 2006-03-23
[QUOTE=WiLLiE]Check the path to the svg.
Press space to see if that refreshes it.[/QUOTE]
/home/bandit/.cubeback.svg
the file is hidden .cubeback.svg

---

### Post by mstlyevil on 2006-03-23
[QUOTE=WiLLiE]Check the path to the svg.
Press space to see if that refreshes it.[/QUOTE]

I got it to work with Fetso, a charecter from Casper the friendly ghost. It looks pretty cool.

---

### Post by WiLLiE on 2006-03-23
[QUOTE=Bandit]/home/bandit/.cubeback.svg
the file is hidden .cubeback.svg[/QUOTE]
Not sure what to tell you then.
Nautilus displays a thumbnail?
Can you double-click it and view in the imageviewer?

[QUOTE=mstlyevil]I got it to work with Fetso, a charecter from Casper the friendly ghost. It looks pretty cool.[/QUOTE]
I'm using tux. What else :mrgreen:

---

### Post by Bandit on 2006-03-23
[QUOTE=WiLLiE]Not sure what to tell you then.
Nautilus displays a thumbnail?
Can you double-click it and view in the imageviewer?


I'm using tux. What else :mrgreen:[/QUOTE]
I can view the image. I dont kow whats up either.
I just installed the latest cvs of both XGL/Compiz.
Still no go.
But I wouldnt worry to much about it. Its no big deal.
Thanks,
Joey

---

### Post by WiLLiE on 2006-03-23
[QUOTE=Bandit]I can view the image. I dont kow whats up either.
I just installed the latest cvs of both XGL/Compiz.
Still no go.
But I wouldnt worry to much about it. Its no big deal.
Thanks,
Joey[/QUOTE]

Tried restarting compiz?

---

### Post by drizek on 2006-03-23
thefuture2 doesnt work ofr me on kde. It works perfectly with the regular thefuture though.

---

### Post by Shikai on 2006-03-23
If it's not working with that path, try removing the /home/user portion.

When I first tried, I had to set the path relative to my home directory. So instead of /home/shikai/.svgfile.svg, try .svgfile.svg

---

### Post by Eklöf on 2006-03-23
Woh, resizing firefox now works ! Sweet.

---

### Post by manicka on 2006-03-23
Joey, it only works for me with square images

---

### Post by chadwick359 on 2006-03-23
Is there any way to get gnome-window-decorator to use a smaller font? The latest XGL seems to render fonts the same way that X did, making them look really big on my system. If anybody knows of a way to do this, I'd appreciate the help.

---

### Post by DrSturgeon on 2006-03-23
> No more glitches with ATi radeons (solved my X700mobile problems)

If anyone cares, it still freezes almost instantly on my X300.

Sorry to be the downer in the midst of all the excitement.

---

### Post by drizek on 2006-03-23
use gnome-control-center for the font

if you dont have it, just apt get it.

---

### Post by bites on 2006-03-23
Everything's working fine here (Nvidia 5700)!  I can even compile and rotate without any hiccups :)

Thanks for the packages..

---

### Post by manicka on 2006-03-23
These packages are simply amazing :D 

Congrats to everyone who is maintaining them. I am just astounded at the pace that this is all moving

---

### Post by LJunkie on 2006-03-23
[QUOTE=DrSturgeon]If anyone cares, it still freezes almost instantly on my X300.

Sorry to be the downer in the midst of all the excitement.[/QUOTE]

Same with my X600. ](*,) ](*,) ](*,)

---

### Post by AnThOnYhO on 2006-03-23
[QUOTE=reggaemanu]I've made all needed packages for the new xgl in the proper ubuntu way, so if you want it instead of the checkinstall packages there are here :

Just needed packages for running xgl (for most users):
[http://www.reggaemanu.info/new-xgl.tar.gz]("http://www.reggaemanu.info/new-xgl.tar.gz") (14Mb)

Or all packages going with xgl (so all "-dev" packages and packages needed for compile the new xgl) :
[http://www.reggaemanu.info/new-xgl-all.tar.gz]("http://www.reggaemanu.info/new-xgl-all.tar.gz") (25Mb)

All packages are tested and works fine for me.

_**Attention**_: thoses packages replace ubuntu's universe ones for mesa/cairo/glitz/xserver-xgl, they are not using /opt/fdo for installing stuff. So don't forget to edit your scripts for launching Xgl and compiz. Both are now in /usr/bin and mesa is in /usr/lib[/QUOTE]


Have anybody try it .I think the dpk way maybe is better than the checkinstall way.

---

### Post by AnThOnYhO on 2006-03-23
Some minutes i apt-get dist-upgrade,I find the xgl is update  (xserver-xgl 7.0.0-0ubuntu3 => 7.0.0-0ubuntu5).
If the DeeZiD  upgrade the repo.

---

### Post by funkenstein on 2006-03-23
Hey dood - first of all - this is SWEET!!
Sure, I had problems with some of the deps, but some common sense and reading the errors/installing what was needed fixed that....
One thing you forgot to mention - 
```
sudo gedit /etc/gdm/gdm.conf-custom
``` and add this to the end of the file:
```
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

...cuz I completely forgot and couldn't understand why, for the life of me, this doesn't work:confused:](*,)](*,)

:mrgreen:

---

### Post by hva on 2006-03-23
for amd64 users: i've built a new compiz package, this time with libsvg-cairo enabled (i hadn't libsvg yesterday) and some of the quinnstorm patches (opaquefocus, transset), altough in my opinion opaquefocus still needs some work, i don't like it much when using expose-like window switching: it doesn't always restore right opacity for chosen window.
as usual: it works for me, i do not guarantee anything.

---

### Post by geearf on 2006-03-23
I can finally use mplayer with you Xgl build (well I think it's because of the new Xgl but I may be wrong ...)

Thanks!

---

### Post by funkenstein on 2006-03-23
I'm getting ```
*** glibc detected *** double free or corruption (out): 0x083821d0 ***
``` whenever I change something in gconf-editor. The only way I can get out of it is killall gconf-editor... but I want to change stuff and I can't :(
speaking of which, where else can I change those options other than the gconf-editor?

---

### Post by funkenstein on 2006-03-23
ok, so I read [_One Thread To Rule Them All_](http://ubuntuforums.org/showthread.php?t=148351) and it explains what to do with gconf-crashing and using the gconf-tool is for editing gconf without the editor.

there I go without reading the friendly forums... again... 8-[

---

### Post by zorglab on 2006-03-23
[QUOTE=funkenstein]I'm getting ```
*** glibc detected *** double free or corruption (out): 0x083821d0 ***
``` whenever I change something in gconf-editor. The only way I can get out of it is killall gconf-editor... but I want to change stuff and I can't :(
speaking of which, where else can I change those options other than the gconf-editor?[/QUOTE]

I'm getting exactly the same problem. Adding GSLICE=only-malloc (or something like that, I don't remember the exact command) doesn't do the trick.

BTW gconf-editor crashes after changing the value in gconf, so nothing gets lost and its still possible to "work" with gconf-editor, at least if you're willing to restart the app after every change you make.

---

### Post by hugmenot on 2006-03-23
[QUOTE=reggaemanu]I've made all needed packages for the new xgl in the proper ubuntu way, so if you want it instead of the checkinstall packages there are here :
[/QUOTE]


Thanks for doing it The Right Way (tm).

Works here.

---

### Post by pouns on 2006-03-23
> Originally Posted by reggaemanu
I've made all needed packages for the new xgl in the proper ubuntu way, so if you want it instead of the checkinstall packages there are here :

Just needed packages for running xgl (for most users):
[http://www.reggaemanu.info/new-xgl.tar.gz](http://www.reggaemanu.info/new-xgl.tar.gz) (14Mb)

Or all packages going with xgl (so all "-dev" packages and packages needed for compile the new xgl) :
[http://www.reggaemanu.info/new-xgl-all.tar.gz](http://www.reggaemanu.info/new-xgl-all.tar.gz) (25Mb)

All packages are tested and works fine for me.

Attention: thoses packages replace ubuntu's universe ones for mesa/cairo/glitz/xserver-xgl, they are not using /opt/fdo for installing stuff. So don't forget to edit your scripts for launching Xgl and compiz. Both are now in /usr/bin and mesa is in /usr/lib

I tried these packages with the radeon driver on an ATI M9 and they didn't work. It says that it can't find a screen. (It works before)
Any idea ?

---

### Post by Melvil on 2006-03-23
[QUOTE=reggaemanu]I've made all needed packages for the new xgl in the proper ubuntu way, so if you want it instead of the checkinstall packages there are here :

Just needed packages for running xgl (for most users):
[http://www.reggaemanu.info/new-xgl.tar.gz]("http://www.reggaemanu.info/new-xgl.tar.gz") (14Mb)
[/QUOTE]

Works perfectly out of the box.

Anyone else noticed the fonts in titlebars are now a bit smaller than in the previous Xgl version? I've got an Ati card

---

### Post by geearf on 2006-03-23
I have upgraded this morning to new packages, and since then I cannot start Xgl anymore.
I'm now using the good packages provided a bit earlier (thanks).

I'm seeing this error in my kdm log : 
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

This is the first time I see it. If I copy the library from ../extensions it complains about somethings it does not know ...

Anyone has an idea about this ?

Thanks

---

### Post by drummer on 2006-03-23
Wow... this is so much smoother! Thanks everyone who's maintaining this, it's awsome. I have a radeon 9250 using open source 'radeon' drivers and was getting terrible 'flicker' and images not rendering fast enough, etc. I thought it was the vid card and was thinking of upgrading to an nvidia 6600gt, but now i'm not so sure if i really need to or not.

I get heaps of cpu load when playing videos in any player... ~66% using x11 output, and 100% using anything else (xv, gl, gl2). Also, spinning the cube with Ctrl+Alt+[left/right] is jerky/laggy if there are windows on the desktop. Flicker isn't so bad, but still occurs with FF especially. Well this build is certainly a vast improvement, but I still have those problems. 

Since the flicker IS a bit better, I'm not blaming that on my vid card... but **would the cpu usage be related to the capabilities of my video card?** That'd be good to know, to see if it's worth upgrading.

This is coming along supurbly though... these 2 peices of software are just beautiful and can only get better. I'm so excited with the direction this is headed. :D

---

### Post by DeeZiD on 2006-03-23
The radeon r200 xorg drivers were patched a few weeks ago.
But these patches didn't made it in dapper (maybe this morning?)

If you want the best possible performance you need the latest cvs drivers.
I will try to build them this evening. Thank god Xorg became modular ;)


regards Dennis

---

### Post by Jeff250 on 2006-03-23
For the Mesa i915 drivers to compile from cvs, you need the latest libdrm from cvs as well.

---

### Post by Qoon3x on 2006-03-23
i can't install al packages.. when i try to install libglitz1-dev i get this error:
(al the other packages are already installed except libglitz-glx-1-dev)

 libglitz1-dev is afhankelijk van xlibmesa-gl-dev | libgl-dev; maar:
  Pakket **xlibmesa-gl-dev** is niet geïnstalleerd. (not installed)
  Pakket **libgl-dev** is niet geïnstalleerd. (not Installed)
 
is there someone else met the same problem and maybe has a fix for it?

---

### Post by Bandit on 2006-03-23
I am actualy having issues with this version.
Many things do seem smoother, and the smaller dailog boxes are fixed.
But totem hangs every now and then when playing a video and if you move things around the screen to quicly the window will disapear.
Tool tips allignment correct so they are now readable.
But... I went back to a previous cvs version. The previous is much more stable on my system and much harder to break.
Cheers,
Bandit

---

### Post by Belfagor on 2006-03-23
hi after i ve installed teh mesa-cvs dep for amd64 my glxextensions seems got broken... and glxinfo gives me that erros

> belfagor@ubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual


how can i fix it?

---

### Post by mfarley on 2006-03-23
Following this HowTo: From the beginning -- I'm very new to linux:

I've downloaded all the listed packages, but some of them are in tar.gz

> sudo dpkg -i <packages>

For this step above, do I need to first untar/unzip all the tarballs?  I tried that, now I have about 12 .deb's, some of them are named very similar.

Can anyone show me an example of all the lines for:

> sudo dpkg -i <packages>

Thanks!

---

### Post by Bandit on 2006-03-23
[QUOTE=mfarley]Following this HowTo: From the beginning -- I'm very new to linux:

I've downloaded all the listed packages, but some of them are in tar.gz



For this step above, do I need to first untar/unzip all the tarballs?  I tried that, now I have about 12 .deb's, some of them are named very similar.

Can anyone show me an example of all the lines for:



Thanks![/QUOTE]
Extract the archives, the debs are inside them..

---

### Post by senning on 2006-03-23
Hi mfarley,
I haven't actually worked up the courage to try these out yet, but here's what you should probably do...
```
sudo dpkg -i libglitz1_0.5.5-0ubuntu1_i386.deb libglitz1-dev_0.5.5-0ubuntu1_i386.deb libglitz-glx1_0.5.5-0ubuntu1_i386.deb libglitz-glx1-dev_0.5.5-0ubuntu1_i386.deb xorg_1.0.1_cvs-1_i386.deb mesa_6.5_cvs032206-1_i386.deb libsvg_0.1.4-0_i386.deb libsvg-cairo_0.1.5-0_i386.deb compiz_0.0.7-0ubuntu4_i386.deb
```
**and**, if you're running GNOME,
```
compiz-gnome_0.0.7-0ubuntu4_i386.deb
```
**or** KDE,
```
compiz-kde_0.0.7-0ubuntu4_i386.deb
```

Mistakes are left as an exercise to the reader :-) .

P.S. Anyone have these working for a Radeon 9200SE?

---

### Post by sleepkreep on 2006-03-23
My minimize effects are gone now :(  How to fix?

---

### Post by byoon on 2006-03-23
This is from 

[http://compiz.blogspot.com/2006/03/zoom-on-launch.html]("http://compiz.blogspot.com/2006/03/zoom-on-launch.html")

> 
Some Gnome users experienced initial problems with getting it to work, chanders eventually solved it here (see the edit)

Ok I think the problem was the list of window types in gconf. For some reason I had a 'Toolbar' in there and no ModalDialog... When this was changed it all works perfectly!!

REV3 works! make sure window_types is [Utility,Dialog,Normal,ModalDialog] is so.


For me, I removed the Dialog and the ModalDialog because I don't like them zooming in.

---

### Post by mfarley on 2006-03-23
[QUOTE=senning]Hi mfarley,
I haven't actually worked up the courage to try these out yet, but here's what you should probably do...

Mistakes are left as an exercise to the reader :-) .
[/QUOTE]

I must be missing the mistakes :)

```
sudo dpkg -i libglitz1-dev_0.5.5-0ubuntu1_i386.deb 

 libglitz1-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
 libglitz1-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
```

```
sudo dpkg -i compiz_0.0.7-0ubuntu4_i386.deb 

 compiz-gnome depends on libpango1.0-0 (>= 1.12.0); however:
  Version of libpango1.0-0 on system is 1.11.99-0ubuntu2.

```

Any ideas? (do I need to get the latest drapper updates?  apt-get update?)

---

### Post by robertknight on 2006-03-23
Hi,

The latest Xgl is a huge improvement.  My desktop is now responsive whilst I am doing CPU intensive background tasks (ie. compiling big projects) which is great.

Thanks for all the hard work everyone!

PS.  I love the zoom-on-create effect!

---

### Post by Technoviking on 2006-03-23
[QUOTE=DeeZiD]
```
#!/bin/bash
LIBMESA=/opt/mesa/lib
LD_LIBRARY_PATH=$LIBMESA gnome-window-decorator & LD_LIBRARY_PATH=$LIBMESA  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus &
```[/QUOTE]
It this right? I do not have a /opt/mesa/lib after updating from quinstorm repo.

---

### Post by Qoon3x on 2006-03-23
[QUOTE=mfarley]I must be missing the mistakes :)

```
sudo dpkg -i libglitz1-dev_0.5.5-0ubuntu1_i386.deb 

 libglitz1-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
 libglitz1-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
```

Same problem here

---

### Post by DeeZiD on 2006-03-23
If you're using Xgl, compiz, mesa etc... from the new quinnstorm repo, you don't need to change the compiz commandline.

I will change the howto this evening ;)

regards Dennis

---

### Post by krusbjorn on 2006-03-23
[QUOTE=Mike Basinger]It this right? I do not have a /opt/mesa/lib after updating from quinstorm repo.[/QUOTE]

I did a dist-upgrade just now, including both the dapper and quinn's repos, and:

> johannes@embla:/opt/mesa/lib$ ls
libGL.so      libGLU.so             libglut.so        libGLw.so
libGL.so.1    libGLU.so.1           libglut.so.3      libGLw.so.1
libGL.so.1.2  libGLU.so.1.3.060500  libglut.so.3.7.1  libGLw.so.1.0.0

---

### Post by DeeZiD on 2006-03-23
@Qoon3x & others:
you don't need to install all these developement packages if you are not going to compile new packages ;)


regards Dennis

---

### Post by DeeZiD on 2006-03-23
@krusbjorn:
are you sure these libraries are from quinnstorms repositore?
They seem to be from my checkinstall package yesterday.

---

### Post by mfarley on 2006-03-23
[QUOTE=DeeZiD]@Qoon3x & others:
you don't need to install all these developement packages if you are not going to compile new packages ;)


regards Dennis[/QUOTE]

What about this one:

```
sudo dpkg -i compiz_0.0.7-0ubuntu4_i386.deb 

 compiz-gnome depends on libpango1.0-0 (>= 1.12.0); however:
  Version of libpango1.0-0 on system is 1.11.99-0ubuntu2.
```

---

### Post by krusbjorn on 2006-03-23
[QUOTE=DeeZiD]@krusbjorn:
are you sure these libraries are from quinnstorms repositore?
They seem to be from my checkinstall package yesterday.[/QUOTE]

Ahh, yeah. Sorry, my mistake.

---

### Post by Technoviking on 2006-03-23
[QUOTE=krusbjorn]I did a dist-upgrade just now, including both the dapper and quinn's repos, and:[/QUOTE]
I'm erroring out on quinn repo now, probably not getting everything.
```

Failed to fetch http://metascape.afraid.org:13666/apt/dists/dapper/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by mfarley on 2006-03-23
[QUOTE=mfarley]What about this one:

```
sudo dpkg -i compiz_0.0.7-0ubuntu4_i386.deb 

 compiz-gnome depends on libpango1.0-0 (>= 1.12.0); however:
  Version of libpango1.0-0 on system is 1.11.99-0ubuntu2.
```[/QUOTE]

Nevermind, got it figured out.. Obvious newbie here..

---

### Post by Technoviking on 2006-03-23
After updated to this version of compiz (and assosted extras), I have noticed some flaws in the window borders. This are very minor, but noticable.

Does anyone have this problem?

---

### Post by qodsec on 2006-03-23
Mike Basinger : I am seeing a similar thing. looks like the scroll bar is not packed up against the window.

---

### Post by flargen on 2006-03-23
Nice works guys!

So, are the new Xgl/mesa/glitz/drm/cairo etc packages that are being updated from quinnstorm´s repo? (yes i do have it enabled). And is the Xgl the one from this thread?

EDIT:
Never mind, I went for it anyway! All packages installed correctly and I think everything is a bit snappier than before with my radeon 9600 128mb. Good stuff ;)

---

### Post by vendetta red on 2006-03-23
I followed this howto for my ubuntu install and using thefuture2 just kills metacity and nothing else. Compiz is still working with my original thefuture script Looking in synaptic, it shows the new xorg 1.0.1_cvs-1 installed, but xserver-xgl isn't installed even though Xgl has to be installed for compiz to work.

Needless to say, I'm a little confused, if xserver-xgl isn't installed then how am I running it and Compiz on top of it? ](*,)

---

### Post by denisesballs on 2006-03-23
After todays updates I get:

```
jesse@dapper:~/systems/newxgl$ sudo dpkg -i *.deb
(Reading database ... 173977 files and directories currently installed.)
Preparing to replace compiz 0.0.7-0ubuntu4 (using compiz_0.0.7-0ubuntu4_i386.deb) ...
Unpacking replacement compiz ...
Preparing to replace compiz-gnome 0.0.7-0ubuntu4 (using compiz-gnome_0.0.7-0ubuntu4_i386.deb) ...
Unpacking replacement compiz-gnome ...
Preparing to replace compiz-kde 0.0.7-0ubuntu4 (using compiz-kde_0.0.7-0ubuntu4_i386.deb) ...
Unpacking replacement compiz-kde ...
Preparing to replace libglitz1 0.5.5-0ubuntu1 (using libglitz1_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz1 ...
Preparing to replace libglitz1-dev 0.5.5-0ubuntu1 (using libglitz1-dev_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz1-dev ...
Preparing to replace libglitz-glx1 0.5.5-0ubuntu1 (using libglitz-glx1_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz-glx1 ...
Preparing to replace libglitz-glx1-dev 0.5.5-0ubuntu1 (using libglitz-glx1-dev_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz-glx1-dev ...
Preparing to replace libsvg 0.1.4-0 (using libsvg_0.1.4-0_i386.deb) ...
Unpacking replacement libsvg ...
Preparing to replace libsvg-cairo 0.1.5-0 (using libsvg-cairo_0.1.5-0_i386.deb) ...
Unpacking replacement libsvg-cairo ...
Preparing to replace mesa 6.5_cvs032206-1 (using mesa_6.5_cvs032206-1_i386.deb) ...
Unpacking replacement mesa ...
Unpacking xorg (from xorg_1.0.1_cvs-1_i386.deb) ...
dpkg: error processing xorg_1.0.1_cvs-1_i386.deb (--install):
 trying to overwrite `/usr/lib/pkgconfig/xorg-server.pc', which is also in package xserver-xorg-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up libglitz1 (0.5.5-0ubuntu1) ...

Setting up libglitz1-dev (0.5.5-0ubuntu1) ...
Setting up libglitz-glx1 (0.5.5-0ubuntu1) ...

Setting up libglitz-glx1-dev (0.5.5-0ubuntu1) ...
Setting up libsvg (0.1.4-0) ...

Setting up libsvg-cairo (0.1.5-0) ...

Setting up mesa (6.5_cvs032206-1) ...
Setting up compiz (0.0.7-0ubuntu4) ...
Setting up compiz-gnome (0.0.7-0ubuntu4) ...
Setting up compiz-kde (0.0.7-0ubuntu4) ...
Errors were encountered while processing:
 xorg_1.0.1_cvs-1_i386.deb
```

I get this when trying the xgl from the repos too. Anyone know how to fix?

---

### Post by hugmenot on 2006-03-23
[QUOTE=Mike Basinger]After updated to this version of compiz (and assosted extras), I have noticed some flaws in the window borders. This are very minor, but noticable.

Does anyone have this problem?[/QUOTE]

[Yes]("http://www.ubuntuforums.org/showpost.php?p=850683&postcount=16")

---

### Post by danmagicman7 on 2006-03-23
Thanks for the packages!

I installed all of them, XGL runs nice and smooth.  However, it doesn't like any buttons on the top, it will hardlock the system sometimes.

However, I have a small dillema

Using thefuture2, I get no errors, no anything, it completes the command, and waits for my next command.

The only thing that happens is that the window bars go away.  :-/

I have an ATI card, and fglrxinfo says it is all started up just fine. Hmmm...

Anybody help?

---

### Post by firetux on 2006-03-23
DeeZiD: Can you please host the files you now have on rapidshare on something else? (attachment maybe?)

(For some ](*,) reason rapidshare says that the ip I requested th file from is not the same as the one that I want to download from.)

thanks in advance

---

### Post by senning on 2006-03-23
denisesballs, unless you have a reason to keep xserver-xorg-dev, remove it (sudo apt-get remove xserver-xorg-dev).  Should solve your problem.

---

### Post by vendetta red on 2006-03-23
[QUOTE=danmagicman7]Thanks for the packages!

I installed all of them, XGL runs nice and smooth.  However, it doesn't like any buttons on the top, it will hardlock the system sometimes.

However, I have a small dillema

Using thefuture2, I get no errors, no anything, it completes the command, and waits for my next command.

The only thing that happens is that the window bars go away.  :-/

I have an ATI card, and fglrxinfo says it is all started up just fine. Hmmm...

Anybody help?[/QUOTE]

Thats exactly the same that happens here, running Nvidia though.

---

### Post by zachtib on 2006-03-23
what exactly is the zoom-on-create effect?
and has anyone built the patched r200 drivers? if so, i'd appreciate it if someone could post them.

---

### Post by flargen on 2006-03-23
Stupid question:
With this new round of Xgl and deps packages, a new mesa was included. With the old Xgl (from battlehorse) I could use the libGL from mesa (again from battlehorse, I think). But now when I try to do that with the mesa 6.5 libGL, I get the missing extension errors back. I have to use /usr/lib/fglrx/libGL.so.1.2.xlibmesa as defined in the compiz shell script. I just wondered if this (old?) version of mesa would have any negative performance issues. And if this libGL is being used, what is the need for installing another version of mesa?
:confused: :confused: :confused:

---

### Post by reggaemanu on 2006-03-23
[quote=flargen]Stupid question:
With this new round of Xgl and deps packages, a new mesa was included. With the old Xgl (from battlehorse) I could use the libGL from mesa (again from battlehorse, I think). But now when I try to do that with the mesa 6.5 libGL, I get the missing extension errors back. I have to use /usr/lib/fglrx/libGL.so.1.2.xlibmesa as defined in the compiz shell script. I just wondered if this (old?) version of mesa would have any negative performance issues. And if this libGL is being used, what is the need for installing another version of mesa?
:confused: :confused: :confused:[/quote]

battlehorse packages install themselves in /opt/fdo, if you've used mine (those in QuinnStorm repository) they replace ubuntu's one, so files are in commons directory ( /usr/bin for binaries and /usr/lib for libraries) so if you had to make a symlink when you've installed battlehorse packages, you probably need to redo a symlink with the right path.
What « missing extension errors » are you talking about?

---

### Post by flargen on 2006-03-23
Thanks for your reply.
I used to have Xgl and a few libs in /opt/fdo/, and compiz and the rest were in /usr/. I did use symlinks so everything appeared in /opt/fdo/ for ease. But now all the newest libs are installed in /usr/ so I removed /opt/fdo/, changed my gdm config to reflect this, and removed all the LD_LIBRARY_PATH=/opt/fdo/lib commands from my compiz startup script.
Everything works great when used how it was setup by default. But the default for compiz is to preload fglrx's mesa libs, instead of using the new system-wide mesa from QuinnStorm's repo. I had it working in the past with the mesa from battlehorse, but now there are some errors that I have only encountered before with a version of mesa that was too old:
```
$ compiz.real --replace gconf
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0
```
Note: I am only using compiz.real here to demonstrate my point.
My main question is - is there any reason why there is a missing GLX extension from the newest mesa, and why does compiz try to use the libGL other than the system-wide one by default?

Thanks

---

### Post by reggaemanu on 2006-03-23
[quote=flargen]
```
$ compiz.real --replace gconf
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0
``` Note: I am only using compiz.real here to demonstrate my point.
My main question is - is there any reason why there is a missing GLX extension from the newest mesa, and why does compiz try to use the libGL other than the system-wide one by default?

Thanks[/quote]

There's some post about a similar problem in the battlehorse page comments. And i had this problem too (with nvidia and battlehorse .deb, not with actual ones).
Xgl seems using libGL.so.1, and compiz uses libGL.so only, so try to reinstall your drivers after install mesa, or reinstall mesa after your driver, or make a symlink to the right lib for libGL.so.1.

---

### Post by geearf on 2006-03-23
ok I have found my problem : 
any installation / upgrade of xorg breaks my nvidia drivers setup (that I knew).
but any installation of these drivers is now breaking my xgl setup, so therefore I have to first update xorg, then install the nvidia binaries, and then update xgl ... dooh what a simple world.

---

### Post by sillysyl on 2006-03-23
[QUOTE=geearf]ok I have found my problem : 
any installation / upgrade of xorg breaks my nvidia drivers setup (that I knew).
but any installation of these drivers is now breaking my xgl setup, so therefore I have to first update xorg, then install the nvidia binaries, and then update xgl ... dooh what a simple world.[/QUOTE]

Rather than updating xgl every time you update xorg and reinstall nvidia drivers, you can have a backup of /usr/lib/xorg/modules/xgl/libglx.so and copy it back there. This file is deleted by the nvidia install which deletes any libglx it can find :)

---

### Post by Shadou on 2006-03-24
I'm still experiencing hardlocks with these packages on my laptop:

os[Linux 2.6.15-19-386 i686]
cpu[1 x Intel(R) Pentium(R) M processor 1.86GHz @ 798MHz]
mem[Physical : 1011MB, 73.9% free]
disk[Total : 72.45GB, 15.50% Free] video[ATI Technologies Inc Radeon Mobility X700] sound[ICH4 - Intel ICH6]

Is there anyway I can debug the hardlocks, so that I may post some useful information (i.e; what/why this is crashing, etc)

Also, I have noticed that if I kill -9 the Xgl process, the fglrx driver spits an error and kernel faults.

---

### Post by Tharna on 2006-03-24
I tried this new xgl with my radeon box (9000pro + xorg-radeon drivers) and now it appears to be stable (had hard freezes earlier), but it appears much slower in some areas. Cube is smooth, but wobbly is allmost a pain with anything that smallest windows, text scrolls reeeeally slow, fade etc. arent nice to watch either.

---

### Post by net-x on 2006-03-24
Is there need to uninstall old glitz,mesa,compiz before?

---

### Post by Omer on 2006-03-24
[QUOTE=net-x]Is there need to uninstall old glitz,mesa,compiz before?[/QUOTE]
The upgrade went smooth for me, w/o removing old debs.

---

### Post by puccaso on 2006-03-24
erm
the how to is fine
but there is nothing that i can see
that has to do with xgl
yea we installed it
but

the only thing we did was nano the future2 file
where is the bit that actually initates xgl?

---

### Post by Shadou on 2006-03-24
You do that in /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom - check the other howtos for details.. these are just updated packages ;)

---

### Post by trorion on 2006-03-24
I'm a bit confused.

I downloaded the packages starting with glitz which gave me 4 .deb packages when I unpacked it.  Which one should I use?  If I try the libglitz1-dev_0.5.5-0ubuntu1_i386.deb package it gives me```
trorion@Dapper:~/Desktop/XGL$ sudo dpkg -i libglitz1-dev_0.5.5-0ubuntu1_i386.deb(Reading database ... 68162 files and directories currently installed.)
Preparing to replace libglitz1-dev 0.5.5-0ubuntu1 (using libglitz1-dev_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz1-dev ...
dpkg: dependency problems prevent configuration of libglitz1-dev:
 libglitz1-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
dpkg: error processing libglitz1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglitz1-dev

```

I dpkg mesa and get the same error.

Is there a specific order I need to extract them?

---

### Post by cywhale on 2006-03-24
Problem removing xorg_1.0.1_cvs...i386.deb-version from the first posting of this thread....

[EDIT/SOLVED]

---

### Post by stubby on 2006-03-24
[QUOTE=trorion]I'm a bit confused.

Is there a specific order I need to extract them?[/QUOTE]

No, just don't install the -dev packages.

---

### Post by geearf on 2006-03-24
[quote=DeeZiD]2. ```
xmodmap /usr/share/xmodmap/xmodmap.<language>
``` 
;)[/quote]

Hello,

the new versions are much better but now my keyboard is not fully functional, and I have no directory named xmodmap in /usr/share.
What should I do? thanks

---

### Post by spiritz on 2006-03-24
I'm using the following one :
DISPLAY=:1 setxkbmap -model pc105 -layout fr -variant basic
DISPLAY=:1 setxkbmap -model pc105 -layout fr -variant basic
(actually I added it twice, since sometimes it doesn't work at first)

---

### Post by geearf on 2006-03-24
ok I'll try that thanks :)

---

### Post by legend_x on 2006-03-24
Eveything seems to work fine but... i cant move any window...and woobly doesn't work neither. I've try to move window with ALT and with the titlebar. No error in any logfile...anyone. I've been using the lastest from QuinnStorm. Thanks for you help ](*,)

---

### Post by Shadou on 2006-03-24
[QUOTE=legend_x]Eveything seems to work fine but... i cant move any window...and woobly doesn't work neither. I've try to move window with ALT and with the titlebar. No error in any logfile...anyone. I've been using the lastest from QuinnStorm. Thanks for you help ](*,)[/QUOTE]

Try chaing /usr/bin/thefuture2 to look like this:

```

#!/bin/bash
LD_LIBRARY_PATH=/opt/mesa/lib gnome-window-decorator &
sleep 2
LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus &
```

I gave it sleep 2, experiment, I've found that compiz doesn't wanna start if it's executed too quickly after g-w-d.

---

### Post by legend_x on 2006-03-24
Thanks a lot but it didn't solve the problem.Same thing. But i've realised that every "plugin" that move or resize windows doesn't work neither, like wobbly "F12" the the ALT right click to rezise a window. Im still diggin for a solution. thanks for your help

---

### Post by legend_x on 2006-03-24
Here's what i've done so far. 

[LIST]
[*]Follow the guide [http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860)
[*]Change my gdm.conf-custom to : 
[I][servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/I]
[*]Add this to my source.list: deb [http://metascape.afraid.org:13666/apt](http://metascape.afraid.org:13666/apt) dapper main
[*]And do an dist-upgrade
[/LIST]

---

### Post by geearf on 2006-03-25
[quote=spiritz]I'm using the following one :
DISPLAY=:1 setxkbmap -model pc105 -layout fr -variant basic
DISPLAY=:1 setxkbmap -model pc105 -layout fr -variant basic
(actually I added it twice, since sometimes it doesn't work at first)[/quote]

I've tried that but all I get is this : 

Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault

I've tried various things that were no good.

---

### Post by Belfagor on 2006-03-25
hi! amd64 debs have killed my glx extensions.. which package includes these glx extensions?

---

### Post by Athropos on 2006-03-25
This new packages seem to automatically do some sort of antialising. AA is disabled on my system for fonts smaller than 16 pt, and with these packages AA is back, regardless of my prefs. This makes small monospaced fonts hard to read.

---

### Post by cywhale on 2006-03-25
Last problem seems to be mesa here: using a startup script 'startcompiz'
```
killall gnome-window-decorator 
wait
#LD_LIBRARY_PATH=/usr/lib gnome-window-decorator & DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib compiz --replace gconf &
LD_LIBRARY_PATH=/opt/mesa/lib gnome-window-decorator & DISPLAY=:1 LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace gconf &
```

the #-line is build to use your new mesa libs, beeing able to update via QuinnStorm-repository. Does not work, get the missing texture extension message.

Second line uses the battlehorse mesa lib i had to download and install to make my xgl/compiz system work again.

Any idea how i be able to use your mesa lib (/usr/lib) ?

---

### Post by DeeZiD on 2006-03-25
If you use the quinnstorm repositore you don't need to add a path the any mesalibs.

The quinnstorm debs will overwrite your old mesa which works very well :)

regards Dennis

---

### Post by trorion on 2006-03-25
[QUOTE=trorion]I'm a bit confused.

I downloaded the packages starting with glitz which gave me 4 .deb packages when I unpacked it.  Which one should I use?  If I try the libglitz1-dev_0.5.5-0ubuntu1_i386.deb package it gives me```
trorion@Dapper:~/Desktop/XGL$ sudo dpkg -i libglitz1-dev_0.5.5-0ubuntu1_i386.deb(Reading database ... 68162 files and directories currently installed.)
Preparing to replace libglitz1-dev 0.5.5-0ubuntu1 (using libglitz1-dev_0.5.5-0ubuntu1_i386.deb) ...
Unpacking replacement libglitz1-dev ...
dpkg: dependency problems prevent configuration of libglitz1-dev:
 libglitz1-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
dpkg: error processing libglitz1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglitz1-dev

```

I dpkg mesa and get the same error.

Is there a specific order I need to extract them?[/QUOTE]

If you are having this problem try installing everything from the original instructions here ([http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)) and then installing the new packages.  Seems to have worked for me.

---

### Post by trorion on 2006-03-25
I've got the system up and running.  Everything seems to work fine except configurations.

gconf-edit will freeze any time I modify anything.  Nothing major it's just irritating to shut down and restart it every time.

There is no way to shut off the wobbly effect (not a fan).  I removed it from /usr/bin/thefuture2, turned it off in gconf-edit but my windows still wobble.  Any ideas?

My "thefuture2" file:
```
#!/bin/bash
LIBMESA=/opt/mesa/lib
LD_LIBRARY_PATH=$LIBMESA gnome-window-decorator & LD_LIBRARY_PATH=$LIBMESA  compiz --replace gconf decoration fade minimize cube rotate zoom scale move resize place switcher opaquefocus &
```

---

### Post by foundation on 2006-03-25
i receive this when starting 'thefuture2' in terminal.
> gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension
i installed all the packages from the first post, or did i ? or is the problem else where ?

- this is probably painfully obvious, but i'm fairly new. :x

---

### Post by firetux on 2006-03-25
[QUOTE=foundation]i receive this when starting 'thefuture2' in terminal.

i installed all the packages from the first post, or did i ? or is the problem else where ?

- this is probably painfully obvious, but i'm fairly new. :x[/QUOTE]

I'm having exactly the same problem.

---

### Post by Belfagor on 2006-03-25
[QUOTE=Belfagor]hi! amd64 debs have killed my glx extensions.. which package includes these glx extensions?[/QUOTE]

:( no idea?

---

### Post by flargen on 2006-03-25
[QUOTE=DeeZiD]If you use the quinnstorm repositore you don't need to add a path the any mesalibs.

The quinnstorm debs will overwrite your old mesa which works very well :)

regards Dennis[/QUOTE]
But using the quinnstorm mesa causes the missing extension error. Which mesa are you people using that resides in /opt/mesa/lib ?

---

### Post by DeeZiD on 2006-03-25
Updated the howto :)

---

### Post by ShawnH on 2006-03-25
Thanks for the howto DeeZid.  it worked great.  I only have one issue.  I can't get the cube and rotate to work.  anyone have any ideas?  I'm running the 64bit version.

---

### Post by DeeZiD on 2006-03-25
Strange. I never had any problems with rotate. :-k

---

### Post by nlopes on 2006-03-25
hello, 

I followed the howto in the first post but it appears that gnome-window-decorator is not working very well for me. It doesn't load, I can't do much with anything. 

Unlike some posts I've seen I get no error or output from the script. As anyone had this problem? This doens't happen in the packages from the dapper repository. Everything is ok there..

thanks

---

### Post by DeeZiD on 2006-03-25
what happens when you type compiz --replace gconf in a terminal?

---

### Post by nlopes on 2006-03-25
```

nl@phoenix: ~$> compiz --replace gconf
nl@phoenix: ~$> 

```

I get no output. All the windows become borderless.

---

### Post by DeeZiD on 2006-03-25
try to kill compiz
```
killall compiz.real gnome-window-decorator -9
```

then open metacity 
```
metacity &
```

open gconf-editor then
```
G_SLICE=always-malloc gconf-editor
```
go to /apps/compiz/general/allscreens/options/ and remove the active plugins line by  clicking with right mouse on the item and selecting "remove key" or something like that (sry, german version of gconf-editor ;) )

then restart compiz```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
```

---

### Post by Shikai on 2006-03-25
Do you get an error if you just run gnome-window-decorator in a terminal?

---

### Post by nlopes on 2006-03-25
cool, removing the plugins worked... Thanks a lot.

by the way does anyone use suspend (apm or acpi) with XGL? With compiz from the dapper repos the screen just went black on resume (all is ok except the black screen). Using nvidia graphics.

---

### Post by DeeZiD on 2006-03-25
Cool, I'll add this to my howto

New section: Troubleshooting :D 

And my new AMD64 ubuntu dapper packages are working, finally :KS :KS :KS

---

### Post by nlopes on 2006-03-25
YEY.. Seems ok with these versions :D :D 

excellent work by the way, great effects.. 

Thanks for the help

---

### Post by DeeZiD on 2006-03-25
Ok.
added a "If it doesn't work..." section ;)

---

### Post by idn on 2006-03-25
[QUOTE=DeeZiD]try to kill compiz
```
killall compiz.real gnome-window-decorator -9
```

then open metacity 
```
metacity &
```

open gconf-editor then
```
G_SLICE=always-malloc gconf-editor
```
go to /apps/compiz/general/allscreens/options/ and remove the active plugins line by  clicking with right mouse on the item and selecting "remove key" or something like that (sry, german version of gconf-editor ;) )

then restart compiz```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
```[/QUOTE]


Thanks this worked for me!

---

### Post by idn on 2006-03-25
Does anyone know how to get the f12 effect and switcher working again - both dont work now

---

### Post by nrwilk on 2006-03-26
DeeZiD, thank you so much for posting the fix for the decoration-less windows in KDE!  Helped me fix the issue, and several others too.

Awesome! :D

---

### Post by dc2447 on 2006-03-26
[QUOTE=nrwilk]DeeZiD, thank you so much for posting the fix for the decoration-less windows in KDE!  Helped me fix the issue, and several others too.

Awesome! :D[/QUOTE] I am having the same no window decoration issue on Kde but I gon't have a /apps/compiz/ section in gconf

anyone have any ideas?

---

### Post by DeeZiD on 2006-03-26
Try to start compiz with the following command first, there's maybe another problem ;)

```
compiz --replace gconf
```

---

### Post by dc2447 on 2006-03-26
> **DeeZiD]Try to start compiz with the following command first, there's maybe another problem  said:**
> 

I lose the window decorations and compiz complains about[quote] davidcam@han:~$ sudo compiz --replace gconf
davidcam@han:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0


---

### Post by DeeZiD on 2006-03-26
Try to reinstall xserve-xgl and the other packages ;)

```
sudo apt-get install xserver-xgl compiz compiz-gnome libgl1-mesa libgl1-mesa-dri libglitz1 --reinstall
```

and then restart

---

### Post by dc2447 on 2006-03-26
[QUOTE=DeeZiD]Try to reinstall xserve-xgl and the other packages ;)

```
sudo apt-get install xserver-xgl compiz compiz-gnome libgl1-mesa libgl1-mesa-dri libglitz1 --reinstall
```

and then restart[/QUOTE] didn't help :(

---

### Post by geearf on 2006-03-26
Which graphical drivers are you using ?

---

### Post by dc2447 on 2006-03-26
[QUOTE=geearf]Which graphical drivers are you using ?[/QUOTE]

Nvidia

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection


Thanks

---

### Post by geearf on 2006-03-26
Well I'm not exactly sure what is your problem but I know I had this too.
For me this is what worked : 
I copied the ligGL.so file from the mesa deb to /usr/lib/nvidia/libGL.so.1.2.xlibmesa (I had to create the dir as well), after that I never got this error message anymore.

---

### Post by fabs0028 on 2006-03-26
The bug with gconf-editor and gslice has gone with the latest update 5 minutes ago :)

---

### Post by cywhale on 2006-03-26
[QUOTE=DeeZiD]If you use the quinnstorm repositore you don't need to add a path the any mesalibs.

The quinnstorm debs will overwrite your old mesa which works very well :)

regards Dennis[/QUOTE]

Hmmm...didn't work, i have to add /opt/mesa as library_path. Any idea? Maybe a libGl.so issue, too ?

---

### Post by dc2447 on 2006-03-26
[QUOTE=geearf]Well I'm not exactly sure what is your problem but I know I had this too.
For me this is what worked : 
I copied the ligGL.so file from the mesa deb to /usr/lib/nvidia/libGL.so.1.2.xlibmesa (I had to create the dir as well), after that I never got this error message anymore.[/QUOTE]

Thanks - I am using apt to install the packages - is there an easy way to download and unpack the debs?

---

### Post by dc2447 on 2006-03-26
[QUOTE=geearf]Well I'm not exactly sure what is your problem but I know I had this too.
For me this is what worked : 
I copied the ligGL.so file from the mesa deb to /usr/lib/nvidia/libGL.so.1.2.xlibmesa (I had to create the dir as well), after that I never got this error message anymore.[/QUOTE] actually I have /usr/lib/nvidia/libGL.so.1.2.xlibmesa  already

---

### Post by jaymode on 2006-03-26
Are there special instructions for those who used the original checkinstall packages to update to the ones with a repo? Because when I try to upgrade it gives me an error. I tried to do sudo apt-get --purge xserver-xgl but that gave me an error to.

---

### Post by ShawnH on 2006-03-26
I'm getting the same issues as ds2447.  When i enter compiz --replace gconf my window decoration disappears (typing 'metacity &' gets it back) and i get the following message.  

shawn@ubuntu:~$ compiz --replace gconf
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0

Any ideas?  I'm using a Nvidia Geforce 6600GT.  I had everything working yesterday but tried something dumb to get the cube working and had to do a fresh install yesterday.  Please help.  :)

---

### Post by geearf on 2006-03-26
[quote=dc2447]actually I have /usr/lib/nvidia/libGL.so.1.2.xlibmesa  already[/quote]
then I don't know, sorry :(

---

### Post by flargen on 2006-03-26
Jaymode, it would probably be best to remove all old xgl related packages and install the new ones from scratch.

---

### Post by ShawnH on 2006-03-26
Ok, I got some funtionality.  I have the cube, wobbly on the menus, etc.   However I'm missing the window decoration.  I've tried the fix on the main page of the howto but it doesn't work.  could it be the coding in thefuture64 (I have an AMD64).  When I had it working yesterday I didn't have the same coding in the script.  any ideas?

---

### Post by jaymode on 2006-03-26
[QUOTE=flargen]Jaymode, it would probably be best to remove all old xgl related packages and install the new ones from scratch.[/QUOTE]

Using synaptic?

---

### Post by flargen on 2006-03-26
[QUOTE=jaymode]Using synaptic?[/QUOTE]
Maybe, but it might be best to look through the howto you used before to see which packages you installed, then close X and run ```
sudo apt-get remove *packages*
``` from command line. Saying that, synaptic should work ok.

---

### Post by JediPottsy on 2006-03-27
Followed the guide and everything worked fine - rebooted :D

got to logon manager - after some wierd black and white square screen
loged in, but now i just have brown screen with mouse

help :S

---

### Post by jaymode on 2006-03-27
JediPottsy

can you give us more info about your system? I had a somewhat similar problem when I was running 16 bit color depth instead of 24 bit, check that in your xorg.conf.

---

### Post by JediPottsy on 2006-03-27
if i press ctrl+alt+backspace and go to terminal, then try to run "compiz --replace  gconf decor..." it says "Compiz.real:Couldn't Open Display", and changing the display back to 0,93,94 in the config doesnt make a difference. I had this same probelm with the 8.23.7 drivers, which is a glitch in the ATI driver, when Xgl is set to run on display 93. So i went back to 8.22.5 and im still getting this problem. I ran thru dpkg-reconfigure and my xorg is setup fine. 24bit colour, fglrx driver. Running fglrxinfo shows at ATI device - and 3D Acceleration is enabled.

---

### Post by peRosine on 2006-03-27
Hi,

I'm with my hands in my hairs...
Keep getting the error:
```

compiz.real: GLX_EXT_texture_from_pixmap is missing

compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Tried everything in the previous threads. Uninstalling.. copying the library etc.

I'm using the latest Nvidia driver with an 6800 GT card. Please help me out here..

---

### Post by Terracotta on 2006-03-27
wow, finally got it working. Had to go to i386 though, maybe next time I'll try x86_64 again. The only thing is: I have to start it manually eacht time and well :s videos are showing double, but I've read that I'm not the only one who has that problem?

---

### Post by stmkjp on 2006-03-27
Hi, DeeZid. Thanks for all your efforts. but I got some problem during update to latest xgl/compiz:

* I have ATI9700 mobility and dapper 6.06 installed.

1) I have custom fonts ( windows .ttc and .ttf fonts for korean) installed with ~/.fonts.conf in my home directory. but updated compiz won't run with my fonts configuration. (previous version works ok, though). when i restart my computer, gnome-window-decorator runs ok but compiz not shown in processes. moreover, all gui windows just blinking and won't shown up. i can barely run a terminal (which i cannot move or resize though).

but after i remove ~/.fonts.conf  and restarted, compiz runs OK. it's weird.
can you help me to getting my original font configuration with compiz?

2) after updating to newest compiz, opaquefocus won't run coz there's no libopaquefocus.so in /usr/lib/compiz . anyway, i resolved this problem with downloading precompiled libopaquefocus.so file you posted.
but I can't control the opacity with <Shift><Control> + button4/5 anymore. it only works with <control><alt>, which is conflicted with zooming plug-in.

according to your post, there's no more opacity plugin in compiz. but i still can see opacity plugin in gconf-editor and /usr/lib/compiz also. should i remove the opacity plugin?

---

### Post by Shikai on 2006-03-27
[QUOTE=stmkjp]
2) after updating to newest compiz, opaquefocus won't run coz there's no libopaquefocus.so in /usr/lib/compiz . anyway, i resolved this problem with downloading precompiled libopaquefocus.so file you posted.
but I can't control the opacity with <Shift><Control> + button4/5 anymore. it only works with <control><alt>, which is conflicted with zooming plug-in.

according to your post, there's no more opacity plugin in compiz. but i still can see opacity plugin in gconf-editor and /usr/lib/compiz also. should i remove the opacity plugin?[/QUOTE]
Opaquefocus has been removed, and replaced by trailfocus. Trailfocus will mimic opaquefocus if you set it's length to 2 in gconf.

The opacity plugin has been changed to a default action (like drop shadows) in the newer compiz, so the plugin is unnecessary. If you're loading it with compiz, you can remove it, and remove libopacity.so from /usr/lib/compiz. The default hotkey for opacity should be <alt>+button4,5 (scroll wheel), but you can change it in gconf-editor. apps --> compiz --> general --> screen0 --> options

---

### Post by PowerLlama on 2006-03-27
After much screwing around (hours and hours) I finally got this to work on my system. I have a few weird problems though.

I can no longer set my mouse sensitivity. Now it's just super high. Very annoying.


Alt-tab no longer works.

I'm not sure what I did to break alt-tab, but every time I tried a different XGL how-to, my mouse speed shot through the roof, and I couldn't change it back. Any help?

Nevermind on the alt-tab, two restarts later and it works.

---

### Post by stmkjp on 2006-03-27
[QUOTE=Shikai]Opaquefocus has been removed, and replaced by trailfocus. Trailfocus will mimic opaquefocus if you set it's length to 2 in gconf.

The opacity plugin has been changed to a default action (like drop shadows) in the newer compiz, so the plugin is unnecessary. If you're loading it with compiz, you can remove it, and remove libopacity.so from /usr/lib/compiz. The default hotkey for opacity should be <alt>+button4,5 (scroll wheel), but you can change it in gconf-editor. apps --> compiz --> general --> screen0 --> options[/QUOTE]

Great. Thanks for your tip, Shikai.:D 
I'll try trailfocus this evening...I didn't know that coz DeeZid didn't mentioned  that in the first posting.

OK. now I have one problem left to resolve. DeeZid or someone else can help me with custom font problem? (multi-byte font)

and one more question, when I "sudo apt-get update", metascape.org site which Deezid mentioned shown, but "Ignored" tag in front of the site name. is it normal? what does "Ignored" mean?

---

### Post by JediPottsy on 2006-03-28
[QUOTE=stmkjp]Hi, DeeZid. Thanks for all your efforts. but I got some problem during update to latest xgl/compiz:

* I have ATI9700 mobility and dapper 6.06 installed.

[/QUOTE]

How?
I have mobility 9700 and ill be damned if i can get it working #-o

---

### Post by stmkjp on 2006-03-28
[QUOTE=JediPottsy]How?
I have mobility 9700 and ill be damned if i can get it working #-o[/QUOTE]

perhaps you tried xgl with default ATI graphic driver. it won't work with default installed ati driver.
you should install binary ATI driver (gfrlx) and it'll work.

you can find the howto at : [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by peRosine on 2006-03-28
If have tried everything and am stuck.. No matter what I do I just keep getting this error:
```

compiz.real: GLX_EXT_texture_from_pixmap is missing

compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Is there a way I can just uninstall it all (when trying to uninstall libgl1-mesa, it takes a lot more programs with it) and start over again? I wont stop trying untill it works! :)

---

### Post by foureight84 on 2006-03-28
i run apt-get update with and i get this error message:

```

Failed to fetch http://metascape.afraid.org:13666/apt/dists/dapper/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

what's up with this? anyone getting this error?

---

### Post by cywhale on 2006-03-28
First of all: 
thank you QuinnStorm and all other developers doing this amazing work!

[QUOTE=JediPottsy]How?
I have mobility 9700 and ill be damned if i can get it working #-o[/QUOTE]

Got it working on Radeon Mobile 9700 (FSC Amilo 1425)
- using binary ubuntu fgrlx driver via apt-get install
- or using ati driver from ati.com -> linux laptop driver

BUT: Only works for me if I'm
- not using gdm-conf...changes
- using custom xsession/startscript similar to thefuture 
- using the mesa-lib from [Battlehorse]("http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl")
and the compiz starter script uses a library path like following:
```
LD_LIBRARY_PATH=/opt/mesa/lib gnome-window-decorator & DISPLAY=:1 LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace gconf &
``` 

Tried to **remove mesa and install mesa from QuinnStorm's repo**, never worked for me. Always got the "GLX_EXT_pixmap_to_texture"-error. 
- Changed LD_LIBRARY_PATH to /usr/lib
- changed LD_LIBRARY_PATH to nothing (removed) like mentioned in another thread

Never worked.

So I had to reinstall the battlehorse-mesa-deb's.

Maybe you should give the battlehorse debs a try if nothing else works, but try to use mesa from QuinnStorm repo before...

Anybody another idea how to use the QuinnStorm debs instead of battlehorse-mesa ?

---

### Post by escape on 2006-03-28
[QUOTE=foureight84]i run apt-get update with and i get this error message:

```

Failed to fetch http://metascape.afraid.org:13666/apt/dists/dapper/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

what's up with this? anyone getting this error?[/QUOTE]

I get this too. Fix your repositories, OP!

---

### Post by Mr Frosti on 2006-03-28
For those experiencing lockups on ATI x300 and x700 cards, please take a look at the following post:

[http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+x300]("http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+x300")

---

### Post by escape on 2006-03-28
This whole thread seriously is worthless without the deb/deb-src... DeeZiD, please fix this..

---

### Post by Bou on 2006-03-29
[QUOTE=DeeZiD]**[SIZE="4"]5. If it doesn't work...[/SIZE]**

Many people (me included) have the problem they don't have any window-decoration after that and they get no error message.

If that happens to you, try that:

kill compiz
```
killall compiz.real gnome-window-decorator -9
```

then open metacity or kwin
```
metacity &
kwin &
```

open gconf-editor then
```
G_SLICE=always-malloc gconf-editor
```
go to /apps/compiz/general/allscreens/options/ and remove the active plugins line by  clicking with right mouse on the item and selecting "remove key" or something like that (sry, german version of gconf-editor ;) )

then restart compiz```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
```[/QUOTE]

I followed your instructions... however, I still get no decoration.

I'm not even sure XGL is properly working, what can I do?

---

### Post by sYs^ on 2006-03-29
Since I updated to this version when I start thefuture my X simply craches to command line :\

Any ideas?

---

### Post by kabtoffe on 2006-03-29
I just thought I'd mention that I actually do have XGL + Compiz working with xorg radeon driver on my laptop. So this actually works with the open-source radeon as well. I think the laptop has a Radeon M7 (can't be bothered to check it now). It's a bit slow though, compared to my desktop computer with AMD64x2 3800+ and Nvidia 6600. I'm using the latest compiz and xgl from Quinn's repositories. So go ahead and try it with the older radeons as well.

---

### Post by sYs^ on 2006-03-29
Ok, It started to work, I dont know why but it's working now :p

But some of the plugins are not working, for example: zoom, resize, switcher, place...

But the others are working, what could be the problem?

Thanks

**_Edit:_** Ok, sorry, I fixed this too, lol, i'm the masterer, but one more question, is it possible to remove shadows from gdesklets?

---

### Post by stmkjp on 2006-03-29
[QUOTE=Bou]I followed your instructions... however, I still get no decoration.

I'm not even sure XGL is properly working, what can I do?[/QUOTE]

@Bou, if you use multibyte character set or use custom font setting - (~/.fonts.conf in your home directory) then try to remove your .font.conf file or not use multibyte font in your font setting, and restart. it worked for me. can't use custom font set is also another problem for me though...:(

---

### Post by escape on 2006-03-29
Thanks for package maintenance, DeeZiD!

---

### Post by geearf on 2006-03-30
still having the same problem :

setxkbmap fr (or anything else ..)
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault


Cannot get my keyboard :(

---

### Post by jkshin on 2006-03-30
[QUOTE=stmkjp]@Bou, if you use multibyte character set or use custom font setting - (~/.fonts.conf in your home directory) then try to remove your .font.conf file or not use multibyte font in your font setting, and restart. it worked for me. can't use custom font set is also another problem for me though...:([/QUOTE]

That bug killed me.
How sad this situation is :???:

---

### Post by geearf on 2006-03-30
Also an other thing, with X glxgears gives me about 3500 fps, but with Xgl I have about 5000 fps, so strange isn't it ?

---

### Post by krusbjorn on 2006-03-30
[QUOTE=geearf]Also an other thing, with X glxgears gives me about 3500 fps, but with Xgl I have about 5000 fps, so strange isn't it ?[/QUOTE]

Yeah, same here :D

---

### Post by brainkilla on 2006-03-31
I have a problem with Xgl, and I find it rather amusing that I managed to get it working on Breezy with Suse .rpms and cannot continue in the same fashion on Dapper either with official or the semi-official packages. The latter are better, but prevent me from enjoying the Compiz goodies persistently displaying error messages like "Cannot load glx module" or, after having done some symlinking, something about SecurityPolicy or samo rgb path... Official ubuntu .3.deb failed throwing at me messages about non-existant fonts/font paths which cannot be found/loaded... Any ideas? Thanx...

---

### Post by Asraniel on 2006-03-31
any chance that this cvs version will go into dapper?

---

### Post by Subbu.exe on 2006-04-01
I Installed XGL According to the Guide, 
**but the**
> CTRL + ALT + Arrow key (switch sides of cube)
CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.
F12 - uses the Expose like trick
Alt- Tab - switcher Vista-style

Doesnt Work, but i can Set the Transparency using Alt+Mousewheel, Rotate Cube using Mouse (using Ctrl+Tab).

The Effects are Working Great, But How to Get those Keys to Work?

---

### Post by Subbu.exe on 2006-04-01
[QUOTE=Subbu.exe]I Installed XGL According to the Guide, 
**but the**


Doesnt Work, but i can Set the Transparency using Alt+Mousewheel, Rotate Cube using Mouse (using Ctrl+Tab).

The Effects are Working Great, But How to Get those Keys to Work?[/QUOTE]

Neva Mind. It Works, I Had to Restart Again ](*,)

---

### Post by saracen on 2006-04-01
any chance to get a mirror?  That repo is going at 6kb/s...

---

### Post by reggaemanu on 2006-04-02
New packages for today' Xgl/Mesa CVS version soon available, i've just sent them to QuinnStorm. (Also contains new versions off composite-proto, fixes-proto, libxcomposite and libxfixes)
Works fine here.

---

### Post by GoA on 2006-04-02
[QUOTE=reggaemanu]New packages for today' Xgl/Mesa CVS version soon available, i've just sent them to QuinnStorm. (Also contains new versions off composite-proto, fixes-proto, libxcomposite and libxfixes)
Works fine here.[/QUOTE]

Great, thanks. :)

---

### Post by peRosine on 2006-04-02
[QUOTE=saracen]any chance to get a mirror?  That repo is going at 6kb/s...[/QUOTE]

That's fast.. Downloaded it myself at 800 bytes/sec.. :-D
It's worth the wait.

---

### Post by sYs^ on 2006-04-02
Hi, I've got some problems with the repos:

```
Ign http://metascape.afraid.org dapper/main Packages
Hit http://hu.archive.ubuntu.com dapper-backports/universe Sources
Hit http://hu.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://metascape.afraid.org dapper/main Packages
Fetched 5B in 1s (5B/s)
Failed to fetch http://metascape.afraid.org:13666/apt/dists/dapper/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

sources.list:

```
deb http://metascape.afraid.org:13666/apt dapper main
deb-src http://metascape.afraid.org:13666/apt dapper main
```

Any ideas? THanks

---

### Post by Asraniel on 2006-04-02
is this for dapper in general or just this specific mirror? because this mirror is too slow to use....

---

### Post by Owdy on 2006-04-02
Is that deb server working? Got this:

> Tiedoston [http://metascape.afraid.org:13666/apt/dists/dapper/Release]("http://metascape.afraid.org:13666/apt/dists/dapper/Release") nouto ei onnistunut  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)


---

### Post by sYs^ on 2006-04-02
[QUOTE=Owdy]Is that deb server working? Got this:[/QUOTE]

same problem, but for somebody else it's working, so I can't understand what's going on here :p

---

### Post by drummer on 2006-04-02
Not working for me either at the moment, was working a day ago though... don't know what's going on :(
Looking at the error from apt, looks like something is incorrectly named on the server, or a file is missing that should normally be there, because the server is accessable through FF, just isn't updating correctly with apt.

---

### Post by malte on 2006-04-02
Very good work! Performance is better and wxgtk apps have borders! =D>

---

### Post by | MM | on 2006-04-03
Its down for me as well, a download started then failed during the download.  Havnt been able to get any contact with the server since.

---

### Post by Subbu.exe on 2006-04-03
I Cannot Access the Repo. Does Anyone Know When its Gonna Come Back Up?

---

### Post by hornett on 2006-04-03
Shame about the server (eventually got the files at 800b/s!) because the debs work really well! 

Don't suppose anybody's got a server with spare bandwidth for this worthy cause?!

---

### Post by Owdy on 2006-04-03
No offence or anything but that server is totally useless...

---

### Post by QuinnStorm on 2006-04-03
[QUOTE=Owdy]No offence or anything but that server is totally useless...[/QUOTE]
This is why I now have a mirror.

```

deb http://www.beerorkid.com/compiz dapper main

```

use that instead.

---

### Post by DeeZiD on 2006-04-03
updated the howto :)

---

### Post by klahjn on 2006-04-03
Wow! i thought Xgl was going to be popular, but already 211 posts!  that's incredible.  I've noticed it has gotten faster and more reliable, i will probably wait  until the new driver gets released, but happy to see it is getting faster and smoother.

---

### Post by Owdy on 2006-04-03
[quote=QuinnStorm]This is why I now have a mirror.

```

deb http://www.beerorkid.com/compiz dapper main

``` 
use that instead.[/quote] Wow, much better. Thanks!

---

### Post by | MM | on 2006-04-03
I luvs you guys ...

---

### Post by hornett on 2006-04-03
QuinnStorm, that mirror works nicely. Thanks for posting your builds!

---

### Post by thumperward on 2006-04-03
OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. OH MY GOD. 

The customary two hours of messing with xorg.conf and issuing magic incantations, but OH, MY GOD. XGL wins everything. This is just deliriously cool.

 - Chris

---

### Post by drummer on 2006-04-03
Chris, I know just how you feel... as do all of us using XGL/Compiz probably.

My first reaction was along the lines of yours :p - "OH... MY... GOD... SO... FRICKIN... COOOOOL... *drool*"..... followed by giggles of delight whenever I used one of the effects. :D

---

### Post by Tymon on 2006-04-03
Sorry if this has been posted before, but X keeps crashing when gdm is launching. I have an ATI card. It runs fine windowed with the Xgl blabla command from a terminal.

---

### Post by golfbuf on 2006-04-03
This is nice.

It would be nice to see the source packages for mesa, xgl and any others.  Can you post them in the repos, or if they're too big, could you put together a list of steps to build from cvs, so we can try ourselves?

TIA,

---

### Post by reggaemanu on 2006-04-03
[quote=Tymon]Sorry if this has been posted before, but X keeps crashing when gdm is launching. I have an ATI card. It runs fine windowed with the Xgl blabla command from a terminal.[/quote] 

I've updated all packages with yesterday's modifications on cvs (concerning ATI) so i hope now it works fine with ATI too.

[quote=golfbuf]It would be nice to see the source packages for mesa, xgl and any others.  Can you post them in the repos, or if they're too big, could you put together a list of steps to build from cvs, so we can try ourselves?[/quote]

They are on the repos...

---

### Post by klahjn on 2006-04-03
My only real suggestion is that they need to fix the games that won't run on top of Xgl.  I know it is some direct rendering issue, but a workaround for the time being might really be nice.  I also don't think a lot of people would mind if the framerate dropped by maybe a few fps until they got the problem entirely fixed.    Just a thought.

---

### Post by Subbu.exe on 2006-04-04
Everything Works Smoothly for Me, But I Have Some CPU Usage Probs.

First, When I Try to Resize any Window the CPU Usage Jumps Up.
Second, Scrolling a Webpage does the Same too.
Third, Sometimes when Opening new Window (from Firefox for Instance), It Seems a Little Jerky.

I Use the Latest XGL/Compiz from the Repos,
My Kernel 2.6.15-19-k7
And Sys. Specs are AMD64 3200, GeForce 6800GT, 1G Ram.

---

### Post by mgsfan on 2006-04-04
well I'm wondering since I used a script to install and run xgl..I think it was moma's if I used the upgraded debs from the repos would I have to reconfigure it again or would I just need to reboot and be done..

---

### Post by | MM | on 2006-04-04
Yes i just had a look, and scolling does indeed ramp the cpu usage up to 100%.

Odd.

---

### Post by hornett on 2006-04-04
Uh-oh seems like there are some problems with the packages...

```
retro@d600:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
compiz-gnome is already the newest version.
The following NEW packages will be installed
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1569kB of archives.
After unpacking 4231kB of additional disk space will be used.
(Reading database ... 81663 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This was all working for me before, I only have the official repos and the beerorkid ones enabled.

Anybody else having this prob?

---

### Post by sYs^ on 2006-04-04
yes, (almost) same here, I've tried to upgrade just a minute ago :\

```
dani@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  xserver-xorg-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3512kB of archives.
After unpacking 131kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 107477 files and directories currently installed.)
Preparing to replace xserver-xorg-core 1:1.0.2-0ubuntu3 (using .../xserver-xorg-core_1%3a1.0.2-0ubuntu4_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by klahjn on 2006-04-04
when using apt-get everything seemed to work fine for me.  you may want to try again after doing an apt-get update.  Hopefully that helps.

---

### Post by RacerII on 2006-04-04
Xgl 7.0.0-0ubuntu7 doesnt work for me.
X fails to start , and it gives me this error: error opening security policy file /etc/xserver/SecurityPolicy .
Same with 1 version newer btw.

This is with an ati radeon 9800 pro card.

---

### Post by sYs^ on 2006-04-04
I tried that of course already. :p

---

### Post by Laterix on 2006-04-04
Same problem here new XGL won't start :( Using ATI 9600 Mobility

---

### Post by sYs^ on 2006-04-04
Some kind of solution:

[http://ubuntuforums.org/showthread.php?t=155097](http://ubuntuforums.org/showthread.php?t=155097)

---

### Post by Tymon on 2006-04-04
X keeps crashing on me... newest version of everything. x300 mobile card. The weird thing is I can start a new Xgl X window from a normal booted non-xgl X server. Everything works in the window (all fx). But with the modded /etc/gdm/gdm.conf and custom files X keeps crashing back to the cli. It tried 5 times or so (I can see the black white screen with mouse pointer).

---

### Post by /dev/clast on 2006-04-04
[QUOTE=Tymon]X keeps crashing on me... newest version of everything. x300 mobile card. The weird thing is I can start a new Xgl X window from a normal booted non-xgl X server. Everything works in the window (all fx). But with the modded /etc/gdm/gdm.conf and custom files X keeps crashing back to the cli. It tried 5 times or so (I can see the black white screen with mouse pointer).[/QUOTE]

same is happening to me and a lot of other users, too.

i hope this will be fixed soon, since there is no workaroud yet, AFAIK :)

---

### Post by Tymon on 2006-04-04
[QUOTE=/dev/clast]same is happening to me and a lot of other users, too.

i hope this will be fixed soon, since there is no workaroud yet, AFAIK :)[/QUOTE]

Weird, I bet there must be because it basically just works...

---

### Post by golfbuf on 2006-04-04
They are on the repos...[/QUOTE]

Which repos .. I'm looking at [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) and don't find anything for xgl, mesa, etc.

---

### Post by varunus on 2006-04-04
Guys, to fix the apt conflict, do the following:

```
sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz

```

This causes apt to divert one of the filenames to .xgl.  It will fix all the problems in a clean way.

---

### Post by erimar77 on 2006-04-05
[QUOTE=/dev/clast]same is happening to me and a lot of other users, too.

i hope this will be fixed soon, since there is no workaroud yet, AFAIK :)[/QUOTE]

you guys really need to try this.. 

[http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854)

it's already worked for a few other ati pci express video cards too, x300, x700, etc...

---

### Post by obey43 on 2006-04-05
i had to reinstall dapper, and i had the overwrite problem which people described... did that code and it worked.

but now when i try Xgl, it loops from Xgl to TTY1 untill Xgl fails...

any help?

---

### Post by 3zero2 on 2006-04-05
when i do "xmodmap /usr/share/xmodmap/xmodmap.us" the F12, Alt-Tab and probably other key combinations do not work.

if i don't issue the xmodmap command everything works fine but I have the shift+backspace bug.

Any solution?

---

### Post by pebe on 2006-04-05
@DeeZiD

I just thought I should mention some typos I noticed while reading your guide. ;) 

> Compiz for ubuntu-users
Open sessions>prereferences>sessions
add "/usr/bin/thefuture" and "xmodmap /usr/share/xmodmap/xmodmap.<language>" (for me it is xmodmap.de) to your additional programs.

sessions>prereferences>sessions should be **system**>**preferences**>sessions

Also one thing that is unclear. Should *thefuture and xmodmap* be added to the 'Session Options' or the 'Startup Programs' tab?

I haven't gotten XGL/compiz to work yet with my ati 8500, but sooner than later.. maybe with some new drivers! :p


Anyhow thanks for the great guide DeeZiD!   :-D

---

### Post by drummer on 2006-04-05
[QUOTE=3zero2]when i do "xmodmap /usr/share/xmodmap/xmodmap.us" the F12, Alt-Tab and probably other key combinations do not work.

if i don't issue the xmodmap command everything works fine but I have the shift+backspace bug.

Any solution?[/QUOTE]
Use xmodmap.us-101 instead, it should return those functions. I also edited my xmodmap.us-101 file because the Super (Windows) keys were incorrectly (?) named as 'Meta' I think and didn't work. That was the reason why the zoom plugin wasn't working for me because those keys were returning a different code than compiz expected and so didn't pick them up. Might be different for you though.

Here is a diff of the files (I made a backup of the origonal first):```
133,134c133,134
< keycode 115 = Super_L
< keycode 116 = Super_R
---
> keycode 115 = Meta_L
> keycode 116 = Meta_R
146d145
< add	mod4	= Super_L Super_R

```I changed the "Meta"s to "Super"s and added the "add mod4..." line below.

---

### Post by /dev/clast on 2006-04-05
[QUOTE=erimar77]you guys really need to try this.. 

[http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854)

it's already worked for a few other ati pci express video cards too, x300, x700, etc...[/QUOTE]

i just read the first few pages of that thread and it seems like they're discussing a totally different problems.
I (we) don't have lockups, xgl simply doesn't start anymore with the new packages.
maybe I missed something? Or does it solve both problems?

clast

---

### Post by mcduck on 2006-04-05
[QUOTE=/dev/clast]i just read the first few pages of that thread and it seems like they're discussing a totally different problems.
I (we) don't have lockups, xgl simply doesn't start anymore with the new packages.
maybe I missed something? Or does it solve both problems?
clast[/QUOTE]
I suppose you have Ati card? The latest xsrever-xgl package has some issues with Ati. To fix this, you can edit your sources.list to comment out the compiz repositories, then run 'sudo apt-get update', 'sudo apt-get remove xserver-xgl' and 'sudo apt-get install xserver-xgl' to get the original Ubuntu version of the package back. After that your problem is gone :)

---

### Post by /dev/clast on 2006-04-05
[QUOTE=mcduck]I suppose you have Ati card? The latest xsrever-xgl package has some issues with Ati. To fix this, you can edit your sources.list to comment out the compiz repositories, then run 'sudo apt-get update', 'sudo apt-get remove xserver-xgl' and 'sudo apt-get install xserver-xgl' to get the original Ubuntu version of the package back. After that your problem is gone :)[/QUOTE]

okay, that's what i would call an ugly workaround ;) Thanks for the tip though!
yeah, I've heard there've been a lot of changes concerning Ati Cards. so, i think it's gonna be fixed really soon. i'm still hoping for some breakthrough changes in the new ATI driver, which should be released these next couple of weeks. :)

well, we'll see. i might just go back and use the original package as you said.

regards,
clast

---

### Post by 3zero2 on 2006-04-05
[QUOTE=drummer]Use xmodmap.us-101 instead, it should return those functions. I also edited my xmodmap.us-101 file because the Super (Windows) keys were incorrectly (?) named as 'Meta' I think and didn't work. That was the reason why the zoom plugin wasn't working for me because those keys were returning a different code than compiz expected and so didn't pick them up. Might be different for you though.

Here is a diff of the files (I made a backup of the origonal first):```
133,134c133,134
< keycode 115 = Super_L
< keycode 116 = Super_R
---
> keycode 115 = Meta_L
> keycode 116 = Meta_R
146d145
< add	mod4	= Super_L Super_R

```I changed the "Meta"s to "Super"s and added the "add mod4..." line below.[/QUOTE]

you rule!! that worked fine. thanks.

---

### Post by Owdy on 2006-04-05
I dont even have those lines. I use xmodmap.fi.

It looks like this:> 
keycode 106 = Insert
! right windows-logo key
! in "windows" keyboards the postion of the key is annoying, is where AltGr
! usually resides, so go definie it as AltGr
keycode 116 = Mode_switch
! right windows-menu key
keycode 117 = Multi_key
!
add Mod1 = Alt_L
add Mod2 = Mode_switch 
But most of functions works, F12 etc. Windows key does nothing, but i use differend keys for those features. 

Zooming with mouse wheel would be nice :)

---

### Post by geearf on 2006-04-05
but from which package do you get those xmodmaf files, I have no directory named like this under /usr/share

---

### Post by Xylene on 2006-04-08
Deleted.

---

### Post by Subbu.exe on 2006-04-09
Am I the only Person getting this:
> Errhttp://www.beerorkid.com dapper Release.gpg
  Temporary failure resolving ‘[www.beerorkid.com’](www.beerorkid.com’)
Fetched 3B in 34s (0B/s)
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg)  Temporary failure resolving ‘[www.beerorkid.com’](www.beerorkid.com’)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


I Cant even Access the website [www.beerorkid.com](www.beerorkid.com)

---

### Post by sYs^ on 2006-04-09
[QUOTE=drummer]Use xmodmap.us-101 instead, it should return those functions. I also edited my xmodmap.us-101 file because the Super (Windows) keys were incorrectly (?) named as 'Meta' I think and didn't work. That was the reason why the zoom plugin wasn't working for me because those keys were returning a different code than compiz expected and so didn't pick them up. Might be different for you though.

Here is a diff of the files (I made a backup of the origonal first):```
133,134c133,134
< keycode 115 = Super_L
< keycode 116 = Super_R
---
> keycode 115 = Meta_L
> keycode 116 = Meta_R
146d145
< add	mod4	= Super_L Super_R

```I changed the "Meta"s to "Super"s and added the "add mod4..." line below.[/QUOTE]

Thanks, I had the same problem with the hungarian xmodmap file (xmodmap.hu-101-lat1) then I added these keycode settings and woala (or what, lol) it's working now, so thanks :p

**Subbu.exe:** Yup, same here.

---

### Post by Subbu.exe on 2006-04-09
Ok, I Managed to Update the Compiz Packages to 0.0.9.

Here are some Annoyances after doing that..
(Forgive a Noob)

1.I Dont want the Cube to Automatically Rotate everytime i move my Mouse to the Corner [-(

2.After Pressing Alt+Tab the Alt-Tab Thingie Doesnt Dissapear, It Sticks there Even After i Release the Buttons, Errrr... :confused:

3.Pressing Shift+Backspace Restarts X,  Its Quite Annoying if you're Typing Real Fast... :(

and Please tell me What Plugins and what shud Loaded and its Configuration...

---

### Post by keyhan on 2006-04-09
I have a question for you all. I have a strange problem with Java 5 applications while using XGL. I can not see anything on the java windows including java conrol-panel. Java 1.4 works better but there are some problems even there.

Has this package solved those problems?

regards Keyhan

---

### Post by sYs^ on 2006-04-09
[QUOTE=Subbu.exe]Ok, I Managed to Update the Compiz Packages to 0.0.9.

Here are some Annoyances after doing that..
(Forgive a Noob)

1.I Dont want the Cube to Automatically Rotate everytime i move my Mouse to the Corner [-(

2.After Pressing Alt+Tab the Alt-Tab Thingie Doesnt Dissapear, It Sticks there Even After i Release the Buttons, Errrr... :confused:

3.Pressing Shift+Backspace Restarts X,  Its Quite Annoying if you're Typing Real Fast... :(

and Please tell me What Plugins and what shud Loaded and its Configuration...[/QUOTE]

2.: remove SPLASH from your fade plugin's window types list.

---

### Post by krusbjorn on 2006-04-09
[QUOTE=Subbu.exe]1.I Dont want the Cube to Automatically Rotate everytime i move my Mouse to the Corner [-(

2.After Pressing Alt+Tab the Alt-Tab Thingie Doesnt Dissapear, It Sticks there Even After i Release the Buttons, Errrr... :confused:[/QUOTE]

1. Open gconf-editor. Apps->Compiz->Plugins->Rotate->Screen0->Options. Uncheck edgeflip. If you dont want the cube to tip over when moving a window, also uncheck edgeflip_move.

2. Open gconf-editor. Apps->Compiz->Plugins->Fade->Screen0->Options. Remove "Splash" from window_types. (I think this is the only fix atm.)

---

### Post by sYs^ on 2006-04-09
Are there any fix for the printscreen crash in the latest compiz (0.0.9) ?

---

### Post by Subbu.exe on 2006-04-09
Lovely.. Thanks Guys it Worked.. :)

The Shift+Bksp is also Solved, i used xmodmap

Does anyone know why the CPU Usage Jumps up When Scrolling a Webpage. I Doesnt Happen when compiz is not Loaded.

and Yeh PrintScreen crashes Compiz.

---

### Post by sYs^ on 2006-04-09
[QUOTE=Subbu.exe]Lovely.. Thanks Guys it Worked.. :)

The Shift+Bksp is also Solved, i used xmodmap

Does anyone know why the CPU Usage Jumps up When Scrolling a Webpage. I Doesnt Happen when compiz is not Loaded.

and Yeh PrintScreen crashes Compiz.[/QUOTE]

I experienced the scrolling problem too but dont know how to fix it. :\

---

### Post by Xylene on 2006-04-09
For some reason I can't get the compiz settings to even load in gconf. I run the editor, click apps -- and what do you know, compiz isn't there! I've done this before but I can't remember what I had to do to get the settings to end up where they're supposed to be and I can't find any information on how to do so. Any tips?

---

### Post by sparX CG on 2006-04-09
Xylene, are you running gconf-editor as root?  Compiz won't show up in there if it's run as root.

---

### Post by Xylene on 2006-04-09
[QUOTE=sparX CG]Xylene, are you running gconf-editor as root?  Compiz won't show up in there if it's run as root.[/QUOTE]
Nope.

I've tried a few different compiz debs and none of them add the entries.

---

### Post by keyhan on 2006-04-09
When using the Alt+Tab button a small window comes up and shows all the windows that are currently up. Now when I release the button I suppose this window should go away but it does not. How do I fix this?

/K ](*,)

---

### Post by Rob2687 on 2006-04-09
[QUOTE=keyhan]When using the Alt+Tab button a small window comes up and shows all the windows that are currently up. Now when I release the button I suppose this window should go away but it does not. How do I fix this?

/K ](*,)[/QUOTE]


Remove Splash from the fade plugin

---

### Post by sparX CG on 2006-04-09
@Xylene:

Did you loaded it like this?

$ compiz --replace gconf &

Because for it to show up in gconf, you must have the gconf plugin loaded.  And you must install the compiz-gnome package too.

Hopefully that helps!

---

### Post by Xylene on 2006-04-09
[QUOTE=sparX CG]@Xylene:

Did you loaded it like this?

$ compiz --replace gconf &

Because for it to show up in gconf, you must have the gconf plugin loaded.  And you must install the compiz-gnome package too.

Hopefully that helps![/QUOTE]
I have no way to load the plugins because I can't set them in gconf-editor, the compiz section simply isn't being added.

---

### Post by Rob2687 on 2006-04-09
The first time you load it it has to be done with all the plugins you want including gconf then it will be added. 
compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &

It does not have to be done as root.

---

### Post by Xylene on 2006-04-09
[QUOTE=Rob2687]The first time you load it it has to be done with all the plugins you want including gconf then it will be added. 
compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &

It does not have to be done as root.[/QUOTE]
Nothing works. Hell, now all of the sudden I can't even get XGL without the plugins (which is ungodly slow) to run like it did before.

I'm using the latest official ATi driver, by the way.

---

### Post by CHUCKYCHUCK on 2006-04-11
hi !
has any ati and kde user installed successfully xgl/compiz with this howto ?? ( i read some other threads dealing with kde and xgl, most of ati users had problems and couldn't get xgl/compiz running )

---

### Post by dusanyu on 2006-04-12
Link for the GPG key is bad

---

### Post by sabin on 2006-04-16
[solved]

guys.. got it working quite nice some time ago.. now I wanted to install the newest compiz debs and after I did so.. when starting compiz with --replace "gconf" option the box nearly freezes at least the X session does so I have to switch to a terminal and kill compiz.real.
however.. I installed the old ones again but I seem to have the same issue. when I remove gconf from the start command, it works but my gconf settings get ignored.. at least nothing happens when I change some stuff in the compiz section.

any clue how to fix that?

greets, sabin

[solved] I did reinstall.. seems that some libraries couldn't be loaded properly or something...

---

### Post by dr slizer on 2006-04-17
I've problems with installing the xserver-xgl package:
```
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Astarte:~# 
```
Anyone who have a solution?

---

### Post by Newcastle on 2006-04-19
Hi everybody im installing Compiz and Xgl in my AMD Athlon 64 3800 Dapper Drake Flight 6, when i start de Gconf-Editor in /apps arent any relationed with compiz... whats the problem?

---

### Post by Styles on 2006-04-19
I have everything working except all my keys will not work, eg. ctrl+alt arrow keys to switch to a diffrent desktop, alt+tab etc.... The only thing that seems to work is ctrl+alt left mouse button for the cube?

I do see all the eye candy working

I do have xmodmap set to /usr/share/xmodmap/xmodmap.us

I also looked in gconf-edit and don't see compwiz under apps even though compwiz and gnome-compwiz is installed.

using an nvidia card

I can't think of anything else to try. Anybody have an idea cause I'm fresh out?

Thanks in advance,

Styles

---

### Post by krusbjorn on 2006-04-19
[QUOTE=Styles]I have everything working except all my keys will not work, eg. ctrl+alt arrow keys to switch to a diffrent desktop, alt+tab etc.... The only thing that seems to work is ctrl+alt left mouse button for the cube?

I also looked in gconf-edit and don't see compwiz under apps even though compwiz and gnome-compwiz is installed.[/QUOTE]

"setxkbmap -model pc105 -layout us -variant basic" could be worth a shot, for the keyboard. But you might need to change "pc105" if you dont have a 105 key keyboard.

Look for compiz, not compwiz ;)

---

### Post by dusanyu on 2006-04-20
link to key is broke

---

### Post by koraa on 2006-04-23
[QUOTE=dusanyu]link to key is broke[/QUOTE]
QFT.  I attempted to locate this a mirror for this key, but was unsuccessful at doing so.  

If someone still has this key, could you post an attachment on this thread?  It would be very much appreciated.

Thank you.

**Edit :: **
It seems I spoke too soon.  It seems the key is no longer gzipped and is accessible at the following URL:

[http://metascape.afraid.org:13666/quinn.key.asc](http://metascape.afraid.org:13666/quinn.key.asc)

---

### Post by _simon_ on 2006-04-23
after installing this, Doom3 no longer runs.

Is there a fix for this or is it a case of if I want eyecandy I have to make sacrifices?

```

simon@ubuntu:~$ doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.2.3/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/simon/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 6800/AGP/SSE/3DNOW!
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.10
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
simon@ubuntu:~$

```

---

### Post by veelivar on 2006-04-23
I've just gone through thte instructions that are currentyl ont eh front page and I have a different probelm to what everyone else is describing here. 

What is happening for me is that the x server is not loading up at all and I am just presented with a command line login request.  it goes to a bule screen tellign me it has not been able to load up and I can find out the followifn info:

```
GDM: Xserver not found /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vf7

Error command could not be exectuted

Please install the Xserver or correct GDM configuration.
```

When I logedin an went to have a look /usr/bin/Xgl dosn't seem to exit.  Any ideas?

I have a clean install of dapper (upgraded) with the nvidia drivers.

Cheers,
Dan

---

### Post by leech on 2006-04-24
[QUOTE=_simon_]after installing this, Doom3 no longer runs.

Is there a fix for this or is it a case of if I want eyecandy I have to make sacrifices?

```

simon@ubuntu:~$ doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.2.3/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/simon/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 6800/AGP/SSE/3DNOW!
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.10
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
simon@ubuntu:~$

```[/QUOTE]


No, Doom3 will not work with Xgl, because Xgl is using your 3D hardware already.  Do a search on the forums for xgame, I haven't tried it yet myself, but it's supposed to create a new X server for when you play a 3D game, so that it can gain direct access to the hardware.

Leech

---

### Post by leech on 2006-04-24
[QUOTE=veelivar]I've just gone through thte instructions that are currentyl ont eh front page and I have a different probelm to what everyone else is describing here. 

What is happening for me is that the x server is not loading up at all and I am just presented with a command line login request.  it goes to a bule screen tellign me it has not been able to load up and I can find out the followifn info:

```
GDM: Xserver not found /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vf7

Error command could not be exectuted

Please install the Xserver or correct GDM configuration.
```

When I logedin an went to have a look /usr/bin/Xgl dosn't seem to exit.  Any ideas?

I have a clean install of dapper (upgraded) with the nvidia drivers.

Cheers,
Dan[/QUOTE]

Do you have xserver-xgl installed?  That is the package that contains /usr/bin/Xgl.  I would think Compiz would depend upon it.  Or maybe it dependsd on either xserver-xgl or xserver-aiglx, or whatever the other package is called...

Leech

---

### Post by thermans on 2006-04-25
I'm confused.  Which is the authoritative source for latest-and-greatest Xgl and compiz stuff?

Is it [www.beerorkid.com]("http://www.beerorkid.com") or [xgl.compiz.info]("http://xgl.compiz.info")?

I have both in my sources.list but neither seem to have been updated in the last week.

---

### Post by 008325 on 2006-04-26
help =_= while i done all step , while i restart

it can not boot to X window .....[-( [-( ](*,) ](*,) 

say X server not found =_=

---

### Post by jakobjs on 2006-04-30
I'm also having this problem as dr_slizer (see his reply at [http://ubuntuforums.org/showpost.php?p=929763&postcount=270)](http://ubuntuforums.org/showpost.php?p=929763&postcount=270)), just installed Dapper Beta 2.

> 
jjs@itchy:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2313kB of archives.
After unpacking 5915kB of additional disk space will be used.
(Reading database ... 83968 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb (--unpack):
** trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jjs@itchy:~$


And no, I don't have an old Xgl package installed, this is a fresh install from yesterday.

---

### Post by krusbjorn on 2006-04-30
[QUOTE=jakobjs]I'm also having this problem as dr_slizer (see his reply at [http://ubuntuforums.org/showpost.php?p=929763&postcount=270)](http://ubuntuforums.org/showpost.php?p=929763&postcount=270)), just installed Dapper Beta 2.



And no, I don't have an old Xgl package installed, this is a fresh install from yesterday.[/QUOTE]

See this post: [http://ubuntuforums.org/showpost.php?p=892263&postcount=236](http://ubuntuforums.org/showpost.php?p=892263&postcount=236)

---

### Post by muximus on 2006-05-02
i followed all the steps of the guide and got xgl up and running.,.thanx for that

but, i cant seem to get any window borders. tried killing compiz n gnome-window-decorator and restarting them as mentioned in the guide, but the window borders just disappear again

any help??

---

### Post by garba on 2006-05-02
[QUOTE=thermans]I'm confused.  Which is the authoritative source for latest-and-greatest Xgl and compiz stuff?

Is it [www.beerorkid.com]("http://www.beerorkid.com") or [xgl.compiz.info]("http://xgl.compiz.info")?

I have both in my sources.list but neither seem to have been updated in the last week.[/QUOTE]

good question i was wondering the same, as of today the most up-to-date version seems to be hosted on xgl.compiz.info, i have the other repo in my sources.list as well but packages are being fecthed from the former

---

### Post by bluevoodoo1 on 2006-05-02
I had Xgl/compiz up and running following this [guide]("https://wiki.ubuntu.com/xglati") (to have a separate Xgl session) and I was really happy with it. Last night, I thought I would do an update with the Repos it suggested--the beerorkid and xgl.compiz.info ones-- and well... It completely borked my Xgl session. After removing those repos and downgrading the packages back to the ones in the dapper repos I'm almost back... but not quite. 

As of now, I have a separate Xgl session. Xgl starts, but anything related to starting compiz, either by putting 'compiz --replace gconf' in startup, or even running that command completely freezes the system.

I have a feeling it might be something to do with a broken libGL.so.1.xlibmesa (sym)link, which has been described elsewhere but to no real detail. I'd like to know where *exactly* it should point to. I'm up for any advice and tips.

I'm using a nvidia card with the nvidia-glx from the repos. 

Again, Xgl/compiz had been running (all effects included), but now... any mention of compiz freezes the system. Ideas?

---

### Post by testube_babies on 2006-05-02
[QUOTE=muximus]i followed all the steps of the guide and got xgl up and running.,.thanx for that

but, i cant seem to get any window borders. tried killing compiz n gnome-window-decorator and restarting them as mentioned in the guide, but the window borders just disappear again

any help??[/QUOTE]

i have the same prob!

---

### Post by bluevoodoo1 on 2006-05-03
By somehow uninstalling and installing nvidia-glx and libgl1-mesa in seemingly a 'correct' order I have gotten compiz to start without freezing, though without any window borders. 

I've tried symlinking most, if not all possibilities of libGL.so and related files (as is suggested [here]("http://www.ubuntuforums.org/showpost.php?p=787197&postcount=664") and [here]("http://ubuntuforums.org/showpost.php?p=759870&postcount=486") ), but still luck. It will freeze or give the following error.

```

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

```

Symlinking is supposed to fix this, but rather causes it to freeze it as well...

---

### Post by muximus on 2006-05-03
still no window borders , so i tried killing compiz n window-decorator and restarting them ...
the window borders still dont appear, but i get the following error message:

compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0x24002b8 to texture
This will fail mysteriously, no GLX_TEXTURE_TARGET_EXT
GL ERROR:1280

wats this about??? compiz is still running the same as b4 though

any help??

---

### Post by hamil on 2006-05-04
[QUOTE=krusbjorn]See this post: [http://ubuntuforums.org/showpost.php?p=892263&postcount=236](http://ubuntuforums.org/showpost.php?p=892263&postcount=236)[/QUOTE]

After following your advice in another thread, I end up with an similar error.
```

E: /var/cache/apt/archives/libglitz1_0.5.5-0ubuntu1_i386.deb:
trying to overwrite <</usr/lib/libglitz.so.1.0.0>>, that also exist in the package glitz-dev

```

I do not have any packages called glitz-dev on my machine, and the only packages I am trying to install is:
```

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

Any clue to what I should do? This is my second attempt to get Compiz working on my machine, so maybe there is something conflicting from the first try?

Brgds
Lasse

---

### Post by krusbjorn on 2006-05-04
[QUOTE=hamil]Any clue to what I should do? This is my second attempt to get Compiz working on my machine, so maybe there is something conflicting from the first try?[/QUOTE]
Which guide did you follow the first time? The glitz files could probably be leftovers since then, but it seems strange if you uninstalled those packages before trying again. Doesnt a search for "glitz" in synaptic turn up any previously installed glitz packages at all?

---

### Post by hamil on 2006-05-04
I followed the guide from this post:
[UbuntuForums](http://www.ubuntuforums.org/showthread.php?t=131267)

And now my whole system acts funny...
I can no longer open synaptic or other things...
When typing in the commands in terminal, it gives this output:

```

sudo nautilus
nautilus: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory

```

What is happening??

Lasse

---

### Post by bluevoodoo1 on 2006-05-04
I got it working again... righteous!

---

### Post by Przemekc1 on 2006-05-05
How can I turn off this option on screen?
[[IMG]http://images1.fotosik.pl/61/sea8nkrwtnrcn9hfm.jpg[/IMG]](http://www.fotosik.pl/pokaz_obrazek/sea8nkrwtnrcn9hf.html)

---

### Post by junior aspirin on 2006-05-05
remove the dock plugin from apps>compiz>general>allscreens>options>activeplugins in the gconf-editor

---

### Post by Przemekc1 on 2006-05-05
Thanks, do you know maybe where can I find description of plugins used in XGL?

---

### Post by krusbjorn on 2006-05-05
[QUOTE=Przemekc1]Thanks, do you know maybe where can I find description of plugins used in XGL?[/QUOTE]

[https://wiki.ubuntu.com/compiz](https://wiki.ubuntu.com/compiz)

---

### Post by mattman on 2006-05-06
I have miniwin listed in pps>compiz>general>allscreens>options>activeplugins but in doesn't show up under plugins so that I can change the settings.

---

### Post by jon_z on 2006-05-06
I installed Xgl and compiz via this method with a Ati 9600 XT, and dapper 6.06 beta 2 fresh install i386..   Im using the k7 kernel.. When Xserver goes to start.. it just sits there with the rotating loading mouse icon...and does not go past that point.. Any ideas?   my Xorg.0.log complains about wacom

```
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by hornett on 2006-05-06
After one of the recent compiz updates, when I run compiz all I get is a white screen. I can see a mouse cursor but that's it :( 

I have a radeon 9000 with opensrc drivers.:-({|=

---

### Post by Anthem on 2006-05-06
Three hundred posts in this thread!  Woohoo!  ;)

Seriously, does anyone know how often is the CVS synced to the repositories?  My first XGL attempt hosed my install.  I'm getting ready to re-attempt, but I want to make sure I'm really good to go.

---

### Post by hamil on 2006-05-10
Well... I do get some errors regarding the key...
It is no longer stored here, and the terminal gives me this output:
```

W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97F ED8A569E
```

Any further guidance would be appreciated... How to use the repos, when I can not download the key?

---

### Post by Subbu.exe on 2006-05-11
Try this for the New Key
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

---

### Post by Przemekc1 on 2006-05-11
I've got question, how could I restore default gconf editor configuration?

---

### Post by jimisdead on 2006-05-11
I've just read through all 31 pages and noticed I am not alone in my problem of having no window decorations... everything else works great - the system works fine, the dock, the cube, wobbly windows all look excellent - only I have no window decorations.

Nothing posted in the thread yet works... does any have any ideas? I'm getting no error messages, just no window decorations.

---

### Post by smittyinside on 2006-05-17
After working for hours last night (and doing 2 or 3 clean installs ](*,) ) I finally got Xgl working with your guide (with window decorations). Cheers to you my man!

-KJS

---

### Post by bluevoodoo1 on 2006-05-17
[QUOTE=jimisdead]I've just read through all 31 pages and noticed I am not alone in my problem of having no window decorations... everything else works great - the system works fine, the dock, the cube, wobbly windows all look excellent - only I have no window decorations.

Nothing posted in the thread yet works... does any have any ideas? I'm getting no error messages, just no window decorations.[/QUOTE]

I personally haven't read through this whole post in a while, so I'll try some ideas that come to mind.

In configuration editor...

compiz > general > allscreens > options
is "decoration" listed in the active plugins? If not add it, it should be the second item.

If you run "gnome-window-decorator" then "compiz --replace gconf"  what happens??

---

### Post by bogdan2412 on 2006-05-18
I'm sorry if this has been said already, but I don't really have time to look through all the posts in this thread and "Search" doesn't really help me... I installed the latest compiz, Xgl from the repository shown in the first post on Kubuntu Dapper (all updated to date) and cube doesn't work... When I try to rotate to another desktop nothing happens... Can anybody help me?

---

### Post by ericesque on 2006-05-19
Quick suggestion from here on out...

please mention your graphics card in each post.  This may help others find more relevant information in search results.

---

### Post by bogdan2412 on 2006-05-19
Sorry about that... My graphics card is a Nvidia Geforce 5200, 128 MB...

---

### Post by blanky on 2006-05-20
Hey guys, I installed this using [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati) and it worked for a day and it was great, everything worked, I could even watch embedded videos in firefox correctly using mplayer-plugin. However, lately it hasn't been working. At first, I had set **gconf-dump** plugin on, just to see what it was, forgot to turn it off and it wouldn't work. So I took it off and it seemed to have had worked, but it only did for a little bit. I heard on a site (*The site of the guy who owns the repos*) that some people were having problems with the wobbly plugin after ubuntu4 (*The package of compiz*), could this be it?

Xgl 0.33
Compiz 0.0.10
Ati 9800 Pro 128MB DDR

The thing I'm wondering about is that it worked fine, but now doesn't, so I was just wondering what it could be.

Also, whenever I 'log off' of xgl, the thing gets to right before the login screen, and hangs (*Cant move my mouse, nothing*). Anyone know what's up?

---

### Post by 23meg on 2006-05-25
Anyone tried running Quinn's latest packages with the latest Nvidia driver (**8762**)? With my Geforce Go6200 TurboCache XGL starts, but as soon as I launch Compiz it crashes and restarts.

**EDIT: Latest version is 8762, not 8756.**

---

### Post by denjin on 2006-05-25
[quote=jon_z]I installed Xgl and compiz via this method with a Ati 9600 XT, and dapper 6.06 beta 2 fresh install i386..   Im using the k7 kernel.. When Xserver goes to start.. it just sits there with the rotating loading mouse icon...and does not go past that point.. Any ideas?   my Xorg.0.log complains about wacom

```
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```[/quote]
I have the same problem with my x600.  However, look in /var/log/X11/gdm (something like that) for :1.log or whatever.  It mentions some glcore error for me.

---

### Post by Jason_25 on 2006-05-25
[QUOTE=23meg]Anyone tried running Quinn's latest packages with the latest Nvidia driver (8756)? With my Geforce Go6200 TurboCache XGL starts, but as soon as I launch Compiz it crashes and restarts.[/QUOTE]
Make sure XGL is actually running not regular X.  If I launch compiz without X, I get a crash back to the login screen.

---

### Post by 23meg on 2006-05-25
[QUOTE=Jason_25]Make sure XGL is actually running not regular X.  If I launch compiz without X, I get a crash back to the login screen.[/QUOTE]
I'm sure it's running; I edited gdm.conf-custom as usual. Everything works with the Dapper repo versions, but no go with Quinn's.

---

### Post by lithorus on 2006-05-25
[QUOTE=23meg]I'm sure it's running; I edited gdm.conf-custom as usual. Everything works with the Dapper repo versions, but no go with Quinn's.[/QUOTE]
You might want to recheck with quinn's, since there was recently a problem with the 0.11ubuntu1 version.

---

### Post by 23meg on 2006-05-25
[QUOTE=lithorus]You might want to recheck with quinn's, since there was recently a problem with the 0.11ubuntu1 version.[/QUOTE]
I'm now doing a fresh RC install and will check again, thanks.

---

### Post by 23meg on 2006-05-27
[QUOTE=23meg]I'm now doing a fresh RC install and will check again, thanks.[/QUOTE]
It's even worse with the fresh install;  XGL sometimes crashes randomly before I start compiz, and sometimes as soon as I start it. Very rarely it crashes a minute or two after it's started.

---

### Post by spockrock on 2006-05-27
quins repo was updated with 0.0.11-ubuntu2 that fixed the issue of compiz not working on single monitor setups

---

### Post by 23meg on 2006-05-27
[QUOTE=spockrock]quins repo was updated with 0.0.11-ubuntu2 that fixed the issue of compiz not working on single monitor setups[/QUOTE]
That's the version I have now, and everything else is set up according to the instructions, but I still have random / instant crashes.

---

### Post by spockrock on 2006-05-27
are you using the dock/miniwin plugin, they are really unstable, disable them

---

### Post by 23meg on 2006-05-28
[QUOTE=spockrock]are you using the dock/miniwin plugin, they are really unstable, disable them[/QUOTE]
I already had them disabled. Updating (once more) to the latest mesa libs fixed the problem.

---

### Post by phorque on 2006-05-31
Has anyone had problems with extremely slow/jerky window resizing in quinn Xgl/Compiz packages? I can't seem to find any other accounts of this.

Everything works great for me, but i just can't resize windows at all because it's so slow.

---

### Post by IbeeX on 2006-06-02
[QUOTE=DeeZiD]

open gconf-editor then
```
G_SLICE=always-malloc gconf-editor
```
go to /apps/compiz/general/allscreens/options/ and remove the active plugins line by  clicking with right mouse on the item and selecting "remove key" or something like that (sry, german version of gconf-editor ;) )

then restart compiz```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
```[/QUOTE]

Hi I am having latest Dapper 6.06 and Nvidia 6800GS card, I installed latest nvidia driver and foloved this instructions but I am unable to start compiz??
when I runn it I don't have window decorations and also when I start gconf-editor
I dont have /apps/compiz/ ??

can somebady help me?

---

### Post by DeeZiD on 2006-06-03
I've updated the HowTo for ATi-users.
The new drivers seem to have the same quality as the nvidia ones.
Even fbos are possible and everything is snappier. :D 


regards Dennis

---

### Post by IbeeX on 2006-06-03
[QUOTE=IbeeX]Hi I am having latest Dapper 6.06 and Nvidia 6800GS card, I installed latest nvidia driver and foloved this instructions but I am unable to start compiz??
when I runn it I don't have window decorations and also when I start gconf-editor
I dont have /apps/compiz/ ??

can somebady help me?[/QUOTE]

Also I get this error 
desktop:~$ gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
[1] 7282
desktop:~$ compiz.real: GLX_EXT_texture_from_pixmap is missingcompiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

thx

---

### Post by DeeZiD on 2006-06-03
Are you sure you're running Xgl?
If you're sure you can try this:
```
sudo apt-get install libgl1-mesa-dri libgl1-mesa --reinstall
```

---

### Post by Paool on 2006-06-03
is xgl works with xfce? I can't find any howto about this...

---

### Post by IbeeX on 2006-06-03
[QUOTE=DeeZiD]Are you sure you're running Xgl?
If you're sure you can try this:
```
sudo apt-get install libgl1-mesa-dri libgl1-mesa --reinstall
```[/QUOTE]
I think I am

desktop:~$ ps aux | grep Xgl
root      4576  3.2  1.7  71376 35764 ?        SL   16:20   0:49 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4621  0.1  0.4  45992  9840 tty7     SLs+ 16:20   0:02 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-Kvxofi -nolisten tcp :93 -terminate
ibrkanac  6784  0.0  0.0   3948   912 pts/0    R+   16:45   0:00 grep Xgl

---

### Post by AThomsen on 2006-06-04
Got it to work! However firefox seems a quite slow when scrolling and changing pages. Resizing windows is also very jerky. Is it because of my video card is to slow (Geforce2 mx)?

Another thing: with compiz enabled all windows has a border also when they are maximized. Is there any way to prevent this?

---

### Post by Basfriends on 2006-06-05
much thnx to the creators of this howto. It is simply brilliant. It works for me just like that. Now I am going to enjoy my new Xgl Ubuntu Dapper... Much thnx to the community.

---

### Post by kno on 2006-06-06
[quote=dusanyu]Link for the GPG key is bad[/quote] 
 ```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

---

### Post by funkenstein on 2006-06-06
w00t!!!
it's the only one of all the compiz howto's I've tried that worked on my turion system - 64bit dapper gnome with nvidia... although I still had to use RAOF's repos from the end of [ THIS ](http://ubuntuforums.org/showthread.php?t=187887) thread to get it functioning... and configuring compiz from gconf-editor is a PITA, and the dock plugin is b0rkt... but everything else makes me cream my pants... *shuffles off to try and break the system some more*

---

### Post by rudefyet on 2006-06-08
great guide...just wish the dock plugin was stable :D

---

### Post by jshein on 2006-06-08
Having some issues here with the .debs

Preparing to replace libgl1-mesa 6.4.1-0ubuntu8 (using .../libgl1-mesa_6.5.1-0ubuntu14_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.5.1-0ubuntu14_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.5.1-0ubuntu14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have any ideas?

---

### Post by RikBlankestijn on 2006-06-08
Hi.

Maybe it's already mentioned I'ven't read through the whole thread, but I also had no window borders and I fixed it by removing [COLOR="SeaGreen"]libopacity.*[/COLOR] from [COLOR="SeaGreen"]/usr/lib/compiz[/COLOR]. I placed them there manually for opacity in the windows. 

kind regards,
Rik

btw. indeed, now opacity does not work unfortunalty...

---

### Post by Particle on 2006-06-11
It doesn't appear to be working for me.  I followed the extra steps because I didn't have window decorations and it just went back to how it was after the steps.  It didn't help the problem.

AMD64 & fglrx

I get this error:
```
particle@tim:~$ gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
[1] 6005
particle@tim:~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Any ideas?

---

### Post by jaymode on 2006-06-11
[QUOTE=Particle]It doesn't appear to be working for me.  I followed the extra steps because I didn't have window decorations and it just went back to how it was after the steps.  It didn't help the problem.

AMD64 & fglrx

I get this error:
```
particle@tim:~$ gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus
[1] 6005
particle@tim:~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Any ideas?[/QUOTE]

Are you using 24 bit color depth? I had a similar message with 16 bit depth and many artifacts.

---

### Post by Particle on 2006-06-11
I don't know how to change my color depth or check it in the first place.  It's as you describe though--when I open a terminal my entire screen corrupts.  Also, it's slow as crap to move or resize windows.

---

### Post by fargoth on 2006-06-12
to set your color depth edit /etc/X11/xorg.conf  - you can either remove the modes with colordepth<24 or change the default colordepth to 24 in the screen section.

---

### Post by Particle on 2006-06-12
Oh, that?  I thought it was something special due to XGL.  Yeah, that entry is set to 24bpp default.

---

### Post by superm1 on 2006-06-15
I just started getting the same problem on amd64 nvidia card from a working configuration - just doing misc updates that were provided from compiz.net

---

### Post by bags on 2006-06-17
hy!
i think there's something wrong with my configuration; I followed the howto but I've no decorations and effects now :( 

I think xgl and compiz are running:
> matteo@matteo-desktop:~$ ps aux |grep xgl
matteo    5959  0.0  0.0   2876   796 pts/0    R+   18:21   0:00 grep xgl
matteo@matteo-desktop:~$ ps aux |grep compiz
matteo    5965  0.0  0.0   2876   800 pts/0    S+   18:21   0:00 grep compiz

I added to system-preferences-sessions a new session ("/usr/bin/thefuture") but every time I restart it disappears; should I log in in a particular way? have you any suggestion? I really don't know what to do..

thanks ;) 
matteo

---

### Post by Cimmo on 2006-06-18
I've kubuntu dapper followed all instructions, but when compiz starts then windows titles disappears and keyboard stop to work!
What can I do?

If I have to provide more infos tell me please.

---

### Post by NETabuse on 2006-06-19
hey there, i have a window content/ titles sop being visible loading of Xgl.. 
runing on: compaq N610c (3 years old) 768MB ram, ati radeon mobility 7500. Running on "ati" driver, not "fglrx" or "radeon". 

it seems that untill i run compiz the decorators / content are not rendered. 

i have a toggle script for doing this.. i usually just login(i can't see what i type so i just guess) alt-f2 to get run dialog, guess type xterm.. then xterm comes up again no window decorators are visible, but content in xterm is. so i just run my toggle scrpit ./Desktop/toggle_compiz.sh and all loads beautifully.. now if i could just get eveything to be visible before running compiz toggle?? any one have a clue?

---

### Post by YourDoom123 on 2006-06-19
Is there a problem with mesa-utils from the cvs right now? I'm not sure if its because i'm testing edgy, or because of xgl, but I can't install, remove, or upgrade any programs because of an error in the mesa-utils program. Here's an example: 
```

arjun@arjun-laptop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libxklavier10
The following packages will be upgraded:
  acpi-support aspell build-essential cdparanoia cpio dhcdbd dmidecode
  gnome-mime-data guile-1.6-libs gzip info intltool-debian less libaspell15
  libattr1 libavc1394-0 libcdparanoia0 libcrypt-blowfish-perl libelfg0
  libexif12 libglib-perl libgnome2-perl libgpg-error0 libguile-ltdl-1
  libhtml-parser-perl libidn11 libjpeg62 liblcms1 libltdl3 libmng1
  libnfsidmap1 libpcap0.8 libpng12-0 libpopt0 libqthreads-12 libraptor1
  libshout3 libsysfs2 libungif4g libwpd8c2a logrotate lsof ltrace menu-xdg
  mii-diag nano netcat patch po-debconf powermgmt-base psmisc sbuild tcpdump
  ttf-arabeyes ubuntu-base ubuntu-minimal ubuntu-standard udev
58 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/8372kB of archives.
After unpacking 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-13_i386.deb (--unpack):
 files list file for package `mesa-utils' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-13_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And thats basically what happens ALL the time. the locales problems are a result of the new libc6, I know that, and a fix should be coming soon, but there are a lot of things I need to upgrade and install still. If anyone else is experiencing this problem, or did, I'd appreciate it if you've found a fix other then completely reinstalling, although I can do that if absolutely necessary. I've posted this in the edgy forum as well to see if anyone knows anything there. just for reference, my mesa-utils version is 6.5.1-0ubuntu16, while the dapper version is 6.3.2-something. In the meantime, i'm gonna keep looking for the problematic file, and see if i can't fix it. nothing looks promising yet.

---

### Post by YourDoom123 on 2006-06-20
fixed! just delete the /var/lib/dpkg/info/mesa-utils.list file, and everything goes without a hitch :)

---

### Post by incidence on 2006-06-21
I'm having a problem, after the xmodmap, ALT -key doesn't work, I can't alt+tab, or use alt+ctrl+arrows, and without xmodmap, alt works, but I can't press shift+backspace, which totally sucks

---

### Post by IbeeX on 2006-06-21
[QUOTE=incidence]I'm having a problem, after the xmodmap, ALT -key doesn't work, I can't alt+tab, or use alt+ctrl+arrows, and without xmodmap, alt works, but I can't press shift+backspace, which totally sucks[/QUOTE]

Same here :(

---

### Post by incidence on 2006-06-24
[QUOTE=IbeeX]Same here :([/QUOTE]

Any idea how to correct this?

---

### Post by atenlaugh on 2006-07-12
I tried, no windows/decorator, anything. I tried restarting as per the instructions, still nothing. No errors. Simply doesn't work, and I don't know if anybody else has had this problem, as there are hundreds and hundreds of posts.

My card is an Nvidia 6200.


Update: When my Ubuntu tried to boot up, it instantly went to "couldn't find X Server", and so on. I could still get in with "startx".

---

### Post by wzzrd on 2006-07-14
Did someone found the key to smooth resizing of windows yet? Slow is really and understatement...

---

### Post by superm1 on 2006-07-17
> **wzzrd said:**
> Did someone found the key to smooth resizing of windows yet? Slow is really and understatement...

I run Xgl on two boxes.  One with an nvidia card, and one with an ATI.  The ATI is horrible about resizing, whereas the nvidia works great.

---

### Post by Recluse on 2006-08-29
I followed the OP instructions, but when it goes to load KDE (using kubuntu of course) it just hangs at the splash screen. All the status stuff goes through, saying it's starting all the devices, but as soon as that's done, it flashes, then loads the regular splash screen and hangs. No errors, nothing. I'm actually posting this from the Kubuntu live CD since I can't get into my windows manager.

I don't know if this has anything to do with it, but when I did the apt-get for all the eye candy, it said there was a version mismatch with one of the packages (I believe it was mesa and glitz) and couldn't fetch.

I'm using an Nvidia card-7900GTX. I was able to run glxgears no problem before hand, so I think that was working fine. If anybody could even at least get me back into the desktop, that'd be great. Thanks in advance for any help!

---

### Post by dracule on 2006-11-28
I followed the guide and still get no window borders.

---

