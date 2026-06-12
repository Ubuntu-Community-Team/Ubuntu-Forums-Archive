---
title: "All internet browser crash"
date: 2015-05-09
forum: Desktop Environments
---

### Post by mfaridi2 on 2015-05-09
[COLOR=#111111][FONT=Ubuntu]I installed Ubuntu 15.0.4 64 bit. My mainboard is an ASUS M2N-PLUS SLI vista edition with AMD CPU, with 4GB of RAM and an nVidia 8500 GT video card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I start Firefox, after opening a new tab Firefox crashes and restarts.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Sometimes, when I open it for first time, it will also crash. I tried to install Midori and Chromium, but all of these browsers crash as well, although chromium appears to crash less.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I set up flash player and pepperflashplugin, but browsers are still crashing and I can not use the Internet as a result.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I run firefox from command line I see

$ firefox &
[/FONT][/COLOR]```




[1] 4070
mostafa@mfaridi-ubuntu:~$ 
(process:4070): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
(process:4099): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
get_contentWindow@chrome://global/content/bindings/browser.xml:404:54
get_securityUI@chrome://global/content/bindings/browser.xml:654:17
browser_XBL_Constructor@chrome://global/content/bindings/browser.xml:778:17
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
1431173849082   addons.xpi  WARN    Exception running bootstrap method shutdown on webapps-team@lists.launchpad.net: ReferenceError: sss is not defined (resource://gre/modules/addons/XPIProvider.jsm -> file:///usr/share/mozilla/extensions/%7Bec8030f7-c20a-464f-9b0e-13a3a9e97384%7D/webapps-team@lists.launchpad.net/bootstrap.js:72:4) JS Stack trace: shutdown@resource://gre/modules/addons/XPIProvider.jsm -> file:///usr/share/mozilla/extensions/%7Bec8030f7-c20a-464f-9b0e-13a3a9e97384%7D/webapps-team@bootstrap.js:72:5 < XPI_callBootstrapMethod@XPIProvider.jsm:4442:9 < shutdownObserver@XPIProvider.jsm:2185:13 
```

---

### Post by TheFu on 2015-05-09
Those errors say "unity" - just a few thoughts.
a) create a new userid, login with it, see if the browsers still crash under the other userid.  This would imply it is a personal settings issue, not an issue with something else.
b) install a different desktop, then do "a" (important to use a different userid for a different desktop so settings don't get munged). xfce, lxde, mate are options to try which are relatively light.
c) There is a bug - [https://bugs.launchpad.net/ubuntu/+source/unity-firefox-extension/+bug/1091288](https://bugs.launchpad.net/ubuntu/+source/unity-firefox-extension/+bug/1091288) which seems as it may be related.

I haven't a clue, but perhaps one of htose will help?  I'd try "c" first, then "a" and lastly "b".

---

### Post by mfaridi2 on 2015-05-10
make new user with adduser command , but Firefox crash too . I must check another desktop

---

### Post by dino99 on 2015-05-10
Please tell us how you have installed 15.04, and which 'third party' packages have been installed (seeing javascript troubles)

note: if you want a stable system, then only use trusted packages from the ubuntu archive

---

### Post by mfaridi2 on 2015-05-10
I install Ubuntu from DVD with default installation . and I install packages from default archive

---

### Post by TheFu on 2015-05-10
> **TheFu said:**
> 
c) There is a bug - [https://bugs.launchpad.net/ubuntu/+source/unity-firefox-extension/+bug/1091288](https://bugs.launchpad.net/ubuntu/+source/unity-firefox-extension/+bug/1091288) which seems as it may be related.

Has a workaround. Did it work for you?

---

### Post by mfaridi2 on 2015-05-10
I disable all addon and plugin or extenssion and firefox work better , but when I open more than 2 tab , it start crash and I can not use it .
chromium show me error about
Aw Sanp and I can not use it

I install adobe flashplugin and pepperflash plung nonfree , but I have crash too

---

### Post by TheFu on 2015-05-10
Perhaps I misread the work-around or the issue, but doesn't it say to remove a few packages that integrate unity with the browsers?? 
Use the package manager you like to do that. Any of apt-get, aptitude, synaptic would be how I did it. Don't know if software center can to it. Sorry.

---

### Post by mfaridi2 on 2015-05-11
How I can get full log about this problem , maybe this problem happen by another driver . yesterday my system work with default novouea driver and today I install Nvidia driver and reset system , but  crash of internet browser not solve.

---

### Post by Bucky Ball on 2015-05-11
By installing more 'stuff' you are quite possibly confusing the issue. Installing video drivers when it was known to work with the others and plopping on flash (which can cause other issues) should be avoided. Roll back the driver (for now) and switch off or uninstall flash (for the moment) and start from the beginning again. Good luck.

---

### Post by mfaridi2 on 2015-05-11
Can this happen some software during installation , does not install good and some software does not have clean installation , and I have to reinstall all of them

---

### Post by Bucky Ball on 2015-05-11
Depends how you install them. If you used Software Centre, command line or Synaptics, it would tell you if there was a problem on install I would think. Try these commands in a terminal and report any and all errors:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```	

This will NOT upgrade your machine to the latest release, only upgrade your currently installed apps, if they need it. Any errors might also give us further clues.

---

### Post by mfaridi2 on 2015-05-11
I run above commands and I do not see error , but when I run ```
sudo apt-get autoremove
``` I see these ```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-generic linux-image-generic thermald
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 698 kB disk space will be freed.
Do you want to continue? [Y/n] 



```
and I choose y . I think everything is OK

---

### Post by mfaridi2 on 2015-05-11
I test another thing right now when I run firefox with this command
```
 firefox -safe-mode 
```
firefox start and can not crash . I do not delete flashplugin and nividia driver
I think something in ubuntu or firefox conflict together and make firefox crash

---

### Post by Bucky Ball on 2015-05-11
Nice observation. An idea: running in safe-mode generally means the plug-ins and extensions are switched off. Boot into safe mode and go Tools> Add-ons. Flash has the option on the right hand side drop down menu to 'Ask' rather than on or off all the time. Set it to ask. Close Firefox and reboot. If you can boot Firefox without issue, go to a site you know needs Flash. Now, when you get to that site, you should see along the top a bar or a pop-up window asking if you want to enable flash. Do so. Does Firefox crash?

If you can't boot into Firefox after setting Flash to 'Ask', boot into safe mode and switch Flash off in the Tools> Addons page. Close Firefox then launch it again. Any luck? Still crashing?

---

### Post by mfaridi2 on 2015-05-11
Last night before I start Firefox with safe mode , I am disable all addon and extensions , today I run it with safe mode , but it crash low and can not crash more than it run in normal mode. 
when Firefox start in safe mode and I go to addon option , I can not find Flashplayer plugin and I can not find Flashplugin in extension . and right now my Firefox does not have any addon and extension . 
when I open normal page like distrowatch and bsdnow.tv with firefox everything is OK in safe mode and it work good , but when I want open ubuntuforums.com , Firefox crash again in safe mode too. I think something in ubuntuforums is heavy and firefox can not work and crash , when I return to normal mode in Firefox sometimes when I open more than 3 tab , it crash and all time crash when I open it for first time .

---

### Post by TheFu on 2015-05-11
Please try the workaround spelled out in that bug report link (launchpad) above and report whether that solves the issue.  If the issue is with the integration between Unity and Firefox (or Chrome or Chromium), ....

---

### Post by mfaridi2 on 2015-05-12
I install synaptic package manager and search unity and find everything are depend on unity and firfox and remove them and then search firefox and remove everything on depend on firefox and remove them . for example xul-ext-unity was integration between firefox and unity and I remove this package . then I open MC and remove mozilla firefox folder from home folder and start it . it start and crash again . so I disable all addon and extension and restart firefox , but it crash again .

I understand new thing today . thunderbird crash too , but other packages like game , viber and ... work good .
each time my system start after login , I see error about internal system error and my system want report it . sometimes I see error about linux-image-kernel , apport.gtk and and my system do not work good .

I go to /var/log and try see message log , but I can not find it . how I can see all error . 
I have 4 HDD on my system , one use by FreeBSD with OpenBox , one use by OpenBSD with Openbox , one use by Linuxmint debian edition 1 with mate , all of these OS work good . and I have problem with ubuntu .

please guide me , I get full log about my system , maybe this help us to solve problem .

---

### Post by mfaridi2 on 2015-05-12
I understand new thing , when I use chromium for internet . sometimes when I type in address bar and press Enter , it crash and I must use reload to see site . sometime when I open site for example distrowatch.com and I do not use it for  5 min . chromium show me ```
 Aw Snap error 
``` and I have to reload it again . to see and use

---

### Post by mfaridi2 on 2015-05-12
I want remove unity and all dependency and want install XFCE , which way is better ?

---

### Post by dino99 on 2015-05-12
Looks like you have some borked settings file(s): either .local, .gnome2, .config or/and .gconf . They are hidden (ctrl+h to unhide) and are cleanly recreated on the next boot (but without your custom settings indeed) . You can try it, but first save them by adding .old to their names for example (only if you care about your settings)

---

### Post by mfaridi2 on 2015-05-12
> **dino99 said:**
> Looks like you have some borked settings file(s): either .local, .gnome2, .config or/and .gconf . They are hidden (ctrl+h to unhide) and are cleanly recreated on the next boot (but without your custom settings indeed) . You can try it, but first save them by adding .old to their names for example (only if you care about your settings)
Thanks
is that enough I open MC or midnight commander and go to user home folder for example /home/mostafa and delete all files and folder there and reboot system and start use it after login ?

---

### Post by dino99 on 2015-05-12
> **mfaridi2 said:**
> Thanks
is that enough I open MC or midnight commander and go to user home folder for example /home/mostafa and delete all files and folder there and reboot system and start use it after login ?

hey be carefull: these hidden files are inside your /home (ctrl+h to unhide them, in case you need it); better to rename them first (right-click on the file and select 'rename' if the menu is in English) and dont erase files or folders (except if you want to break your installation ;) ) and then simply reboot to get these files cleanly recreated.

---

### Post by mfaridi2 on 2015-05-12
> **dino99 said:**
> hey be carefull: these hidden files are inside your /home (ctrl+h to unhide them, in case you need it); better to rename them first (right-click on the file and select 'rename' if the menu is in English) and dont erase files or folders (except if you want to break your installation ;) ) and then simply reboot to get these files cleanly recreated.
I do that . firefox still crash , but chromium has less crash and work better , I want remove completely unity and install xfce , maybe my problem solve

---

### Post by Bucky Ball on 2015-05-13
I don't think it will make any difference, but:

```
sudo apt-get install xfce4
```

... or install xfce4 from Software Centre or Synaptics. Log out> choose 'xfce session' from the 'Sessions' menu> log in. You're there. This method will only install the desktop environment, NOT Xubuntu. 

Your other options are to download the ISO and install Xubuntu or download the mini.iso, install it and add xfce4 and any apps you want. That's what I do.

---

