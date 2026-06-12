---
title: "Flash player settings dialog unclickable"
date: 2008-11-10
forum: Desktop Environments
---

### Post by jason_Xtreme on 2008-11-10
Each time I connect to a site with flash apps that want to access the allow/deny dialog flash freezes.
The actions still take place but flash becomes unclickable

Intrepid 32 bit
Lastest flash from repos

Any1 else has had this problem??
Any fixes??

---

### Post by ratmandall on 2008-11-12
> **jason_Xtreme said:**
> Each time I connect to a site with flash apps that want to access the allow/deny dialog flash freezes.
The actions still take place but flash becomes unclickable

Intrepid 32 bit
Lastest flash from repos

Any1 else has had this problem??
Any fixes??

Bump.

Same thing happens to me, same specs.

To test, Go to live.yahoo.com
Right click the video playing choose settings then see if you can click the pop up and change settings?

---

### Post by jason_Xtreme on 2008-11-23
not a fix more of a work around and i bet this is more comlplicated than needs be.
I install youplayer for firefox which then asked to adjust so flash settings through the adobe website.
i just set everything to disabled site i wasnt using mic/camera features anyway.
now the app loads ok.

---

### Post by PoHandle on 2008-12-04
I used jason_Xtreme's suggestion and was able to work around the problem.

To clarify:
I went to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html) to use Adobe's global settings manager.  On the flash dialog, I clicked on the Website Privacy Settings tab (the one that looks like a monitor with an eye on it), then clicked on the website that I wanted to allow usage of my hardware (in my case, [www.woome.com](www.woome.com)) and clicked always allow.

I agree that this is unnecessarily complicated.  I hope this is fixed with future updates.

---

### Post by olegueret on 2008-12-17
Right-clicking on the flash movie also gives me a disabled "Settings..." option. 

I've discovered that this is caused when the flash movie is set to be shown in windowless mode (wmode=opaque or wmode=transparent) in flash player 10. 

For example, youtube and vimeo videos have wmode=window and doesn't have this problem, but Metacafe uses wmode=transparent and settings option is not clickable.

I've already reported this bug to [Adobe]("https://bugs.adobe.com/jira/browse/FP-1211").

(tested in hardy - FF 3.0.4 and Opera 9.62, flash player 10, both adobe-flashplugin and official tar.gz from Adobe)


> **ratmandall said:**
> Bump.

Same thing happens to me, same specs.

To test, Go to live.yahoo.com
Right click the video playing choose settings then see if you can click the pop up and change settings?

---

### Post by shaolinchamp on 2009-01-09
yeah, i only run into to the dialog on sites like saphrachat.

---

### Post by fluocantus on 2009-01-17
When I go into the settings I can't change anything. I can't change any tabs nor can I confirm or cancel any changes (like with how much data flash can store)

---

### Post by itisbasi on 2009-03-01
I have this problem only on megavideo.com and supernovatube. The settings dialog is enabled in youtube though....I can't figure out why... it's the same adobe flash player 10 running in all these sites...!!!

---

### Post by binbash on 2009-03-01
same issue here

---

### Post by pierre.fr34 on 2009-03-08
> **olegueret said:**
> Right-clicking on the flash movie also gives me a disabled "Settings..." option. 

I've discovered that this is caused when the flash movie is set to be shown in windowless mode (wmode=opaque or wmode=transparent) in flash player 10. 

For example, youtube and vimeo videos have wmode=window and doesn't have this problem, but Metacafe uses wmode=transparent and settings option is not clickable.

I've already reported this bug to [Adobe]("https://bugs.adobe.com/jira/browse/FP-1211").

(tested in hardy - FF 3.0.4 and Opera 9.62, flash player 10, both adobe-flashplugin and official tar.gz from Adobe)

Same problem for me.

Adobe doesn't seem to be very reactive on this. Their answer is completely useless ( [[COLOR="Blue"]_see here_[/COLOR]]("http://www.adobe.com/devnet/flashplayer/articles/fplayer10_security_changes_02.html#head35") ) ! Why is Linux the only affected OS ??:-?

---

### Post by psmaster on 2009-03-12
I have the same problem. I have only tried it in stickam and Hulu so far, Hulu works, Stickam does not

---

### Post by hobo343 on 2009-05-13
> **pierre.fr34 said:**
> Same problem for me.

Adobe doesn't seem to be very reactive on this. Their answer is completely useless ( [[COLOR=Blue]_see here_[/COLOR]]("http://www.adobe.com/devnet/flashplayer/articles/fplayer10_security_changes_02.html#head35") ) ! Why is Linux the only affected OS ??:-?


well their answer is somewhat useful but geared more for the developer of your favorite site not the end user. i tried chan ging the <embed> tag's wmode parameter from transparent to window like they tell you to (i used firebug while looking at the page) but still didn't work for me on namemytune.com. so simple yet so annoying...

---

### Post by diazamet on 2009-05-19
Flash will read some settings from a file.

I found that setting the option:
[INDENT]
[FONT="Courier New"]WindowlessDisable=true[/FONT][/INDENT]

in the file:

[INDENT][FONT="Courier New"]/etc/adobe/mms.cfg[/FONT][/INDENT]

Allows me to use my webcam on UStream.

---

### Post by mag1 on 2009-05-21
> **diazamet said:**
> 
I tried that and restarted my browser, didn't work for me, though i didn't have an adobe folder or mms.cfg in etc and made it myself so that may be the problem, i did a search but didn't find it elsewhere?

---

### Post by mag1 on 2009-05-31
This seems like a pretty silly artificially created problem by the flash devs from what i've read, it needs fixing!

---

### Post by pete on 2009-06-25
[LIST=1]
[*]Go to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html")

[*]Go to the Website Privacy Settings tab (it's the one that looks like a monitor with an eye on it) in the little Flash applet.  
[*]Scroll down the Visited Websites list until you find [www.ustream.tv](www.ustream.tv).
[*]select that line.
[*]change the privacy setting to "Always allow".
[/LIST]

From that point forward, ustream should work fine with your webcam and mic.  Unfortunately, the Linux implementation of Flash is apparently incapable of prompting you for access like the Windows and Mac version do.  **Be warned, though--**you will have just made it so you will *never* get prompted, and any time you go to the Ustream site, it will automatically have access to your webcam/mic.

---

### Post by frazerr on 2009-10-18
> **pete said:**
> [LIST=1]
[*]Go to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html")

[*]Go to the Website Privacy Settings tab (it's the one that looks like a monitor with an eye on it) in the little Flash applet.  
[*]change the privacy setting to "Always allow".
[/LIST]

From that point forward, ustream should work fine with your webcam and mic.

Thanks pete, that worked to see my webcam,
but now I cant hear any sound from flash and clicking on setting just freezes flash.  any ideas what to do?

---

### Post by gux2k3 on 2009-12-11
Hi, I have the same problem and found the issue

I have cursor fx installed, I noticed some behaviour issues with the click, like I have to triple click an icon on the desktop (first focus an then doubleclick) when I disabled it the problem was gone.

If you dont have cursorfx I recommend you disabling ANY software that may be involved with the cursor behavior . In have also ubuntu but havent tried, but my best guess maybe a beryl module involving the cursor or the window is the source

My specs

Windows 7 32bits
dual boot ubuntu
Opera 9.64
IE 8
google chrome 3.0.195
firefox
all browsers gave the same results

hope this helps

---

### Post by fchx on 2009-12-12
I have the same issue.

If I turn off gnome-do the problem dissapears and I can click in the preferences.

---

### Post by chenxiaolong on 2009-12-12
That is a bug in the Ubuntu packaged version of Flash. You will have to uninstall "flashplugin-nonfree" and "flashplugin-installer" and download the flash player from Adobe.

x32 edition:[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

x64 edition: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Then, you will have to extract the tar.gz file and copy "libflashplayer.so" to "~/.mozilla/plugins".

Then enjoy your working Flash!!

---

### Post by ethanay on 2010-02-17
> **chenxiaolong said:**
> That is a bug in the Ubuntu packaged version of Flash. You will have to uninstall "flashplugin-nonfree" and "flashplugin-installer" and download the flash player from Adobe.

x32 edition:[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

x64 edition: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Then, you will have to extract the tar.gz file and copy "libflashplayer.so" to "~/.mozilla/plugins".

Then enjoy your working Flash!!

Tried that.  Didn't resolve anything.

---

### Post by xifer on 2010-03-14
> **diazamet said:**
> Flash will read some settings from a file.

I found that setting the option:[INDENT]
[FONT=Courier New]WindowlessDisable=true[/FONT][/INDENT]in the file:
[INDENT][FONT=Courier New]/etc/adobe/mms.cfg[/FONT][/INDENT]Allows me to use my webcam on UStream.


Excellent - thanks for that - it worked for me.  flash still doesn't find my camera but it's a step in the right direction!

---

### Post by dumpa on 2010-03-16
> **fchx said:**
> I have the same issue.

If I turn off gnome-do the problem dissapears and I can click in the preferences.

Same problem, it becomes clickable after turning off gnome-do

---

### Post by arbosis on 2010-03-17
Not working for me, sites like chatrolling are still unusable. (I already selected it as always in the macromedia settings manager site).


Using chromium and arora on Kubuntu 9.10

---

### Post by xifer on 2010-03-18
try adding this other parameter to /etc/adobe/mms.cfg

AVHardwareDisable=false

and running firefox like this

```

 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

```

---

### Post by gyurman on 2010-04-13
I don't have 
/etc/adobe/mms.cfg
Why? Shell I make it?

---

### Post by xifer on 2010-04-13
> **gyurman said:**
> I don't have 
/etc/adobe/mms.cfg
Why? Shell I make it?


Why - because most installations shouldn't need the file.

Yes - create it yourself - those settings certainly helped me out.

---

### Post by chokas on 2010-04-22
> **fchx said:**
> I have the same issue.

If I turn off gnome-do the problem dissapears and I can click in the preferences.

Lol, this worked for me, now I remember why I dont't like docks

Thanks FCHX

---

### Post by Zenmij on 2010-05-05
Just want to add that:

Using the Web panel settings on the Adobe site, along with;
Disabling my windows manager/effects,

worked for me.


Thanks.

---

### Post by throneless on 2010-09-19
The solution that worked for _me_ (i'm on ubuntu 10.04 / flash player 10):

1- Get a video on megavideo.com

2- when the video start playing right click on it and the settings button will be clickable again.

3- Change what you need to change (for me it was 'disabling the hardware acceleration" option).

4- Now your settings are set for all the videos that require flash player.

---

### Post by ayanamist on 2011-12-08
I'm suffering the same problem on Firefox and Google-Chrome (not Chromium)
I'm using Ubuntu 11.10 w/o Gnome-Do, i nearly use default settings come with installation.
I'm a newbie and don't know how to turn off window manager or window effects.
Can someone post details?

---

### Post by someitalian123 on 2012-01-07
I have the same problem on 11.10, I don't remember having this problem on 10.10.

Edit: Just logged out and tried the flash settings while in unity 2d and I didn't have the problem. whatever the problem is it's a problem with unity 3d.

---

### Post by Stray Wolf on 2012-01-12
I use the betterprivacy addon for firefox which doesn't allow the storing of LSO's such as flash settings so it would be really convenient for the dialog to be clickable. For now, I have to right click>select global settings>select website privacy>select allow>reload page>re-sign in...just clicking allow would be waaaaay easier.

---

### Post by Sir Noob on 2012-01-18
> **someitalian123 said:**
> I have the same problem on 11.10, I don't remember having this problem on 10.10.

Edit: Just logged out and tried the flash settings while in unity 2d and I didn't have the problem. whatever the problem is it's a problem with unity 3d.

This worked for me.

---

### Post by Stray Wolf on 2012-01-25
> **xifer said:**
> Why - because most installations shouldn't need the file.

Yes - create it yourself - those settings certainly helped me out.
 
Create it? Out of a what? I'd like to get this fixed too.

---

### Post by tomdkat on 2012-01-26
> **someitalian123 said:**
> Edit: Just logged out and tried the flash settings while in unity 2d and I didn't have the problem. whatever the problem is it's a problem with unity 3d.How did you access the flash settings while in Unity 2D?  I'm also running Ubuntu 11.10 (64-bit) and when I right-click on a Flash video in Firefox 9, I get a context menu with "Settings" (which I can't click), "Global Settings" (which takes me to a page on Adobe's website), and "About Adobe Flash Player..." (which takes me to the page which displays the current Flash player version info).

Thanks!

Peace...

---

### Post by hanzj on 2012-02-04
> **Stray Wolf said:**
> I use the betterprivacy addon for firefox which doesn't allow the storing of LSO's such as flash settings so it would be really convenient for the dialog to be clickable. For now, I have to right click>select global settings>select website privacy>select allow>reload page>re-sign in...just clicking allow would be waaaaay easier.

I did "right cick > select Global Settings" but I don't know how to do "Select Website Privacy" because I don't see "Website Privacy."

I'm using Adobe Flash Player version  11.1.102.55.

UPDATE: I think you're giving instructions for the Firefox plugin "betterprivacy". I am using Chrome 16.0.912.77. I'm trying to click on the Flash Player Settings dialog that pops up on [http://armorgames.com/play/12009/the-last-stand-union-city](http://armorgames.com/play/12009/the-last-stand-union-city).

---

### Post by jalmado on 2012-03-10
I found a solution: I was using google chrome in ubuntu linux and I installed a chrome extension called "Flashcontrol". Now the adobe flash player settings window doesn't appear anymore.

---

### Post by hanzj on 2012-03-12
thanks. will try this "FlashControl" when the need arises.

---

### Post by hanzj on 2012-05-01
FlashControl doesn't seem to do the job. It can block the Flash application completely, but I want to still allow the Flash app but just block the question that pops up.

---

### Post by linuxuser12345 on 2012-05-07
<Deleted by poster>

---

### Post by linuxuser12345 on 2012-05-07
Here we go... The bug re-appears in 12.04! This NEEDS to be fixed, and if Adobe isn't going to fix it, Google should, at the least!
Anyways, I submitted a bug report here:
[https://bugs.launchpad.net/arora/+bug/995699](https://bugs.launchpad.net/arora/+bug/995699)



Please help us all out and contribute to the bug report. Thanks :)
If you are running Google Chrome or Chromium, please go to your global menu, Help < Report an Issue. This makes Google aware of the problem, as well. Google will be a crucial key in getting this problem FINALLY fixed, as they distribute Flash Player to the masses as well, using the Google Chrome web browser, which is Flash-integrated.

---

### Post by someitalian123 on 2012-05-21
The problem has returned for me in 12.04, now it doesn't even work in unity 2d anymore.

---

### Post by melitz on 2012-05-27
> **someitalian123 said:**
> I have the same problem on 11.10, I don't remember having this problem on 10.10.

Edit: Just logged out and tried the flash settings while in unity 2d and I didn't have the problem. whatever the problem is it's a problem with unity 3d.

This worked for me too!! Running Ubuntu 12.04 x64 :-)

---

### Post by marianoa on 2012-12-05
Hi,

I had the same problem (flashplayer settings window unclickable) with Unity on Quatal for englishcentral.com.
I solved it going to this Adobe page

[http://www.macromedia.com/support/documentation/it/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/it/flashplayer/help/settings_manager06.html)

where I've been able to choose the settings I needed for the specifc website
(there's a list of the browsed websites and you can select the setting for each website). Then I reloaded the page on englishcentral.com and it works.

Hope this helps (and that I'm not repeating something that's already known)!

---

