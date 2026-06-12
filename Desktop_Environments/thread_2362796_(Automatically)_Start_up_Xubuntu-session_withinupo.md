---
title: "(Automatically) Start up Xubuntu-session within/upon Ubuntu (16.04 LTS)"
date: 2017-06-02
forum: Desktop Environments
---

### Post by xinuzi on 2017-06-02
The subject may have been handled here before, but had some problems with lightdm after installing xubuntu in ubuntu 16.04 LTS, after installing the xubuntu-session with

```

sudo apt-get install xubuntu-desktop

```

All the files in '**/etc/lightdm/lightdm.conf.d/**' disappeared.
I got a xubuntu-sessions-greeter but without other sessions.

Luckily the files were available in:

'**/usr/share/lightdm/lightdm.conf.d/**'

Copied them to '/etc/lightdm/lightdm.conf.d/' .

Not sure if that was really necessary, but after that the unity greeter appeared again.

Finally edited '**/etc/lightdm/lightdm.conf**' this way (with autologin-rule):

[Seat:*]
user-session=xubuntu
greeter-session=unity-greeter
autologin-user=myusernameinlowercaseletters

 Fairly fast and configurable this xubuntu-session. Nice!

Remarks always welcome.

---

### Post by xinuzi on 2017-06-03
A few minor problems with that xubuntu flavour:

Sound icon missing in xubuntu session top bar. 
Activated it by activating ubuntu indicator.
Lost Volume settings control for a moment, but it's back in the meantime.

The ubuntu-indicator in xubuntu-upon-ubuntu conflicts a bit with the file menu of some applications (e.g. Firefox),
or suddenly disappears with the notification 'no indicators' in the top menu bar.

Don't know quite yet what causes this behaviour and how to solve it.

Everything else works fine in this xubuntu.

---

### Post by Bucky Ball on 2017-06-04
Are you after support or just comments, as this is a support area. ;)

You've effectively mashed together Xubuntu with Ubuntu. That can cause conflicts, redundancy and unexpected issues. If you just wanted the Xubuntu desktop environment (and desktop environments is where you've posted this) you just install that. xfce4 is the desktop environment used by Xubuntu. Then you choose an xfce4 session at login.

Mashing two OSs together like can create a 'dog's breakfast' and moving your lightdm files around, and possibly others, to try and fix mayhem may not end well. At least it's still all working.

Best advice is to go for one or the other, Xubuntu or Ubuntu, or just install the Xubuntu desktop environment; xfce4.

```
sudo apt install xfce4
```

That's it. When you install '*buntu-desktop' anything *on top of another OS*, you are effectively jamming one OS on top of another. Messy. You are currently running Ubuntu *and* Xubuntu on one hybrid install. Things may be fine, but don't be shocked if not. :|

Some newer users post saying they wanted the desktop environments so they installed lubuntu-desktop, xubuntu-desktop, kubuntu-desktop, etc. and now their computer is not working or they are getting bizarre or not previously seen behavior or conflicts. If you are after the desktop environment, best to install the desktop environment, not the whole OS. ;)

Have a look in your apps menus. Do you have Xubuntu apps in there that do exactly the same thing as ones already installed with Ubuntu? If so, you don't need one of them. Bloat and a possible cause of conflict. 

Good luck.

---

### Post by xinuzi on 2017-06-04
Guess I mashed up questions with comments before, indeed, Bucky Ball.
Shortened my 'talk-talk' in the meantime ;)

When I installed xubuntu over ubuntu I got 2 xsessions: xubuntu and xfce-session.
Installed xfce4.
Will select a xfce-session on next start up and see if the (sound)indicator problem is still there.

I'm trying out different ubuntu flavours to get an idea of what pleases me most.
I understand that mixing those flavours can cause havoc.
Will probably do a full system install of the most pleasing ubuntu flavour/version on this computer (after having taken a holliday <g>).

Thanks for your help.

---

### Post by Bucky Ball on 2017-06-04
All good. Best way to try them is directly from the install disk with the 'Try *buntu' option. Another way to go once you know the elements you like, apps and DE and what not, is to start with the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") or [an Xubuntu-core install]("https://xubuntu.org/news/introducing-xubuntu-core/") and build it up from there installing the apps you want/need. 

Takes a bit more time as you learn, but you'll learn and end up with a snappy system with no bloat. Xubuntu-core gives you the Ubuntu kernel (which all flavours are built on), the xfce4 desktop, a few default Xubuntu things and not much else. You are required to install everything else. I generally start with opening a terminal and installing synaptic and firefox so I have a graphic package manager and web browser then take it from there. :) 

Enjoy.

---

### Post by xinuzi on 2017-06-05
Everything with xubuntu in ubuntu works very satisfactory/fast/effective now (after that 'xfce4'-install? I'm still selecting the 'xubuntu'-session at startup though but it has more possibilities now.)

Chose a xubuntu workbar environment ('Modern' I think) from within the xubuntu workbarsettings (or how is it called in English) and edited the top workbar further: only whiskermenu to te left, wifi-volumecontrol(PulseAudio plugin)-date(orage)-andsomeother-icons to the right.
Other, bigger, more primordial shortcut icons in the configurable centered bottom (semi-)transparent bar aka panel.
Top and bottom bars: hide-show.

No ubuntu-indicator in the workbars as it messes things up.

I don't think it will be necessary to do a full clean xubuntu install as it works fine now next to/upon/within the existing ubuntu 16.04 LTS xenial unity x64 platform.

Cheerio!

---

### Post by Bucky Ball on 2017-06-05
Good news. If you're happy, please mark as solved from Thread Tools at top right to help other and save them time. :)

---

