---
title: "No wallpaper in Gnome 3"
date: 2011-06-02
forum: Desktop Environments
---

### Post by tetsura on 2011-06-02
Hi.

Trying Ubuntu yet again (seems to occur every 6 months or so!)

I've installed Natty, and wasn't so keen on Unity so I decided to try Gnome 3. Not sure if I prefer it either but better than unity I think so giving it a go.

Anyway, my problem is that I don't have a wallpaper and changing it doesn't have any effect, it's just a solid colour, any ideas?

At first I didn't have a desktop at all but changing a setting in the gnome 3 tweak tool (Have file manager handle the desktop > on) fixed that. Then I went to install nautilus elementary but that messed up my wallpaper, hence it's now blank. I've reverted to Nautilus now but I'm not sure elementary actually worked as it didn't look any different.

Thanks in advance!

---

### Post by ratcheer on 2011-06-02
I think you need to use the gsettings command to add wallpaper to gnome-shell. Download the wallpaper file to your hard drive. Run this command to show it on your desktop. Run the command as your username, not under sudo.

gsettings set org.gnome.desktop.background picture-uri  'file:///home/alan/images/Travel/Holiday in Yorkshire Dales/p7130047.jpg' 

Of course, use the actual directory and filename of your chosen wallpaper file.

Tim

---

### Post by tetsura on 2011-06-20
Sorry for such a late reply!

Thanks but it didn't work, just said "0:expected value".

I'm going to revert to Gnome 2 anyway, but thanks.

---

