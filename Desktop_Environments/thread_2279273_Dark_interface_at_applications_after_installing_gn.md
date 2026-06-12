---
title: "Dark interface at applications after installing gnome-desktop"
date: 2015-05-22
forum: Desktop Environments
---

### Post by chrisasl92 on 2015-05-22
Hello, 

I'm using Ubuntu 14.04.2 and Unity DE.
I was trying to solve some issues with compiz and Unity, so I tried installing Gnome desktop to see if the issue occurred with this DE as well.
My main DE is Unity, and this is what I want to stay with, so I selected it again at the login-screen.

[B]The problem is that after installing the Gnome-desktop, non-default themes are always black ([I]although they shouldn't).

[/I][/B]*Example:* Themes like [Moka, Orchis]("http://mokaproject.com/"), [Numix Light]("http://satya164.deviantart.com/art/Numix-Light-GTK3-theme-391993388") (which I as using) are now dark. This affects applications as well (when I choose one of these themes), i.e. this is how gedit looks when I choose [Numix Light]("http://satya164.deviantart.com/art/Numix-Light-GTK3-theme-391993388"):

[IMG]http://i.imgur.com/WunC8C0.png[/IMG]

**What I've tried:**
[LIST=1]
[*]removing gnome-desktop with ```
sudo apt-get purge gnome-desktop
```
[*]reinstalling ubuntu-desktop
[*]reinstalling the Numix Light theme
[/LIST]

None of those worked, and the themes continue to look black.

What can I do?
Would completely removing gnome-desktop, and unity-desktop, and reinstalling the latest, provide a solution to this? (I've tried this already, but stating it just in case I did sth wrong).


[B]EDIT:
1. Add login screen pictures
[/B]Looks like this even with the default Radiance theme
[img]http://i.imgur.com/ty8OuHL.jpg[/img]
[img]http://i.imgur.com/XXWqgDu.jpg[/img]
[img]http://i.imgur.com/NX6dB7q.jpg[/img]

---

### Post by ajgreeny on 2015-05-22
The problem is that gnome-desktop is just a meta-package that is a list of real packages to install; removing the gnome-desktop will not remove any of that list, only the meta-package list itself, so you will need to find out what all the others were.

If you installed using synaptic you can go to File->History from the menu and search for gnome-desktop and you will see everything else that was installed at the same time and using that list, remove them all.
Software-centre has a History icon in the toolbar which will give you the same info and allow you to search for gnome-desktop, and will again list all packages installed at that time.
If you used the terminal and apt-get you can look for the date by using command ```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log | grep gnome-desktop
```which will give you lines from those log files and show the date you installed gnome-desktop.  You can then amend the command's final grep term to use the date (just date, not time as well) instead of gnome-desktop, and you will then see listed all the packages that were installed on that date.

---

### Post by chrisasl92 on 2015-05-22
Great, thank you for the helpful terminal cmd, this was what I needed, and this is its output:
```

/var/log/dpkg.log:2015-05-22 11:43:21 install ubuntu-gnome-desktop:amd64 <none> 0.32
/var/log/dpkg.log:2015-05-22 13:24:52 install gnome-desktop3-data:all <none> 3.8.4-0ubuntu3.1
/var/log/dpkg.log:2015-05-22 13:24:53 install libgnome-desktop-3-7:amd64 <none> 3.8.4-0ubuntu3.1

```

The first one, was already uninstalled.
Hastily then I removed the 2nd one, which in its turned removed this packages as well:
```

cheese* eog* gnome-desktop3-data* gnome-font-viewer* gnome-screensaver*  
gnome-session-bin* indicator-bluetooth* indicator-keyboard*
libgnome-desktop-3-7* nautilus* nautilus-sendto* nautilus-share*
ubuntu-desktop* ubuntu-session* unity* unity-control-center*
unity-control-center-signon* unity-greeter* unity-settings-daemon*
unity-tweak-tool* webaccounts-extension-common* xul-ext-webaccounts*

```
I stopped there, cause I think some of these need to be reinstalled, like nautilus, and ubuntu-desktop along with unity*. Should I proceed with installing them?

Also, should I remove the latest one?

---

### Post by ajgreeny on 2015-05-22
Now try code ```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log | grep 2015-05-22 11:
``` to narrow down the timing on that day when you installed the ubuntu-gnome-desktop package.

It is always worth running the apt-get remove commands with the -s option (simulate) first to check what else will be removed, but that may now be too late, however you can always get back those that were removed with ```
sudo apt-get install ubuntu-desktop
``` if necessary.

I have just checked on my Virtual install of ubuntu to get a full list of all packages installed with the ubuntu-gnome-desktop package and I have attached it as a txt file; I hope it may be of some help and allow you to remove some, at least, of the possible 131 packages.

---

### Post by chrisasl92 on 2015-05-22
Ok, so I see [this list of packages]("http://pastebin.com/D0NvXhaM") (narrowed down to "11:4"). How should I proceed now? 
Should I uninstall all the gnome* related ones?

---

### Post by ajgreeny on 2015-05-22
You could try removing the packages you can see are obviously related to the new DE one by one, but ensuring that you do not also remove packages that you feel you need to keep.  My list of those is below.

gnome-shell
gnome-online-accounts
gnome-online-miners
gnome-icon-theme-full
gir1.2-gnomedesktop-3.0
gnome-shell-extensions
gnome-icon-theme-extras
gnome-backgrounds
gnome-shell-common
gnome-themes-standard-data
ubuntu-gnome-wallpapers-trusty
ubuntu-gnome-default-settings
plymouth-theme-ubuntu-gnome-logo
gnome-tweak-tool
gnome-sushi
gnome-documents
gnome-color-manager
ubuntu-gnome-wallpapers
plymouth-theme-ubuntu-gnome-text
ubuntu-gnome-desktop
gnome-themes-standard

I more often than not use synaptic for package management, never the software-centre, so I can only speak for synaptic or terminal use.  Synaptic will warn you with a list of packages that are to be removed as well as the chosen one so you can back out if you need to.  Terminal commands will also warn you and ask for a "y" or "n" so again giving you a chance to say "n" or No.

It is possible, in view of your main problem, that you can look for any theme packages that were installed and remove only them; perhaps that will put your colours back to normal.

Other than that, I'm afraid I can't think of other ways.

---

### Post by chrisasl92 on 2015-05-24
Thank you for your help, I have now uninstalled these packages (there were some left) and rebooted.

I had the [Orchis GTK Theme]("http://mokaproject.com/orchis-gtk-theme/") which as you see it's mainly grey. I've purged and installed it and applied it to face a black interface again. :( 
In the link above, you can see how it should look, and here you can see how it looks at my PC:
1. Nautilus
[IMG]http://i.imgur.com/z64UgQ4.png[/IMG]
2. Gedit
[IMG]http://i.imgur.com/0V00IgF.png[/IMG]

I am really confused on how to proceed.

---

### Post by Copper Bezel on 2015-05-24
Hmm. That's definitely Orchis's Dark theme. Under Gnome, if you have "Global Dark Theme" enabled, then all applications (including gedit) would look like that, instead of it being restricted to the apps that request the dark theme (like Image Viewer and Totem.) Under Unity, it shouldn't be having an effect at all. And you've even tried other themes that don't *have *a dark theme counterpart. 

Best I can say at this stage is that this should be a configuration issue, and it's probably in shared config areas like dconf as opposed to config for software you specifically installed with Gnome Shell. Getting rid of the packages probably won't fix the problem, because it's not the software that's broken. 

Next step is simply to sign into your computer using the Guest account and see what you see. I'm betting it won't have any kind of forced dark theme.

---

### Post by chrisasl92 on 2015-05-24
I've added screenshot of the login screen at the 1st post, in a hope that they might help sb recognize the problem.


Hmm, just used the dbconf editor to look through the settings and the only possibly related thing I could was this [com > unity > unity-greeter]
[img]http://i.imgur.com/DwOXLvQ.png[/img]

**Coppel Bezel, you were right! **Changed to the guest account and switched to Orchis theme, and it looked as it should! 
So, now, where can I look for the troublemaking configs?

---

### Post by Copper Bezel on 2015-05-25
This is strange - I'd think anything related to this *should *be in dconf - but do you have a file at ~/.config/gtk-3.0/settings.ini?

---

### Post by chrisasl92 on 2015-05-26
[B]That was it!

[/B]The contents of this file were:
> [Settings]
gtk-application-prefer-dark-theme=1

Changed it to "=0" and it works just fine! Thank you so much for your help, Copper Bezel!

---

### Post by Copper Bezel on 2015-05-27
No problem! Just be sure to mark the thread Solved. = D

---

