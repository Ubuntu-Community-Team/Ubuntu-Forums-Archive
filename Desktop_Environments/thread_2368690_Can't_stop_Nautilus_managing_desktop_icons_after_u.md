---
title: "Can't stop Nautilus managing desktop icons after upgrade to 17.04"
date: 2017-08-14
forum: Desktop Environments
---

### Post by wurlyfan on 2017-08-14
Hi there.

After upgrading to Ubuntu 17.04 from 16.04, I can't get my desktop back to what I'm used to because all the desktop icons are too large (see image). I'm using Gnome Flashback (Compiz) and used to use Nemo to manage desktop icons. Now. however, I can't stop Nautilus from managing desktop icons and its smallest icon size is too large, and shortcuts on the desktop open in Nautilus rather than Nemo

If I use gsettings to enable Nemo to control the icons, the Nemo icons appear in addition to Nautilus's ones (but at a size I can reduce acceptably). The command

"gsettings set org.gnome.desktop.background show-desktop-icons false"

doesn't stop Nautilus icons appearing. Can anyone help?

---

### Post by again? on 2017-08-14
I can't kill nautilus in the flashback sessions on 17.04
Unity session works ok.
May have something to do with systemd change.
Either a bug or intended behaviour.

From the file /usr/share/xsessions/gnome-flashback-compiz.desktop in 17.04
```
Exec=/usr/lib/gnome-session/run-systemd-session gnome-session-flashback.target
```

From same file in 16.04
```
Exec=/usr/lib/gnome-flashback/gnome-flashback-compiz
```

Sorry no answer...just some info. :p

---

### Post by again? on 2017-08-14
Looking at the /usr/share/gnome-session/sessions/gnome-flashback-compiz.session file it lists nautilus-classic as a requirement,
and in turn /usr/share/applications/nautilus-classic.desktop has a setting "X-GNOME-AutoRestart=true",
which will automatically restart "nautilus --no-default-window --force-desktop" if it quits.

You could edit gnome-flashback-compiz.session to remove nautilus-classic as a requirement.

Make a backup first 
```
sudo cp /usr/share/gnome-session/sessions/gnome-flashback-compiz.session /usr/share/gnome-session/sessions/gnome-flashback-compiz.session.bak
```

Then edit gnome-flashback-compiz.session
```
gksudo gedit /usr/share/gnome-session/sessions/gnome-flashback-compiz.session
```

Look for and delete (including trailing semicolon)
```
nautilus-classic;
```
In my file it was at the very end.

Seems to work ok with my quick test but
if you run into problems, replace the edited version with the backup.
```
sudo mv /usr/share/gnome-session/sessions/gnome-flashback-compiz.session.bak /usr/share/gnome-session/sessions/gnome-flashback-compiz.session
```

---

### Post by wurlyfan on 2017-08-14
Thanks, guber2, it's getting late here so I'll try this tomorrow

---

### Post by wurlyfan on 2017-08-15
Hi guber2. I followed your suggestion and it worked to a point: my desktop icons were once again drawn by Nemo and at the right size. However, I lost my wallpaper (background) and also some other desktop features. I'm going to see if Gnome can handle the background directly, although I'm at the limit of my understanding about how Gnome, Nemo and Nautilus interact! Still, I might learn something. Thanks for your help so far, if you have any other suggestions I'd be glad to hear them.

---

### Post by again? on 2017-08-15
If neither nautilus or nemo are running at startup you will see your greeter background and have no icons
or interaction with the desktop.

We have stopped nautilus starting up and running the command 
```
gsettings set org.nemo.desktop show-desktop-icons true
```
should set nemo to startup because of the [COLOR="#0000FF"]condition[/COLOR] in the /etc/xdg/autostart/nemo-autostart.desktop file
```
[Desktop Entry]
Type=Application
Name=Nemo
Comment=Start Nemo desktop at log in
Exec=nemo -n
[COLOR="#0000FF"]AutostartCondition=GSettings org.nemo.desktop show-desktop-icons[/COLOR]
X-GNOME-Autostart-Delay=2
NoDisplay=false
```

When you log in, check to see if nemo is running in system monitor.(also check nautilus is not running)
[ATTACH=CONFIG]276411[/ATTACH]
This terminal command will also show if nautilus or nemo is running
```
ps aux | grep -E '[n]autilus|[n]emo'
```
eg
```
[COLOR="#006400"]glen@ZestyUbu:~$[/COLOR] **ps aux | grep -E '[n]autilus|[n]emo'**
glen      4453  0.1  1.5 834536 60476 ?        Sl   17:37   0:01 nemo -n
```
If it's not running, hit alt+F2, type in 
```
nemo -n
``` 
and hit Enter.
Nemo should immediately start drawing the desktop.

If that works add nemo to startup applications.
[ATTACH=CONFIG]276412[/ATTACH]

---

### Post by again? on 2017-08-15
Just realized I am using the webupd8 nemo3 ppa which has a version of nemo, patched to draw the desktop background and Unity Control Center support.
[ATTACH=CONFIG]276413[/ATTACH]

To use this ppa read this installation guide.
[http://www.webupd8.org/2016/11/nemo-320-with-unity-patches-and-without.html](http://www.webupd8.org/2016/11/nemo-320-with-unity-patches-and-without.html)

Should have no problems if just running the Flashback session but take note of this section:
> [COLOR="#FF0000"]Important[/COLOR]: do not use this PPA if you use Linux Mint or if you use the Cinnamon desktop in Ubuntu! 
Also, if you've added any Cinnamon PPAs, you'll have to purge them before using this Nemo PPA.

After adding the ppa and upgrading, logout and back in to run the newer nemo version.

---

### Post by wurlyfan on 2017-08-17
Hey guber2, I'm using the stand-alone version of Nemo as well, and when I tried all this again it worked perfectly. So many thanks for your help

---

### Post by again? on 2017-08-18
OK. Good.
Always knew "Finding Nemo" would have a happy ending. :p

---

