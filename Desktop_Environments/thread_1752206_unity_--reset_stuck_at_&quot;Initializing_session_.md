---
title: "unity --reset stuck at &quot;Initializing session options...done&quot;"
date: 2011-05-07
forum: Desktop Environments
---

### Post by n0y0x on 2011-05-07
Hi there,

I had installed the compiz configuration tool from the software center and I was fiddling around with it and broke unity. So, looking online, I found places that told me to run 

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

to reset the unity settings.

I ran the first command, no problem. Now I'm trying to run unity --reset and I'm always stuck on the line "Initializing session options...done"

Here is the full output:
```

unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

```

Please help! I really like unity and didn't realize how much it had grown on me until I had to go back to gnome 2.

Thanks!!

---

### Post by Cukkimo on 2011-05-08
I have exactly the same problem, and funny enough: For the same reason... :D

---

### Post by jagannn on 2011-07-04
i too have same issue,,, plz help

---

### Post by wildmanne39 on 2011-07-04
> **jagannn said:**
> i too have same issue,,, plz help
Hi, click on reset unity and compiz in my signature and reset unity, I assume you changed some settings in compiz, if you want to change setting in compiz have a look at this guide after you have reset unity, it is for the cube and effects but can be used to change other settings too.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by 73ckn797 on 2011-07-04
> **wildmanne39 said:**
> Hi, click on reset unity and compiz in my signature
Please clarify. I do not find what you are talking about.

---

### Post by wildmanne39 on 2011-07-05
> **73ckn797 said:**
> Please clarify. I do not find what you are talking about.
Hi, look below this text there in my signature there are for sentences one says **reset unity and compiz** put your cursor over it and you can see it changes colors to red click on it and follow the directions for resetting unity.

---

### Post by jagannn on 2011-07-05
> **wildmanne39 said:**
> Hi, click on reset unity and compiz in my signature and reset unity, I assume you changed some settings in compiz, if you want to change setting in compiz have a look at this guide after you have reset unity, it is for the cube and effects but can be used to change other settings too.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Hi,
I already tried this, while on GUI mode i pressed Alt+Ctrl+F2 it takes to me to command mode, here i fired the command "**unity --reset**" and following is the output i can see

>>>
[PHP]unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done[/PHP]
>>>

but it stuck at this point, there is no progress after this (i waited for more than 30min :( )

what should i do next. plz suggest

---

### Post by wildmanne39 on 2011-07-05
> **jagannn said:**
> Hi,
I already tried this, while on GUI mode i pressed Alt+Ctrl+F2 it takes to me to command mode, here i fired the command "**unity --reset**" and following is the output i can see

>>>
[PHP]unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done[/PHP]
>>>

but it stuck at this point, there is no progress after this (i waited for more than 30min :( )

what should i do next. plz suggest
Hi, at that point lightly tap your power button and it should bring up the shutdown window then restart and it should be fixed, it never shows more then what you showed on your screen but it is done after about three minutes.

---

### Post by catrincm on 2011-07-05
I am also resetting unity for the same reason (trying to get desktop-cube or something like that in ccsm). Mine has stopped at initializing composite options...done. Pressing the power button does nothing. Any advice?

[edit] doing "sudo service gdm restart" seems to have fixed the problem

---

### Post by 73ckn797 on 2011-07-05
> **wildmanne39 said:**
> Hi, look below this text there in my signature there are for sentences one says **reset unity and compiz** put your cursor over it and you can see it changes colors to red click on it and follow the directions for resetting unity.
There is no signature showing up. See attached screenshot.

---

### Post by wildmanne39 on 2011-07-05
> **73ckn797 said:**
> There is no signature showing up. See attached screenshot.Hi, thats strange, I can see the stuff in my signature and click on it after I have posted it, I also notice that my avatar is not on your screenshot, I think it is a problem on your end, but I am not sure of that.

---

### Post by 73ckn797 on 2011-07-05
> **wildmanne39 said:**
> Hi, thats strange, I can see the stuff in my signature and click on it after I have posted it, I also notice that my avatar is not on your screenshot, I think it is a problem on your end, but I am not sure of that.
It does not show on either my laptop or desktop computers. I will check my forum settings. Later he said: Problem is mine, settings to see avatars and signatures were not checked in User CP settings. ............................... Nevermind!

---

### Post by jagannn on 2011-07-05
> **wildmanne39 said:**
> Hi, at that point lightly tap your power button and it should bring up the shutdown window then restart and it should be fixed, it never shows more then what you showed on your screen but it is done after about three minutes.

I tried as you instructed, but it was not helpful. still i cant able to see desktop panel. Is there any other way to solve this issue. 
or
Do i need to re-install Ubuntu 11.04 ? :(

---

### Post by 73ckn797 on 2011-07-05
> **wildmanne39 said:**
> Hi, click on reset unity and compiz in my signature and reset unity, I assume you changed some settings in compiz, if you want to change setting in compiz have a look at this guide after you have reset unity, it is for the cube and effects but can be used to change other settings too.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

I ran the commands in your signature, which were some of what I have already tried. My situation is that Unity and Gnome Classic (no effects) are working fine. The Gnome Classic DE has no window borders and all effects are gone.

Here is the result of the commands:
```
computer@computer-Laptop:~$ gconftool-2 --recursive-unset /apps/compiz-1
computer@computer-Laptop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:2456): DEBUG: Unity accessibility initialization
** (<unknown>:2456): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:2456): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:2456): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2456): DEBUG: PlaceEntry: Applications
** (<unknown>:2456): DEBUG: PlaceEntry: Commands
** (<unknown>:2456): DEBUG: PlaceEntry: Files & Folders
Starting unity-window-decorator
** (<unknown>:2456): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:2456): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:2456): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:2456): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window
** (<unknown>:2456): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
```

---

### Post by wildmanne39 on 2011-07-05
Hi, I am doing some research to see if there is an answer, I have not seen this problem where resetting unity did not work.

---

### Post by wildmanne39 on 2011-07-05
> **73ckn797 said:**
> I ran the commands in your signature, which were some of what I have already tried. My situation is that Unity and Gnome Classic (no effects) are working fine. The Gnome Classic DE has no window borders and all effects are gone.

Here is the result of the commands:
```
computer@computer-Laptop:~$ gconftool-2 --recursive-unset /apps/compiz-1
computer@computer-Laptop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:2456): DEBUG: Unity accessibility initialization
** (<unknown>:2456): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:2456): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:2456): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2456): DEBUG: PlaceEntry: Applications
** (<unknown>:2456): DEBUG: PlaceEntry: Commands
** (<unknown>:2456): DEBUG: PlaceEntry: Files & Folders
Starting unity-window-decorator
** (<unknown>:2456): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:2456): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:2456): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:2456): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window
** (<unknown>:2456): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
```Hi, I found that some people have solved this problem with this command.
```
unity --repair
```

---

### Post by 73ckn797 on 2011-07-05
> **wildmanne39 said:**
> Hi, I found that some people have solved this problem with this command.
```
unity --repair
```
That returns a message that there is no "--repair" option available according to the man page for unity.

---

### Post by 73ckn797 on 2011-07-05
I have started a thread here [http://ubuntuforums.org/showthread.php?p=11017141#post11017141](http://ubuntuforums.org/showthread.php?p=11017141#post11017141)

I will use that one for further research/resourcing of this issue.

---

### Post by wildmanne39 on 2011-07-05
> **73ckn797 said:**
> I have started a thread here [http://ubuntuforums.org/showthread.php?p=11017141#post11017141](http://ubuntuforums.org/showthread.php?p=11017141#post11017141)

I will use that one for further research/resourcing of this issue.Hi,Sorry I did not find an answer that worked for you.

---

### Post by 73ckn797 on 2011-07-05
> **wildmanne39 said:**
> Hi,Sorry I did not find an answer that worked for you.
I appreciate your input.
I ended up reverting back to 10.04 via a fresh install. Upon restarting I had the same problem. I then deleted all folder in /home that were no application specific then re-installed 10.04. The problem no longer exists. There must have been a config file in /home that was messed up but I do not know what that was. I prefer the old Gnome DE anyway. I will likely keep 10.04 LTS until the next LTS and decide whether I want to stay with Ubuntu or use a different DE. I have been looking at Lubuntu.

---

### Post by wildmanne39 on 2011-07-06
> **73ckn797 said:**
> I appreciate your input.
I ended up reverting back to 10.04 via a fresh install. Upon restarting I had the same problem. I then deleted all folder in /home that were no application specific then re-installed 10.04. The problem no longer exists. There must have been a config file in /home that was messed up but I do not know what that was. I prefer the old Gnome DE anyway. I will likely keep 10.04 LTS until the next LTS and decide whether I want to stay with Ubuntu or use a different DE. I have been looking at Lubuntu.Hi, I am glad you got it fixed even though it took a reinstall, if I had thought I would have told you to create another user account and see if that worked, because that is done a lot when there is a configuration issue that has to do with just one user account.

---

### Post by 73ckn797 on 2011-07-06
> **wildmanne39 said:**
> Hi, I am glad you got it fixed even though it took a reinstall, if I had thought I would have told you to create another user account and see if that worked, because that is done a lot when there is a configuration issue that has to do with just one user account.
I thought about that solution from reading about it in other similar posts during my searching around. 
The laptop is not a critical computer though I use it daily with my work. It only holds data that gets backed up daily to the desktop computer. It is a Toshiba Satellite nearly 5 years old. The volume knob broke off a while back so it does not get used for very much other stuff.

It only takes a little over an hour to do a fresh install along with the additional programs that are used. Using a separate /home partition helps the whole process work faster. I could never have an up and running system that fast when I used Windows, especially on the laptop. The Toshiba install disk would take several hours, over 3 hours the last time it was installed. That was before my switching to Ubuntu. I only use Windows XP in a Virtualbox setup on the desktop computer. I have an OEM Windows disk which does not take too long to install.

---

