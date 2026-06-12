---
title: "AWN and Compiz Fusion: It did work, but it won't now..."
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by smartboyathome on 2007-06-24
I installed AWN earlier (using the instructions found on the site) and got it to work with Compiz Fusion. When I started it up again (I got an error, logged out, and logged back in) it broke. I really liked AWN and would like it fixed, please help!

Here is the error I get when starting it in a terminal:
```

(avant-window-navigator:30908): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(avant-window-navigator:30908): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(avant-window-navigator:30908): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
/home/aabbott/.themes/Salocin/gtk-2.0/gtkrc:213: Unable to locate image file in pixmap_path: "panel.png"
APPLET : /usr/lib/awn/applets/taskman.desktop

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:30908): Wnck-WARNING **: Unhandled action type (nil)

```

EDIT: I am using Compiz Fusion flawlessly. Also, I installed Screenlets, could that conflict with AWN?

---

### Post by smartboyathome on 2007-06-24
It works again, for some odd reason (I uninstalled Screenlets, so that could have been it).

---

### Post by smartboyathome on 2007-06-24
I ran some tests today, and this problem did, in fact, arise because of the Screenlets (I didn't even run screenlets in my tests, and it still effected AWN). If anyone else could look into it further (or replicate the problem) so that this could be resolved (or a patch could be made) i would be grateful.

EDIT: I got a screenshot of the problem. You can view that screenshot at:
[http://i42.photobucket.com/albums/e318/smartboyathome/Screenshot-2.png](http://i42.photobucket.com/albums/e318/smartboyathome/Screenshot-2.png)

---

### Post by andrewsomething on 2007-06-25
I don't know why that would be happening. :( 

I've got AWN, Compiz-Fusion, and Screenlets all running fine. Without any special tweaking. 

Just a thought, how are you running screenlets at startup? "screenlets-tray" works for me...

I really don't know, but if you can think of any other information post it. The great thing about Ubuntu is how helpful the other users are. I'm sure that some one out there experienced this problem and fixed it. They just haven't seen this thread yet.

---

### Post by smartboyathome on 2007-06-25
Thanks for replying. :)

I do have some more info. It has errors when I install it and don't start it up at all (even after installing). The only way to fix this is to uninstall Screenlets. I am wondering, but where did you install your screenlets from? I installed it from the Feisty repos .

---

### Post by andrewsomething on 2007-06-25
> **smartboyathome said:**
> Thanks for replying. :)

I do have some more info. It has errors when I install it and don't start it up at all (even after installing). The only way to fix this is to uninstall Screenlets. I am wondering, but where did you install your screenlets from? I installed it from the Feisty repos .

Try adding the following to your source list  (sudo gedit /etc/apt/sources.list).

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets 

Then run this in a terminal:

wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

I believe that is the developer's repo. It might be more up to date.

---

### Post by smartboyathome on 2007-06-25
Well, I will have to try again on a new Feisty partition, as fdisk ruined it :'( I will get back to you when I get it installed again so I can use it. I really want them both!

PS: I am writing this from my Gutsy partition.

---

### Post by smartboyathome on 2007-06-25
It works! Thanks! :)

---

