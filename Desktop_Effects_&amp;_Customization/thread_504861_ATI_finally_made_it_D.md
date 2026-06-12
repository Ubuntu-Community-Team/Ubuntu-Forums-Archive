---
title: "ATI finally made it :D"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by fjoesne on 2007-07-19
I'm currently running compiz-fusion with ati's new driver, in xorg 7.2 with composite and the whole nine yards. the only thing i really had to do was run compiz with --force-fglrx... seeing a few problems with scrolling on most applications, like its not refreshing or something. im guessing this has something to do with compiz.  any ideas?

---

### Post by FiggyG on 2007-07-19
Are you getting the AMD testing logo on the bottom of your screen?

---

### Post by hellboy195 on 2007-07-19
> **fjoesne said:**
> I'm currently running compiz-fusion with ati's new driver, in xorg 7.2 with composite and the whole nine yards. the only thing i really had to do was run compiz with --force-fglrx... seeing a few problems with scrolling on most applications, like its not refreshing or something. im guessing this has something to do with compiz.  any ideas?

Strange.


@FiggyG : I also have this logo. Annoying. A friend of mine have this logo with the message (testing/no 3d) but I have 3D. I thought this is a stable release because of the release from the windows drivers and there isn't mentioned that this is unstable. And the changelog is as short as normal ;) And there aren't many improvements. Or is this a secret developing surprise?

---

### Post by fjoesne on 2007-07-19
no amd testing logo at the bottom.. :) 
I think i have seen something on this flickering gtk issue somewhere on this forum, im just not sure where i saw it.. every time i scroll now i have to "refresh" by spinning the cube or alt-tabbing once.

---

### Post by marsmissionaries on 2007-07-19
sweet. Hopefully there will be a non testing driver soon....im getting tired of XGL and it's crappyness.

---

### Post by misfitpierce on 2007-07-19
Sounds nice if it means you dont have to XGL session anymore. I hope this means the end of ATI's crappy support for linux... If it does ive truly gone to heaven.

---

### Post by synthaxx on 2007-07-19
Sounds good guys, keep us updated. I was allmost going over to the dark side (you know .. "vidia-nay") :D

---

### Post by amadeus266 on 2007-07-19
I have bookmarked this thread due to wanting to upgrade to my ATI X1800 from my ATI 9200. Please keep us informed.

BTW. I have Fusion running and I am NOT using an XGL session. The only problem I have had is random freezes.

---

### Post by misfitpierce on 2007-07-19
I only use XGL b/c I had made it for beryl which needed it to run correct with all effects...

But yea keep us updated on the watermark thing and if you find way to take off etc.

---

### Post by amadeus266 on 2007-07-19
Didn't need XGL for Beryl either. Which card do you have?

---

### Post by misfitpierce on 2007-07-19
ATI Xpress 200... I could never get it working without XGL session with restricted driver set.

---

### Post by hellboy195 on 2007-07-20
I have the same card ^^
It's pain but once I got it running with XGL and everthing was running but the performance was really bad. Because of the fglrx I think. That would be great if Compiz fusion is running with X and fglrx. Crappy XGL.

---

### Post by misfitpierce on 2007-07-20
They say it is on new driver from what im told... Im on 8.38.7 now and considering move to 8.39 if it does run in X and the watermark on screen can be taken off.

---

### Post by Canesfan2020 on 2007-07-20
its early and I didnt go to bed until 2 am

so, just to clarify..

what your saying is that the PROPRIETARY ATI driver can now run composite + DRI at the same time now plus AIGLX support?

---

### Post by hellboy195 on 2007-07-20
Hmm now I tried it but it's not running.
I enable AIGLX and Composite in the xorg.conf and restarted X.

hellboy@ubuntu:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)

hellboy@ubuntu:~$ glxinfo | grep texture_from_pixmap
GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

and 

hellboy@ubuntu:~$ compiz --force-fglrx
There is already the metacity win manager running, you should use the --replace option to override it.

I installed all things from compizfusion repo. (btw I'm using feisty)


but : 

hellboy@ubuntu:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


What can i do?

---

### Post by synthaxx on 2007-07-20
> **hellboy195 said:**
> What can i do?

Try "compiz --replace --force-fglrx" .

Worked for me .. once :)

---

### Post by jimminy_kriket on 2007-07-20
Time for my stupid question of the day:

Whats wrong with XGL? I run it and have no problems, its not slow or anything. Why the hate?

Also, where do you get the new drivers? :D

---

### Post by hellboy195 on 2007-07-20
> **synthaxx said:**
> Try "compiz --replace --force-fglrx" .

Worked for me .. once :)

Actually it'S working :) Ok with major issues but it's working. Althougth i started gtk-window-decorator i lost the top of my windows :(

---

### Post by synthaxx on 2007-07-20
> **jimminy_kriket said:**
> Time for my stupid question of the day:

Whats wrong with XGL? I run it and have no problems, its not slow or anything. Why the hate?

Also, where do you get the new drivers? :D

XGL caused me no end of headaches. Firstly not supporting my dualscreen setup (something about texture sizes not able to exceed 2048x2048, i run 1920x1200+1280x1024).
Secondly it's unstable, incredibly unstable. Running (then) beryl and switching desktops on the cube would randomly lockup my system.

You can get the drivers from [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") btw.

Be aware though, it gives you an annoying "AMD Testing use only" banner in the bottom right corner of every monitor... not a biggy, but annoying nonetheless.

---

### Post by Rob2687 on 2007-07-20
The driver does not support AIGLX.

This force-fglrx thing sounds like no-copy or whatever that was done in Beryl.

---

### Post by misfitpierce on 2007-07-22
XGL is fine and all but when running my ATI card in XGL it disables direct rendering and I must go into a normal session to play any sort of 3D game etc.

---

### Post by jimminy_kriket on 2007-07-23
> **misfitpierce said:**
> XGL is fine and all but when running my ATI card in XGL it disables direct rendering and I must go into a normal session to play any sort of 3D game etc.

I think the same thing happens to me, xgl reports use of the mesa drivers, xfce reports use of the proper (at least i think) ati drivers.

When you do "glxinfo" does it report direct rendering? Mine doesnt :( , although i think i have it because i can run Compiz.

---

### Post by hinogi on 2007-07-29
> **jimminy_kriket said:**
> I think the same thing happens to me, xgl reports use of the mesa drivers, xfce reports use of the proper (at least i think) ati drivers.

When you do "glxinfo" does it report direct rendering? Mine doesnt :( , although i think i have it because i can run Compiz.

thats the general paradoxon every ati user has to cope with. its somehow like XGL uses direct rendering all for itself and doesn't grant other applications this option so its marked as disabled. you can easily see this by starting a game for example that needs this enabled, textures will go haywire and lighting will be gone. if you then just swicht to a gnome session everything will be Ok again.
so currently it seems impossible to have XGL and DRI at the same time, unless the rumors of aiglx working with ati are true but i highly doubt that unless someone can show me how its done :B

---

### Post by woody_sud on 2007-08-02
> **misfitpierce said:**
> XGL is fine and all but when running my ATI card in XGL it disables direct rendering and I must go into a normal session to play any sort of 3D game etc.

Yeah, and thats why XGL is a pain in... I have a desktop with Nvidia +AIGLX and all run sweet eye candy and games, but my notebook with ATI has ATI x1400 and well... you know...

Ok, I have latest ATI driver 9.39.4 installed by envy, had to enable composite in xorg.conf???

---

### Post by Jonq on 2007-08-02
i got ati mobility radeon x700 and --force-fglrx works for me alsoevery compiz plugin works only down side of it having contents of window overlapping, if thats fixed bye bye Xgl :p

---

### Post by jpereira on 2007-08-05
You might want to take a look at **[thread=518426]this thread[/thread]** on how to easily run a separate X just for a specific application, this overcoming the inability to run some 3D games in Xgl.

---

### Post by jpereira on 2007-08-06
Well, there are ways around it, check above post. :)

---

### Post by iLoVe.cF- on 2007-08-11
HOW the f does you get the option --force-fglrx ? .. i dont get that option.. just installed compizfusion..

Tried to install source, but naaa.. cant get it to work.. runs from the howto @ compiz webby.

---

