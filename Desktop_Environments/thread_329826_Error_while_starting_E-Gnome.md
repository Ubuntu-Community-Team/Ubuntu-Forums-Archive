---
title: "Error while starting E-Gnome"
date: 2007-01-02
forum: Desktop Environments
---

### Post by yooden on 2007-01-02
Hi,

I just installed Edgy on my notebook after running Debian Woody and Sarge for a few years. So far I'm getting mixed results, hardware is detected almost completely (took me a while on Woody/Sarge) but I cannot enter known hosts in /etc/hosts without killing network-admin. Doh.

Now my notebook is pretty slow (867MHz Crusoe), so I want to use Enlightenment instead of whatever Gnome suggests. E starts up fine on its own (and is noticeable faster), but I get an error trying to start the session named 'E-GNOME' from GDM. Here is what my ~/.xsession-errors says:
```

Xsession: unable to launch "starte16 GNOME" X session --- "starte16 GNOME" not
found; falling back to default session.

```

I can't find Edgy's files which manage these sessions, nor could I google anything about this error. 'starte16' does exist twice on my system, once in /usr/bin and once in /usr/bin/X11.

What could be the reason for the error? What could I do to learn more?

tia,
Yooden

---

### Post by Dot Communist on 2007-01-02
i get this same issue id like a fix too :]

---

### Post by cleardays on 2007-01-04
I have the same problem, I check my computer, I have the command 'starte16' but it is located in directroy of '/usr/bin/starte16',  THen I make a link to '/usr/sbin/',  it works! try yours:)

---

### Post by yooden on 2007-01-04
> **cleardays said:**
> I have the same problem, I check my computer, I have the command 'starte16' but it is located in directroy of '/usr/bin/starte16',  THen I make a link to '/usr/sbin/',  it works! try yours:)

Thanks, but that doesn't seem to help, I get the same error message.

---

### Post by andy gee on 2007-01-28
Same problem here. I downloaded Enlightenment through the Ubuntu repos. Enlightenment works fine - and fast - but I'm missing Gnome apps, so I tried the E-Gnome option that was auto installed into the graphical login sessions options list, and got the same error:

Xsession: unable to launch "starte16 GNOME" X session --- "starte16 GNOME" not
found; falling back to default session.

I changed the default to E-Gnome, and it still reverts to the default I had before that (XFCE). I haven't had time to try the advice given above, does it work for everyone? Any other ideas?

---

### Post by cephalon on 2007-01-29
[CENTER][/CENTER]

Anyone found anything yet?  I found a E-GNOME executable in /usr/share/doc/enlightenment/examples that calls "exec /etc/X11/xdm/Xsession e-gnome"  

Not so sure what this means exactly, or how to take a look at what the individual Sessions are calling, but it's interesting, nonetheless.

If anyone has any ideas, lets keep this thread going -- it sounds like a lot of us are having issues.

---

### Post by andy gee on 2007-01-31
Just tried the suggestion to > make a link to '/usr/sbin/' from /usr/bin/starte16, and unless I've linked it incorrectly (it seems ok) it doesn't work for me either (Edgy, E16 from repos).

Yes, lets keep this open. I want my E-Gnome!

---

### Post by tjk on 2007-02-05
I'm another one that needs an answer to this situation  -- can anyone help?

---

### Post by yooden on 2007-02-05
This is now Bug #83380: [https://launchpad.net/ubuntu/+bug/83380](https://launchpad.net/ubuntu/+bug/83380)

---

### Post by andy gee on 2007-02-07
Thanks for posting the bug, yooden.

:)

---

### Post by qx48 on 2007-02-10
Hi. i'm probably very new at this. 
i've installed e16 and can access it, but can't see or access any of my applications (or know how to). ideally, i'd be running this e-gnome, but i have the same problem. i tried the "bug#83380" link, and cannot tell whether this problem has been solved yet. any help is greatly appreciated.

---

### Post by yooden on 2007-02-10
Could you please use capitals where appropriate? That would make you posts easier to read, esp. for foreigners.

> **qx48 said:**
> i've installed e16 and can access it, but can't see or access any of my applications (or know how to).

Try the three mouse buttons on the background. You should get a menu.

> **qx48 said:**
> ideally, i'd be running this e-gnome, but i have the same problem. i tried the "bug#83380" link, and cannot tell whether this problem has been solved yet.

Read the bug report carefully and you will find out. There is also a status at the top.

---

### Post by andy gee on 2007-02-17
Dear qx48,
> Hi. i'm probably very new at this.  Most people here are also new at this, don't let it phase you. As far as E-Gnome using E16 from the repos goes, I have given up on it. From what I've read on the bug reporting, there is no solution to the E-Gnome problem yet. I still use Gnome mostly - it's slow for me, but stable. 
> i've installed e16 and can access it, but can't see or access any of my applications (or know how to)
I also had the same problem - none of the mouse buttons worked the way they were supposed to, and I couldn't access any applications, either. I fixed it, but I can't remember how. Sorry!

There are a few alternative, depending on whther you want the speed of E16, or just want something sexier than Gnome. I've used the window managers/desktop environments below at some point and can recommend them. The first four are minimal and fast, the last ones are sexy as hell, but don't speed things up and have not been very stable for me.

1. Try E17. Look at [http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17]("http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17"),  and [http://www.ubuntuforums.org/showthread.php?t=20216&highlight=e17]("http://www.ubuntuforums.org/showthread.php?t=20216&highlight=e17"). Although E17 is still in development and crashes for me sometimes, it's otherwise stable and *very* fast. There's also a lot of eye candy, but importantly it is quick. It's not hard to install - I've been using Linux for less than 6 months, and if I can install and manage it, so can you. The only disadvantage to E17 is that it doesn't ship with a desktop you can work from (ie put icons and shortcuts on), and I haven't found an add-on one that I like. It has excellent instructions at start, lots of themes, and the mouse buttons work properly. IMHO it's better than E16.

2.  Xfce (with Ubuntu is Xubuntu) is also great. It's fast, has a desktop you can put things on, a file manager - its now a full desktop environment. With Xfce 4.4, you can even add Gnome applets to the panel - the ones you can't do without and prevented you from trying another desktop environment. There's nothing you can do in Gnome that you can't in Xfce4.4, and lots you can do in Xfce you can't do in Gnome - compositing eye candy and screen warping, for example.However, it's second on the list, since its filer, thunar, keeps crashing for me. 

3. Fluxbox, Blackbox, Openbox, Icewm, etc. These are minimal window managers that are not fast - they're *BLINDINGLY* fast, even on old machines. Most do screen warping, which is not in Gnome. They tend to take time to customise, and most do it through scripts. Not hard, but be prepared to learn more about Linux. There is no desktop with icons, no file manager, no pager, you have to find them and install them and configure them youself. Not hard, just time consuming.

4. Fvwm crystal. This was a surprise, since fvwm is really not my cup of tea. Fvwm crystal is nice, minimal, fast, and looks good. very stable too. Configuration is a snap too. Couldn't find a desktop for it though.

There are lots more minimal window managers. Google or do a search on synaptic for 'window manager'.

If you have a fast machine though, maybe you want something sexy, like a 3d desktop or wobbly windows. Google 'Compiz' and 'Beryl' - again, theres some work in them, and Beryl especially has had its stability problems on my machine, but you'll learn alot doing it and a tremendous sense of satisfaction once you get them installed. If they were stable and quciker for me, I'd only ever use Xfce and Beryl, but since I have an old machine and not much patience, I only ever use it if I'm not in a hurry.

One thing about eye-candy is that it can actually make work easier. Take beryl - you can set windows deform as you move them, wiggle a bit as they stop (fun, but also makes them feel more real to me), and I never have to think about where things are, since a quick flick of the mouse to a corner brings up all my windows, minaturised on one screen. I just have to click on the one I want.

If I had a core 2 duo machine with a couple of gigs of RAM I'd use Beryl and Gnome or more probably Xfce. With the way things stand now, I'm usually using E17 and Xfce 4.2 most of the time, and Gnome when I have. The beauty of Ubuntu is that I can choose from between 20 (at last count) different window managers or desktop environments at login, and installation is easy.

I hope this long ramble helps.

And now for my question to everyone - can one use a compositor like Beryl with E17? Now *that* would be sexy as hell!

---

### Post by P235 on 2007-02-21
From the bug report:


> 
It seems that the Exec option requires a script w/o a parameter. Here's what I did with my setup (I used e-kde but should work with e-gnome as well). Note that you must be root to do this:

Create a script /usr/bin/startekde with the following two lines:

#!/bin/sh
/usr/bin/starte16 KDE

Save then chmod a+x /usr/bin/startekde

Then edit /usr/share/xsessions/-e-kde.desktop and change the Exec= option to:

Exec=/usr/bin/startekde

Logout from your GUI then hti Ctrl-Alt-Backspace to restart login manager.


Can someone translate this into a gnome solution rather than a kde solution for me?

Also chmod a + x means...?  x for execute? a for?

---

### Post by Simon Bridge on 2007-02-24
To boot into E-Gnome...

You need to edit /usr/share/xsessions/egnome.desktop so it looks like the one below:
```
[Desktop Entry]
Encoding=UTF-8
Name=E-Gnome
Comment=Log in Gnome using E16 as WM
Type=XSession
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/start-egnome
Exec=gnome-session
TryExec=/usr/local/bin/e16

```

For this to work, you have to create the file /usr/bin/start-egnome with the contents below:
```
#!/bin/sh
# Hack to get Gnome to start with E16 as the WM
# called from /usr/share/xsessions/egnome.desktop
/usr/local/bin/starte16 GNOME

```

I trust I don't need to feed anyone *here* the commands to do all this editing and creating? :)

---

### Post by Simon Bridge on 2007-02-24
While we are on the subject - if anyone installs Enlightenment 0.16.8x (from source or CVS - the version in repos is 0.16.7x) ten the configuration directory has changed, and you won't be able to access the old themes or backgrounds (or anything else).

The documentation hasn't been updated to reflect this.

The new config directory is: ~/.e16/
The old config directory is: ~/.enlightenment/

So to get your backgrounds, um, back ...

mv ~/.enlightenment/backgrounds/* ~/.e16/backgrounds/

You'll need to install themes by CVS or source as well.
Third party (user supplied) themes will need to go in ~/.e16/themes and so on.

There are some changes to the way E16 hadles theming and so forth, so it is not safe to just replace the content of ~/.e16 with the content of ~/.enlightenment to get your old configuration.

This is quite useful from a development POV as it allows you to have two versions of E16 available for comparison: the prev release which in the starting point, and the new release that you're working on.

It also allows a more companionable relationship with DR17, whose config winds up in ~/.e/e ... though my crystal ball says this will turn into ~/.e17/e when version number 0.18 is finally out (or maybe as soon as when 0.17.0 is out, DR17 = verno 0.16.9999.)

And a caveat for those contemplating E17 via aptitude ... apt seems to consider E17 as an upgrade on E16... and will replace packages (at least this happened to me) with otherwise the same name.

I'm trying to find the actual data for the documentation so maybe it can be updated. Developers notoriously hate writing documentation... anyone know anything?

---

