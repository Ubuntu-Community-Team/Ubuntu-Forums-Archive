---
title: "Is there a way to install 10.04 default theme on 14.04? Maybe something similar?"
date: 2014-05-13
forum: Desktop Environments
---

### Post by 03927e9c on 2014-05-13
Hello, I've been using Ubuntu for five years, back in 2010 I installed 10.4 and never upgraded until now, I just installed 14.4 (from zero, removing the older one) and first of all I hate Unity so I got rid of it installing gnome-flasback, but I also want to use the icons and theme from Ubuntu 10.4, these are horrible (it's just a matter of each one). So, is there a way I can install it? Or something very similar?

Thanks in advance.

OFF TOPIC: I tagged the thread with "lubuntu", please change it to "ubuntu".

---

### Post by Frogs Hair on 2014-05-13
You could try the following themes . I did get the old icons to work by extracting the folders from the.deb,renaming them ubuntu-mono 10.04 and placing them in  home .icons. [U]Caution Installing from the .deb will conflict with the currently installed theme. 
[/U]

[http://packages.ubuntu.com/lucid/all/ubuntu-mono/download](http://packages.ubuntu.com/lucid/all/ubuntu-mono/download)

 [http://www.noobslab.com/2014/04/ambiance-crunchy-themes-updated-install.html](http://www.noobslab.com/2014/04/ambiance-crunchy-themes-updated-install.html)

---

### Post by grahammechanical on 2014-05-13
The problem is not with Ubuntu or with Unity but with Gnome DE. It is now at version 3 and this means that all the themes that worked with Gnome 2 and Gnome panel do not work with Gnome 3 because there were not built by the GKT that Gnome 3 presently uses. You need to find themes built using GTK3.

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

By the way, since you mentioned it. I hate that old fashioned look. You love it. I hate it. But why mention it in the first place? If you want help. just ask and if we can we will help. But leave aside personal tastes. It is not the Ubuntu way. It causes arguments.

---

### Post by buzzingrobot on 2014-05-13
The Gnome in 10.04 used Gtk2.  Gnome3 and many current themes are built on Gtk3. Themes need to support Gtk2 and Gtk3 to correctly display Gtk2 and Gtk3 apps.

---

### Post by hitman2k9 on 2014-05-13
Most themes will support gnome-flashback , and install gnome-tweak-tool to customize it . 
[http://itsfoss.com/best-themes-ubuntu-1310/](http://itsfoss.com/best-themes-ubuntu-1310/)
[http://www.upubuntu.com/2012/07/a-list-of-best-15-ubuntu-1204-themes.html](http://www.upubuntu.com/2012/07/a-list-of-best-15-ubuntu-1204-themes.html)
Here are a few that I used to use :). If you want the GTK2 feel completely you might want to look into mate if so. Hope this helps , I also faced the same when i upgraded from 10.04 LTS.

---

### Post by 03927e9c on 2014-05-13
Thanks everybody for the replies. Well, first I gotta say that I actually wanted the "humanity theme from 10.4", it's just that I used it for so many years that I thought it was the default, my apologies. Anyways, I went to to /usr/share/icons/ and pasted [http://packages.ubuntu.com/lucid/all/humanity-icon-theme/download](http://packages.ubuntu.com/lucid/all/humanity-icon-theme/download) as "Humanity-old", then I chose it on Ubuntu Tweak and nothing changed, I also tried with the "Humanity" pack that comes with 14.4 and still nothing, the only change is in the icons next to to the hour (right upper bar).

This is how I actually want it to look like, but from your replies I'm guessing it's almost imposible (the gtk version problem)

[Album of screenshots]("http://imgur.com/a/6zWir")

---

### Post by buzzingrobot on 2014-05-14
Did you install that humanity-icon-theme package or just drop it in /usr/share/icons?  Click on the deb file and it should be installed correctly into /usr/share/icons.

The window decorations in that screenshot look very much like those in the Clearlooks theme, only a different color.  Clearlooks is GTK2 only, but the Clearlooks-Phenix-theme reproduces that look for GTK2 and GTK3.  I've never tried it in Unity, though.  

Gnome 2 had, and Mate retains, tools to make individual adjustments of window decorations, controls, colors, etc. I don't believe Unity easily enables that kind of fine-grained approach without manually editing theme files.

[You could probably get that look by using Mate, installing Clearlooks-Phenix-theme, playing with the colors, and installing that icon theme. The gcolor2 app is handy to determine colors displayed on screen:  Click on something and it displays that color's hex code. Note that Mate is an entirely separate desktop environment that you use instead of Unity. Linux Mint, based on Ubuntu and using Ubuntu repos, has a new Mate release based on 14.04 due out probably around the end of May.]

---

### Post by 03927e9c on 2014-05-15
Thanks, I just installed Mate and the theme you suggested, and by far is the closest look that I've been looking for.

About your question, yes, I just copy-n-paste it (with sudo rights) the icon pack, but now I just clicked on it to install it and I get an error saying that there's a newer version installed, so it won't let me install it. What can I do?

---

### Post by buzzingrobot on 2014-05-15
> **03927e9c said:**
> 

About your question, yes, I just copy-n-paste it (with sudo rights) the icon pack, but now I just clicked on it to install it and I get an error saying that there's a newer version installed, so it won't let me install it. What can I do?

If the package is already installed, there really isn't a need to install it again. The icons available to the system are located in folders in the /usr/share/icons directory. Point your file manager there and see if it's there.

In Unity, you can install the Unity-Tweak-Tool to change themes and icons. There's no tool installed by default to do that.

In Mate, it's System->Preferences->Appearance. The "Customize" button there will allow you to switch away from a themes default icon set.

---

### Post by 03927e9c on 2014-05-16
Ok, nevermind the icons. I have a doubt, if I'm using Mate, that means that I'm on GTK2?, if yes, that means that I can use the 10.4 live CD and copy the theme and icons?

---

### Post by buzzingrobot on 2014-05-16
Mate is currently based on GTK2.  The next version, 1.10, will be able to be built on Gtk2 Gtk3 libraries, as each distribution chooses.

GTK is a toolset that provides graphic display elements developers can use, rather than coding them from scratch. GTK2 vs GTK3 should not affect icon use, although older icon sets may not include icons for newer applications. Themes are different. Old GTK2 themes from Gnome 2/10.04 probably won't theme GTK3 apps correctly. Most (all?) themes included with Mate are GTK2 and GTK3 compatible.

---

### Post by 3rdalbum on 2014-05-17
Personally, I think if you want everything to look and work the same for many years, then Ubuntu is not the distribution for you. It is, by definition, a fast-paced distro. Some would argue that Linux is not an operating system for people who dislike change.

If you haven't already spent time with Unity, I would still recommend you use it for a week and see if you like it. It's very, very, very different to Gnome so it takes a little bit of time to get used to, but once you're used to it you might find you love it. Just don't expect it to be anything like Gnome 2.

---

### Post by 03927e9c on 2014-05-18
> **buzzingrobot said:**
> Mate is currently based on GTK2.  The next version, 1.10, will be able to be built on Gtk2 Gtk3 libraries, as each distribution chooses.

GTK is a toolset that provides graphic display elements developers can use, rather than coding them from scratch. GTK2 vs GTK3 should not affect icon use, although older icon sets may not include icons for newer applications. Themes are different. Old GTK2 themes from Gnome 2/10.04 probably won't theme GTK3 apps correctly. Most (all?) themes included with Mate are GTK2 and GTK3 compatible.
Ok I got it, but sorry if I ask this again, is it possible to copy the Clearlooks theme from the 10.4 live CD and use it in 14.4?

> **3rdalbum said:**
> Personally, I think if you want everything to look and work the same for many years, then Ubuntu is not the distribution for you. It is, by definition, a fast-paced distro. Some would argue that Linux is not an operating system for people who dislike change.

If you haven't already spent time with Unity, I would still recommend you use it for a week and see if you like it. It's very, very, very different to Gnome so it takes a little bit of time to get used to, but once you're used to it you might find you love it. Just don't expect it to be anything like Gnome 2.
I'm sorry, but it's nothing against the change, but the concept that Unitiy is based on, I find it very, very, awful and poor, it's just me. Also, Linux is based on that you can change and work around it the way you can, so I disagree with you, if Linux changes, and you don't like, you can work around it the way you want. I'm sick of people trying to convince others to use Unity. I'm not convincing anybody not to use it. I already got a similar reply to this in the first page, which I didn't pay no attention on purpose.

---

