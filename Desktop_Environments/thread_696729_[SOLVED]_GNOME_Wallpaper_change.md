---
title: "[SOLVED] GNOME Wallpaper change"
date: 2008-02-14
forum: Desktop Environments
---

### Post by kasnam on 2008-02-14
I used to change my background of GNOME every minute with

```
gconftool-2 -s /desktop/gnome/background/picture_filename /path/picture.svg -t string
```

this worked fine. The wallpaper changed immediately in the moment the script is called, even with programs running in foreground.
But then I changed something (after installing the new linux headers I rebooted and before that I killed some processes and saved the session, so the original configuration the script worked with is lost) and now it changes only after switching the workdesk or doing a wallpaper change with the gui.
The problem is, I dont know what server has to run to make this work or what ran before i made the mistake.
gconfd-2, gnome-settings-deamon, gnome-vfs-deamon are running.
Any hint can be useful!

Using 7.10, 
2.6.22-14-generic
GNOME 2.20.1

---

### Post by kasnam on 2008-02-14
I just played around with changing the wallpaper with perl and voilà it worked, immediately.
But only when switching between different wallpapers with different filenames.
So I tried switching between different wallpapers with gconftool-2 and it worked too. 
Now I am not sure if I made any mistake, 

But why was it possible to "RELOAD" the wallpaper before???:confused:

My Code looks something like this:

every minute do:
 overwrite picture.svg with new data
 gconftool-2 -s /desktop/gnome/background/picture_filename /path/picture.svg -t string

Please Help!

---

### Post by kasnam on 2008-02-14
It seems nobody is facing this problem too or has experience with gnometools.
Anyway there is a workaround:
Just before executing the command, change something else of background properties.
In particular changing the code to the following worked for me:
```

every minute do:
overwrite picture.svg with new data
gconftool-2 -s /desktop/gnome/background/picture_options centered -t string
gconftool-2 -s /desktop/gnome/background/picture_filename /path/picture.svg -t string

```

---

