---
title: "Problem loading SCIM panel icon"
date: 2009-03-07
forum: General Help
---

### Post by erebus314 on 2009-03-07
I have just got ubuntu 8.10 (2 days ago on an ASUS X59SL laptop), and suffice to say, I don't really know what I am doing.  I followed this guide on softpedia earlier today on customizing the desktop:
[http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml](http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml).  This guide advises you to remove basically everything from your top panel and hide it, replacing its functionality with AWN's.

It worked pretty well, until I realised that I needed to use SCIM from the panel for inputting IPA. I was able to restore everything on the panel quite easily, except for the little SCIM keyboard.

I looked around on google for a while and all I could really find was suggestions to add the Keyboard Indicator to the panel, but this gives me something else. I can also get the icon to return by going to /usr/lib/scim-1.0 and loading scim-panel-gtk but this just loads the icon with no functionality except right clicking (which brings up a little menu with a shortcut to the SCIM settings).

I tried reinstalling, and I have compared my settings on this user account with those on my root account (I haven't played with that so the SCIM keyboard still works). I still haven't been able to get it to load. I am sure the fix must be a simple one, but I just can't find it.

I am a linguistics student, so that I've managed to sabotage one program I really needed is particularly irritating.  I would really appreciate some help on this.

Thanks

EDIT: I have tried reloading the panel to its default settings using the terminal however the SCIM icon still does not load in the notification area and does not work when I force it to. I have also created a new user account but the new user account has the same problem. Yet SCIM is still working correctly on my original account.

---

### Post by erebus314 on 2009-03-11
Still no fix.

As my original user account still has scim running properly I decided to have a closer look at what was going on. I opened up System Monitor and wrote down the name of every process running on the original account and compared them to the ones running on the broken scim account.

The results were unsurprising, the only difference was on the broken one:

scim-bridge
scim-helper-manager
scim-launcher -d -c socket -e socket -f x11
scim-launcher -d -c -simple -e all -f socket --no-stay
scim-panel-gtk --display :0.0 -c socket -d --no-stay

were not running, on the working account they were. No other differences.

So I tried running them with alt+F2 (including the -d -c etc parameters, which I don't understand at all) and the panel loaded up again, but left clicking still didn't work...

The processes were running though, with the same mysterious parameters.

I killed them as they weren't working so I was back to the same state I was when I logged in and this time tried doing the same thing from a terminal, getting this output:

dean@yep:~$ scim-bridge
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
dean@yep:~$ ../../usr/lib/scim-1.0/scim-helper-manager
Can't initialize SocketServer.
dean@yep:~$ ../../usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Starting SCIM as daemon ...
dean@yep:~$ ../../usr/lib/scim-1.0/scim-launcher -d -c -simple -e -f socket --no-stay
Loading -simple Config module ...
Can not load -simple Config module. Using dummy module instead.
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
dean@yep:~$ ../../usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
GTK Panel of SCIM 1.4.7

Failed to initialize Panel Agent!
dean@yep:~$ 

Again scim keyboard loaded on panel but doesn't not respond.

I checked system monitor and all processes are running.

I did notice that:

scim-bridge
scim-helper-manager
scim-launcher
scim-launcher

are all listed as do_select on the waiting channel but that is probably normal and for all I know part of what I told it to do with those parameters.

Does anyone have any ideas what is happening here as I can't think what to do next?

Thanks

---

### Post by newgalois on 2009-03-25
I have the exact same problem and people don't seem to care about it! All guides I found talked about changing things in the Language setting, which does bring the icon on start up. But it's a useless icon as you described. Sorry I'm not helping or anything, but I understand that this issue is very annoying!

Btw, many of my friends who use 8.10 don't have the problem. Perhaps something wrong with our setting. But which, I don't know. Maybe we should really debug the thing (I'm not sure I'll have time for this).

Please let me know if you find a solution! Many thanks.

---

### Post by mdurham on 2009-03-25
Did you try: 
System->Preferences->SCIM Input Method Setup
Select: Panel->GTK and set "Show tray icon"

Cheers, Mike

---

### Post by newgalois on 2009-03-26
I did that with no luck. However, after a bit of googling, I tried this in terminal with scim running:
GTK_IM_MODULE=scim gedit
and scim works, i.e. I can left click and the input method I choose works, whenever the gedit window has focus. I also tried
GTK_IM_MODULE=scim firefox
and again, I can input my language in firefox.

So, it seems that somehow GTK_IM_MODULE was not set correctly for my profile. I tried
export GTK_IM_MODULE=scim
but it doesn't work.

Anyone knows how to set this environment variable?

Many thanks!

---

### Post by mdurham on 2009-03-26
newgalois, I did a scan for GTK_IM_MODULE in my home dir and this is what I found.
Maybe it's of some use???

~/mike/.xinput.d/en_AU contains:
> 
XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"


~/mike/.xinput.d/en_US contains
> 
#
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"


---

### Post by newgalois on 2009-03-26
I tried to change the GTK_IM_MODULE in en_US into scim, but it was no use. If I change it in my .bashrc, then whenever I launch a program from terminal, scim works (because it is a child process of bash). However, if I don't change it in .bashrc, then when I echo $GTK_IM_MODULE in terminal, I get xim. I have changed the variables from xim to scim in the following places:
.profile
/etc/environment
.gnomerc
but it hasn't changed. I guess some script that runs AFTER those scripts sets it back to xim, but I don't know which script :-(. I don't mind writing a new script and making it run at start up to set this variable. But I don't know how to set the variable for the whole session :-(.

By the way, I guess you're using KDE instead of GNOME? Then (I'm sure you knew this, but just in case) QT_IM_MODULE should replace GTK_IM_MODULE in all my posts.

What did you use to scan your computer? I used google desktop, but it doesn't scan "hidden files", which includes all files listed above, so it's no use.

Thanks

---

### Post by mdurham on 2009-03-27
> **newgalois said:**
> 
By the way, I guess you're using KDE instead of GNOME? Then (I'm sure you knew this, but just in case) QT_IM_MODULE should replace GTK_IM_MODULE in all my posts.

What did you use to scan your computer? I used google desktop, but it doesn't scan "hidden files", which includes all files listed above, so it's no use.

Thanks

What makes you think I'm using KDE? I'm using Gnome.
I used the normal search prog from Paces->Search for files and set the "show hidden and backup files" from "Select more options"
Cheers, Mike

---

### Post by newgalois on 2009-03-27
> **mdurham said:**
> What makes you think I'm using KDE? I'm using Gnome.
I used the normal search prog from Paces->Search for files and set the "show hidden and backup files" from "Select more options"
Cheers, Mike

Because I show QT_IM_MODULE=scim-bridge in your config file. Btw, somehow I don't see Search in my "Places" menu!

---

### Post by mdurham on 2009-03-28
> **newgalois said:**
> Because I show QT_IM_MODULE=scim-bridge in your config file. Btw, somehow I don't see Search in my "Places" menu!

This is how it looks on my computer:

---

### Post by newgalois on 2009-03-29
Thanks! I guess I didn't see the search menu because I removed beagle from my system. Anyway, it will only search my home folder ... I guess something is wrong at the system level.

I'm sorry but I must say I give up (for now) ... until I have time to really sit down and track the problem - which may take days. 

Let me know if you find any solution to this problem.

Thanks

---

### Post by erebus314 on 2009-04-10
> **mdurham said:**
> newgalois, I did a scan for GTK_IM_MODULE in my home dir and this is what I found.
Maybe it's of some use???

~/mike/.xinput.d/en_AU contains:


~/mike/.xinput.d/en_US contains

Thanks, this worked for me. I found that .xinput.d did not exist at all in my home directory. I created the folder and copied the file en_GB from my other account into it and logged out and back in and SCIM worked. Whenever a new user account is created this folder also needs to be manually added for SCIM to work, which is a bit strange, but a fix nonetheless.

I don't want to mark this topic as solved just yet as it doesn't appear to have solved newgalois problem which seems to be closely related.

---

