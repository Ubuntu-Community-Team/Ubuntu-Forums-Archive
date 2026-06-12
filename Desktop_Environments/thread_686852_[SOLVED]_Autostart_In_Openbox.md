---
title: "[SOLVED] Autostart In Openbox"
date: 2008-02-03
forum: Desktop Environments
---

### Post by Mark76 on 2008-02-03
I'm trying out openbox and I like the look of it, but I'd like it more if I could work out how the damned autostart works.  From what I've read you have to edit the autostart menu in ~/.config/openbox. Well, I did this, then I restarted and nothing happened.

I'd like to be able to have pypanel, clawsmail, pidgin, my feh wallpaper and swiftweasel launch at start up

---

### Post by ayoli on 2008-02-03
> **Mark76 said:**
> I'm trying out openbox and I like the look of it, but I'd like it more if I could work out how the damned autostart works.  From what I've read you have to edit the autostart menu in ~/.config/openbox. Well, I did this, then I restarted and nothing happened.

I'd like to be able to have pypanel, clawsmail, pidgin, my feh wallpaper and swiftweasel launch at start up

The file is called autostart.sh. You got a sample in /etc/xdg/openbox.
Here is what my autostart.sh looks:
```

# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background (the last bg set with feh)
eval `cat $HOME/.fehbg` &

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  export GTK_MENUBAR_NO_MAC=1 # disable mac menu menu
  gnome-settings-daemon &
fi

# Preload stuff for KDE apps
if which start_kdeinit >/dev/null; then
  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
fi

# transparency
xcompmgr -cC -t-3 -l-5 -r5 &

sleep 2;
pypanel &
sleep 1;
conky &

```

---

### Post by Mark76 on 2008-02-03
I copied the following lines from your autostart script

# transparency
xcompmgr -cC -t-3 -l-5 -r5 &

sleep 2;
pypanel &
sleep 1;
conky &

Pasted them into mine, logged out and in again and nothing happened.  Maybe it only works with a complete reboot.

---

### Post by Mark76 on 2008-02-03
Nope. Still nothing

---

### Post by ayoli on 2008-02-03
Actually I don't need to reboot to see changes.
And it even doesn't need to be executable :
```
&#9492;&#9472;($)> ll /home/ayoli/.config/openbox/autostart.sh
-rw-r--r-- 1 ayoli users 705 2008-02-03 17:40 /home/ayoli/.config/openbox/autostart.sh
```

---

### Post by ayoli on 2008-02-03
More infof in [urukrama's guide]("http://urukrama.wordpress.com/openbox-guide/") (autastarting applications section comes after gtk theming, at the middle of the page).

---

### Post by Mark76 on 2008-02-03
What the heck is 

> ($)> ll /home/ayoli/.config/openbox/autostart.sh?

I pasted it into a terminal (not forgetting to change your name for mine) and got this

bash: syntax error near unexpected token `/home/mark/.config/openbox/autostart.sh'


I then tried it without the ($)> and got this

> mark@Panopticon:~$ ll /home/mark/.config/openbox/autostart.sh
bash: ./ll: Permission denied
mark@Panopticon:~$ sudo ll /home/mark/.config/openbox/autostart.sh
sudo: ll: command not found
mark@Panopticon:~$ 

So I have no idea what the hell you did.

---

### Post by ayoli on 2008-02-03
> **Mark76 said:**
> What the heck is 

?

I pasted it into a terminal (not forgetting to change your name for mine) and got this

bash: syntax error near unexpected token `/home/mark/.config/openbox/autostart.sh'


I then tried it without the ($)> and got this



So I have no idea what the hell you did.

sorry I paste too much and used an alis you don't have, try : 
```
ls -l /home/mark/.config/openbox/autostart.sh
```
you don't need sudo for that.

this :
```
&#9492;&#9472;($)>
```is only a part of my bash prompt :)

---

### Post by urukrama on 2008-02-03
How do you start Openbox? If you start it with startx and the ~/.xinitrc or if you have created your own custom xsession, make sure you start *openbox-session* rather than *openbox* (both should be either in /usr/bin/ or /usr/local/bin). The autostart file is only run when you launch openbox-session. Note that the autostart file will also not be used when you use Openbox as a window manager in Gnome, KDE or Xfce.

Also, are you sure the file is named autostart.sh and not just autostart? And that you have read&write permissions for the file?

---

### Post by Mark76 on 2008-02-03
I guess I'm using it as a window manager in XFCE.

How do I launch it as a standalone app?

---

### Post by ayoli on 2008-02-03
> **Mark76 said:**
> I guess I'm using it as a window manager in XFCE.

How do I launch it as a standalone app?

If you use gdm to log in, select "Sessions" before login and pick openbox-session in the menu

---

### Post by urukrama on 2008-02-03
> **Mark76 said:**
> I guess I'm using it as a window manager in XFCE.

How do I launch it as a standalone app?

At the login screen (GDM or KDM) press F10 and click Sessions. If Openbox is listed there, select it and log in as usual. Openbox will then start. You will see a blank screen (if you don't have anything in your autostart.sh file). Right click and you have the root menu.

If you don't have an entry for Openbox there, you can create one. Here's how you do it:

Open a terminal and type:
```
sudo mousepad /usr/share/xsessions/openbox
```

(Replace mousepad with whatever your favourite text editor is)

An empty file will open. Add the following to it:

```
[Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Log in using the Openbox window manager (without a session manager)
Exec=/usr/bin/openbox-session
TryExec=/usr/bin/openbox-session
Icon=openbox.png
Type=XSession
```

(Double check that openbox-session is in /usr/bin/ as in the above text, otherwise edit the Exec and TryExec lines with the appropriate location)

Restart X (Ctrl+Alt+Backspace) and select Openbox from the Sessions menu in GDM (as mentioned above).

---

### Post by Mark76 on 2008-02-03
Ah, yeah.

I was using SLIM as my login manager.  For some reason it doesn't work in SLIM, but it's fine in GDM.

Thanks

---

### Post by urukrama on 2008-02-04
> **Mark76 said:**
> I was using SLIM as my login manager.  For some reason it doesn't work in SLIM, but it's fine in GDM.

I haven't used Slim extensively, but as far as I recall, you should be able to see your sessions menu when you press F1. I suppose it reads the same files as GDM for this, but can't confirm this.

---

### Post by Mark76 on 2008-02-04
Nah, openbox was an option, but not openbox-gnome, openbox-kde or openbox-session.  So I assume it was all three in one.

---

### Post by urukrama on 2008-02-04
It seems Slim doesn't read the /usr/share/xsessions file. A [bug]("http://developer.berlios.de/bugs/?func=detailbug&bug_id=12005&group_id=2663") has been filed in September, but nothing has come from it yet.

You can edit the /etc/slim.conf file though. Have a look at the SLIM entry in the [Gentoo]("http://gentoo-wiki.com/HOWTO_SLiM_setup") and [Arch]("http://wiki.archlinux.org/index.php/SLIM") wikis.

---

### Post by heri on 2008-02-06
> **ayoli said:**
> More infof in [urukrama's guide]("http://urukrama.wordpress.com/openbox-guide/") (autastarting applications section comes after gtk theming, at the middle of the page).

Wow, the urukrama's guide is really great =D>

Thank's for your info ayoli.

---

### Post by urukrama on 2008-02-06
> **heri said:**
> Wow, the urukrama's guide is really great =D>

I'm glad you like it :cool:

---

