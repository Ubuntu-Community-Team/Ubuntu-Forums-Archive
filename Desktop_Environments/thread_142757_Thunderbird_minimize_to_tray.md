---
title: "Thunderbird minimize to tray"
date: 2006-03-11
forum: Desktop Environments
---

### Post by spencewah on 2006-03-11
I'm running the Ubuntu configured thunderbird build (1.0.7) 

I've been fiddling around with the options but I can't seem to find one that will let me minimize Thunderbird to the system tray. Is there one that I'm just missing? If not, is there some way to install this functionality?

---

### Post by OffHand on 2006-03-11
I don't know about version 1.07 and/or Linux but I got an extension in my Thunderbird 1.5 (on XP) that lets me minimize to the tray. It's also available for Firefox 1.5. (on XP). I forgot what it is called so you will have to find it yourself. 
Goodluck.

---

### Post by deck1 on 2007-03-04
A bit later, but have found an aplication that does it:

**Alltray**:

*With AllTray you can dock any application with no native tray icon (like Evolution, Thunderbird, Terminals) into the system tray.*

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

---

### Post by killabc on 2007-03-04
I'm using a extension New Mail Icon. Its excellent..Its minimize thunderbird to tray correctly and displayer message when i have a new mail.

---

### Post by 23meg on 2007-03-04
> **deck1 said:**
> A bit later, but have found an aplication that does it:

**Alltray**:

*With AllTray you can dock any application with no native tray icon (like Evolution, Thunderbird, Terminals) into the system tray.*

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

Keep in mind that Alltray doesn't have drag and drop support.

---

### Post by sintoris on 2007-03-11
The extension New Mail Icon can be found at: [http://moztraybiff.mozdev.org/releases.html]("http://moztraybiff.mozdev.org/releases.html")

---

### Post by zedfrugnug on 2007-04-30
I'd like to have thunderbird startup and minimize to tray at boot-up.
Has anyone tried this?

---

### Post by kodoku on 2007-04-30
> **zedfrugnug said:**
> I'd like to have thunderbird startup and minimize to tray at boot-up.
Has anyone tried this?

First, install [this]("https://addons.mozilla.org/en-US/thunderbird/addon/2110")

Then, install [this]("https://addons.mozilla.org/en-US/thunderbird/addon/2831")

I'm sure you can figure out the little individual settings :)

---

### Post by Kent84 on 2007-04-30
I'm sure the MinimizeToTray extension doesn't work in Linux.

---

### Post by zedfrugnug on 2007-05-08
I'm using alltray right now, but it doesn't work properly.
To start up thunderbird with alltray on boot up, I've added this command " alltray mozilla-thunderbird &" to sessions.
This does always start up TB on boot up, but not always with alltray:confused: 

Alltray also is inconsistent in use; somtimes closing TB will minimize it to tray and sometimes it will close altogether...

I'll try new mail icon later.

---

### Post by bunker on 2007-05-08
I had the same problems a while ago.  AllTray is pretty flaky and generally not worth the hassle; instead use kdocker.

```
kdocker -d mozilla-thunderbird &
```

In your startup script.  You can also run it without arguments and it will give you a little crosshair to click on windows to dock.

I use KDE, but according to their docs it will work on any NET WM compliant window manager - that includes GNOME.

Other decent alternatives to this are using gkrellm (which looks really sweet anyway ;)), or 'new mail icon' as advised above.

(Edit: spelling.)

---

### Post by renaux on 2007-10-10
> **kodoku said:**
> First, install [this]("https://addons.mozilla.org/en-US/thunderbird/addon/2110")

Then, install [this]("https://addons.mozilla.org/en-US/thunderbird/addon/2831")

I'm sure you can figure out the little individual settings :)HAHAHA, yeah works great w/ windows, but this isn't exactly a windows forum, the download pages you link to even say it's not available for linux, but you get an "A" for effort.
Regards,
Jason

---

### Post by j3x11 on 2007-10-28
> **bunker said:**
> I had the same problems a while ago.  AllTray is pretty flaky and generally not worth the hassle; instead use kdocker.

```
kdocker -d mozilla-thunderbird &
```

In your startup script.  You can also run it without arguments and it will give you a little crosshair to click on windows to dock.

I use KDE, but according to their docs it will work on any NET WM compliant window manager - that includes GNOME.

Other decent alternatives to this are using gkrellm (which looks really sweet anyway ;)), or 'new mail icon' as advised above.

(Edit: spelling.)

Just tried this.  This works excellent.  Thanks Bunker!

Also I would change your Thunderbird mail icon shortcut in your bar to reflect this also.  Right click it and then "properties". Modify the Command to "kdocker -d thunderbird %u".

---

### Post by apple_and _linux on 2007-10-30
> **bunker said:**
> I had the same problems a while ago.  AllTray is pretty flaky and generally not worth the hassle; instead use kdocker.

```
kdocker -d mozilla-thunderbird &
```

In your startup script.  You can also run it without arguments and it will give you a little crosshair to click on windows to dock.

I use KDE, but according to their docs it will work on any NET WM compliant window manager - that includes GNOME.

Other decent alternatives to this are using gkrellm (which looks really sweet anyway ;)), or 'new mail icon' as advised above.

(Edit: spelling.)

The kdocker works, but it quits as soon as I close the terminal!  And, when I reopen it, it doesn't dock Thunderbird.  I'll try gkrellm now...

---

### Post by itsjustarumour on 2007-11-09
> **Kent84 said:**
> I'm sure the MinimizeToTray extension doesn't work in Linux.

Alas, you are right.

[https://addons.mozilla.org/en-US/thunderbird/addon/2110](https://addons.mozilla.org/en-US/thunderbird/addon/2110)

"MinimizeToTray is not available for Linux".

---

### Post by Stephen Howard on 2007-11-09
I'm using New Mail Icon v1.2.3 - works nicely but you lose the 'feature' whereby incoming mail is displayed.

It is really irritating that Thunderbird doesn't come with built-in support for docking.  It seems a fundamental feature of any desktop mail client.

---

### Post by aysiu on 2007-11-09
If you use IceWM, you can minimize *any* application (including Thunderbird) to the system tray.

---

### Post by nutter78 on 2007-11-15
Try Alltray - just sudo apt-get install alltray

This app will minimize to tray any application - hope this helps  :)

---

### Post by itsjustarumour on 2007-11-20
> **zedfrugnug said:**
> I'm using alltray right now, but it doesn't work properly.
To start up thunderbird with alltray on boot up, I've added this command " alltray mozilla-thunderbird &" to sessions.
This does always start up TB on boot up, but not always with alltray:confused: 

Alltray also is inconsistent in use; somtimes closing TB will minimize it to tray and sometimes it will close altogether...

I'll try new mail icon later.

Works just fine for me!

---

### Post by Seto89 on 2007-12-23
Frankly, the new mail icon is not really solving the problem. It's able to place a permanent tray icon up there, but you still need to keep Thunderbird running, so instead of allowing you not to have it open fully, it just adds another icon at the tray...

I was more hoping for a Linux alternative to the minimize to tray add-on....

---

### Post by kneewax on 2008-01-20
Agreed it's a real flaw of TB not to have this support without extensions.  I have never liked having mail clients 'open' on the taskbar whether in Windoze or Linux.  I really like TB and have been using it in Win since the early Betas but since migrating to Ubuntu I am seriously thinking about dumbing it for something a bit more 'native'.  

Its a shame there isn't a suitable extension to minimise to the Ubuntu Panel - The minimise to tray extension in Windoze is excellent.  

Does evolution do this?

Cheers Kneewax

---

### Post by nemilar on 2008-01-23
There is a tutorial on how to get Thunderbird to minimize to the tray here: [http://www.techthrob.com/tech/thunderbirdtray.php]("http://www.techthrob.com/tech/thunderbirdtray.php")

---

### Post by kellemes on 2008-01-27
> **Kent84 said:**
> I'm sure the MinimizeToTray extension doesn't work in Linux.


Indeed, so instead you can use one of the following options..
[https://addons.mozilla.org/en-US/firefox/addon/4868](https://addons.mozilla.org/en-US/firefox/addon/4868)
[http://kdocker.sourceforge.net/](http://kdocker.sourceforge.net/)

---

### Post by G_u_s on 2008-01-27
> **Seto89 said:**
> Frankly, the new mail icon is not really solving the problem. It's able to place a permanent tray icon up there, but you still need to keep Thunderbird running, so instead of allowing you not to have it open fully, it just adds another icon at the tray...

I was more hoping for a Linux alternative to the minimize to tray add-on....

Actually, it seems that when you click on the icon up there, it masks the Thunderbird window, so the behaviour is the same than for any systray'able app.

Thanks to the guy who suggested this extension, it's just great =)

---

### Post by ivancamilov on 2008-03-12
Wow dude this is what I've been looking for (and I think everyone who posted here). Firetray is a really nice extension, thanks for posting this!

---

### Post by keithpitt on 2008-03-15
This worked for me:

[URL="http://www.techthrob.com/tech/thunderbirdtray.php"]http://www.techthrob.com/tech/thunderbirdtray.php
[/URL]
Keith

---

### Post by ublackwhiteu on 2008-03-27
well, but what about a plugin that works on both platforms?

I'm using thunderbird on ubuntu and vista and the "minimize to try" button always gives an error message when thunderbird is started in ubuntu. (of course it does, it can't find anything to be minimized into)

seems like I have to decide on which platform I want to enjoy the privilege of minimizing thunderbird to the tray :(

---

### Post by ivancamilov on 2008-03-27
But making this extension would be really challenging, since the 'tray' inUbuntu (either the Gnome Panel or it's equivalent in KDE) is substancially different from the System Tray in Windows.

---

### Post by ublackwhiteu on 2008-03-27
> **ivancamilov said:**
> But making this extension would be really challenging, since the 'tray' inUbuntu (either the Gnome Panel or it's equivalent in KDE) is substancially different from the System Tray in Windows.

it would be sufficient to have two different ways to do it for each plattform that just don't produce an error message on the other platform.
the alltray works fine, so basically all that's needed is an windows minimizing-plugin that doesn't produce the error message when opened in ubuntu :)

---

### Post by ublackwhiteu on 2008-03-30
guess I found the answer to the problem

how-to minimize thunderbird (or firefox) to the system tray - when using its profile cross plattform (ubuntu & windows)

**ubuntu**
alltray only works every 3rd or 4th time I actually click on it so:

1. get [kdocker]("http://kdocker.sourceforge.net/") (also available in the packets)
2. go to *System-->preferences-->main menu*
*applications-->internet-->thunderbird* and doubleclick on thunderbird
write **kdocker thunderbird %u** in the command line

now thunderbird will always appear in the system tray when started :)


**windows**
the "minimize to tray" mozilla-plugin produces an error message in ubuntu. don't use it / uninstall it. instead:

1. get [TrayIt]("http://www.teamcti.com/trayit/trayit.htm") (free software, read the page :) )
2. simply unpack it in any folder you want and run the *.exe
now you can minimize *any* application to the system tray by *pressing Ctrl + click on minimize*


now you can use thunderbird cross platform and minimize it on ubuntu and windows without any error messages :)

---

### Post by StiveG on 2008-04-01
Kdocker : Exactly what I was looking for, it works!

Thanks!!

---

### Post by aspora.isernia on 2008-05-23
Hi guys,
I installed firetray (0.1.8) for thunderbird: it shows the icon in the systray, but the option "Close button minimizes to tray" does not work at all. I'm the only one with this problem?
My system is Hardy Herod and Thunderbird is version 2.0.0.14 (20080505).

---

### Post by prince_niceguy on 2008-05-27
I am using "New Mail Icon". It minimizes thunderbird to the tray when you click on the icon in the tray. I think that is sufficient for me.

---

### Post by sciurus on 2008-06-27
[Firetray]("http://code.google.com/p/firetray/downloads/list") ( firetray_0.1.9_x86_64.xpi) is working great for me with Thunderbird (2.0.0.14). After turnign the feature on in the firetray preferences, the close button minimizes thunderbird to the tray.

---

