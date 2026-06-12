---
title: "another wine whine..."
date: 2005-11-04
forum: Desktop Environments
---

### Post by dr.drake on 2005-11-04
Wine really doesn't seem to want to work for me...
I first tried the install from   [this thread]("http://www.ubuntuforums.org/showthread.php?t=29996")  , but got stuck on the IE install which you need for further installs. so I had to abort and uninstall all I had done.  
it actually gave me a wine folder in Kmenu, but I can't open even the wine-configuration panel from there, altough I could for a while from the 'run command' by typing winecfg. 
I also had a folder on my desktop with 'my computer' showing all the windows options (windows, program files, etc.). but anyway, I couldn't get on so I deleted it all and I decided to just do it through synaptic.
I did the install, it seems installed, but there is nothing I can do with it, I tried a a very small working (according to the winehq-site) app called irfanview, but like with everything I try, I just get a dancing white square next to my pointer.
rightclicking exe's does give me the option 'wine windows emulator' but no action...

did anybody have similar experiences and solved them, or does anybody know a solution?

thanks, eric

---

### Post by aysiu on 2005-11-04
Is there any reason you don't like the wine in the repositories?

---

### Post by dr.drake on 2005-11-04
[QUOTE=aysiu]Is there any reason you don't like the wine in the repositories?[/QUOTE]

ehrm...

because it doesn't work?
(or at least: I haven't seen any proof of it yet)
could be that I messed up the wine in the repositories by trying that other instal, but don't know how to get rid of that anymore...

:( eric.

---

### Post by SickTwist on 2005-11-04
[QUOTE=dr.drake]Wine really doesn't seem to want to work for me...
I first tried the install from   [this thread]("http://www.ubuntuforums.org/showthread.php?t=29996")  , but got stuck on the IE install which you need for further installs. so I had to abort and uninstall all I had done.  
it actually gave me a wine folder in Kmenu, but I can't open even the wine-configuration panel from there, altough I could for a while from the 'run command' by typing winecfg. 
I also had a folder on my desktop with 'my computer' showing all the windows options (windows, program files, etc.). but anyway, I couldn't get on so I deleted it all and I decided to just do it through synaptic.
I did the install, it seems installed, but there is nothing I can do with it, I tried a a very small working (according to the winehq-site) app called irfanview, but like with everything I try, I just get a dancing white square next to my pointer.
rightclicking exe's does give me the option 'wine windows emulator' but no action...

did anybody have similar experiences and solved them, or does anybody know a solution?

thanks, eric[/QUOTE]

You're not alone. I avoided Wine for some time because of a less-than-stellar experience with it in the past. When the recent release of Wine 0.9 hit the news, I decided to give it another chance.

I've read documentation on Wine's site, searched the Ubuntu forums, and searched the Internet in an attempt to tame this beast--to no avail. Although I applaud Wine's developers for investing so much energy in the project, I just don't understand how people have success running programs with it. I've tried installing Corel Office 7, Mastercook Deluxe 6, and Print Shop Deluxe 6. Since all three of these programs have been around for almost 10 years, I figured at least one would work. However, the only thing these programs did was achieve varying degrees of failure. There is not even a clear way (that I have found) to diagnose *why* a program crashes. The only troubleshooting tip I have seen is to change the version of Windows that Wine reports.

I also have not been able to install Internet Explorer which I have heard is required by some programs. Are there other libraries/programs/fonts that Wine needs installed to make it run better--who knows? I have not seen a list anywhere.

If anybody in the forums has had some experience with setting up Wine, running programs, and/or troubleshooting crashes, your input is most welcome. Or if you know of any good (and current) "Wine Guides" on the Internet, that would be a great resource as well.

PS I realize that there are Linux alternatives to the programs that I tried installing with Wine. However, my interest in these programs is not personal. I have family members that are not willing to switch to Linux until their Windows apps of choice are supported. That is my reason for tinkering with Wine. *I* would rather avoid Windows programs--especially those that are not Free Software. :)

---

### Post by NemoTheLobster on 2005-11-04
[QUOTE=dr.drake]I tried a a very small working (according to the winehq-site) app called irfanview[/QUOTE]

Try XnView ([http://www.xnview.com/](http://www.xnview.com/)) for a decent irfanview replacement.

I've had mixed results with wine, but I'm always left disappointed.  I do use it for some of my kids games though.  Might have more success with Crossover Office or Cedega.

---

### Post by Zwack on 2005-11-04
Hmmm.... I'm using Wine with a few programs (Palace, Rocket librarian....) and it works fine for me...

I have 0.0.20050725-0ubuntu1 installed...   

I hope that this helps,

Z.

---

### Post by aysiu on 2005-11-04
[QUOTE=dr.drake]ehrm...

because it doesn't work?
(or at least: I haven't seen any proof of it yet)
could be that I messed up the wine in the repositories by trying that other instal, but don't know how to get rid of that anymore...

:( eric.[/QUOTE] Proof is that I use Wine for Filezilla just about every couple of days. Do you want to see [a screenshot](http://i22.photobucket.com/albums/b337/psychocats/7e3de071.png)? Will that convince you?

To install it with apt-get, just follow these instructions to get the right repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then type this in a terminal ```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by SickTwist on 2005-11-04
aysiu and zwack,
Did you change any of Wine's default settings (graphics, audio, Windows version, etc)?

aysiu,
How did you install Internet Explorer? What version of Wine do you have installed?

Please enlighten us :)

---

### Post by aysiu on 2005-11-04
[QUOTE=SickTwist]aysiu and zwack,
Did you change any of Wine's default settings (graphics, audio, Windows version, etc)?[/quote] No.

> 
aysiu,
How did you install Internet Explorer? What version of Wine do you have installed?

Please enlighten us :) I used ies4linux. It has a script that does everything for you. You need only wine and cabextract (both of which can be installed via Synaptic). Then, you click on the shell script, and ie6 is in /home/username/bin/ie6. I moved it, of course.

---

### Post by kvidell on 2005-11-04
Just last night actually, I built the WineX CVS...
Aside from being a very lengthy build, it's fine.

I haven't tried any games yet, but PuTTy works ;P
- K

---

### Post by SickTwist on 2005-11-04
Kevin, what is WineX--Cedega's fork of Wine? How does it differ? Where did you get the source? Thanks in advance! :)

---

### Post by Zwack on 2005-11-04
[QUOTE=SickTwist]aysiu and zwack,
Did you change any of Wine's default settings (graphics, audio, Windows version, etc)?

Please enlighten us :)[/QUOTE]

The relevant bits of my wine config... I had to change a couple of these to get Palace working... I've not bothered with sound, I can't remember if it is working or not... but it's irrelevant for the applications I use.

[Version]
"Windows" = "win98"
"DOS" = "6.22"
[x11drv]
"PerfectGraphics" = "N"
"ScreenDepth" = "24"
"Desktop" = "800x600"
"UseDGA" = "Y"
"UseXVidMode" = "Y"
"UseXRandR" = "Y"
"UseTakeFocus" = "Y"
"DXGrab" = "N"
"DesktopDoubleBuffered" = "Y"

I also had to install a couple of specific DLLs to get the apps to work properly...   But they are DLLs that I have had to install in windows for those apps.

I hope that this helps...

Z.

---

### Post by SickTwist on 2005-11-04
[QUOTE=aysiu]No.

 I used ies4linux. It has a script that does everything for you. You need only wine and cabextract (both of which can be installed via Synaptic). Then, you click on the shell script, and ie6 is in /home/username/bin/ie6. I moved it, of course.[/QUOTE]

I found and tried this script. It did mange to install IE but it keeps IE segregated from the default Wine directory (~/.wine). I wish I knew how the author of that script managed to get it to work because I still can't include IE with the other programs installed by Wine. The secret must be in the custom wine configuration files that are included with ies4linux.

---

### Post by SickTwist on 2005-11-04
[QUOTE=Zwack]The relevant bits of my wine config... I had to change a couple of these to get Palace working... I've not bothered with sound, I can't remember if it is working or not... but it's irrelevant for the applications I use.

[Version]
"Windows" = "win98"
"DOS" = "6.22"
[x11drv]
"PerfectGraphics" = "N"
"ScreenDepth" = "24"
"Desktop" = "800x600"
"UseDGA" = "Y"
"UseXVidMode" = "Y"
"UseXRandR" = "Y"
"UseTakeFocus" = "Y"
"DXGrab" = "N"
"DesktopDoubleBuffered" = "Y"

I also had to install a couple of specific DLLs to get the apps to work properly...   But they are DLLs that I have had to install in windows for those apps.

I hope that this helps...

Z.[/QUOTE]

In which file are these options? I see system.reg, userdef.reg, and user.reg in my ~/.wine directory. (I'm running Wine v0.9)

---

### Post by dcstar on 2005-11-04
[QUOTE=SickTwist]In which file are these options? I see system.reg, userdef.reg, and user.reg in my ~/.wine directory. (I'm running Wine v0.9)[/QUOTE]

"config"

---

### Post by dcstar on 2005-11-04
BTW, the latest version of **wine-config-sidenet** (1.9.0) works with Wine 0.90 and allows you to install IE6 on Breezy (I just did it myself!):

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by SickTwist on 2005-11-04
[QUOTE=dcstar]"config"[/QUOTE]

Please forgive my ignorance. Where is config? Do I have to create it? Is config still used in Wine 0.9?

jconte@kunto:~ $ ls -l .wine/
total 248
drwxr-xr-x  2 jconte jconte     96 2005-11-04 22:24 dosdevices
drwxr-xr-x  4 jconte jconte    104 2005-11-04 22:24 drive_c
-rw-r--r--  1 jconte jconte 230017 2005-11-04 22:25 system.reg
-rw-r--r--  1 jconte jconte   1622 2005-11-04 22:25 userdef.reg
-rw-r--r--  1 jconte jconte  16048 2005-11-04 22:25 user.reg
jconte@kunto:~ $

---

### Post by Zwack on 2005-11-05
~/.wine/config

Reading the Wine FAQ I found...

5.3. How do I configure Wine to run on my system?

As of Wine release 20050725 the config file has been disabled and the values are now stored instead in registry files in your .wine directory. The preferred method to configure Wine is with winecfg, winefcg is a tool to make it easy for new users to edit some of the contents of there registry files. 

So... It looks like the older changes that I made are now no longer being used...

I looked at the settings in winecfg and everything looks like defaults.  I checked my applications are still working...

Sorry I can't be more help...
Z.

---

### Post by dr.drake on 2005-11-06
[QUOTE=aysiu]Proof is that I use Wine for Filezilla just about every couple of days. Do you want to see [a screenshot](http://i22.photobucket.com/albums/b337/psychocats/7e3de071.png)? Will that convince you?
[/QUOTE]
I meant that on my computer I couldn't get it to work. I know of friends who have it working, just not with me, I needed proof on my computer.

[QUOTE=aysiu]To install it with apt-get, just follow these instructions to get the right repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then type this in a terminal ```
sudo apt-get update
sudo apt-get install wine
```[/QUOTE]
ofcourse I did that, it is actually the first part of the post I linked to.
in the mean time i did do the sidenet install kind of succesfully, although it still wont do all of the process.
anyway, I got wine working. kindof.
- IE kept crashing on me whenever a page using flash came up, and now just crashes.
- I got irfanview to work (mind you, I didn't need this programm, I just used it as a test program to test wine) and installed Image Composer (the MS version of photoshop/gimp) of which only a very limited number of functions work...
this was the program I really needed: I always use a combo of image composer and photoshop to make graphics for websites. I tried the gimp, but it is just not as user friendly...

rightnow I'm thinking of installing VMWare, so at least i will get a working version of IE to test my websites on,

thanks for everybody trying to help...

eric.

---

### Post by Zwack on 2005-11-06
[QUOTE=dr.drake]
rightnow I'm thinking of installing VMWare, so at least i will get a working version of IE to test my websites on,
[/QUOTE]

As an aside, wouldn't it be nice if everyone had followed standards and you didn't need to do this.  One browser would be enough (and maybe a text mode browser so that you can tell what it looks like for people using Lynx/Braille screen readers?)

Z.

---

