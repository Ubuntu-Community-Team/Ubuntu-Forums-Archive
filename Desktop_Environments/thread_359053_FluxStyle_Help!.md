---
title: "FluxStyle Help!"
date: 2007-02-11
forum: Desktop Environments
---

### Post by ZeroXR on 2007-02-11
I am trying to install a theme on FluxBox and even used [Err's guide]("http://errr-online.com/e107_plugins/content/content.php?content.5") but got lost at this point:

> Thats it now its installed. Now all you need to do is reload the config

    right click menu: fluxbox menu > reload config

I don't see the "reload config" command. The next part confuses me a bit too...

> If this doesnt work make sure your menu has the follwoing entry:

    [submenu] (User Styles) {Choose a style...}
    [stylesdir] (~/.fluxbox/styles)
    [end]

Can someone point me in the right direction? Am I overlooking something? I am using Ubuntu 6.10 and I have FluxBox 1.0rc2.

I have FluxStyle 1.0 installed, but I can't find the command to run the program either.

---

### Post by ZeroXR on 2007-02-11
A mod can move this to Absolute beginners, if need be. I may have put it in the wrong section. :(

---

### Post by paparucino on 2007-02-12
> **ZeroXR said:**
> 
I don't see the "reload config" command. The next part confuses me a bit too...

You should have an item called "restart", this reolad the config.


> 
Can someone point me in the right direction? Am I overlooking something? I am using Ubuntu 6.10 and I have FluxBox 1.0rc2.

Look in  /home/your home/.fluxbox
All config files are there and they all are text files easy to adapt to your convenience

---

### Post by ZeroXR on 2007-02-14
paparucino, thank you for the reply! It actually made a lot more sense!

I have changed my menu file with the new commands from Err's site, but I still don't see viz_plaid style that I extracted to /home/zeroxr/.fluxbox/styles directory. Is there a something else that I am missing still?

---

### Post by yabbadabbadont on 2007-02-14
Upload your ~/.fluxbox/menu file to [http://pastebin.ca/](http://pastebin.ca/) or a similar service and then please post a link to it here.  Also, what is the output of running, "ls -l ~/.fluxbox/styles"?  (Just run it in a terminal window, in case you didn't already know that :))

---

### Post by ZeroXR on 2007-02-16
[http://pastebin.ca/358464](http://pastebin.ca/358464)

Here's the output of using:

```
ls -l ~/.fluxbox/styles
```

```
total 4
drwxr-xr-x 3 zeroxr zeroxr 4096 2007-02-11 14:14 viz_plaid

```

---

### Post by yabbadabbadont on 2007-02-16
What is the output when you run:

grep -i stylesdir /etc/X11/fluxbox/fluxbox-menu

and

grep -i menufile ~/.fluxbox/init

---

### Post by ZeroXR on 2007-02-16
> **yabbadabbadont said:**
> What is the output when you run:

**1)**grep -i stylesdir /etc/X11/fluxbox/fluxbox-menu

and

**2)**grep -i menufile ~/.fluxbox/init

**1)**
[stylesdir] (/usr/share/fluxbox/styles)
[stylesdir] (~/.fluxbox/styles)

**2)**
session.menuFile:       ~/.fluxbox/menu

---

### Post by yabbadabbadont on 2007-02-16
Try changing your ~/.fluxbox/menu so that it looks like this:

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

You shouldn't have needed to add what you did, since the directory you added is already included in /etc/X11/fluxbox/fluxbox-menu.  (which is why I had you grep for it there by the way)

---

### Post by RedSquirrel on 2007-02-16
> **ZeroXR said:**
> http://pastebin.ca/358464

Here's the output of using:

```
ls -l ~/.fluxbox/styles
``````
total 4
drwxr-xr-x 3 zeroxr zeroxr 4096 2007-02-11 14:14 viz_plaid

```


The syntax of your menu is incorrect. You are missing an [end]:

What you have:

```

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[submenu] (User Styles) {Choose a style...}
[stylesdir] (~/.fluxbox/styles)
[end]

```What you should have:

```

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[submenu] (User Styles) {Choose a style...}
[stylesdir] (~/.fluxbox/styles)
[end]
[end]

```In my opinion, you would be best off if you used **fluxbox-generate_menu** to make a menu that has everything you need. See this post:

[http://ubuntuforums.org/showpost.php?p=2151986&postcount=109](http://ubuntuforums.org/showpost.php?p=2151986&postcount=109)

That post is a slightly modified version of the steps found under "Traditional Menu Generation" in the Fluxbox Ubuntu wiki (which is the first item in my signature).

---

### Post by RedSquirrel on 2007-02-16
> **yabbadabbadont said:**
> Try changing your ~/.fluxbox/menu so that it looks like this:

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

You shouldn't have needed to add what you did, since the directory you added is already included in /etc/X11/fluxbox/fluxbox-menu.  (which is why I had you grep for it there by the way)

Did that '/etc/X11/fluxbox/fluxbox-menu' file exist on your system when you installed Fluxbox? I have never had that file. I've heard that the 'menu' package is supposed to create it for you *automagically*, but it has never done so in my experience. 

If I start Fluxbox immediately after installing it from the repositories, I have an emply Fluxbox menu (because the target of the [include] line above doesn't exist). This means I either have to generate a menu or create one manually. Not hard to do, but I'm just curious if you had that /etc/X11/fluxbox/fluxbox-menu file initially.

---

### Post by RedSquirrel on 2007-02-16
> **yabbadabbadont said:**
> Upload your ~/.fluxbox/menu file to [http://pastebin.ca/](http://pastebin.ca/) or a similar service and then please post a link to it here. 


Why would you recommend this over just putting the contents of ~/.fluxbox/menu directly in the forum message? Just curious...

---

### Post by yabbadabbadont on 2007-02-16
> **RedSquirrel said:**
> Why would you recommend this over just putting the contents of ~/.fluxbox/menu directly in the forum message? Just curious...

I didn't know how big his menu was going to be, so I had him dump it at pastebin rather than make a huge post...

---

### Post by yabbadabbadont on 2007-02-16
> **RedSquirrel said:**
> Did that '/etc/X11/fluxbox/fluxbox-menu' file exist on your system when you installed Fluxbox? I have never had that file. I've heard that the 'menu' package is supposed to create it for you *automagically*, but it has never done so in my experience. 

If I start Fluxbox immediately after installing it from the repositories, I have an emply Fluxbox menu (because the target of the [include] line above doesn't exist). This means I either have to generate a menu or create one manually. Not hard to do, but I'm just curious if you had that /etc/X11/fluxbox/fluxbox-menu file initially.

Menu will create the files, but only if it has the fluxbox helper script installed in /etc/menu-methods.  (and possibly the base files in /etc/X11/fluxbox)  What I do when I reinstall is to install fluxbox from apt, then it's build dependencies using apt-get build-dep.  I then save off the following files: ```
/root # tar -tvzf fluxmenu-backup.tar.gz 
-rwxr-xr-x root/root      1177 2006-05-04 23:44:23 menu-methods/fluxbox
drwxr-xr-x root/root         0 2007-02-13 04:10:56 X11/fluxbox/
-rw-r--r-- root/root       306 2006-05-04 23:46:56 X11/fluxbox/keys
-rw-r--r-- root/root       535 2006-05-04 23:47:01 X11/fluxbox/system.fluxbox-menu
-rw-r--r-- root/root        66 2006-05-04 23:47:01 X11/fluxbox/fluxbox.menu-user
-rw-r--r-- root/root      2334 2007-02-13 04:10:56 X11/fluxbox/menudefs.hook
-rw-r--r-- root/root      2851 2007-02-13 04:10:56 X11/fluxbox/fluxbox-menu
-rw-r--r-- root/root      1435 2006-05-04 23:47:01 X11/fluxbox/init
```
Once I've done that, I remove fluxbox using apt and then build and install it from the svn code.  I restore the files I backed up and finally create a ~/.fluxbox/usermenu file that contains:```
[submenu] (Debian Menu)
[include] (/etc/X11/fluxbox/menudefs.hook)
[end]
```
fluxbox-generate_menu then includes usermenu in the main menu and it in turn includes the standard debian menu entries created when update-menus is run after packages are installed.

---

### Post by RedSquirrel on 2007-02-22
> **yabbadabbadont said:**
> Menu will create the files, but only if it has the fluxbox helper script installed in /etc/menu-methods.  (and possibly the base files in /etc/X11/fluxbox)  What I do when I reinstall is to install fluxbox from apt, then it's build dependencies using apt-get build-dep.  I then save off the following files: ```
/root # tar -tvzf fluxmenu-backup.tar.gz 
-rwxr-xr-x root/root      1177 2006-05-04 23:44:23 menu-methods/fluxbox
drwxr-xr-x root/root         0 2007-02-13 04:10:56 X11/fluxbox/
-rw-r--r-- root/root       306 2006-05-04 23:46:56 X11/fluxbox/keys
-rw-r--r-- root/root       535 2006-05-04 23:47:01 X11/fluxbox/system.fluxbox-menu
-rw-r--r-- root/root        66 2006-05-04 23:47:01 X11/fluxbox/fluxbox.menu-user
-rw-r--r-- root/root      2334 2007-02-13 04:10:56 X11/fluxbox/menudefs.hook
-rw-r--r-- root/root      2851 2007-02-13 04:10:56 X11/fluxbox/fluxbox-menu
-rw-r--r-- root/root      1435 2006-05-04 23:47:01 X11/fluxbox/init
```Once I've done that, I remove fluxbox using apt and then build and install it from the svn code.  I restore the files I backed up and finally create a ~/.fluxbox/usermenu file that contains:```
[submenu] (Debian Menu)
[include] (/etc/X11/fluxbox/menudefs.hook)
[end]
```fluxbox-generate_menu then includes usermenu in the main menu and it in turn includes the standard debian menu entries created when update-menus is run after packages are installed.


Thanks for the info. 

I have been experimenting with the menu configuration and I have it pared down to just two entries: "Debian Menu" (using your menudefs.hook idea) and the usual "fluxbox menu" (with its standard entries and one I added to list the backgrounds so I can change the background easily).

```
[submenu] (Backgrounds)
 [wallpapers] (~/.fluxbox/backgrounds) 
 [wallpapers] (~/misc/wallpapers) 
[end]

```I tend to use keyboard shortcuts for the things I use most often, so I only open the menu on occasion. Still, it's nice to have it neat & tidy!

I have started a new thread regarding the reasons for compiling fluxbox versus installing from the repositories. I would be very interested in hearing your opinion on this if you have time. 

Thanks.

Here it is:

[http://ubuntuforums.org/showthread.php?p=2195622](http://ubuntuforums.org/showthread.php?p=2195622)

---

