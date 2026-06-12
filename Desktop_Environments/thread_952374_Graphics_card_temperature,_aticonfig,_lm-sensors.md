---
title: "Graphics card temperature, aticonfig, lm-sensors"
date: 2008-10-19
forum: Desktop Environments
---

### Post by Eremit on 2008-10-19
[COLOR="Red"]Update[/COLOR]
Solution on karmic:

Uninstall "sensors-applet"
Get source for version >=2.2.5 ( [http://sensors-applet.sourceforge.net/index.php?content=source](http://sensors-applet.sourceforge.net/index.php?content=source) ).
Make sure aticonfig is working (see below).
Compile and install (one possibility is with "checkinstall").
The sensors-applet should now list you graphics card temperature.

[COLOR="Silver"]On my ATI Radeon HD4850 I can read out the temperature and fan speed with aticonfig:
```
aticonfig --adapter=0 --od-gettemperature
aticonfig --pplib-cmd "get fanspeed 0"
```

Is there a way to tell lm-sensors, respectively the sensors-applet, this temperature, so that I can display it in the gnome-panel?[/COLOR]

---

### Post by gen0 on 2008-10-27
Hi Eremit,

I can't help you with your problem, but could you describe the steps you took to get 'aticonfig --pplib-cmd "get fanspeed 0"' working?  I'm trying to do the same for my X1950 - not sure if just the card is unsupported or if I've done something wrong.

---

### Post by Eremit on 2008-10-29
I have this command from somewhere in the forum here. Of course you have to have the proprietary driver running.
Maybe your card just doesn't support reading out the fan speed?
Is temperature working?

I posted the issue in the lm-sensors mailing list and they didn't want to hear about the aticonfig tool because its proprietary software. They want to code it themselves as a kernel module/driver. So I guess it will take some time  until it's supported...

---

### Post by Cammy on 2008-10-29
Eremit, I suppose you could always use lm-sensors to display the temp on conky.

---

### Post by sirdiego on 2008-12-29
Hey Eremit, you got some news for this? I have the same problem and dont know how to read out temp with lm-sensors :/

---

### Post by Eremit on 2009-01-14
Sorry no news. I gave up a while ago... :\

---

### Post by Eremit on 2009-03-03
[COLOR="Silver"]Hi all,

I made a small applet in python. Please test it and give me feedback.
(I reused the icons from sensors-applet 2.2.1)[/COLOR]

[COLOR="Red"]Update[/COLOR]

This package is outdated and shouldn't/can't be used any more.

---

### Post by crypto178 on 2009-04-03
Your applet works fine, thank you :)

---

### Post by blacksm1th on 2009-04-21
> **Eremit said:**
> Hi all,

I made a small applet in python. Please test it and give me feedback.
(I reused the icons from sensors-applet 2.2.1)

Nice work. Thank you. Can you make it like "sensors-applet" with more visual options?
It's working with x64 Intrepid too :).
```
# getlibs -i python-gnome2-extras_2.19.1-0ubuntu11_i386.deb 
# getlibs -i atitemp_0.1.0-1_i386.deb 

```

---

### Post by bobo38_fr on 2009-07-17
Thanks for this applet... it looks pretty nice ! but I'm afraid it is not working on my config

I'm told that [french]"Erreur : Architecture « i386 » incorrecte"[/french]
which can be translated "Error : incorrect architecture i386"

for sure yes ! my config is 64 bits : could you precise your method, please ?

> # getlibs -i python-gnome2-extras_2.19.1-0ubuntu11_i386.deb 
# getlibs -i atitemp_0.1.0-1_i386.deb

thanks you so much !

---

### Post by bobo38_fr on 2009-07-17
Okay I've found getlibs !!
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
this forum is really full of treasures (k10temp install method, this homemade applet for ATI HD4850, and now informations about a software to run 32 bit with 64 bits !!)

install is done...
...but now I do not manage to launch the applet !

---

### Post by bobo38_fr on 2009-07-17
mmm... 

```
Installing libraries ...
```with nothing more does not mean "installation is successful"... atitempmain.py was not copied in /usr/bin directory. I used ```
sudo dpkg -i --force-architecture atitemp_0.1.0-1_i386.deb 
```
atitempmain.py is now at the right place but i'm afraid i do understand the way to use getlibs.:confused:

Blacksm1th, should you add some more informations about the way you installed atitemp .deb package on a 64 bits architecture ?

---

### Post by myk02k on 2009-10-04
Well, I hit a road block trying to install on Jaunty x64.  Here's what I tried:

-Downloaded "getlibs-all" & "atitemp_0.1.0-1_i386.deb" from recommended source.
-Did the following in a terminal:

# sudo apt-get install python-gnome2-extras
# sudo getlibs -i atitemp_0.1.0-1_i386.deb
# sudo apt-get install python2.5
# sudo dpkg -i --force-architecture atitemp_0.1.0-1_i386.deb

I added the ATI Temp panel applet and it only shows the GPU icon, but no temperatures.  Any ideas?

---

### Post by myk02k on 2009-10-07
aticonfig --adapter=0 --od-gettemperature
ERROR - ATI Overdrive(TM) is not supported on Adapter 0 - ATI Mobility Radeon HD 4500 Series

aticonfig --pplib-cmd "get fanspeed 0"
PPLIB command execution has failed!
ati_pplib_cmd: execute "get" failed!

---

### Post by myk02k on 2009-10-17
Is it possible that there is a 32 bit dependency that I am not meeting to get this applet running?

---

### Post by Ozsmoka on 2009-11-07
Hi found this thread at random, thanks for the code for getting sensor data for my 4870x2.

Like everyone here I'd love to find some way to display this info in my panel beside lm-sensors or with lm-sensors.

I'm using an x86 install of Karmic and tried to install with the .deb package. I got the error

"Error: Dependency is not satisfiable: python2.5-gnome2-extras"

Is there a repo I'm missing, or is this due to the fact that Karmic uses Gnome 2.28?

Thanks for sharing your app with us.

Cheers,

oz

---

### Post by rodgersan on 2009-12-12
The 2.2.5 release of gnome-sensors-applet brings aticonfig support. I couldn't make it work though. Compilation went fine without any error.

Has anyone succeeded in compiling with aticonfig?

Regards,

EDIT: It works now, I forgot to run the "sudo aticonfig --initial -f" command. However, fan speed isn't displayed.

---

### Post by Arlukin on 2009-12-16
> **rodgersan said:**
> The 2.2.5 release of gnome-sensors-applet brings aticonfig support. I couldn't make it work though. Compilation went fine without any error.
But you also had to update to GNOME 2.8 manually? Or was it possible to do in another way?

---

### Post by rodgersan on 2009-12-17
> **Arlukin said:**
> But you also had to update to GNOME 2.8 manually? Or was it possible to do in another way?

Hi, didn't need to update anything, I'm using Gnome 2.28 which is shipped with Karmic. Is that what you meant?

Regards,

---

### Post by Arlukin on 2009-12-18
> **rodgersan said:**
> Hi, didn't need to update anything, I'm using Gnome 2.28 which is shipped with Karmic. Is that what you meant?

Regards,
Strange, on the page [http://sensors-applet.sourceforge.net/index.php?content=requirements](http://sensors-applet.sourceforge.net/index.php?content=requirements) you can see that it requires "GNOME 2.8 desktop environment, with     GTK >=2.4.0 and libpanelapplet-2". And when I tried to compile it, the ./configure complained about the GTK version. Maybe you have the right GTK version, and the Gnome 2.8 wasn't really required?

---

### Post by rodgersan on 2009-12-18
> **Arlukin said:**
> Strange, on the page [http://sensors-applet.sourceforge.net/index.php?content=requirements](http://sensors-applet.sourceforge.net/index.php?content=requirements) you can see that it requires "GNOME 2.8 desktop environment, with     GTK >=2.4.0 and libpanelapplet-2". And when I tried to compile it, the ./configure complained about the GTK version. Maybe you have the right GTK version, and the Gnome 2.8 wasn't really required?

They really need to update their features page. I don't know what gtk version you need to compile it successfully but I'm pretty sure that it will compile fine with any gnome release from the 2.20.

Unfortunately, if you want to use the 2.2.5, you will need to compile it by yourself afaik.

Regards,

EDIT: If you are using Karmic (as stated in your profile), we have the same version (2.18). What is the terminal output?

---

### Post by Arlukin on 2009-12-19
> **rodgersan said:**
> They really need to update their features page. I don't know what gtk version you need to compile it successfully but I'm pretty sure that it will compile fine with any gnome release from the 2.20.

Unfortunately, if you want to use the 2.2.5, you will need to compile it by yourself afaik.

Regards,

EDIT: If you are using Karmic (as stated in your profile), we have the same version (2.18). What is the terminal output?
Hmm, my fault, their is no Gnome 2.8 just 2.28 so it was a typo on their web page. I probably just need to upgrade my gtk version. I kind of gave up when I saw that it was required to upgrade my Gnome version. Thanks for brining some sense into my head =)

---

### Post by rodgersan on 2009-12-19
> **Arlukin said:**
> Hmm, my fault, their is no Gnome 2.8 just 2.28 so it was a typo on their web page. I probably just need to upgrade my gtk version. I kind of gave up when I saw that it was required to upgrade my Gnome version. Thanks for brining some sense into my head =)

Are you sure that you need to update gtk? I hadn't to. Good luck anyway!

---

### Post by Arlukin on 2009-12-19
> **rodgersan said:**
> Are you sure that you need to update gtk? I hadn't to. Good luck anyway!
Ok, I admit it, I'm ******* noob. I didn't look at the error messages when running the ./configure, and I didn't use my head. Of course I forgot to install all the -dev packages. 

But now when they are installed the compile worked fine, and the applet showing me the ATI temp.

---

### Post by rodgersan on 2009-12-19
> **Arlukin said:**
> Ok, I admit it, I'm ******* noob. I didn't look at the error messages when running the ./configure, and I didn't use my head. Of course I forgot to install all the -dev packages. 

But now when they are installed the compile worked fine, and the applet showing me the ATI temp.

=D>\\:D/ (this one is funny)

---

### Post by Eremit on 2010-01-08
Hi all, sorry I didn't respond for so long.
I updated my relevant posts on the first thread page.
Please do not use my package any longer.

sensors-applet >2.2.5 can show the graphics card temperature now and it can be compiled and installed on karmic in a few seconds. I can give detailed instructions if someone needs it ;)

---

### Post by andrewthomas on 2010-04-01
> **Eremit said:**
> [COLOR=Red]Update[/COLOR]
Solution on karmic:

Uninstall "sensors-applet"
Get source for version >=2.2.5 ( [http://sensors-applet.sourceforge.net/index.php?content=source](http://sensors-applet.sourceforge.net/index.php?content=source) ).
Make sure aticonfig is working (see below).
Compile and install (one possibility is with "checkinstall").
The sensors-applet should now list you graphics card temperature.

By the way, it is now available in a debian package here:

[http://packages.debian.org/sid/sensors-applet](http://packages.debian.org/sid/sensors-applet)

---

### Post by andrek on 2010-07-31
I'm using sensors-applet 2.2.7 from debian sid on my Maverick system and it still doesn't show my ATI card ( mobility 4570 - dell studio 15 laptop ) temperature. This is the screenshot showing the list of sensors it detects :

[[img]http://j.imagehost.org/t/0694/sensors.jpg[/img]](http://j.imagehost.org/view/0694/sensors)

None of these is the right one - checked by aticonfig. ( which is fully working )
Any ideas?
[B]
edit[/B]

Ok, I compiled it from sources and now it shows aticonfig sensor! Hooray!
So, looks like the packages from both debian sid and ubuntu maverick don't show the aticonfig sensor at all. Maybe I should file a bug then?

---

### Post by andre_f on 2010-10-15
> **andrek said:**
> I'm using sensors-applet 2.2.7 from debian sid on my Maverick system and it still doesn't show my ATI card ( mobility 4570 - dell studio 15 laptop ) temperature. This is the screenshot showing the list of sensors it detects :

[[img]http://j.imagehost.org/t/0694/sensors.jpg[/img]](http://j.imagehost.org/view/0694/sensors)

None of these is the right one - checked by aticonfig. ( which is fully working )
Any ideas?
[B]
edit[/B]

Ok, I compiled it from sources and now it shows aticonfig sensor! Hooray!
So, looks like the packages from both debian sid and ubuntu maverick don't show the aticonfig sensor at all. Maybe I should file a bug then?

Hi everyone!

Thanks for the help andrek!! Finally it's working (Lucid 10.04)...I had to compile from the source (2.2.7).

:guitar:

---

