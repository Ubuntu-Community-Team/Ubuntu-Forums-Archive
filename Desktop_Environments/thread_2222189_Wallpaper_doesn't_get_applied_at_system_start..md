---
title: "Wallpaper doesn't get applied at system start."
date: 2014-05-05
forum: Desktop Environments
---

### Post by livingcorpse on 2014-05-05
I'm using Nemo and I replaced it with Nautilus. I set the Nemo to show desktop icons and set Nautilus not to. Also I did this command do set Nemo default file manager:

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

Everything was working fine until I decided to try out Gnome Shell and uninstall it. It used to show the default Gnome wallpaper (the one that changes throughout the day, abstract) so I removed all Gnome wallpapers. Now, even though I set my wallpaper properly before restarting, everytime it starts it shows me a black screen.

It looks like all I need to do is to go to appearance setting and suddenly the wallpaper I choose is set correctly. It's like something can't read my wallpaper preference until I open any setting window that has anything to do with wallpaper.

I would appreciate any help I can get.

---

### Post by grumblebum2 on 2014-05-05
When you say you uninstalled gnome-shell, how and what exactly did you remove?
You could check to see if you removed a component of ubuntu.
This will only simulate(**-s**) and not actually install anything but will show what may be missing...
```
sudo apt-get **-s** install ubuntu-desktop
```


This is the procedure I use to set nemo as the default file browser.

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.nemo.desktop show-desktop-icons true
```

Then use this command to show all startup applications....
```
cd /etc/xdg/autostart/ && sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Open startup applications and change the "Files" entry command from **nautilus -n** to **nemo -n**

I don't actually do this though because there are still little annoyances.
If nautilus hasn't been started, right clicking on the rubbish icon takes 2 clicks because the first click starts nautilus as it only works with nautilus.
Clicking on a mounted usb drive opens nemo in my home directory and not the usb directory.
So i just leave nautilus as default and let it draw the desktop and just have a nemo icon on the launcher.

---

### Post by livingcorpse on 2014-05-06
I ran that -s command and it just gave me Thunderbird, which I uninstalled before. I set Nemo to draw desktop and Nautilus not to. I also changed Files startup item to "nemo -n". But nothing changed.

If I let Nemo draw the desktop wallpaper settings wallpaper turns to black after restarting. This does not happen when Nautilus is set to draw the desktop.

Looks like some parts of Nemo can not start until I somehow force it to (like clicking on Appearance on System Settings)

---

### Post by grumblebum2 on 2014-05-06
You should see nemo running in the system monitor as soon as you login.
If you manually start nemo or nautilus does the background appear?

Only other suggestion would be have a look in dconf-editor.
Hit ctrl+f and search for "background" and see what you can find.

---

### Post by livingcorpse on 2014-05-06
I figured it out. I was using the webupd8 nemo PPA and the admin there sent me a .desktop file that runs nemo with 2 second delay. It seems like my external HDD can't start fast enough for nemo to take the wallpaper image from there. Thank you for your replies.

---

