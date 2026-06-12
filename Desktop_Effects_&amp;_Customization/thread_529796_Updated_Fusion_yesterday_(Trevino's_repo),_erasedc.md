---
title: "Updated Fusion yesterday (Trevino's repo), erased/changed my settings, shortcuts?"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-19
I updated Compiz Fusion yesterday and just tried it out a few minutes ago.
The good news is that it seems to be much faster.
The bad news is that my settings were lost, and I think some of the "Actions" tabs that were present before are now gone...?
The Actions tabs for rotating the cube is gone so I can't figure out how to set it to rotate when I hold the middle mouse button, and the "Water Effect" settings aren't working (under the "Actions" tab, there's only "point" and "line", neither of which it lets me set).

It seems that the settings manager has been revamped and lost some of it's previous usability in the process; Can anyone give me any tips?

---

### Post by Mike_88 on 2007-08-19
Yes, this repo update seems to be causing some problems.

I've lost my settings as well, and it appears to be a result of the fact that prior to the update they were stored in ~/.compizonfig, but following the update they are being stored in ~/.config/compiz/compizconfig.  I guess we may have to wait for an update.

---

### Post by rainwalker on 2007-08-19
Arg, that's annoying...

Do you know how to change the cube caps to just a solid color (besides black)?
If I enable cubecaps it uses the CF logos, neither of which I really like.

---

### Post by crazyhunk on 2007-08-19
I have seen in the Compiz Fusion Forums that trevino's repos are broken now.... and they will be fixing ti soon.... incase ur fusion is broken u can use Amarnaths repos or use the beautifull script done by ElemonGW 

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by rainwalker on 2007-08-19
> **crazyhunk said:**
> I have seen in the Compiz Fusion Forums that trevino's repos are broken now.... and they will be fixing ti soon.... incase ur fusion is broken u can use Amarnaths repos or use the beautifull script done by ElemonGW 

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)


Thanks, but things are technically working so I'm not going to mess with it. I'm actually going to follow the whole "if it aint broke, don't fix it" thing this time...

My 3D windows don't work either; If I try to enable it, it just disables by itself.

---

### Post by KhaaL on 2007-08-19
I have the very same symptoms, Rainwalker. My move windows plugin cant be setup (neither by CSSM or the .ini file directly), screensaver is broken and there's a lot more broken in this update... can't wait til' it's fixed :|

If you know how to switch to another repo and fix this, please let us know!

---

### Post by Lord Illidan on 2007-08-19
Same problem as you have, but will stick with it until another update is released.

---

### Post by rainwalker on 2007-08-19
Alright, good to know I'm not the only one :)

I'm going to stick with Trev's repo as well

---

### Post by rainwalker on 2007-08-19
It's going to be interesting to see how all of this Compiz Fusion stuff tides over in the update to Gutsy when it comes out, because it's coming with CF included (if I've heard correctly).

---

### Post by KhaaL on 2007-08-19
Hopefully they'll also include the extras and unsupported plugins into universe repos, I really like my gears & screensaver :)

btw, you got a great sig' rainwalker... very poetic!

---

### Post by sdowney717 on 2007-08-19
My 3d windows in the cube wont work.
The fish atlantis in the cube dont work.

etc.......

Is there a way to restore the previous files, nullify the update?

also the rotate the  3d cube is running very slowly, dragging when it used to twirl and whorl super fast.

---

### Post by rainwalker on 2007-08-19
Yeah, my only annoyance is that with the screensaver, the cube will rotate and all but eventually the cube will go black (I'm guessing it's like the cube going into screensaver)
Unfortunately, a screensaver of my rotating cube in screensaver mode isn't very useful...


Thank you :) I admit I didn't make it up myself, but I spread it around wherever I can
I like yours, especially the link to the pic (I used to run w2k, hated it with a passion)

---

### Post by rainwalker on 2007-08-19
> also the rotate the 3d cube is running very slowly, dragging when it used to twirl and whorl super fast.
Mine only runs quickly with the opacity at 100%, but that's the way it's always been.

---

### Post by bapoumba on 2007-08-19
This may be of some help. A friend of mine has [posted earlier on his blog]("http://ubuntufr.free.fr/?p=82") about this (sorry, it's in French). I cannot confirm as I'm not using CompizFusion, but he fixed it copying the conf file to the proper place (the code is his):
```
cp ~/.compizconfig/Default.ini ~/.config/compiz/compizconfig/

```
SGDG !
(Sans Garantie du Gouvernement = Without the guarantee of the Government)

EDIT: may be another solution here:
[http://ubuntuforums.org/showthread.php?t=529510]("http://ubuntuforums.org/showthread.php?t=529510")

---

### Post by steveneddy on 2007-08-19
[QUOTE=bapoumba;3218350]This may be of some help. A friend of mine has [posted earlier on his blog]("http://ubuntufr.free.fr/?p=82") about this (sorry, it's in French). I cannot confirm as I'm not using CompizFusion, but he fixed it copying the conf file to the proper place (the code is his):
```
cp ~/.compizconfig/Default.ini ~/.config/compiz/compizconfig/

```

This worked great for me.

Thanks.

---

### Post by s_spiff on 2007-09-09
Tried installing using the same repos, but get this error. Anyone?
```
spiff@spiffed:~$ sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  compizconfig-settings-manager
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/600kB of archives.
After unpacking 3658kB of additional disk space will be used.
Selecting previously deselected package compizconfig-settings-manager.
(Reading database ... 149328 files and directories currently installed.)
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.6.99~git20070903+jbs3_amd64.deb) ...
Setting up compizconfig-settings-manager (0.6.99~git20070903+jbs3) ...
spiff@spiffed:~$ sudo apt-get install compiz-fusion-*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-plugins-unofficial for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unsupported for regex 'compiz-fusion-*'
The following extra packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
The following NEW packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2935kB of archives.
After unpacking 8880kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-fusion-plugins-main compiz-fusion-plugins-extra
Install these packages without verification [y/N]? y
Selecting previously deselected package compiz-fusion-plugins-main.
(Reading database ... 149490 files and directories currently installed.)
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.5.2+git20070829-0ubuntu1~ppa1_amd64.deb) ...
Unpacking compiz-fusion-plugins-unofficial (from .../compiz-fusion-plugins-unofficial_0.0.1+git20070728~jbs0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070728~jbs0_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libcolorfilter.so', which is also in package compiz-fusion-plugins-main
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package compiz-fusion-plugins-unsupported.
Unpacking compiz-fusion-plugins-unsupported (from .../compiz-fusion-plugins-unsupported_0.5.2~git20070831+jbs3_amd64.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.5.2+git20070829-0ubuntu1~ppa1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070728~jbs0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jonty-comp on 2007-09-15
I'm also getting this error, I switched to this repo with the promise of plugins-unofficial and now I have no compiz. :(

---

