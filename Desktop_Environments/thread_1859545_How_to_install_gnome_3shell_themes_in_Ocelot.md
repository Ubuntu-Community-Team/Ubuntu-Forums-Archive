---
title: "How to install gnome 3/shell themes in Ocelot?"
date: 2011-10-14
forum: Desktop Environments
---

### Post by fullerenedream on 2011-10-14
I just updated to Ocelot today and I'm a fairly new Linux user. I'm playing with gnome shell and I'd like to change the gnome 3 and gnome shell themes. There are some instructions for how to do this around the web, but they seem to be from people who were running beta versions. Will their instructions be correct?

What is the simplest (read: easy for noobs) way to install gnome 3 and gnome shell themes?

Thanks for your help!


Edit: I tried to follow the instructions from this website:
[COLOR=Blue]http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html[/COLOR]
to install the gnome shell user themes extension.

Adding the webupd8 gnome 3 ppa seemed to work fine, but when I entered this command (as instructed),[FONT=Verdana]

[/FONT][COLOR=Blue]sudo apt-get install gnome-shell-extensions-user-theme gnome-tweak-tool[/COLOR]

I just get an error message:

[COLOR=Blue]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions-user-theme[/COLOR]

Maybe the webupd8 gnome 3 ppa didn't actually get added? I can't really tell because I don't understand what the terminal said. Here's what it spit out when I tried to add it:

[COLOR=Blue]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.uqkE2MXZNb --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)[/COLOR]

What do you think? Did it even get added?

---

### Post by gg234 on 2011-10-14
try this [http://www.ubuntugeek.com/install-gnome-shell-extensions-on-ubuntu-11-10-using-ppa.html](http://www.ubuntugeek.com/install-gnome-shell-extensions-on-ubuntu-11-10-using-ppa.html)

---

### Post by fullerenedream on 2011-10-14
Thanks. I ran the code that it said to run. But I am a fool because I then realized I don't know exactly what I did.

Where it says "Loads a shell theme from ~/.themes//gnome-shell", what does the double slash mean? Does the gnome-shell part of that mean a folder or a file? Do I have to name my desired theme gnome-shell and put it in the right place, or perhaps I can put all my themes in a folder called gnome-shell and then they will appear in the Shell Theme dropdown in Advanced Settings?

Also, that link was about gnome shell themes. What do I do for gnome 3 themes?


Edit: I tried making a folder called gnome-shell in the .themes folder that's in my Home folder. I unpacked a gnome shell theme and put its folder into the new gnome-shell folder. Then I checked to see if it appeared in Advanced Settings (which I think is a fancy name for gnome tweak tool), but it's not there. What am I doing wrong?

Oh, one more thing. Should I be seeing something in the Shell Extension section of Advanced Settings now? Because there's still nothing there.

---

### Post by crdlb on 2011-10-14
[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

> User Theme extension: Lets you load GNOME Shell themes from ~/.themes/THEME_NAME/gnome-shell or /usr/share/THEME_NAME/gnome-shell. This extension is especially useful when used with GNOME Tweak Tool. This way, you can install and switch between GNOME Shell extensions with a click. Install both User Theme extension and GNOME Tweak Tool:

That is a better explanation.

There aren't many GTK3 themes yet, but the method is basically the same.

---

### Post by collisionystm on 2011-10-14
It depends on the file you download. Some themes require you to replace files in your /usr/share/themes/atwaita

other you simply need to do this..

mkdir /home/username/.themes

put files into .themes folder ( its a hidden folder, press CTRL + H to show it )

Use gnome-tweak-tool to choose your new theme.

---

### Post by fullerenedream on 2011-10-14
Awesome, thank you everyone, I am getting some of these to work! Damn gnome shell is sexy! :D

---

### Post by merlinus on 2011-10-14
I installed the shell extensions following directions at the webpage cited, but there are no options listed for Shell Extensions in the Advanced Settings tool.  I did log out, and then logged in again.

Also, I downloaded a few gtx3 themes and extracted them to /usr/share/themes, but they do not show up in the list of Themes.

Help appreciated, especially in terms of installing a dark theme.

---

### Post by ian_balisy on 2011-10-14
Hi there,

I'm having problems getting gnome shell themes to install on my system. Gnome Tweak Tool works and I can switch between the standard themes using it, but my problem is a little different. Probably linked to my inexperience and stupidity when it comes to Ubuntu.

I download the theme (Nord is the one I'm trying to use), then I extract the folder to the desktop just so I can copy and paste it myself. Then, when I try to put it in the themes folder, it says that I don't have permission to do anything with this folder.

Any way to fix this?

---

### Post by merlinus on 2011-10-14
You need to do this as root.  One way is to open a terminal, and type:

gksudo nautilus

This will open the file browser with root privileges, and you can then copy the files to your directory of choice.

Do be careful, however, because it is possible to royally screw things up!

---

### Post by crdlb on 2011-10-14
You can also use ~/.themes/ to install themes for just your user.

---

### Post by fullerenedream on 2011-10-14
I got some gnome 3 and gnome shell themes going, yay! Then I logged out and logged back in to play with unity and... unity is broken :(

It shows my desktop background and a grey panel at the top that just shows a file menu that doesn't do anything. At least ctrl-alt-del worked so I could switch back to gnome shell.

I tried switching back to the default themes and then logging in with unity but it's still broken. I was able to switch back and forth before I got the themes working. It's frustrating because I really want to play with gnome shell AND unity! Also annoying because unity seemed more stable so far.

Anyone else have this problem? Any idea how to fix it?

---

### Post by ian_balisy on 2011-10-15
Thanks merlinus, got the folder into the themes directory. However, now when I pull up gnome tweak tool, I can only change the shell theme. The Nord theme doesn't show up in the window themes option and there. What am I doing wrong? Do I need to download other files to get the window theme? Because right now, I don't really see the point in just having the shell theme if the windows are still going to be default. Can anyone give a brief step-by-step GNOME Shell installation using GNOME Tweak Tool? This would be very useful to many, including myself, within this thread.

Thanks!

---

### Post by merlinus on 2011-10-15
From my experience, the only themes that will work have to be gtk3+.  And not even all of these!

Maddening....

---

### Post by fullerenedream on 2011-10-15
Some of my metacity themes are working too, as window themes. Hacked Dark Compact and Tactile look pretty good.

---

### Post by ian_balisy on 2011-10-15
> **merlinus said:**
> From my experience, the only themes that will work have to be gtk3+.  And not even all of these!

Maddening....

Could you tell me (and others wondering the same thing) how to get and install these gtk3+ themes? I'm familiar with deviantart and they have some there, I think, but it would be nice to know which ones are confirmed working properly on Ocelot.

Also, quite maddening.

---

### Post by fullerenedream on 2011-10-15
gtk3+ themes:
[http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167](http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167)

---

### Post by BazookaAce on 2011-10-15
> **ian_balisy said:**
> Could you tell me (and others wondering the same thing) how to get and install these gtk3+ themes? I'm familiar with deviantart and they have some there, I think, but it would be nice to know which ones are confirmed working properly on Ocelot.

Also, quite maddening.

I've tried these GTK3 themes, and they are fully working: 

[http://half-left.deviantart.com/art/SLAVE-GTK3-256366787?q=boost%3Apopular%20gtk3&qo=0](http://half-left.deviantart.com/art/SLAVE-GTK3-256366787?q=boost%3Apopular%20gtk3&qo=0)

[http://grvrulz.deviantart.com/art/Elegant-Brit-gnome3-208925032?q=boost%3Apopular%20gtk3&qo=12](http://grvrulz.deviantart.com/art/Elegant-Brit-gnome3-208925032?q=boost%3Apopular%20gtk3&qo=12)

[http://half-left.deviantart.com/art/GNOME-3-Adwaita-Improved-206172213?q=boost%3Apopular%20gtk3&qo=25](http://half-left.deviantart.com/art/GNOME-3-Adwaita-Improved-206172213?q=boost%3Apopular%20gtk3&qo=25)

You can also go to Gnome-look-org. The themes under "GTK3" works too. Enjoy!

---

### Post by ian_balisy on 2011-10-15
BazookaAce: Ok, I've got both the Window Theme and GTK3 theme working from Zukitwo, but the shell still doesn't work. It shows up grey with "File Edit View Go Bookmarks Help" on the left hand side, it isn't as tall so there's a space in between the shell and the maximized windows, all the fonts are small and white. Any solutions to this?

---

### Post by BazookaAce on 2011-10-15
Aha! Open Gnome Tweak Tool (advanced settings) and disable "let file manager handle desktop". If the shell still doesn't theme correctly press ALT+F2 and hit R. If it still doesn't work try to log out and in again.

---

### Post by ian_balisy on 2011-10-15
> **BazookaAce said:**
> Aha! Open Gnome Tweak Tool (advanced settings) and disable "let file manager handle desktop". If the shell still doesn't theme correctly press ALT+F2 and hit R. If it still doesn't work try to log out and in again.

Thank you! Could not figure that out, didn't even cross my mind that that might be the problem.

---

### Post by fullerenedream on 2011-10-16
Has anyone else had problems with Unity not displaying right after playing around with gnome 3/shell themes? In Unity all it displays is my desktop background and a grey top panel with file, edit, etc on it. Nothing responds to clicking anywhere but ctrl-alt-del works so I can log out.

Edit: it's the same menu that appears behind Activities in the top panel when I try to use a gnome shell theme with a transparent panel. (I've heard the fix for that is turning off the global menu, but I like the global menu in Unity, so I'm not sure what to do about that either.)

Edit the 2nd: fixed the transparent panel problem by turning off the "have file manager handle the desktop" option like [COLOR=Black][BazookaAce]("http://ubuntuforums.org/member.php?u=724195")[/COLOR] said.

---

