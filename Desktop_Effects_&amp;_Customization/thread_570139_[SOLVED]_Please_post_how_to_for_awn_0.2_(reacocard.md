---
title: "[SOLVED] Please post how to for awn 0.2 (reacocard?)"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-10-07
I installed the bzr (around the time stacks came out) by means of this thread:

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

But the release of 0.2 just hit the Digg from page, and I want it!

[http://digg.com/linux_unix/Awn_0_2_released_the_best_dock_on_linux_just_got_stable_Pics_Vids](http://digg.com/linux_unix/Awn_0_2_released_the_best_dock_on_linux_just_got_stable_Pics_Vids)

(pics and vid here - [http://njpatel.blogspot.com/2007/10/01-01.html](http://njpatel.blogspot.com/2007/10/01-01.html) )


How can I upgrade?



Is this repo -

[http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/)

going to get hit with the update, and prompt me to upgrade if it's in my sources?


Like I said, I have the bzr, so since this release is not bzr, will I need to uninstall and reinstall?

If so, what is the best method? (I'd like automatic updates in the future)

Thanks!

---

### Post by coldstatue on 2007-10-07
BTW - I tried

bzr update
./autogen.sh && make clean && make && sudo make install

After the first command, I got some errors about not being able to delet folders, because they were not empty. i tried again and got 

Tree is up to date at revision 129.

so, i went ahead with the build.
It worked ok, but I have no new features

---

### Post by JBAlaska on 2007-10-07
1- Install build tools and all of the dependencies:
```
sudo apt-get install build-essential automake1.9 autotools-dev bzr libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev
```

2- Download 0.2 from here, to a tmp location:
```
https://launchpad.net/awn/+download
```

3-open a term in the temp location and type:
```
./configure
```
```
make
```
```
sudo make install
```

The above worked for me and gave me all kinda cool new options!

---

### Post by andrewsomething on 2007-10-07
Reacocard's repo will continue to be updated often. It is the development branch.  All changes that are in the new release are already in bzr. I assume reacocard will release debs of the new stable release as well. When he does, you'll be able to install that with "sudo apt-get install avant-window-navigator" with his repo enabled or you can continue using what you already are using if you don't mind the bumps that some time occur when using the the developmental snapshots.

---

### Post by coldstatue on 2007-10-07
ok, thanks Andrew. I'd rather wait for it to hit the repos, so I don't have to rebuild for every new feature. That's not Andrew Or####hl is it?

JB, with that build, did you get all of these applets?

[http://wiki.awn-project.org/index.php?title=Awn_Extras#Installation](http://wiki.awn-project.org/index.php?title=Awn_Extras#Installation)

I tried to build the extras, but have no directory like the ones referred to for autogen.sh. (awn-extras/awn-applets/awn-core-applets) I have an applets folder within ~avant-window-navigator, but no files for compilation. Doesn't matter really, just curious. i can wait.

---

### Post by cypresstwist on 2007-10-07
Compiled just fine :D

---

### Post by JBAlaska on 2007-10-08
> **coldstatue said:**
> ok, thanks Andrew. I'd rather wait for it to hit the repos, so I don't have to rebuild for every new feature. That's not Andrew Or####hl is it?

JB, with that build, did you get all of these applets?

[http://wiki.awn-project.org/index.php?title=Awn_Extras#Installation](http://wiki.awn-project.org/index.php?title=Awn_Extras#Installation)

I tried to build the extras, but have no directory like the ones referred to for autogen.sh. (awn-extras/awn-applets/awn-core-applets) I have an applets folder within ~avant-window-navigator, but no files for compilation. Doesn't matter really, just curious. i can wait.

The build I used did not come with the extra applets, I used the same procedure as in your link to get them. I think if you use synaptic to install the "awn-core-applets-bzr", you will have the required dir's to update the extra applets.
This is probably not the official way to do it...but it does work lol.

---

### Post by SSB on 2007-10-08
any idea how long it'll take for the update to hit the repos everyone here has been using? I saw this update on digg while i windows and got so excited I had to switch over here, but I saw no update :(

---

### Post by itchywolf on 2007-10-08
Those applets aren't new, I've been using them for weeks now. I got all excited when you said "new applets" :(

I doubt the repo's will be updated soon, they just recently updated them so that python applets would work, and the guy who maintains the repo's seems to be pretty busy in real life because the python applets have been around and working for everyone else for a long time. Just download the tar.gz and do the configure make make install routine and copy the applets to your applets directory. I'm a total newb and had never even compiled anything from source before, but I'm glad I did, it actually WORKED when the repo's gave me nothing but grief with non-working/busted applets. If you need help just look around here: [http://www.planetblur.org/hosted/awnforum/](http://www.planetblur.org/hosted/awnforum/) there are how-tos and very helpful people there.

If make bitches about something missing just google what it's looking for and install the appropriate packages.

Pretty crazy to expect the repos to be updated any time soon, seeing as how AWN is still in development and it's just as easy to compile it yerself.(If I can do it, anyone can.) Anyway, sorry if I'm being a jerk but my back is killing me and it's almost 4am... Anyway, like I said,  I wouldn't be surprised to see a month go by without it being added to the repos, seeing as how it took so long just to get the stupid python applets working.

---

### Post by coldstatue on 2007-10-08
> **JBAlaska said:**
> The build I used did not come with the extra applets, I used the same procedure as in your link to get them. I think if you use synaptic to install the "awn-core-applets-bzr", you will have the required dir's to update the extra applets.
This is probably not the official way to do it...but it does work lol.

i already have awn-core-aplets-bzr. still, no directories as listed there. I will look into it and post back, in case others are having this issue.

---

### Post by coldstatue on 2007-10-08
Well, it looks like the times I tried, the trunk directory was not actually created. It works now. the full path for me was
~/avant-window-navigator/trunk/awn-applets/awn-core-applets
The extra applets are available, but not functioning. We'll see what happens when 0.2 hits the repo

---

### Post by coldstatue on 2007-10-08
> **itchywolf said:**
> Those applets aren't new, I've been using them for weeks now. I got all excited when you said "new applets" :(

I doubt the repo's will be updated soon, they just recently updated them so that python applets would work, and the guy who maintains the repo's seems to be pretty busy in real life because the python applets have been around and working for everyone else for a long time. Just download the tar.gz and do the configure make make install routine and copy the applets to your applets directory. I'm a total newb and had never even compiled anything from source before, but I'm glad I did, it actually WORKED when the repo's gave me nothing but grief with non-working/busted applets. If you need help just look around here: [http://www.planetblur.org/hosted/awnforum/](http://www.planetblur.org/hosted/awnforum/) there are how-tos and very helpful people there.

If make bitches about something missing just google what it's looking for and install the appropriate packages.

Pretty crazy to expect the repos to be updated any time soon, seeing as how AWN is still in development and it's just as easy to compile it yerself.(If I can do it, anyone can.) Anyway, sorry if I'm being a jerk but my back is killing me and it's almost 4am... Anyway, like I said,  I wouldn't be surprised to see a month go by without it being added to the repos, seeing as how it took so long just to get the stupid python applets working.

Thanks itchy, and sorry about the 'new applets' tease. They are for me. :0) I might just compile if it's that far out.

---

### Post by coldstatue on 2007-10-08
ok, ok. after a lot of hemming an hawing, I did it. It works great. Thanks all.

---

### Post by dmber on 2007-10-09
awesome, thank you very much!!

---

