---
title: "ALT-TAB not working in gnome classic?"
date: 2012-04-29
forum: Desktop Environments
---

### Post by codingman on 2012-04-29
When I am using gnome classic, ALT-TAB is interpreted as TAB instead I am clueless on what to do :confused:.

---

### Post by kohoutek1 on 2012-04-29
I presume you're using alt-tab to switch windows?

A bug has been reported to Launchpad on this issue. Until it's resolved, install Compiz Config Settings Manager, then use the "Scale" settings there to set ALT-TAB as you want it. Works nicely, actually. 

Hope that helps.

---

### Post by codingman on 2012-04-29
Thanks, that was really helpful, usually ccsm is a big pain because it breaks my desktop.

---

### Post by aryasheel on 2012-04-29
-- worked --
 Thanks to kohoutek1
Steps are different though :)
 [LIST]
[*]CompizConfig Setting Manager
[*]opened the manager and navigated to window management
[*]checked application switcher (previously disabled ) 
[*]Worked like a charm
[/LIST]

---

### Post by papimigas on 2012-06-01
Thank you!
This happened to me too in 12.04, under gnome classic :p

---

### Post by rpaskudniak on 2012-06-03
> **kohoutek1 said:**
> I presume you're using alt-tab to switch windows?

A bug has been reported to Launchpad on this issue. Until it's resolved, install Compiz Config Settings Manager, then use the "Scale" settings there to set ALT-TAB as you want it. Works nicely, actually. 

Hope that helps.

I have the identical problem and I have seen a few suggestions about installing Compiz Config Settings Manager.  Problem: Synaptic shows I have installed it but I can't find it on any of my menus.  I ran this find before posting:
```
find / -name compizconfig-settings-manager
```
All it has found is these two entries:
> /usr/share/pyshared-data/compizconfig-settings-manager
/usr/share/doc/compizconfig-settings-manager
The first is a short config file (476 bytes) and the latter is a directory containing documentation.  BTW, appending \* to the end of the search string didn't turn up anything helpful either.  Even after reinstalling CCSM.

So where in blazes is the actual executable? ](*,) 

By the way, I also tried [Applications]->[System Tools]->]System Settings]->[Keyboard], then I clicked the Shortcuts tab.  I can see clearly that the "Switch Applications" shortcut is set to Alt-Tab. (See attachment.) It just ain't working!  If this can be enabled from CCSM, fine, but I gotta find it first! 

HELP!!

Thank you all.

---

### Post by nalin4linux77 on 2012-06-15
Dear Friends
       It is very easy to configure thees keys via Keyboard Shortcuts 
System settings >>> Keyboard >>> Shortcuts Page >>>  Navigation >>> Switch application
Also we can set other keys like Alt+F4(close) ... In this editor :guitar:

---

### Post by nohammer on 2012-06-24
sorry for the bump 
I've got the Keyboard Shortcut set up in the keyboard settings, but alt-tab is still not working for me. I'd rather not set up compiz just for window switching. This is fresh install of 12.04 if that makes a difference. I think that I might have had issues with alt-tab as well previously in 11.10.

---

### Post by hictio on 2012-06-24
What version of Ubuntu are you guys running? I don't have any problem Alt Tabbing windows with my Ubuntu GNOME Shell Remix 12.04 (32 bits) running Gnome Classic.

---

### Post by chris282 on 2012-06-27
Same problem here, using Ubuntu 12.04 and Gnome Classic.

Keyboard shortcuts are already configured.

Installed Compiz Config Settings Manager (which I find in System Tools >>> Preferences, re above) and checked Application Switcher, but alt-tab then crashes my desktop.

---

### Post by chrispat on 2012-07-10
Alt+Tab works OK with Gnome Classic **Without Effects**. Since I'm not interested in effects and don't know what they are, and don't want to have anything to do with compiz, this is the perfect solution for me.

---

### Post by Upsonp on 2012-08-02
I was able to enable alt-tab using gconf-edit, which I downloaded to move the min, max, close buttons on the title bar to the right.

open a terminal, if you don't have gconf-edit use
```
sudo apt-get update
``````
sudo apt-get install gconf-editor
```after install is complete use
```
gconf-editor
```navigate to
apps > Metacity > general

Scroll to the last option
workspace_switcher_keyboard_cycle and check it off.

---

### Post by Nalin x Linux on 2012-09-22
I think this will help you to solve this issue <<<

Open Gedit and copy following code. 

```

gconftool -s /apps/metacity/global_keybindings/switch_windows --type string '<Alt>Tab'
gconftool -s /apps/metacity/window_keybindings/minimize --type string '<Alt>F9'
gconftool -s /apps/metacity/global_keybindings/show_desktop --type string '<Ctrl><Alt>D'
gconftool -s /apps/metacity/window_keybindings/close --type string '<Alt>F4'
gconftool -s /apps/metacity/window_keybindings/activate_window_menu --type string '<Alt>space'
gconftool -s /apps/metacity/window_keybindings/begin_move --type string '<Alt>F7'
gconftool -s /apps/metacity/window_keybindings/begin_resize --type string '<Alt>F8'
gconftool -s /apps/metacity/window_keybindings/maximize --type string '<Alt>F11'
gconftool -s /apps/metacity/global_keybindings/unmaximize --type string '<Alt>F5'

```

save it in your home folder named **set_key.sh**

Open startup application and add a new program and fill entry's as follows 
Name : **set_key**
command : **/home/username/set_key.sh**
**Now time to reboot your system !!**

---

### Post by dibuntux on 2012-10-31
> **aryasheel said:**
> -- worked --
 Thanks to kohoutek1
Steps are different though :)
 [LIST]
[*]CompizConfig Setting Manager
[*]opened the manager and navigated to window management
[*]checked application switcher (previously disabled ) 
[*]Worked like a charm
[/LIST]

Upgraded from 10.04 to 12.04 lts amd64 - works ok with the above...
Thanks!

---

### Post by mteppo on 2012-11-16
> **chris282 said:**
> Same problem here, using Ubuntu 12.04 and Gnome Classic.

Keyboard shortcuts are already configured.

Installed Compiz Config Settings Manager (which I find in System Tools >>> Preferences, re above) and checked Application Switcher, but alt-tab then crashes my desktop.

Same problem. 
Then unchecked Application Switcher and checked "Static Application Switcher" and now Alt-Tab works the way I'd expect.

---

### Post by mikko.ostlund on 2012-11-27
Trying to summarize this thread into a step-by-step guide to a solution: 

DEFINITION OF PROBLEM TO BE SOLVED: 
You are running "Gnome Classic" and "Alt-Tab" does not work, i.e. it does 
not switch applications; it just has the same effect as typing "Tab" 
alone, without holding down "Alt". 

GUIDE TO SOLUTION:
The root of the problem, likely, lies in that you are running "Gnome Classic" 
together with "Compiz". Compiz is an "OpenGL compositing manager", which 
allows you to turn on a lot of cool visual effects to your desktop; e.g. to 
have your application windows behave like "jelly", instead of stiff rectangles, 
when you move them around. 

1. Do you really want these "cool visual effects" provided by Compiz? 
If yes, go to step 2 below. 
If no, log out and log in with "Gnome Classic (without effects)" instead 
of "Gnome Classic". Alt-Tab probably works now. Do NOT proceed to step 2. 

2. So you want Compiz *and* Alt-Tab working together? Ok, install the 
"Compiz configuration settings manager" as follows: 
 2.1 In a terminal window, type "sudo apt-get install compizconfig-settings-manager" and press enter. 
 2.2 Press "Enter" again after a few seconds, when asked whether you want 
to proceed with installation. 
 2.3 When the installation is complete, type "ccsm" and press enter. This starts the 
     "Compiz configuration settings manager" graphical user interface. 
 2.4 In "Compiz configuration settings manager", click "Window Management" 
(in the left pane), then, in the right pane, UNcheck "Application Switcher" 
and CHECK "Static Application Switcher". 
 2.5 Exit from "Compiz configuration settings manager". 
 2.6 I hope it works now.

---

### Post by redscorp on 2013-01-02
Hi boys and girls (probably)!

> **mikko.ostlund said:**
> 
2. So you want Compiz *and* Alt-Tab working together? Ok, install the 
"Compiz configuration settings manager" as follows: 
 2.1 In a terminal window, type "sudo apt-get install compizconfig-settings-manager" and press enter. 
 2.2 Press "Enter" again after a few seconds, when asked whether you want 
to proceed with installation. 
 2.3 When the installation is complete, type "ccsm" and press enter. This starts the 
     "Compiz configuration settings manager" graphical user interface. 
 2.4 In "Compiz configuration settings manager", click "Window Management" 
(in the left pane), then, in the right pane, UNcheck "Application Switcher" 
and CHECK "Static Application Switcher". 
 2.5 Exit from "Compiz configuration settings manager". 
 2.6 I hope it works now.

I have no "Application Switcher" in Window Management" group... It's Ubuntu 12.10 x64. Where can I do to fix Alt-Tab problem?

Thanks!

---

### Post by redscorp on 2013-01-02
> **redscorp said:**
> Hi boys and girls (probably)!

I have no "Application Switcher" in Window Management" group... It's Ubuntu 12.10 x64. Where can I do to fix Alt-Tab problem?

Thanks!

FIXED: package "compiz-plugins" was somehow missing on my Ubuntu 12.10 x64... Now "Application Switcher" is there and ALT-TAB works too. :guitar:.

PS: [http://www.itworld.com/software/312591/enable-alt-tab-gnome-classic-ubuntu-1210](http://www.itworld.com/software/312591/enable-alt-tab-gnome-classic-ubuntu-1210)

---

### Post by bijupp on 2013-02-24
thanks it works for me

---

### Post by dakra137 on 2013-03-12
**No-new-software** based solution:


Based on Yevgen Yampolskiy's suggestion in [http://askubuntu.com/questions/135685/alt-tab-does-not-switch](http://askubuntu.com/questions/135685/alt-tab-does-not-switch) , 
I renamed the .gconf* and .gnome2* folders in my home folder to ..gconf* and ..gnome2*, logged out, and back in.  
****Problem solved****.  
By the way, I had been using 12.04 for 8 months until this problem struck after I stupidly did 
```
`sudo service lightdm restart` 

```from an <alt><ctrl>F1 console session. Stupidly, because I was running gnome classic without effects.

---

### Post by DavidBooth on 2013-04-03
[**[COLOR=#000000]rpaskudniak[/COLOR]**]("http://ubuntuforums.org/member.php?u=589706"), CompizConfig Settings Manager was installed as /usr/bin/ccsm and place in the menu under Applications->System Tools->Preferences.

I'm on Ubuntu 12.04 running gnome-classic, since I could not stand the frustratingly dumbed-down Unity desktop that ships with 12.04.

---

### Post by temenchat on 2013-05-02
Yeaayy working.... !!! Very simple solution !!
Thanks a lot
:guitar:



> **nalin4linux77 said:**
> Dear Friends
       It is very easy to configure thees keys via Keyboard Shortcuts 
System settings >>> Keyboard >>> Shortcuts Page >>>  Navigation >>> Switch application
Also we can set other keys like Alt+F4(close) ... In this editor :guitar:

---

### Post by arijit_bosco on 2013-06-14
> **aryasheel said:**
> -- worked --
 Thanks to kohoutek1
Steps are different though :)
 [LIST]
[*]CompizConfig Setting Manager
[*]opened the manager and navigated to window management
[*]checked application switcher (previously disabled ) 
[*]Worked like a charm
[/LIST]


Thanks aryasheel. Indeed that worked like a charm. 

And in order to access CompizConfig Setting Manager I had to go to System tools -> Preferences.

There was a warning advising to exercise caution with this settings manager.

Is this some king of application developed by Ubuntu? 

Thanks once again!

---

### Post by azertyh on 2013-06-15
> **nalin4linux77 said:**
> Dear Friends
       It is very easy to configure thees keys via Keyboard Shortcuts 
System settings >>> Keyboard >>> Shortcuts Page >>>  Navigation >>> Switch application
Also we can set other keys like Alt+F4(close) ... In this editor :guitar:

hello,
i set the shortcut as CTRL+F12 and CTRL+SHIFT+F12 but none of them works.
and if i dont want to install ccsm, what to do?

---

### Post by kotoponus on 2013-06-27
Thanks, Arysheel, for the summary!

---

### Post by danicheman on 2013-08-16
> **redscorp said:**
> FIXED: package "compiz-plugins" was somehow missing on my Ubuntu 12.10 x64... Now "Application Switcher" is there and ALT-TAB works too. :guitar:.

PS: [http://www.itworld.com/software/312591/enable-alt-tab-gnome-classic-ubuntu-1210](http://www.itworld.com/software/312591/enable-alt-tab-gnome-classic-ubuntu-1210)

Thanks so much.  This also helped me solve the mystery of the missing alt-tab in Gnome Fallback on Ubuntu 13.04

---

### Post by brijeshbmehta on 2014-03-02
Its working fine with CompizConfig Setting Manager in ubuntu classic

 Thanks to kohoutek1

Here are the Steps for it.
  goto ubuntu software center
  search for CompizConfig Setting Manager
  install it
  open it and go to window management some where at bottom
  check application switcher (which is previously unchecked)
  you are ready to rock!!!!!

be careful when applying other effects because it may not be supported by your hardware so do not apply all the effect at once.
Enjoy Linuxing!!!!! :)

---

