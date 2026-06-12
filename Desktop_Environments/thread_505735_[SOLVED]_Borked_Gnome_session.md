---
title: "[SOLVED] Borked Gnome session"
date: 2007-07-20
forum: Desktop Environments
---

### Post by supreme_geek_overlord on 2007-07-20
Hi everyone,

A while back, while trying to make Beryl start up more seamlessly, I ignorantly tinkered around with the "Sessions" configuration applet and, after clicking the "Save the current session" button, ended up messing up my Gnome session completely.

Now when I log in, the splash screen get as far as "Panel", and then stops. Though the system functions fine in the background, it is obvious that some programs (including Beryl) haven't started up. However, after an arbitrary time out (~1-5 minutes I suppose), the system fires to life again, and the rest of the programs start up as they should.

Here is my ~/.gnome2/session file:

```

[Default]
0,id=117f000101000118020692000000055580005
0,RestartStyleHint=1
0,Program=update-notifier
0,CurrentDirectory=/home/tim
0,CloneCommand=update-notifier --sm-config-prefix /update-notifier-TKvhhA/
0,RestartCommand=update-notifier --sm-config-prefix /update-notifier-TKvhhA/ --sm-client-id 117f000101000118020692000000055580005 --screen 0
1,id=117f000101000118020692100000055580008
1,RestartStyleHint=2
1,Priority=50
1,Program=gnome-cups-icon
1,CurrentDirectory=/home/tim
1,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-OdY9eA/
1,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-OdY9eA/ --sm-client-id 117f000101000118020692100000055580008 --screen 0
2,id=117f000101000118020692200000055580010
2,Program=evolution-exchange
2,CurrentDirectory=/
2,CloneCommand=evolution-exchange --sm-config-prefix /evolution-exchange-08V2PC/
2,RestartCommand=evolution-exchange --sm-config-prefix /evolution-exchange-08V2PC/ --sm-client-id 117f000101000118020692200000055580010 --screen 0
3,id=117f000101000118020691600000055580001
3,RestartStyleHint=2
3,Priority=40
3,Program=nautilus
3,CurrentDirectory=/home/tim
3,CloneCommand=nautilus --sm-config-prefix /nautilus-tGSFhA/
3,RestartCommand=nautilus --sm-config-prefix /nautilus-tGSFhA/ --sm-client-id 117f000101000118020691600000055580001 --screen 0 --load-session /home/tim/.nautilus/saved-session-6N5XST
4,id=117f000101000118020691600000055580002
4,RestartStyleHint=1
4,Priority=40
4,Program=gnome-volume-manager
4,CurrentDirectory=/home/tim
4,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-ro82MC/
4,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-ro82MC/ --sm-client-id 117f000101000118020691600000055580002 --screen 0
5,id=117f000101000118020691600000055580000
5,RestartStyleHint=2
5,Priority=40
5,Program=gnome-panel
5,CurrentDirectory=/home/tim
5,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-ohIuhD/
5,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-ohIuhD/ --sm-client-id 117f000101000118020691600000055580000 --screen 0
6,id=117f000101000118020691900000055580004
6,Program=gnome-power-manager
6,CurrentDirectory=/home/tim
6,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-DNfPKC/
6,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-DNfPKC/ --sm-client-id 117f000101000118020691900000055580004 --screen 0
7,id=117f000101000118020692100000055580006
7,RestartStyleHint=0
7,Program=evolution-alarm-notify
7,CurrentDirectory=/home/tim
7,CloneCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-0iiWHC/
7,RestartCommand=/usr/lib/evolution/2.10/evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-0iiWHC/ --sm-client-id 117f000101000118020692100000055580006 --screen 0
9,RestartCommand=beryl-manager
10,RestartCommand=restricted-manager --check
11,RestartCommand=/usr/lib/evolution/2.10/evolution-alarm-notify
12,RestartCommand=nm-applet --sm-disable
13,id=117f000101000118020691700000055580003
13,RestartStyleHint=2
13,Priority=20
13,Program=metacity
13,CurrentDirectory=/home/tim
13,RestartCommand=gnome-wm --sm-client-id default0
num_clients=14
```I realize I could just delete that file, but I see that /usr/share/gnome/default.session is generic Gnome, not Ubuntu-specific, and I would like to restore the session back to how it was after a fresh install.

Does anyone have an example *working* session file that I could use, or perhaps a better idea altogether? Thanks in advance.

(Oh, by the way, I just noticed that Metacity entry at the bottom my session file. Does that need to be there, since Beryl à la Emerald is working just fine?)

---

### Post by kevinlyfellow on 2007-07-20
Unfortunately that is what happens when you start Beryl up "seamlessly".  You succeeded in what you needed to do, but there are bugs in beryl.  Same goes with compiz fusion.  I'd recommend putting compiz --replace back into the startup programs.

---

### Post by supreme_geek_overlord on 2007-07-21
Alright, but where should I put it?

To clarify, I don't really know what changed in my session file--I only know that it hasn't worked since I "saved" the session. I imagine that more than one thing needs to be corrected, so unless you know I'm wrong, then the easiest way to fix this problem is to start from scratch. The problem is, I don't have what I need to do that (namely, a pristine session file).

Besides, I'm a little confused as to all the XGL/Beryl/AIGLX/Compiz terminology, but since I'm running Beryl over (I believe) the new nVidia drivers, I don't think "compiz --replace" is what I want.

---

### Post by kevinlyfellow on 2007-07-21
> **supreme_geek_overlord said:**
> Alright, but where should I put it?

To clarify, I don't really know what changed in my session file--I only know that it hasn't worked since I "saved" the session. I imagine that more than one thing needs to be corrected, so unless you know I'm wrong, then the easiest way to fix this problem is to start from scratch. The problem is, I don't have what I need to do that (namely, a pristine session file).

Besides, I'm a little confused as to all the XGL/Beryl/AIGLX/Compiz terminology, but since I'm running Beryl over (I believe) the new nVidia drivers, I don't think "compiz --replace" is what I want.

To start over with the gnome-session-properties, I'm pretty sure that you can just rename the sessions file and let gnome figure out what defaults to use (don't remove it until you know everything is ok).  Alternately, what you can do is close every program that you do not want to start up automatically through the gnome-sessions tool (middle tab) and then remove all additional startup programs that you don't want to use (first tab) and then save your session.  gnome-session-properties is a headache imo.

beryl --replace is probably necessary (sorry about the mix up in the previous post, beryl and compiz are similar window managers, which now have merged as compiz fusion).  There are a number of ways to start up a window manager (beryl is a window manager, like metacity, and gnome runs on top of it).  The best option imo is just to add 'beryl --replace' under the startup programs tab in gnome (if you use gnome).  If you use emerald, then you may need to do this instead 'beryl --replace && emerald --replace'  If that doesn't suit you, we can find one that works for you.

---

### Post by supreme_geek_overlord on 2007-07-23
> **kevinlyfellow said:**
> To start over with the gnome-session-properties, I'm pretty sure that you can just rename the sessions file and let gnome figure out what defaults to use (don't remove it until you know everything is ok). [...]  gnome-session-properties is a headache imo.

Yeah, since clicking one button apparently took my session beyond repair, I've given up on gnome-session-properties.

I've also been aware of the option to just move/delete the user-specific session file, but the reason I wanted to ask first was that *the system default, /usr/share/gnome/default.session, doesn't look like it has Ubuntu-specific elements in it*. I am not using my Ubuntu system currently, but the "update-notifier" comes to mind as an example: there is no reference to it in the default.session file, but shouldn't it be started up by gnome-session? (Maybe it was only added to the user session file after I messed it up, but I doubt that.)

I thought perhaps someone would be able to quickly give me a good pristine Ubuntu session file, but it's becoming obvious that deleting the file and piecing it back together manually is going to be easier. No big deal I suppose--thanks anyway.

> (sorry about the mix up in the previous post, beryl and compiz are similar window managers, which now have merged as compiz fusion).That's alright, there are too many to keep track of... I miss the quaint old days of Metacity. ;)

Yes, though, I do believe that "beryl --replace" was what I was using before. In any case, that wasn't my main issue, and I'm sure I'll be able to figure it out. Thanks.

---

### Post by kevinlyfellow on 2007-07-24
> **supreme_geek_overlord said:**
> I thought perhaps someone would be able to quickly give me a good pristine Ubuntu session file, but it's becoming obvious that deleting the file and piecing it back together manually is going to be easier. No big deal I suppose--thanks anyway.

One way to get a 'pristine' one is to just create a new user account and steal the one for the new user.  I'm not convinced that it will give you anything different than if you were to just delete the file.

---

### Post by supreme_geek_overlord on 2007-07-24
Good idea. I'll check it out, and see if it's any different. Thanks for the tip.

---

### Post by supreme_geek_overlord on 2007-07-28
Well, now I'm just confused.

First, kevinlyfellow was right: deleting the session file under my home directory was all I needed to do. Apparently, the programs listed under the "Additional startup programs" in gnome-session-properties have nothing to do with the session file. As these are the so-called "non-session-managed applications," this isn't *too* much of a surprise. What confuses me, however, is that nowhere can I find exactly *where* these are stored. Can anyone shed some light on that, since no manual pages or internet documentation I can find mentions these at all?

Second--and though not necessarily a problem, this has been bugging me for quite some time--why does gnome-session-properties under my Ubuntu system not have some of the options listed in not only my local documentation and the [COLOR=blue][COLOR=Blue][Gnome website]("http://www.gnome.org/learn/users-guide/2.14/prefs-sessions.html")[/COLOR][/COLOR], but also [COLOR=blue][COLOR=Blue][Ubuntu's online documentation]("https://help.ubuntu.com/7.04/user-guide/C/prefs-system.html")[/COLOR][/COLOR]? All that appears under the "Session Options" tab you can see in the attached picture--no "Show Splash Screen", "Prompt", or "Sessions" options. Is this normal for Ubuntu, and why?

---

### Post by kevinlyfellow on 2007-07-29
I've found the startup programs.  They are in ~/.config/autostart  What a terrible place!

Sometimes I'm not sure why I use gnome...

As for the other thing, I have the same session options.  But gnome devs are always looking to get rid of options.  Looks like they did a great job there.  Repeat, Sometimes I'm not sure why I use gnome...

---

### Post by supreme_geek_overlord on 2007-08-04
Wow. Well, thanks for the info. I'm sure I never would have found the autostart file. 

Yeah, Gnome irks me quite a bit too--I think the only reason I use it is because I can't find a way to make KDE aesthetically tolerable. The simplicity is nice, too, but stripping features is going too far.

---

### Post by kevinlyfellow on 2007-08-04
100% agree with you on that.  I'm usually very fond of gnome, but there are just some things that make me loose faith to it.  The way configuration is handled is becoming too much of a mess and there are just tons of little things that are moving in the wrong direction.  When user contact devs with their concerns, the devs just say "too bad, if want it that way you'll have to fork."

Gnome does win out in a  lot of respects though.  They have good ideas, but the development in between these ideas are tough.  Perfect example is gnome-screensaver.  I think what they did was a great idea.  Support for screensaver themes simplifies things and allows nice customization in a straightforward way.  But what they forgot to make was a graphical interface for making the themes.  Honestly, I still can't configure all of the screensavers the way I like it!  I've gotta learn gui programming...

Just so you know, I located the mystery config files via the grep command.

---

### Post by supreme_geek_overlord on 2007-08-04
For reference's sake, I have a few things to add. First, the ~/.config/autostart directory is apparently part of the [Freedesktop XDG specification]("http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html") and contains *.desktop files which are started up somewhere along the way (although exactly when and by what is anyone's guess). Also, as the specification page says, the directory is user-specific, its system-wide counterpart residing at /etc/xdg/autostart by default.

As a final note, a lot more interesting information can be found at [standards.freedesktop.org]("http://standards.freedesktop.org"), some of which pertains to this problem. Overall, though, everything related to X, Gnome, and KDE seems to be in a confusing limbo between the old proprietary ways and the as-yet-unfinished Freedesktop specs. [sigh]

---

