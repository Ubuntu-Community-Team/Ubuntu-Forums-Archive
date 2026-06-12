---
title: "No Wallpaper/Background in Pantheon Shell"
date: 2013-08-17
forum: Desktop Environments
---

### Post by su:bhatta on 2013-08-17
Hi,
Got greedy that Elementary Luna is finally out! Today I added the daily build ppa of eOS & installed pantheon or more precisely 'elementary-desktop' on top of my XFCE!

Now, Elementary desktop is working fine, no problems, other than the fact that I cannot set any wallpaper !!!
Not from system Settings in Pantheon, neither through Dconf Editor!

A screenshot is attached! 

No problens with Xfce session though! Everything works just as it should there![ATTACH=CONFIG]245436[/ATTACH]

---

### Post by su:bhatta on 2013-08-17
Ok, here is what i did:
```
apt-get remove pantheon-shell pantheon midori lingo  wingpanel plank pantheon-terminal pantheon-xsession-settings contractor  slingshot-launcher scratch marlin elementary-theme elementary-icon-theme  ttf-droid footnote switchboard plank-theme-pantheon snap  switchboard-gnome-control-center preload


```

Now, after a simple apt-get autoremove, i have lost my Ubuntu Studio custom menu et all, at least buggy elementary desktop is gone !!!

Any ideas??

---

### Post by Frogs Hair on 2013-08-17
I had a similar problem on 12.10 was unable to resolve the problem with the dconf tools, so I decided to put Pantheon on hold for now. Can describe custom menu ? Did you add a menu in the main menu application or are you referring to something else ?

---

### Post by su:bhatta on 2013-08-17
Actually Ubuntu Studio comes with a custom menu, with separate sections for Audio, Video and Graphics editing applications which are bundled together!
Now, after removing Pantheon Shell et al and doing a apt-get autoremove, the applications are all under 'multimedia and  graphics'!

The well designed menu sorting is gone and a ton of thing shows under Settings with two of Screenshot, online accounts etc! 

Never had this problem with adding and removing other metapackages like E17, Kubuntu-desktop, razor-qt which all i've tried already...
Actually, I really liked the Pantheon-shell, it worked well with my low-latency audio stuff, no dropouts!

I've already tried apt-get install ubuntustudio-desktop, but it says the latest version is already installed !!

Anyways, everything is working all in all....
But really like that pantheon shell, tried Elementary OS  in a partition in May-June '13,  liked it!!! Hence thought it would be good to have it back on top of my U'Studio Xfce!

Just found this page: [https://launchpad.net/ubuntu/+source/ubuntustudio-menu](https://launchpad.net/ubuntu/+source/ubuntustudio-menu) maybe it will help!!

---

### Post by Frogs Hair on 2013-08-17
Try the following command to find out  if the package is installed . If it is right click the top panel and look for add and remove items or similar words and try enable the menu.```
 sudo apt-get install ubuntustudio-menu
```

---

### Post by su:bhatta on 2013-08-17
I didn't have ubuntustudio-menu installed, I got it installed, but am not able to make it work still....
Letz see where it goes...;)

Love the fun of playing around in the linux world, i do !!!

---

### Post by su:bhatta on 2013-08-20
marked this as solved! This seems to be a problem with installing Pantheon Shell!

---

### Post by priyanku-mgr on 2013-10-27
Well since the actual issue would still persist (no background) and Google keeps directing to this page, I thought of writing the workaround. By default right click and desktop icons in pantheon is disabled. There are two ways how a wallpaper is managed in pantheon: 1.) pantheon-wallpaper, 2.) Through Nautilus or nemo.
Now to enable it through pantheon-wallpaper(right click still wont work):
1.) Install dconf-tools
2.) Open dconf-editor
3.) org>pantheon>cerbere> add 'pantheon-wallpaper' to the list
4.) org>pantheon>wallpaper> change the file location and the wallpaper changes
To enable right-click and wallpaper through nautilus:
1.) Open terminal:-   nautilus -n
2.) Now add nautilus -n in the cerbere list as mentioned above.

Nemo is the file manager of cinnamon which was made by forking from Nautilus. Cinnamon at present breaks unity in Ubuntu 13.10 so I won't be mentioning that method.

---

### Post by su:bhatta on 2013-10-28
Hi priyanku, glad you shared that.

Now my question:
Currently I am using Ubuntu Gnome 13.10 with Gnome 3.10 & Ubuntu Studio Metas added. 

Will this workaround work if I install elementary-desktop with the ppa?

P.S> I don't think it is possible to install elementary-desktop because of GTK+ version problems. Please ignore.

---

### Post by priyanku-mgr on 2013-10-29
But I am using it without any GTK+ version issues.. You might give it a try..

---

### Post by su:bhatta on 2013-10-29
I tried yesterday & there were a ton of unmet dependencies. 

How did you install, with which ppa's ?

---

