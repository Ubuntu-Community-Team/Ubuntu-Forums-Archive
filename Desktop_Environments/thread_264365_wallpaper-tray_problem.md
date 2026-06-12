---
title: "wallpaper-tray problem"
date: 2006-09-24
forum: Desktop Environments
---

### Post by 13east on 2006-09-24
i've been trying to get this nice little wallpaper to work but can't seem to configure it.  i can't add any folder into the directory list and can't set any of the options (the apply option is unclickable).  would really appreciate some help.

---

### Post by Boatswain on 2006-10-27
> **13east said:**
> i've been trying to get this nice little wallpaper to work but can't seem to configure it.  i can't add any folder into the directory list and can't set any of the options (the apply option is unclickable).  would really appreciate some help.

I've got the same problem going on.  Did you manage do get it fixed, or does anyone else out there have any info?

Tom

---

### Post by little cazy on 2006-11-27
me three.

---

### Post by the_joker on 2006-12-01
> **13east said:**
> i've been trying to get this nice little wallpaper to work but can't seem to configure it.  i can't add any folder into the directory list and can't set any of the options (the apply option is unclickable).  would really appreciate some help.
There is a fault with the repo version of this package. Running the program from a terminal shows the following output when the configuration menu is displayed:

> (wp_tray:25264): libglade-WARNING **: could not find signal handler 'on_button_close_pressed'.

(wp_tray:25264): libglade-WARNING **: could not find signal handler 'on_button_apply_pressed'.

(wp_tray:25264): libglade-WARNING **: could not find signal handler 'on_button_add_dir_pressed'.

(wp_tray:25264): libglade-WARNING **: could not find signal handler 'on_button_rem_dir_pressed'.


I'm not sure how to fix the issue, however you can set all the options using gconf-editor. In a terminal, type gconf-editor, select the key /apps/wp_tray and modify the parameters. It may help to have the configuration window open at the same time, so you can check the options.

I managed to set it up in this way and it seems to be working fine.

On another note, I attempted to build the newest version from the source available at [http://planetearthworm.com/projects/wp_tray/index.php](http://planetearthworm.com/projects/wp_tray/index.php) but for the life of me, I can't figure out where it went.

I'll create a new thread for this issue, and link back to it from here.

---

### Post by the_joker on 2006-12-01
I've posted a new thread at [http://ubuntuforums.org/showthread.php?p=1831054](http://ubuntuforums.org/showthread.php?p=1831054) detailing the issues I've epxerienced compiling the latest version.

---

### Post by DJ_Peng on 2006-12-03
@Joker:
Were you able to set it to get a random image? I couldn't see how to specify that in the Configuration Editor.

---

### Post by the_joker on 2006-12-03
> **DJ_Peng said:**
> @Joker:
Were you able to set it to get a random image? I couldn't see how to specify that in the Configuration Editor.
That's a good question. It seems that my wallpaper is changing randomly, however I didn't find an option for it in the gconf-editor.

I did select Random in the wp_tray configuration panel - it may have been stored correctly. The terminal output seems to indicate that only the buttons don't work, so if the selection mode changes, it is possible that the setting is stored correctly.

At the very least, it's worth a try. Hope this helps.

---

### Post by the_joker on 2006-12-04
> **the_joker said:**
> 
On another note, I attempted to build the newest version from the source available at [http://planetearthworm.com/projects/wp_tray/index.php](http://planetearthworm.com/projects/wp_tray/index.php) but for the life of me, I can't figure out where it went.

I'll create a new thread for this issue, and link back to it from here.

Update: I found that the new version does not install as an application - it is created to be a panel applet.

To use it, click your right mouse button on the panel, select Add to Panel... and select Wallpaper Tray from the Utility section of the window. :mrgreen: 

Everything is working fine, and the dialog boxes appear to be working fine. Installation can be a bit of a pain - if anyone wants step-by step instructions, I may be able to remember how I got it all working.

---

### Post by DJ_Peng on 2006-12-08
Where did you find the new version? I've got version 0.4.6.3build1 from Synaptic, but what you found seems even better. Does it do picture randomization?

---

### Post by the_joker on 2006-12-08
> **DJ_Peng said:**
> Where did you find the new version? I've got version 0.4.6.3build1 from Synaptic, but what you found seems even better. Does it do picture randomization?
You need to install it from source, which is available at the project's homepage: [http://planetearthworm.com/projects/wp_tray/index.php](http://planetearthworm.com/projects/wp_tray/index.php)

---

### Post by DJ_Peng on 2006-12-08
Shiny. I'll make that part of this weekend's projects. I assume I should uninstall the one I have first.

---

### Post by DJ_Peng on 2006-12-08
I extracted it and tried running sudo ./config from within the extracted directory but it ended with > checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

What am I missing?

---

### Post by DJ_Peng on 2006-12-08
Doh! I download my installers to a separate drive. I moved it into my home folder and ended up in dependency hell. Once I found all the dependencies I played hell getting all of the Boost Filesystem C++ library. I think I got it installed, and I ran it from the Terminal, but I can't see any evidence that it's running.

---

### Post by the_joker on 2006-12-27
> **DJ_Peng said:**
> Doh! I download my installers to a separate drive. I moved it into my home folder and ended up in dependency hell. Once I found all the dependencies I played hell getting all of the Boost Filesystem C++ library. I think I got it installed, and I ran it from the Terminal, but I can't see any evidence that it's running.

You will need to add it to your gnome-panel.

I've moved on to KDE, but I think it was simply a matter of right-clicking the panel, and selecting "Add to Panel".

You should find the new WP_Tray applet at the bottom of the window.

Hope this helps.

---

### Post by DJ_Peng on 2006-12-27
It is, and I even found how to make it run at login, although I disabled it until after the holidays. Thanks for all the assistance.

---

### Post by Kat of Zion on 2007-01-26
> **the_joker said:**
> Update: I found that the new version does not install as an application - it is created to be a panel applet.

To use it, click your right mouse button on the panel, select Add to Panel... and select Wallpaper Tray from the Utility section of the window. :mrgreen: 

Everything is working fine, and the dialog boxes appear to be working fine. Installation can be a bit of a pain - if anyone wants step-by step instructions, I may be able to remember how I got it all working.

Im not getting any utilities in the "Add to Panel" dialog that speak about the Wallpaper Tray. It is installed but doesnt appear on the list.

-Kat

---

### Post by the_joker on 2007-01-28
> **DJ_Peng said:**
> It is, and I even found how to make it run at login, although I disabled it until after the holidays. Thanks for all the assistance.

> **Kat of Zion said:**
> Im not getting any utilities in the "Add to Panel" dialog that speak about the Wallpaper Tray. It is installed but doesnt appear on the list.

-Kat

Kat, check your "Add to Panel" Applet for WP_Tray. It should be at the bottom of the panel, and is not necessarily under the Utilities category.

---

### Post by kkram13 on 2007-02-04
I'm having the same problem as Kat - I've installed it from a .tar.gz, got it to compile after sorting out the dependencies, make and sudo make install worked. I can see wp_tray in /usr/local/libexec, but nothing shows up when I go on the panel, Add to Panel - nothing about wp_tray in any of the sections. :(  Any ideas?

Where I can see the program is if I go to Applications -> System Tools -> Configuration editor and then under apps. Another thread suggested ticking all the boxes there and inserting the right directory where the background files are. No joy.

Oh - I'm using Edgy. Any help would be much appreciated!

Mark

P.S. Alternatively: how would I go about uninstalling the program? Does sudo make uninstall work?

|\/|<

---

### Post by saabsista on 2007-02-18
Hello everybody from Italy,

I got the older version (0.4.6-3build1 edgy) to work.
I downloaded and installed it with synaptic, then I used Gconf to set the options, and I added the command "wallpaper-tray" to startup programs in the session manager.

But I don't know what exactly "check files are images" and "follow symlinks" options mean. Does anybody do? :confused: 

I'd also like to try the newest version, but I'm very new to compiling, sources and stuff, so I'd really appreciate to receive those step-by-step instructions from the_joker ... :)

thanks
sabrina

---

### Post by gtr225 on 2007-03-12
Hey I just figured out that if you want to change "picture options", you can do so by right clicking on your desktop and select Change Desktop Background. From there you can select the style and Wallpaper Tray should follow the changes you make.

---

### Post by DJ_Peng on 2007-03-12
Awesome tip. That saves me from having to manually scale some of my desktop pics.

---

### Post by gtr225 on 2007-03-12
I think the only setting left is the one for what order to choose pictures. That I've yet to figure out how to change, though I leave it on random anyway.

---

### Post by kspn on 2007-06-22
This is kinda a dumb question but what is the location of the image file that this app changes?

I am running XUbuntu, so if I need a different program the let me know.

Edit: don't worry I am using a script to change the Wallpaper now

---

### Post by yabbadabbadont on 2007-06-22
Does anyone know how well it handles a truly large wallpaper collection?  (in excess of 50,000 images)

---

