---
title: "Sessions not showing up (login screen)"
date: 2011-02-24
forum: Desktop Environments
---

### Post by Ir0nMa1deN on 2011-02-24
[IMG]http://4.bp.blogspot.com/_KsoXvaxfuyk/S9MR0pa4uxI/AAAAAAAAASk/izFxsFL9U3c/s1600/lxde-ubuntu-installation-10-04-7.png[/IMG]

That little menu on the bottom doesn't show up for me. I just installed kde from synaptic and rebooted the computer. Since I have ubuntu set to automatically log me in it did and I manually logged out to get to the login screen and get into KDE. As I said before it didn't show up so I just logged back in and ran "startkde" in a terminal. The KDE desktop is there but the Ubuntu menu bar is still on the top (with some missing icons :-?) The KDE menubar on the bottom shows up with all the icons and everything but the minimized windows are all messed up (like shadow text or something). Anyway, is there some way for me to get the SESSIONS menu onto my login screen so that I can get into KDE the normal way?

---

### Post by Krytarik on 2011-02-26
Did you mind that you have to enter/click your username before, to get those Session options!?

---

### Post by doublewitt on 2011-03-05
I'm having a similar problem:

the normal login screen does not appear, and the bottom toolbar either - all I have is a direct login screen to the kde desktop - and from there, i cannot choose gnome anymore...

what happened...? I wouldn't know!
how can I fix this?
any help would be appreciated...

---

### Post by Krytarik on 2011-03-05
@doublewitt: Are you somehow able to provide a screenshot of those screen? Because I don't really know what you have there, it may be KDM (instead of GDM), but those should also provide the session options.

---

### Post by doublewitt on 2011-03-05
> **Krytarik said:**
> @doublewitt: Are you somehow able to provide a screenshot of those screen? Because I don't really know what you have there, it may be KDM (instead of GDM), but those should also provide the session options.

I don't know how to make a screenshot when the KDM screen appears... but there is no "option" to choose session (GDM)...

---

### Post by Krytarik on 2011-03-06
Check if "gdm" is installed:
```
dpkg -l|grep gdm
```
If so, use this command to choose it:
```
sudo dpkg-reconfigure gdm
```
If not, install it:
```
sudo apt-get install gdm
```

---

### Post by doublewitt on 2011-03-06
Thanks - this helped somewhat. This is what I got in the terminal:

[I]doublewitt@InfoDesk:~$ dpkg -l|grep gdm
ii  gdm                                            2.30.2.is.2.30.0-0ubuntu5                               GNOME Display Manager
rc  gdm-guest-session                              0.15                                                    gdm extension for guest session
ii  python-gdm2setup                               0.5.3-lucid-1                                           GDM2 Setup utility and libraries
doublewitt@InfoDesk:~$ sudo dpkg-reconfigure gdm
[sudo] password for doublewitt: 
doublewitt@InfoDesk:~$ sudo apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
doublewitt@InfoDesk:~$[/I] 


now when I restart my computer, the normal login window does appear - but - on the bottom toolbar, the available sessions are KDE and XTERM - no GNOME...

---

### Post by Krytarik on 2011-03-06
Assuming that you still have Gnome installed, check the available sessions in "/usr/share/xsessions". There should be

gnome.desktop:
```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```gnome-failsafe.desktop:
```
[Desktop Entry]
Name=Failsafe GNOME
Comment=This session logs you into GNOME without user applications
Exec=gnome-session -f
TryExec=gnome-session
X-GDM-FailSafe=true
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```To check if Gnome is indeed installed:
```
dpkg -l|grep ubuntu-desktop
```This checks for the usual Ubuntu Gnome metapackage. You can also check for "gnome", this should list quite a number of packages.

---

### Post by doublewitt on 2011-03-07
In the folder you mention, I only have the two (KDE and xterm). So what happened to Gnome...?! Anyways, the gnome and the gnome-failsafe are NOT there. I guess there is a way to fix that. Ofcourse, that's beyond me...

running the command in the terminal: [COLOR="Blue"]dpkg -l|grep ubuntu-desktop[/COLOR]
does nothing.

@Krytarik - thanks for your help thus far... I feel like we're getting closer to the solution...

---

### Post by Krytarik on 2011-03-07
> **doublewitt said:**
> 
running the command in the terminal: [COLOR=Blue]dpkg -l|grep ubuntu-desktop[/COLOR]
does nothing.

LOL ;-)  Then you might have removed it by following one of those instructions to install KDE!?
Anyway, just install it then:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by doublewitt on 2011-03-07
Oh thank you so much - that did the job!!!
Now I have in sessions options - GNOME and FAILSAFE.
Wow, I'm back to my world now... I feel so good!

Nonetheless, I'm still bewildered about gnome disappearing...

@Krytarik - thanks again...

---

### Post by ImTheBatman on 2011-03-09
Sorry for bumping this thread, but I am having the same problem and the fix mentioned in the first page (reconfiguring GDM) did not work for me (I have GDM installed already). I get to the user selection screen with an almost blank toolbar at the bottom (there's a shutdown button and something about accessibility options, and that's it).

Anyone has any ideas?

---

### Post by ImTheBatman on 2011-03-09
Okay, my situation got worse - I used the login screen settings to edit the default session to KDE, but now I can't return to GNOME - the "Unlock" button in the login settings is unpressable and if I manually edit GDM's config file it still logs on to KDE (even though I set it to gnome)

...What do I do now?

---

### Post by Krytarik on 2011-03-09
First, the "Session" (and other) options only appear *after* you clicked your username.

The default session in "/etc/gdm/custom.conf" doesn't have an effect if the concerning user already logged in at least one time, then the session stored in the users "~/.dmrc" will be run by default.

And please post the content of "/etc/gdm/custom.conf".

---

### Post by ImTheBatman on 2011-03-09
> **Krytarik said:**
> First, the "Session" (and other) options only appear *after* you clicked your username.

The default session in "/etc/gdm/custom.conf" doesn't have an effect if the concerning user already logged in at least one time, then the session stored in the users "~/.dmrc" will be run by default.

And please post the content of "/etc/gdm/custom.conf".
I finally managed to get back to GNOME by removing KDE's *.desktop files from the xsession directory. The content of my custom.conf file is (and this didn't change since I manually edited it as I mentioned in the previous post):
```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=batman
TimedLoginEnable=false
TimedLogin=batman
TimedLoginDelay=10
DefaultSession=gnome
```Now I'm left with the GDM sessions thing. When I click on my username in GDM it automatically logs in. Is that an expected behavior or is something wrong?

---

### Post by ImTheBatman on 2011-03-09
Okay, I noticed something weird - if I set KDM as the default session manager, everything works fine and I can choose the session from their session list. However, KDM requires me to enter my user's password upon logging in, which GDM does not (this is weird considering I do have a password set up and I do have to use it for sudo and the likes).

---

### Post by Krytarik on 2011-03-09
I really wouldn't remove KDE's session files.

Regarding the non-existent password query, check in "System -> Administration -> Users and Groups" if the password query on login is disabled.

---

### Post by ImTheBatman on 2011-03-09
> **Krytarik said:**
> I really wouldn't remove KDE's session files.

Regarding the non-existent password query, check in "System -> Administration -> Users and Groups" if the password query on login is disabled.
ALRIGHT! As I suspected, the cause of the session issue was the lack of password query. I enabled it and bam, the toolbar with the sessions and all appeared.

Thank you for helping, and I hope someone at GNOME reads this thread and will fix it because I really can't seem to find a link between password querying and session management.

---

