---
title: "XFCE 14.04 - no Network Manager applet in panel"
date: 2014-08-12
forum: Desktop Environments
---

### Post by 2CV67 on 2014-08-12
I just updated from 13.10 to 14.04 (I am a deliberate late-adopter, hoping bugs will be fixed before I get to them...).

Everything seems to be fine, except I no longer have the Network Manager applet showing in the notification area of the panel.
The WiFi is working OK, just no applet.

If I run "sudo nm-applet" then the applet appears & stays there for that session, but disappears on logout/login or reboot.
Also, Terminal gives the following message & does not return to normal status position as there is still a process running:
```
chris@Acer-desk:~$ sudo nm-applet
[sudo] password for chris: 
nm-applet-Message: using fallback from indicator to GtkStatusIcon
......
```

I read a lot of bug reports & forum posts on this general subject, mostly dating back to April 2014 & mostly proposing ideas that could work for some people, but didn't see a clear indication of what the problem is, nor a clear definite solution.

I suppose that after 4 months exposure of an LTS version, there should be a good solution somewhere?

Can anybody show me where?

Thanks!

---

### Post by ajgreeny on 2014-08-12
You should run nm-applet as user, not as root.  It is normally one of the startup applications and if it is not already starting with a new session you should add it to the startup applications using command **nm-applet**.

On my Xubuntu 12.04.5 there is an entry (for nm-applet in /etc/xdg/autostart; do you have a similar entry of nm-applet.desktop in that folder?

---

### Post by 2CV67 on 2014-08-12
Hi, ajgreeny & thanks for your interest!

If I try to run nm-applet as user, I don't get the applet, I do get a different error message & the terminal does stick with a process still running:
```
chris@Acer-desk:~$ nm-applet

** (nm-applet:5938): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-peIFpIJIiw: Connection refused
```

Maybe this gives a clue to the problem?

In etc/xdg/autostart, I do have an entry "nm-applet.desktop".

Note that throughout all this, the actual wifi connection is working OK.

---

### Post by ajgreeny on 2014-08-12
I have also noticed that I have a selected (ie, tick in the box) entry for Network (nm-applet) in my Session and Startup list in xfce settings-manager.  That entry is not editable when I highlight it, as it is there as a result of the entry in /etc/xdg/autostart, but some others that I have personally added are editable.

Make sure your entry for network in your user startup applications settings in settings-manager is also selected, like mine; if not, tick the box and see if that helps.

---

### Post by 2CV67 on 2014-08-13
Thanks for your continuing interest!

In Session and Startup > Application Autostart, I do have an entry "Network (Manage your network connections)".
It is selected & is not editable.

On my same PC, I still have 12.04LTS as lifebelt & that continues to show the Network applet correctly.
I looked in /etc/xdg/autostart & found an item called "network".
The content is similar, but not identical to the item "nm-applet" in 14.04 - see below.

```
12.04 Network:
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

```
14.04 nm-applet:
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
AutostartCondition=GNOME3 unless-session gnome
X-Ubuntu-Gettext-Domain=nm-applet
```

I tried launching nm-applet directly, by double-clicking on it in etc/xdg/autostart, and got the following warning:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/warning_zps2ae6f72f.jpg[/IMG]

When I clicked on "Launch anyway", nothing happened...

If I open etc/xdg/autostart as Root & double-click on nm-applet, I get the same message, but if I then click to Launch anyway, then the applet appears as required...

That is as far as I can get...

---

### Post by 2CV67 on 2014-08-13
I opened /etc/xdg/Autostart and looked at the properties of nm-applet.desktop.
As Root, I checked the box for "Allow this file to run as a program" which was previously blank.
Double-clicking as user to launch it from /etc/xdg/Autostart gave no result (but no error message).
Double-clicking as Root put the applet on the panel as required.
So I thought that was it.

But on rebooting - no applet.

Using terminal > "nm-applet" gave a warning, did not launch the applet & left terminal with program running.
Using terminal > "sudo nm-applet" did launch the applet, but with a warning & left terminal with a program running.

I suppose there is a clue in the warnings in terminal for the 2 cases:

```
chris@Acer-desk:~$ nm-applet

** (nm-applet:3017): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-CKWffgcuAg: Connection refused
```

```
chris@Acer-desk:~$ sudo nm-applet
[sudo] password for chris: 

** (nm-applet:3056): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-CKWffgcuAg: Connection refused
nm-applet-Message: using fallback from indicator to GtkStatusIcon
```

Somewhere along the line, the item in /etc/xdg/Autostart which had been called nm-applet.desktop, with a generic-cog icon, has changed its name to Network, with a specific icon...

I am out of my depth here!

---

### Post by ajgreeny on 2014-08-13
> I am out of my depth here! 						
So am I; sorry I can't help more.

---

### Post by Toz on 2014-08-13
In 14.04, the Network Manager applet is displayed via the "Indicator plugin", not in the notification tray (I don't remember if it was different in 13.10 or not). Can you check to see if you have the Indicator Plugin added to the Panel?

You also have a ~/.cache/xfce4-indicator-plugin.log file that might yield some useful information.

---

### Post by 2CV67 on 2014-08-14
> **Toz said:**
> In 14.04, the Network Manager applet is displayed via the "Indicator plugin", not in the notification tray

Ah - that's the first I have heard of that.
Thanks very much for the information!

Indicator Plugin was not installed at all, so I installed it via SynApt then added it to the panel.
The Network applet then appeared OK in the panel!  :)
But along with lots of other items I don't really want.
I suppose I can hide them, but haven't got round to that yet.

The big new problem is that Indicator Plugin repeatedly "Unexpectedly leaves the panel"...

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/indicator_zpsf5912d80.jpg[/IMG]

I added it back half a dozen times, but it doesn't stick.   :(

Do I have to keep battling with Indicator Plugin, or is there hope of just getting the Network applet back in the notification tray?

---

### Post by Toz on 2014-08-14
Do you have indicator-appmenu installed? If so, you need to disable it from showing on the indicator plugin. See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606").

In that same dialog box, you can disable which other icons you don't want to appear.

---

### Post by 2CV67 on 2014-08-14
Thanks, Toz - you have hit the nail on the head exactly again!

Indicator-appmenu WAS installed (not by me - by default, I suppose).
Having hidden it by checking, Indicator-Plugin now seems stable, including the Network applet. :D
I will now gently try removing the unwanted items (all except the Network applet!) as you suggested.

Several thoughts:
I am EXTREMELY grateful that somebody like yourself bothers to read these posts, happens to know the answers & takes the trouble to respond!
I can easily understand & excuse that bugs happen & get past all the testing - that's why I am a late-adopter.
I find it less easy to understand why bugs with known solutions are still being distributed in LTS versions after 4 months.
I would somehow expect there to be a list of known problems & known workarounds to be available & targeted by corresponding requests to search engines, forums etc.
Replacing the existing fragmentary sticky "known bugs & workarounds" on the forum by a fuller version in list form might be helpful?

Anyway - THANKS again!

---

### Post by danemaslen on 2014-08-28
> **2CV67 said:**
> Indicator Plugin was not installed at all, so I installed it via SynApt then added it to the panel.
The Network applet then appeared OK in the panel!  :)

As I (appear to) have the same problem as you had, I've been trying to apply the solution that worked for you.  The first problem I encountered was that the reference to "Indicator plugin" did not enable me to identify the package that I needed to install using Synaptic Package Manager.  Eventually I came to the tentative conclusion that xfce4-indicator-plugin was the most likely answer.  Was I right?  I have reasons for doubting that I was: after the installation I can't find anything obvious in the list of items in 'Add to panel'.  What should I be looking for?

---

### Post by 2CV67 on 2014-08-28
Sorry, my xfce PC has just died (after 11 years) so I can't look at it to help you.
Hopefully Toz will come to the rescue again...

I am now struggling with new (& old) problems, dual-booting Unity 14.04.1 with Windows 8.1 - lots of fun ;)

---

### Post by Toz on 2014-08-28
> **danemaslen said:**
> As I (appear to) have the same problem as you had, I've been trying to apply the solution that worked for you.  The first problem I encountered was that the reference to "Indicator plugin" did not enable me to identify the package that I needed to install using Synaptic Package Manager.  Eventually I came to the tentative conclusion that xfce4-indicator-plugin was the most likely answer.  Was I right?  I have reasons for doubting that I was: after the installation I can't find anything obvious in the list of items in 'Add to panel'.  What should I be looking for?

Yes, the name of the package is xfce4-indicator-plugin, and the name of the plugin is "Indicator Plugin". Is it not listed?

What version of Xubuntu or Xfce are you using?

---

### Post by danemaslen on 2014-08-29
Ignore me!  Either I'm going mad or my netbook is.  I've now realised that although the symptoms I was seeing seemed identical to the original poster's, the problem was different (I'm not running Xubuntu).  Most puzzlingly as of this morning the Network Manager applet is appearing in my panel.  I swear it wasn't there yesterday and that I haven't successfully done anything to fix it.  Like I said, either I'm going mad or my netbook is (and I fear I know which of those is more likely to be the case).

---

### Post by atp2 on 2014-09-03
So the key solution for the original poster here, was to install the Indicator Plugin, but also to [post=13098098]disable indicator-appmenu[/post], (as described in [bug 1311606]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606"))?  And that gets you full correct nm-applet Network Manager support?

That sounds promising, thanks for the pointer!  I will check if that works for me once I have my laptop in front of me again...

For anybody else who has similar problems that were *not* fixed by the above, see also [network icon disappeared in xubuntu - Bug # 1302462]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1302462").

And here's some additional information as I understood it up till now:

The root cause of these problems seem to be that something is seriously buggy either with the "Indicator Applet" itself, or with its interactions with some other component.  But unfortunately I haven't seen a clear explanation of what (it's possible no one knows yet), nor even what the various different moving parts are.

What I found, is that with Xubuntu 14.04.1, the usual Ubuntu nm-applet that let's you control network access (pick which wireless network to join, etc.) was *completely gone* from the toolbar, like it never existed.  The workaround I used was simple, but cryptic:

In the Xubuntu settings menu thing, go to Session and Startup, Application Autostart, and then *disable* the "Indicator Application"
service.  This workaround is mentioned in the bug report above.  Once I did that, the nm-applet just suddenly appeared, on its own, on my toolbar.  Strangely, I did *not* have to explicitly add it.

Then I asked myself, wait, how the heck do I control the sound on this laptop?  On older versions of Ubuntu, there was always a little volume widget on the toolbar, but now it's gone.

Well, AFAICT Xubuntu 14.04.1 does not have any stand-alone volume widget at all, instead a volume slider is included in the "Indicator Applet"...  Which apparently is part of the default Xubuntu install, but I didn't remember *ever* seeing on my toolbar at all!  So I added the Indicator Applet to my toolbar, at which point the my nm-applet "Network" widget immediately disappeared.  I briefly saw that the Indicator included some sort of network control but it was crap, did not let me select which wirless network I wanted, completely useless compared to the normal nm-applet.  Worse, the Indicator Applet soon crashed, frequently and repeatedly, making it essentially unusable!

Even with the Indicator Applet removed from my toolbar, my Network widget does not come back until I again disable the "Indicator Application" service like above, and then log out and in again.
   
After some googling, I discovered that the Indicator Applet crashes are reported here:[INDENT]/var/log/apport.log
[/INDENT]
 Which then points to some sort of stack trace, e.g.:[INDENT]/var/crash/_usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.crash
[/INDENT]

---

