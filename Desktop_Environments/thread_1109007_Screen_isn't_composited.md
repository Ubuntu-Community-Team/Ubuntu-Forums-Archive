---
title: "Screen isn't composited"
date: 2009-03-28
forum: Desktop Environments
---

### Post by ATR on 2009-03-28
Hey any help appreciated greatly on this matter. (And I hope this is the right place for the issue)

I turned on the computer today and when the desktop loaded this error came up:

Starting avant-window-navigator    (at the top)

Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.


Thus no settings to do with compiz work. (no dock appears, no effects).
Of course I've tried to simply run compiz (alt F2 - compiz) but nothing happens. The screen shakes but then compiz still is not running and nothing changes. I just tried re-installing my graphics driver too but still no luck. 

I really am stuck with anything else to do here. I have a suspicion of why it has happened though. I have a feeling it's to do with updates I downloaded last night, because it's happened before where I've downloaded updates, and then next boot up something doesn't work. 

That's all I know, if anybody has any ideas I will be very greatful

Thank you :]

---

### Post by ajgreeny on 2009-03-28
In Alt+F2 try ```
compiz --replace
``` which is the normal command for starting compiz and replacing metacity.

---

### Post by ATR on 2009-03-28
Thanks but that didn't work either. And I just remembered something I had to do last time I had a graphics problem which was go on appearence and click extra. But now I do that and it says:

Desktop effects could not be enabled

and that's it.

Thanks and any more help?

---

### Post by ATR on 2009-03-28
Okay I ran that command in terminal and this came up:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2000028 specified for 0x2000033 (Starting a).


Not sure what it means but all those not presents can't be good. Also everything is starting to go wierd, the tops of windows are dissapearing and things..
So again any swift help greatly appreciated

---

### Post by theitzamna on 2009-04-02
I have exectly same situation here after yesterday's update. Got all screen effects gone away, awm doesn't start with exact mistake and compiz doesn't wanna start:

root@pureenergy:/home/itzamna# compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: xterm 
no xterm found, exiting

---

### Post by Giblet5 on 2009-04-02
Do you have an nvidia card?

Is the nvidia module loaded?
```
lsmod | grep nv
```

Have you run:
```
sudo nvidia-xconfig
```

---

### Post by houdinihound on 2009-04-25
Old post so I assume the OP has resolved the issue.  

But for any others out there, I had exact same problem and doing what giblet5 suggested above showed no nvidia drivers installed.  So I went to System -> Administration -> Hardware Drivers and it too showed no Nvidia driver selected.  Selecting the latest one (and rebooting) resolves the problem.

Thanks to giblet5 for pointing in the right direction.

---

### Post by dragon99 on 2009-04-25
My problem very similar. Just did a fresh install of jaunty.

I get same error on boot ' screen isnt composited'. However, if I activate the compiz-fusion icon, it shows that the manager _is_ compiz, and that emerald is the decorator. If I then reload the manager option in the fusion-icon, compiz kicks in, emerald works, and my awn dock appears.

Question is how do I get jaunty to load compiz, emerald, and awn properly on bootup?

---

### Post by dragon99 on 2009-04-25
Forgot to mention that I'm not running restricted drivers for my nvidia as I'm using EnvyNG with the latest available drivers. I had my Hardy installation running perfect this way.

---

### Post by dragon99 on 2009-04-25
Resolved!

All I had to do was add compiz in the System-->startup programs. :lolflag:

---

### Post by dryphi on 2009-04-30
I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

---

### Post by gsarig on 2009-05-05
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

Same thing here... In my case it's a clean install, keeping the home folder from the previous installation...

---

### Post by mj_ja55 on 2009-05-07
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

I also am having this problem.  It started after I upgraded to 9.04.

---

### Post by ljrmorgan on 2009-05-15
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

Yeh, I get this too when I log out - is this an AWN problem?

---

### Post by enz1m3 on 2009-05-19
I don't know about the shutdown one, but the problem on login can be solved by adding the following to the startup programs:

gnome-panel
compiz

if you're wondering how you're going to add this when you're not able to run anything, just right-click the wallpaper and create a launcher with the name and command: "xterm" (no quotes), then, run it and type: "gnome-panel &" (again, without quotes) then you can see the panel and go to system -> preferences -> startup applications, adding the two apps I stated above.

If you have any problems, let me know, I'll gladly help

---

### Post by TheSeanKelly on 2009-05-20
I'm getting the same issue with a clean install of Jaunty and NO copying of settings from intrepid.  Completely clean; using nvidia 180 and install AWN, there it is.

---

### Post by enz1m3 on 2009-05-21
> **TheSeanKelly said:**
> I'm getting the same issue with a clean install of Jaunty and NO copying of settings from intrepid.  Completely clean; using nvidia 180 and install AWN, there it is.
what same issue? the error on login or logout?

---

### Post by TRANQU111TY on 2009-06-21
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

+1 here and my specs are in sig.

---

### Post by enz1m3 on 2009-06-21
As I said before, I'm not entirely sure what causes this on shutdown, but it's not problematic as it doesn't reduce performance, though there should be a fix out there by now...

---

### Post by bgreenaway on 2009-06-22
I am also getting the composite error on logout, but does not seem to cause any other problem (I am also using AWN). Would still like to get rid of it though.

---

### Post by Zeedok on 2009-06-23
I'm not sure if I am having the same problem, but sometimes (say 50% of the time) compiz (or maybe emerald) is not running on login.  AWN is running, but the window decoration and icons are not.  I found that if I run a system configuration program (eg "Sound preferences") or logout and login again, everything kicks in.

I have "compiz" and "emerald --replace" in startup applications.

Anyone have any suggestions??

---

### Post by Darkspark on 2009-07-03
I have "compiz" and "emerald --replace" in startup applications.

Anyone have any suggestions??

What are the options being passed to compiz. If that is the only windows decorator you are using, and you have fusion-icon you can pass it the option of --force-compiz to fusion-icon on startup. That might help.

---

### Post by enz1m3 on 2009-07-03
@Zeedok and @Darkspark

Try adding "compiz --replace" to see if it works.

If you don't see the bottom/top gnome panel bar, also add "gnome-panel".

Report if you continue to have any issues.

---

### Post by Metralha on 2009-11-14
I has having the same problem in 9.10 and I found a good and simple solution... Alt + F2 ->gconf-editor -> /apps/avant-window-navigator/ and uncheck show_dialog_if_non_composited. Sorry for the bump but its just to keep it register for someone else in the same situation.

Tks

---

### Post by msriram on 2009-11-30
I connected a 22" monitor to my laptop, and tried to use 1650x1050 resolution (for some reason 1920x1200 isnt working with Ubuntu)..

My problems are:
1. Use monitor alone to view stuff. 
All I could do was to use "mirror screen" which gives me a crappy resolution of 1280x758 (or) use dual monitor arrangement with 1650x1050 + 1400x1050 ... Yes my laptop is IBM thinkpad which has a funny screen size..

If I uncheck the option to use laptop in the dual monitor arrangement, I get a error in the center of the monitor "Incorrect Input Signal" with which I could not work.. But its fine to have dual monitor arrangement, and I can adjust with it.
But here comes second problem....

2. Now, AWN and Compiz fusion (desktop effects) stopped working since the new monitor arrangement is weird. 

```

administrator@ubuntu:~$ avant-window-navigator 
(awn-applets-migration:8916): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

administrator@ubuntu:~$ compiz -fusion
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (3080x1050) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -fusion

administrator@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (3080x1050) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize"

administrator@ubuntu:~$ lspci | grep VGA 
01:00.0 VGA compatible controller: ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)

administrator@ubuntu:~$ lspci | grep PCI
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)

```

Can anyone help me getting AWN working? I suppose there is some file, which I can modify and use 3080x1050 as a valid resolution for COMPIZ..

Thanks in advance

---

### Post by enz1m3 on 2009-11-30
@msriram

Have you tried any of the solutions above in this thread?

---

### Post by msriram on 2009-11-30
@enz1m3  
Yes.. I did them, and posted the result above..  I also tried installing ubuntu tweak. That didn't help me either...

Thanks

---

### Post by enz1m3 on 2009-11-30
Oh, sorry, wasn't paying real attention there :/

So, for your compiz --replace issue, have you tried this: [http://ubuntuforums.org/showthread.php?t=611877](http://ubuntuforums.org/showthread.php?t=611877) ?

---

### Post by msriram on 2009-11-30
Ok, guys.. I know this will sound funny, But it worked for me..

1. Use "Mirror Screen" and get the  crappy resolution on the Big Screen.

2. Enable Visual Effects by right clicking Desktop -> Change Desktop Background, and changing Appearance Preferences/Visual Effects to Normal or Extra.

3. Now, compiz is enabled. AWN works.. Here after, you can change Display Preferences (Screen Resolution) to un-check "Mirror Screen" and choose the ideal resolution(which is available) for the monitor ... 1680x1050 for me...

Compiz stays, and AWN continues to work...!

I hope this solves my issue. But the problem by large is still mysterious..

---

### Post by amirmku on 2009-12-01
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.
I too have the same problem ............
i have compiz fusion icon added on the start up application but it didnt work for me

---

### Post by msriram on 2009-12-01
From my experience, the error "Screen isn't composited" happens when compiz fails to load, or when it is not open. Look at the error log which you get when you try "compiz -fusion"
 and try to make sense out of it...

Probably your compiz is killed just before your computer is shut-down. And may be you have some application, like AWN or beryl that requires compiz...


Cheers

---

### Post by dawet_ayu on 2009-12-07
> **dryphi said:**
> I am getting this same error message. However it is on system shutdown (not on login). While shutting down I get the message
"Warning: screen isn't composited. Please run compiz (fusion) or another ..."  
It sits for a moment then closes automatically and the system continues to shut down.

AWN runs fine.

Note I have recently updated to 9.04 and just started having this problem.

I have this problem too, I use 9.10 and have no idea to solve this problem

---

### Post by mmdmurphy on 2009-12-20
This solution (below) worked for me. I had to install proprietary drivers to get enhanced background, then everything worked. Kinda makes sense when you think about it.


> **msriram said:**
> Ok, guys.. I know this will sound funny, But it worked for me..

1. Use "Mirror Screen" and get the  crappy resolution on the Big Screen.

2. Enable Visual Effects by right clicking Desktop -> Change Desktop Background, and changing Appearance Preferences/Visual Effects to Normal or Extra.

3. Now, compiz is enabled. AWN works.. Here after, you can change Display Preferences (Screen Resolution) to un-check "Mirror Screen" and choose the ideal resolution(which is available) for the monitor ... 1680x1050 for me...

Compiz stays, and AWN continues to work...!

I hope this solves my issue. But the problem by large is still mysterious..

---

