---
title: "flash fullscreen glitches"
date: 2011-05-29
forum: Desktop Environments
---

### Post by 13east on 2011-05-29
machine: thinkpad edge14 kubuntu 11.04 x64 w/ firefox flash64 and java6

1. when launching fullscreen flash videos, the video will be placed on the background and the main window has to be minimized to view the video (this glitch can be replicated on windows7x64 as well so I'm assuming this is either flash or firefox problem)

2. related to problem #1; the first problem wouldn't be too much of a trouble if minimizing the window worked all the time; sometimes the flash video doesn't get redrawn into fullscreen; I click the fullscreen button, the video freezes but audio continues, minimize window and nothing happens, restore original window and the video continues in the embedded player; sometimes have to click the fullscreen quite a few times for it to actually be redrawn to fullscreen

3. related to problem #1; when minimizing the main window to view the fullscreen video in the background, the taskbar remains in view and doesn't get transposed by the video (problem for sites like megavideo where the video seekbar is at the bottom of the screen and cannot be accessed due to the protruding taskbar; temporary fix is to switch the taskbar visibility settings from "always visible" to "windows can cover")

4. and lastly, when launching a flash video to fullscreen the screen completely blackens (sometimes w/ audio and sometimes w/out) and the entire desktop environment is inaccessible; pressing "Esc" doesn't dismiss the new black screen, cannot "Alt + Tab" to running process in the background and no shortcuts work anymore (force logout doesn't work, menu launch shortcut doesn't work); only thing that works is hard shutdown by holding the power button down for five+ seconds. This glitch has occurred quite a few time and is not a one-off error.

I've only seen the first problem occur when I was running Ubuntu 11.04x64 and only started seeing the other glitches after the fresh installation of Kubuntu 11.04x64.

Majority of my time on the computer is online surfing and watching videos so this is a big problem, especially the last one where any unsaved data is lost when I have to do a hard shutdown.

If anyone knows how to fix any of these problems, I would very much appreciate your help.

Thank You.

---

### Post by ivanovnegro on 2011-05-29
I could recommend you the Flash Aid addon for Firefox but unfortunateley it did not solve my problem this time with the freeze of the system on Kubuntu 11.04 watching a full screen video. This to me seems a bug in Kubuntu/KDE also on 32bit as on Xubuntu it runs perfectly.
I noticed this to be one of the major issues on KDE 11.04 because for me its the best KDE release ever of Ubuntu.
Maybe Lovinglinux (creator of Flash Aid and Firefox expert) could help with a workaround, your not the first with this issue.

---

### Post by lovinglinux on 2011-05-29
How did you install flash?

The problem with the fullscreen video being drawn in the background also happens to me, but only on particular web sites. So I think is probably due to how the web site implements flash.

---

### Post by 13east on 2011-05-29
> **ivanovnegro said:**
> I could recommend you the Flash Aid addon for Firefox but unfortunateley it did not solve my problem this time with the freeze of the system on Kubuntu 11.04 watching a full screen video. This to me seems a bug in Kubuntu/KDE also on 32bit as on Xubuntu it runs perfectly.
I noticed this to be one of the major issues on KDE 11.04 because for me its the best KDE release ever of Ubuntu.
Maybe Lovinglinux (creator of Flash Aid and Firefox expert) could help with a workaround, your not the first with this issue.

-will try the flash aid and report back on the results; question: i have flash64 installed, when using the beta flash installation from adobe labs will it remove x64 flash and install x86 version instead?

-I've been an exclusive gnome user for 5+ years; wanted to try the slick interface of KDE, only switched to Kubuntu less than a week ago, I like it so far and would like to explore it further; all other of my complains are minor compared to the last one about flash crashing my system, this is a very major issue that i hope gets resolved soon or I might have to give up on KDE before I get started.  


> **lovinglinux said:**
> How did you install flash?

The problem with the fullscreen video being drawn in the background also happens to me, but only on particular web sites. So I think is probably due to how the web site implements flash.

I used this ubuntu community guide to run flash64 and java6 with [[COLOR="Red"]sevenmachines ppa[/COLOR]]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") for flash installation.

---

### Post by lovinglinux on 2011-05-29
> **13east said:**
> -will try the flash aid and report back on the results; question: i have flash64 installed, when using the beta flash installation from adobe labs will it remove x64 flash and install x86 version instead?

-I've been an exclusive gnome user for 5+ years; wanted to try the slick interface of KDE, only switched to Kubuntu less than a week ago, I like it so far and would like to explore it further; all other of my complains are minor compared to the last one about flash crashing my system, this is a very major issue that i hope gets resolved soon or I might have to give up on KDE before I get started.  




I used this ubuntu community guide to run flash64 and java6 with [[COLOR="Red"]sevenmachines ppa[/COLOR]]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") for flash installation.

Disable the sevenmachines ppa and remove the flashplugin installed by it before running Flash-Aid.

---

### Post by ivanovnegro on 2011-05-29
> **13east said:**
> -will try the flash aid and report back on the results; question: i have flash64 installed, when using the beta flash installation from adobe labs will it remove x64 flash and install x86 version instead?


It will install the appropriate version for your system, so that would be x64.

---

### Post by lovinglinux on 2011-05-29
Before running flash-aid, do this:

```
sudo apt-get purge flashplugin64-installer
```

I will add this to a future version of Flash-Aid.

---

### Post by 13east on 2011-05-29
> **lovinglinux said:**
> Before running flash-aid, do this:

```
sudo apt-get purge flashplugin64-installer
```

I will add this to a future version of Flash-Aid.

> **lovinglinux said:**
> Disable the sevenmachines ppa and remove the flashplugin installed by it before running Flash-Aid.

-disabled sevenmachines ppa and removed the plugin installed by it
-ran flash-aid and installed flashplayer64 thorough the script

-still seeing issues w/ fullscreen video playback like needing to manually minimize firefox window to view fullscreen video, refusing to go to fullscreen and not covering the taskbar when going to fullscreen; not seeing the black screen which crashes the desktop environment as of yet.  Are these issues just a prevalent bug that are yet to be resolved or is there anything else I can do on my machine to fix it?

-also, will the flash plugin update normally through kubuntu update manager or do I need the flash-aid plugin installed to receive flash upgrades?

Any help you could provide with this issue would be very much appreciated.
Thank you.

---

### Post by schnelle on 2011-05-30
You can try with disabling hardware acceleration in flash. Play any video on youtube, right mouse click on it and go to settings. Then uncheck "enable hardware acceleration".
Also you can try with unchecking "suspend desktop effects for fullscreen windows" in SystemSettings>Desktop effects>Advanced tab.

---

### Post by lovinglinux on 2011-05-30
> **13east said:**
> -also, will the flash plugin update normally through kubuntu update manager or do I need the flash-aid plugin installed to receive flash upgrades?

When installed, Flash-Aid has a feature that checks for new flash versions from Adobe Labs once a day. However, it only alerts you about the new version. You still need to run the Wizard to install the update.

---

### Post by Zorael on 2011-05-30
> **13east said:**
> 1. when launching fullscreen flash videos, the video will be placed on the background and the main window has to be minimized to view the video (this glitch can be replicated on windows7x64 as well so I'm assuming this is either flash or firefox problem)
This is KWin's focus stealing prevention being a bit aggressive. I thought this only happened with Chromium, however. You say it happens with Firefox too?

You can make a window rule to fix this problem. I've been preparing a patch to suggest to the Kubuntu guys for inclusion into the **kde-window-manager** package that would install this rule by default, but I'm still polishing it. As it is right now, *it probably only works with the native 32-bit and native 64-bit Flash*, and I probably only get access to a 64-bit machine at Wednesday at the earliest.

> [list=1][*]System Settings -> Window Behavior -> Window Rules -> New...
[*]Window tab
[indent]Description: **Disable focus stealing prevention for fullscreen Flash plugin** (or similar)
Window class (application type): **exe**
Match: **Exact match**[/indent]
[*]Window Extra tab
[indent]Window title: **exe**
Match: **Exact match**[/indent]
[*]Workarounds tab
[indent]Focus Stealing Prevention: **check**
[list][*]**force**
[*]**none**[/list][/indent]
[*]OK
[*]Apply[/list]

Since the repository Flash plugin is the 32-bit plugin wrapped in [NSPluginWrapper](http://en.wikipedia.org/wiki/NSPluginWrapper) to work in 64-bit browsers, the window title and window class is probably **npviewer.bin** instead of **exe**. If the above doesn't work, try changing it to that. The final catch-all rule should probably have a value like **exe|npviewer.bin** in both the Window title and Window class fields, with their accompanying Match settings set to **Regular Expression**.

You can get the needed information by entering the following a terminal, then hopping to a browser and start some Flash content in fullscreen, and finally click the Flash content when the cursor changes after 10 seconds.
```
$ sleep 10; xwininfo
```
The terminal output should list the window information KWin needs to match the rule with the window.

A properly set up rule should hopefully help your other points 2, 3 and 4, too.

---

### Post by lovinglinux on 2011-05-30
> **Zorael said:**
> This is KWin's focus stealing prevention being a bit aggressive. I thought this only happened with Chromium, however. You say it happens with Firefox too?

You can make a window rule to fix this problem. I've been preparing a patch to suggest to the Kubuntu guys for inclusion into the **kde-window-manager** package that would install this rule by default, but I'm still polishing it. As it is right now, *it probably only works with the native 32-bit and native 64-bit Flash*, and I probably only get access to a 64-bit machine at Wednesday at the earliest.



Since the repository Flash plugin is the 32-bit plugin wrapped in [NSPluginWrapper](http://en.wikipedia.org/wiki/NSPluginWrapper) to work in 64-bit browsers, the window title and window class is probably **npviewer.bin** instead of **exe**. If the above doesn't work, try changing it to that. The final catch-all rule should probably have a value like **exe|npviewer.bin** in both the Window title and Window class fields, with their accompanying Match settings set to **Regular Expression**.

You can get the needed information by entering the following a terminal, then hopping to a browser and start some Flash content in fullscreen, and finally click the Flash content when the cursor changes after 10 seconds.
```
$ sleep 10; xwininfo
```
The terminal output should list the window information KWin needs to match the rule with the window.

A properly set up rule should hopefully help your other points 2, 3 and 4, too.

Thanks for sharing. I have included a link to your post in my tutorials, in the [flash issues & solutions]("http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions") section. This will be probably useful for many KDE users.

---

### Post by 13east on 2011-05-30
@lovinglinux:

I had to do a fresh installation of Kubuntu 11.04x64 on my machine last night because I wanted to remove Nepomuk but it also removed few other key programs that depended on it and the OS wouldn't load anymore.

Now, trying to reinstall flash64 w/ Flash-Aid but I'm having no success w/ the extension.  I've tried install flash-aid from both mozilla website and your website but with the same results multiple times. I run wizard mode to install from adobe labs, script runs successfully and gives me a message that installation is complete and to restart firefox.  Once I restart and go to youtube, get a message that no compatible plugin found; run the wizard again and there is no option to remove old version of plugin from my system and get the same outcome no matter how many times I run the extension or even if I reboot the computer completely.  

I've tried manually downloading the file from adobe website and running it under Advanced Mode but with no luck their either.

Copy of terminal script to be executed:
> #!/bin/bash

cd "/home/sanish/.mozilla/firefox/febeprof.muntou/extensions/flashaid@lovinglinux.megabyet.net/chrome/content/tmp" && rm -f *flash* && wget [http://updates.webgapps.org/flashplayer64](http://updates.webgapps.org/flashplayer64) && tar xvf *flash* libflashplayer.so && sudo chown root:root libflashplayer.so && sudo chmod 0644 libflashplayer.so && sudo mv libflashplayer.so /usr/lib/mozilla/plugins/ && rm -f *flash* && sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'OverrideGPUValidation')
if test -z "${TWEAK}";then
echo 'OverrideGPUValidation=true' | sudo tee -a /etc/adobe/mms.cfg
fi
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg

Copy of Generated Report from Flash-Aid:
> Ubuntu Architecture

Linux nix-edge14 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox						install
firefox-kde-support				install
kubuntu-firefox-installer			install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

Plugin locations



Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
skypebuttons.so:$
/usr/lib/mozilla/plugins/skypebuttons.so:$
:$
1302471138000:1:1:$
Mime Type x-skype for Skype Buttons:$
Skype Buttons for Kopete:$
1
0:application/x-skype:Skype Buttons::$

[INVALID]


---

### Post by lovinglinux on 2011-05-30
> **13east said:**
> @lovinglinux:

I had to do a fresh installation of Kubuntu 11.04x64 on my machine last night because I wanted to remove Nepomuk but it also removed few other key programs that depended on it and the OS wouldn't load anymore.

Now, trying to reinstall flash64 w/ Flash-Aid but I'm having no success w/ the extension.  I've tried install flash-aid from both mozilla website and your website but with the same results multiple times. I run wizard mode to install from adobe labs, script runs successfully and gives me a message that installation is complete and to restart firefox.  Once I restart and go to youtube, get a message that no compatible plugin found; run the wizard again and there is no option to remove old version of plugin from my system and get the same outcome no matter how many times I run the extension or even if I reboot the computer completely.  

I've tried manually downloading the file from adobe website and running it under Advanced Mode but with no luck their either.

Copy of terminal script to be executed:


Copy of Generated Report from Flash-Aid:

Run the wizard again, but instead of executing the script, use the export function. Then attach the exported script to your post so I can see if there is something wrong with it. The script will be located in your Desktop.

---

### Post by 13east on 2011-05-30
> **lovinglinux said:**
> Run the wizard again, but instead of executing the script, use the export function. Then attach the exported script to your post so I can see if there is something wrong with it. The script will be located in your Desktop.

Exported Script attached:

---

### Post by lovinglinux on 2011-05-30
> **13east said:**
> Exported Script attached:

There is nothing wrong with the script.

Please run it, copy and paste the entire terminal output here.

---

### Post by 13east on 2011-05-30
> **lovinglinux said:**
> There is nothing wrong with the script.

Please run it, copy and paste the entire terminal output here.

The only difference I can remember from the old installation was that "OverrideGPUValidation=true" was stated twice at the end of the terminal read-out yesterday as opposed to only once here.

Terminal Output:
> ***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
--2011-05-30 16:48:32--  [http://updates.webgapps.org/flashplayer64](http://updates.webgapps.org/flashplayer64)
Resolving updates.webgapps.org... 209.190.61.7
Connecting to updates.webgapps.org|209.190.61.7|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz) [following]
--2011-05-30 16:48:33--  [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)
Resolving download.macromedia.com... 23.0.19.191
Connecting to download.macromedia.com|23.0.19.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4310219 (4.1M) [application/x-gzip]
Saving to: `flashplayer64'

55% [===================================================================================>                                                                     ] 2,383,611   18.9K/s  eta 19s     ^55% [===================================================================================>                                                                     ] 2,387,931   18.9K/s  eta 19s     ^55% [===================================================================================>                                                                     ] 2,392,251   19.0K/s  eta 19s     ^100%[========================================================================================================================================================>] 4,310,219    328K/s   in 34s     

2011-05-30 16:49:07 (123 KB/s) - `flashplayer64' saved [4310219/4310219]

libflashplayer.so
[sudo] password for sanish: 
Sorry, try again.
[sudo] password for sanish: 
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************


---

### Post by 13east on 2011-05-30
> **13east said:**
> The only difference I can remember from the old installation was that "OverrideGPUValidation=true" was stated twice at the end of the terminal read-out yesterday as opposed to only once here.

Terminal Output:

I don't know how to explain it but now the installation seems to have executed correctly; I can view flash videos at youtube, megavideo and other websites with no problem.

I'm also not seeing any of the original glitches that I was complaining about following lovinglinux and schnelle advices to turn off hardware acceleration and disabling the suspension of desktop effects for fullscreen apps.

@Zorael:

Will try your suggestion to stop the focus stealing prevention.  Although there is already a rule in there to stop focus stealing prevention for XV windows (Description: (Default) Disable focus stealing prevention for XV / Window Class: ^xv .*), although it doesn't seem to be doing anything to stop the earlier glitches or to disable focus stealing as it was useless for running pokerstars under wine.

p.s. @ lovinglinux: thx for your prompt and very helpful advices; saved me a lot of headache.

---

### Post by Zorael on 2011-05-30
> **13east said:**
> Although there is already a rule in there to stop focus stealing prevention for XV windows (Description: (Default) Disable focus stealing prevention for XV / Window Class: ^xv .*), although it doesn't seem to be doing anything to stop the earlier glitches or to disable focus stealing as it was useless for running pokerstars under wine.
That xv one is doing the same thing this new one would do, except for [video content](http://en.wikipedia.org/wiki/X_video_extension). It just needs a Flashy friend.

---

### Post by 13east on 2011-05-30
> **Zorael said:**
> That xv one is doing the same thing this new one would do, except for [video content](http://en.wikipedia.org/wiki/X_video_extension). It just needs a Flashy friend.

So do you recommend I keep XV enabled along w/ your protocol rules?  Right now I have it disabled.

Also, do you where the online instructions are for windows/application configure settings so as that my earlier 1-4 complains don't reappear?  I've used it to tweak Dolphin, Konsole, and Wine settings, I really like how it works and would like to configure it for other applications as well.

Thx.

---

### Post by lovinglinux on 2011-05-30
> **13east said:**
> I don't know how to explain it but now the installation seems to have executed correctly; I can view flash videos at youtube, megavideo and other websites with no problem.

I'm also not seeing any of the original glitches that I was complaining about following lovinglinux and schnelle advices to turn off hardware acceleration and disabling the suspension of desktop effects for fullscreen apps.

@Zorael:

Will try your suggestion to stop the focus stealing prevention.  Although there is already a rule in there to stop focus stealing prevention for XV windows (Description: (Default) Disable focus stealing prevention for XV / Window Class: ^xv .*), although it doesn't seem to be doing anything to stop the earlier glitches or to disable focus stealing as it was useless for running pokerstars under wine.

p.s. @ lovinglinux: thx for your prompt and very helpful advices; saved me a lot of headache.

You are welcome.

---

### Post by Zorael on 2011-05-30
> **13east said:**
> So do you recommend I keep XV enabled along w/ your protocol rules?  Right now I have it disabled.
I guess it's safe to disable it, but if you ever find that video ends up in the background of other windows much like Flash is doing here, just remember that the rule is still there to reactivate.

> **13east said:**
> Also, do you where the online instructions are for windows/application configure settings so as that my earlier 1-4 complains don't reappear?  I've used it to tweak Dolphin, Konsole, and Wine settings, I really like how it works and would like to configure it for other applications as well.
I *think* it's all one and the same issue. KWin and Flash neither really know where focus should go so Flash either ends up maximized properly, maximized but with the panel in front, not at all, or into some midway broken state where nothing really makes sense.

If there are any guides to writing these window rules, I don't know of them. I just played around, mostly adding rules to make stuff skipping the task manager. I don't need Skype, Konversation or Kopete entries in the task manager when I have perfectly good system tray icons to use. :>

---

### Post by digbysellers on 2011-06-07
Mint 10.10, Gnome: 

"suspend desktop effects for fullscreen windows"

Any idea if a similar setting exists in Gnome? - Perhaps one just has to disable compiz. Otherwise for Gnome it's either compiz or fullscreen flash video (maybe)? Sometimes I wonder if avoiding M$ is worth all the bother...

---

### Post by 13east on 2011-06-07
> **digbysellers said:**
> Mint 10.10, Gnome: 

"suspend desktop effects for fullscreen windows"

Any idea if a similar setting exists in Gnome? - Perhaps one just has to disable compiz. Otherwise for Gnome it's either compiz or fullscreen flash video (maybe)? Sometimes I wonder if avoiding M$ is worth all the bother...

I only have 1 machine w/ kubuntu 11.04 and no gnome installations so I can't test this out but you can try these two suggestion posted on other websites:
1) [YouTube video]("http://www.youtube.com/watch?v=SeO8YytqEKE&feature=related")

2) [LinuxMint Website]("http://community.linuxmint.com/idea/view/1465") = you can try remoulder's suggestion to install fusion-icon to turn compiz on and off as needed from the sys-tray

---

### Post by Mr_Bumpy on 2011-06-21
One way I have previously dealt with Flash videos opening behind the browser in KDE is to assign the "Lower" action to the middle mouse button in System Settings -> Window Behavior -> Window Behavior -> Titlebar Actions.

Now if Flash opens fullscreen behind the browser, I can simply middle-click on the browser's titlebar to lower the browser behind the flash content.  This seems to work much better than trying to minimize the browser (which often takes the fullscreen flash video with it).

---

