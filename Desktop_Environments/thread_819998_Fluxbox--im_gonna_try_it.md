---
title: "Fluxbox--im gonna try it"
date: 2008-06-05
forum: Desktop Environments
---

### Post by sports fan Matt on 2008-06-05
Since im bored im trying fluxbox..ill post what I think

---

### Post by kerry_s on 2008-06-05
sudo apt-get install fluxbox menu
sudo update-menus

log out, select fluxbox and your good to go.

for nautilus> nautilus --nodesktop

---

### Post by AnLGP on 2008-06-05
it's good stuff. :)

---

### Post by Inxsible on 2008-06-05
Good luck. I like it a lot and I am going to do a minimal + fluxbox over this weekend :)

---

### Post by atomkarinca on 2008-06-06
Her are some applications for you then:

gmrun: you can configure alt+f2 combination for this little app and have a nice run dialog.
wbar: a lightweight dock.
scrot: command line screen capturing application. You can bind it to Print Screen.
skippy: emulates compiz's scale plugin.
GKrellM: very nice system monitor.

Here are some documentation for [keys]("http://ubuntuforums.org/showthread.php?t=617812"), [menu]("http://ubuntuforums.org/showthread.php?t=371144") and [startup]("http://fluxbox-wiki.org/index.php/Howto_edit_the_startup_file").

---

### Post by Anzan on 2008-06-06
I am really enjoying Fluxbox for when I just want to get a lot of work done.

I recommend it highly.

---

### Post by RedSquirrel on 2008-06-06
> **kerry_s said:**
> for nautilus> nautilus --nodesktop

```
nautilus --no-desktop
```;)

---

### Post by sports fan Matt on 2008-06-06
Ill have to test it further in a few days as life has been crazy around here plus i'll be out of town for a few days..i'll post more info in a few days

---

### Post by kerry_s on 2008-06-06
> **RedSquirrel said:**
> ```
nautilus --no-desktop
```;)

thanks, i was close. :lolflag:

---

### Post by RedSquirrel on 2008-06-07
> **kerry_s said:**
> thanks, i was close.

I had to look it up in an online man page the other day for someone else. I think it's been about 18 months since I last used nautilus. :)

---

### Post by Happy_Man on 2008-06-07
Dude, Fluxbox rocks. Then again, so does Openbox. 

(RedSquirrel, please don't kill me for saying that)

---

### Post by RedSquirrel on 2008-06-07
> **Happy_Man said:**
> Dude, Fluxbox rocks. Then again, so does Openbox. 

(RedSquirrel, please don't kill me for saying that)

The OP should check out openbox as well. They're both good. I'm running openbox right now. :)

---

### Post by eriqjaffe on 2008-06-08
> **atomkarinca said:**
> gmrun: you can configure alt+f2 combination for this little app and have a nice run dialog.

Fluxbox comes with fbrun, which does the same thing - it's just not as attractive.

---

### Post by Inxsible on 2008-06-08
What's the keybinding for fbrun?

Alt +F2 takes me to the second desktop (F1-F4)

---

### Post by atomkarinca on 2008-06-08
> **Inxsible said:**
> What's the keybinding for fbrun?

Alt +F2 takes me to the second desktop (F1-F4)

You should change it in the keys file.

```
nano ~/.fluxbox/keys
```

Comment the line starting with "Mod1 F2..." and add this to the end:

```
Mod1 F2 :Exec fbrun
```

or if you installed gmrun, you can change it with fbrun. Now right-click on the desktop and select Reconfigure.

---

### Post by fanderal on 2008-06-08
Just loaded 8.04 and fluxbox, and had the problem of reverting to the gnome desktop when opening nautilus. Did "nautilus --no-desktop" in the terminal and it opened nautilus without the desktop going back to gnome. I thought it was like a mode switch; do it once and that's it. Nope. So I added the "--no-desktop" to the exec command for nautilus in the menu. Works great.

Thanks for the info!

---

### Post by brijam on 2008-06-09
> **Inxsible said:**
> Good luck. I like it a lot and I am going to do a minimal + fluxbox over this weekend :)

I'd like to do this.  Anyone know the complete list of packages needed?

starting with sudo apt-get install x11-common, i guess...

ending with sudo apt-get install fluxbox

---

### Post by urukrama on 2008-06-09
Brijam, see [aysiu's guide]("http://psychocats.net/ubuntu/minimal"), and replace icewm with fluxbox.

---

### Post by Inxsible on 2008-06-09
> **brijam said:**
> I'd like to do this.  Anyone know the complete list of packages needed?

starting with sudo apt-get install x11-common, i guess...

ending with sudo apt-get install fluxboxWhat are the problems that you are facing?

I would suggest that you first make a list of all the apps that you need and want on the install. For eg..something to this effect...

NOTE: Remember that the apps that I have mentioned below are all lightweight because that's what ppl with Fluxbox often want. YMMV. The total number of applications for each category are too numerous to mention - and most likely I don't even know half of them.

1) Xorg - obviously
2) File Manager -  PCManFM, emelFM2, clex(CLI based)
3) Window Manager - you have probably chosen one already
4) Editor -- I would suggest leafpad here..it does not have too many dependencies. Very lightweight
5) to get desktop icons - iDesk
6) to get panels - fbpanel is lightweight, but you can get xfce4-panel if you like too
7) A package manager - most ppl go with Synaptic here but there are others
8 )Browser - Kazehakase is lightweight but no plugins - firefox is the only choice which has all plugins opera to an extent.
9) Terminal - lots of choices - aterm, eterm, xterm, rxvt,mrxvt, urxvt, Sakura, tilda, xfce4-terminal...the list goes on
10)Image viewer - Mirage is lightweight
11) CD/DVD burner - Recorder - but you will have to compile this from source since I am not aware of any available deb packages. There might be some out there
12)you may need to install alsa-utils and alsa-conf and or alsa-oss for sound
13)your graphics card drivers
14)gFTP - for ftp
15)SSH - openssh-server
16)display manager - GDM, KDM, WDM, XDM - I am a minimalist and I dont install DMs at all. simply login at CLI and have a login script take you directly to your desktop. DMs are a waste of space after you login anyway :)
17) Time and Date management - orage

...If I rbr anything else.. I will add to that list. Now all you have to do is```
sudo apt-get install *package-name1 package-name2 ......*
```

---

### Post by urukrama on 2008-06-10
> **Inxsible said:**
> 2) File Manager -  PCManFM, emelFM2, clex(CLI based)
[...]
10)Image viewer - Mirage is lightweight
[...]
16)display manager - GDM, KDM, WDM, XDM - I am a minimalist and I dont install DMs at all. simply login at CLI and have a login script take you directly to your desktop. DMs are a waste of space after you login anyway :)
17) Time and Date management - orage

Some alternatives to the above:
**Thunar**: the xfce file manager. Light and pretty.
**Feh**: the fastest image viewer. It can also be used to set the desktop background.
**Gpicview**: a light Gtk image viewer.
**Slim** is a lighter displau manager than GDM or KDM, and looks a lot better than XDM.

You can also use **Osmo** as an alternative for Orage.

---

### Post by Inxsible on 2008-06-10
> **urukrama said:**
> Some alternatives to the above:
**Thunar**: the xfce file manager. Light and pretty.
**Feh**: the fastest image viewer. It can also be used to set the desktop background.
**Gpicview**: a light Gtk image viewer.
**Slim** is a lighter displau manager than GDM or KDM, and looks a lot better than XDM.

You can also use **Osmo** as an alternative for Orage.I love thunar, but it has a few xfce dependencies that I can live without in my fluxbox or enlightenment installations :)

Thanks for the heads up on Feh - will check it out. I use mirage currently.

No DMs for me :) and I have never used Osmo, but I will check it out.

---

