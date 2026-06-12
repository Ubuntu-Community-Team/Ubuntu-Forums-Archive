---
title: "awn applets showing up as white lines, awn works otherwise"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by weezerisrock on 2007-11-08
I am having this problem, I've removed the windows list from my gnome panel, and everything shows up ok in awn, even my shortcuts however, my applets are not showing up.  None of them except the taskmanager.  They all show up as white lines.

Here is my code when I run it in terminal

```
Screen is composited.
LOADED : /home/mckayr/.config/awn/launchers/awn_launcher-1.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/lib/awn/applets/weather.desktop

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
Traceback (most recent call last):
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 8, in <module>
    import awn
ImportError: No module named awn
Traceback (most recent call last):
  File "/usr/lib/awn/applets/weather/weather.py", line 30, in <module>
    import awn
ImportError: No module named awn

```

I imagine I have to be missing something for that many warnings and criticals lol, can anyone help me out?

Thanks

---

### Post by rainwalker on 2007-11-08
Only a few of mine don't work; the Gmail Checker, Notification Area, and Stacks
None of them have ever worked for me, though. They always just appear as a white line, same as you.

I'll let you know if I figure anything out

---

### Post by itsjustarumour on 2007-11-10
> **rainwalker said:**
> Only a few of mine don't work; the Gmail Checker, Notification Area, and Stacks
None of them have ever worked for me, though. They always just appear as a white line, same as you.

I'll let you know if I figure anything out

Hi Rainwalker,

I'm getting EXACTLY the same problem as you, all the icons look fine apart from those for Gmail Checker, Notification Area and Stacks which just show as vertical white lines. Really scratching my head on this one, maybe its just a bug with AWN although I haven't researched it yet....

itsjustarumour

---

### Post by itsjustarumour on 2007-11-10
OK, from the official AWN Wiki at [http://wiki.awn-project.org/index.php?title=FAQ](http://wiki.awn-project.org/index.php?title=FAQ)

Q: "Why does my bar have one or more thin, vertical, white lines that extend beyond the dock?"

A: "Most likely, there is a problem with one or more of your applets. One of the most common problems is with the notification area applet. You need to remove all system trays/notification areas from your existing panels before you can use AWN's. To figure out what the problem is with other applets, run AWN via the command prompt, determine which applet(s) is/are causing the errors by analyzing the error output, and reporting bugs via Launchpad or the forum, depending on whether you got the applet from Awn Extras or separately from the forums, respectively."

---

### Post by itsjustarumour on 2007-11-10
I've found a way to make the GMail checker applet appear - it requires that python-libgmail be installed:

> sudo apt-get install python-libgmail

Now try adding it in again as normal and it should appear.  I still can't get rid of the notification "bubble" though!

---

### Post by jimerickso on 2007-11-10
thanks itsjustarumour! now if i could just get the other applets to work!

---

### Post by itsjustarumour on 2007-11-11
> **jimerickso said:**
> thanks itsjustarumour! now if i could just get the other applets to work!

No worries, and I even got rid of the notification bubble after a reboot!  Don't seem to be able to customise the applet though - I have to enter my GMail login details every time I restart my machine, and theres no indication as to how often its polling my POP account.  Maybe theres a  config file somewhere....

---

### Post by ryodoan on 2007-12-03
Well, thanks to this post the gmail applet no longer appears as a white line, however, the aRSS applet still is not working for me.  It shows up as a white line.  Any ideas on what I might need to install to make it start working?

And any further information on if there is a config file for AWN / applets?

---

### Post by robusch on 2007-12-16
> **ryodoan said:**
>  the aRSS applet still is not working for me.  It shows up as a white line.  Any ideas on what I might need to install to make it start working?

From the [AWN Wiki ]("http://wiki.awn-project.org/index.php?title=RSS_Applet") - "Requires feedparser (python-feedparser, xdg-utils)"

So, 
```
sudo apt-get install python-feedparser xdg-utils
```

xdg-utils was already installed on my machine..


Also, you need to create a feedlist file at "~/.config/awn/applets/.feedlist" containing your feeds. (One feed per line)

Once I did the above, the applet worked great.

---

### Post by Beaucephus on 2007-12-21
I fixed my problems with the white lines by installing the package **python-libawn0**.  Removing the existing buttons from my other panels like the FAQ suggested did nothing.

The error I was getting from the apps referenced a certain line number and said  ```
ImportError: No module named awn
```

The offending line was always 

```
import awn
```

Working sweet now with that undocumented dependency satisfied.

---

### Post by fluteflute on 2008-01-25
Thank you. 
```
sudo aptitude install python-libawn0
```
and now everything works!

---

### Post by xecure on 2008-01-30
```
sudo aptitude install python-libawn0
```I have done that yet, the GMail app still does not work for me

---

### Post by The Hunt For Ida Wave on 2008-02-07
I'm having a the same problem (four vertical white lines displayed) only it's my show desktop icon that's bugging up.

---

### Post by billybag on 2008-03-03
i am having the same problem. i have the curved version of AWN installed and when i try to install libawn0 and pythonawn, it wants to get rid of pretty much my wwhole AWN install. i think because my AWN is v3.1 and lib and pyth are 2.1

any ideas?

---

### Post by xecure on 2008-03-03
ok guys i up dated to a newer version of AWN and it comes with a working versioin of mail applet. you can get a working version without updating by goign here: [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1440&page=1&isLive=true]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1440&page=1&isLive=true")

---

### Post by borobudur on 2008-03-03
[robusch]("http://ubuntuforums.org/member.php?u=34222")  works great for me too. Thanks!

---

### Post by al-fil on 2008-04-02
I'm getting three vertical lines:
```
Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/separator.desktop

** (awn-applet-activation:12490): WARNING **: This desktop file does not exist /usr/lib/awn/applets/main-menu.desktop


** (awn-applet-activation:12488): WARNING **: This desktop file does not exist /usr/lib/awn/applets/separator.desktop


** (awn-applet-activation:12492): WARNING **: This desktop file does not exist /usr/lib/awn/applets/separator.desktop
```
What am I missing?

---

### Post by al-fil on 2008-04-02
OK problem solved.
1) did a complete removal:
[http://ubuntuforums.org/showthread.php?t=685928]("http://ubuntuforums.org/showthread.php?t=685928")
2) then did a fresh install from repository:
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

---

