---
title: "How to setup openbox?"
date: 2014-10-15
forum: Desktop Environments
---

### Post by Higgins909 on 2014-10-15
I've tried a few times over the years to get openbox on a linux computer....
Right now I have a crappy computer (not my only computer) that I want to put to use, as a nippy linux web browser or similar.

I installed 32bit 14.????? (downloaded it today) desktop version and got it setup, and installed openbox from the program installer thing.
I logged out switch desktop mode and logged back in.
...my hotkey for terminal didnt work either, so I had to right click to get that open :/

Now I have no idea what to do :/  I tried watching a few videos but when they right clicked they had more stuff, while I had like 7 things to click.

Thanks,
Higgins909

---

### Post by CantankRus on 2014-10-15
Openbox is just a window manager so what you were looking at was
possibly [**_[COLOR="#B22222"]LXDE[/COLOR]_**]("http://wiki.lxde.org/en/Main_Page")/Lubuntu which use Openbox as the window manager.
If you're starting with a stand-alone openbox session you have to add your own panels etc.
The right click on the desktop and keyboad shortcuts depends on the rc.xml file being used.
eg in Lubuntu it uses **~/.config/openbox/lubuntu-rc.xml** while just an **Openbox session** will use **~/.config/openbox/rc.xml **

---

### Post by Higgins909 on 2014-10-15
How do I add all my own pannels and stuff?

---

### Post by andrew.46 on 2014-10-15
I cannot help that much with OpenBox as I run its brother Fluxbox, however there is a great guide from the arch people:

Openbox
[https://wiki.archlinux.org/index.php/openbox](https://wiki.archlinux.org/index.php/openbox)

which might provide a starting point. Incidentally was there a particular reason you decided on openbox rather than fluxbox?

---

### Post by vasa1 on 2014-10-15
> **andrew.46 said:**
> I cannot help that much with OpenBox as I run its brother Fluxbox, however there is a great guide from the arch people:

Openbox
[https://wiki.archlinux.org/index.php/openbox](https://wiki.archlinux.org/index.php/openbox)

which might provide a starting point. Incidentally was there a particular reason you decided on openbox rather than fluxbox?
You can also look at [http://openbox.org/wiki/Help:Getting_started](http://openbox.org/wiki/Help:Getting_started)

I use Openbox because it came with Lubuntu. I guess if Lubuntu came with Fluxbox, I'd be using that.

BTW, why did you install Ubuntu and not Xubuntu or Lubuntu if your computer is "crappy"?

---

### Post by vasa1 on 2014-10-15
> **Higgins909 said:**
> How do I add all my own pannels and stuff?You may want to be a bit more explicit.

---

### Post by CantankRus on 2014-10-16
> **Higgins909 said:**
> How do I add all my own pannels and stuff?
Determine what you want to start in the openbox session with a  **~/.config/openbox/autostart** file.
eg
```
## Openbox autostart
## ====================
## Note*: some programs, such as 'nm-applet' are run via XDG auto-start.
## Run '/usr/lib/openbox/openbox-xdg-autostart --list' to list any
## XDG autostarted programs.

## GNOME PolicyKit and Keyring
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &

## Set pcmanfm to draw wallpaper
pcmanfm --desktop &

## start up a panel
#lxpanel &
tint2 &

## start conky
#conky -p 5 -c /home/glen/conky/configs/openbox-panel.conkyrc &
#conky -p 5 -c /home/glen/conky/configs/gmail-conkyrc &

## Start up power management
#xfce4-power-manager &

## Start the Clipboard manager after 3 seconds wait
(sleep 3s && glipper) &

## start volume manager after 15 seconds
(sleep 15s && volumeicon) &

## Turn on Numlock at start-up
#numlockx on &

## Start Composite manager
#xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &
compton &

## simple dock
#plank &

## Application launcher
kupfer  --no-splash &

```

First pic shows lxpanel and plank.
Second pic shows tint2.
Use an application launcher like kupfer if you want a minimal desktop.

---

### Post by Higgins909 on 2014-10-26
CantankRus, I will try that out soon.
Idk I like ubuntu and the commands and am used to the filesystem somewhat.
I've tried Lubuntu and or maybe not Xubuntu and hated the gui and the commands were different or something.

I know this is a stupid though, but it would be kinda cool to me if I could make it look like some sort of mac from some time period, I mainly love their window looks for say file browser.
I'd love to make the computer into some snappy web browser, fast ftp from my file server, fast file browser window, and a text editor (probably libre) folder icon of a mac... lol at me :D

---

### Post by Higgins909 on 2014-10-26
oh, I thought this time I'd give some specs, a 800mhz single core cpu, 512MB of ram, 2hdd one 80gb os/storage 40gb swap/storage... I wonder if it can even play any games, maybe joe quake, lol. (its still a very fun game)

---

