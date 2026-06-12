---
title: "Gnome online accounts on Xubuntu, possible?"
date: 2018-04-14
forum: Desktop Environments
---

### Post by josefranw on 2018-04-14
It's a simple question... Can it be done? If so, how?

Thanks in advance.

---

### Post by again? on 2018-04-16
Have a look [HERE]("https://askubuntu.com/questions/733061/gnome-online-accounts-goa-with-xubuntu").
Also note the you tube link in the comments.

eg I tested in Xubuntu 17.10
```
sudo apt install gnome-online-accounts
sudo apt install gnome-control-center
```

Then copy the launcher to your local directory to edit the Exec command.
Desktop files in **~/.local/share/applications** override the originals for the $USER.
The user desktop files won't be overwritten with updates. 
```
cp /usr/share/applications/gnome-control-center.desktop ~/.local/share/applications/
```

Now you need to edit the local desktop file's "Exec"  and "OnlyShowIn" lines.
The edits tell the application you're in the GNOME env and add XFCE to the OnlyShowIn variable so as it appears in the application menu.  
These 2 sed commands will do it.
```
sed -i '/Exec/c\Exec=env XDG_CURRENT_DESKTOP=GNOME gnome-control-center' ~/.local/share/applications/gnome-control-center.desktop
sed -i '/OnlyShowIn/c\OnlyShowIn=GNOME;Unity;XFCE;' ~/.local/share/applications/gnome-control-center.desktop
```

Here, the launcher shows up in Settings > Settings
or test with...
```
xdg-open ~/.local/share/applications/gnome-control-center.desktop
```

I don't use online accounts so whether or not this will work for your purpose I don't know.

---

### Post by firstplato.com on 2019-01-30
@guber2 thanks bro, you are really show the great job.. It's really like a magic for me.. really appreciate it.. thanks..

---

### Post by MZ250Supa5 on 2019-09-24
I'm totally confused about this I've followed the directions on how to install this on Xubuntu 18.04 and it just doesn't work for me. None of the menus show any of the apps, not gnome control center or gnome online accounts. I can, however launch them through the command line, but gnome control center is just a blank box.

I've tried the step below and the only result I get is a message to tell me that it's not a directory (?)

"Now you need to edit the local desktop file's "Exec"  and "OnlyShowIn" lines.
The edits tell the application you're in the GNOME env and add XFCE to the OnlyShowIn variable so as it appears in the application menu.  
These 2 sed commands will do it.
```
sed -i '/Exec/c\Exec=env XDG_CURRENT_DESKTOP=GNOME gnome-control-center' ~/.local/share/applications/gnome-control-center.desktop
sed -i '/OnlyShowIn/c\OnlyShowIn=GNOME;Unity;XFCE;' ~/.local/share/applications/gnome-control-center.desktop
```.

I'd be very happy if someone could enlighten me somewhat.Why does something that, to be quite honest, can be a real pain in the proverbial on Ubuntu Mate through its constant reminders to bnackup have to be so bloomin difficult to install on Xubuntu?

---

