---
title: "How to match window to customized firefox profile icon in Docky?"
date: 2011-06-30
forum: Desktop Environments
---

### Post by Dngrsone on 2011-06-30
I am running Ubuntu 10.04 desktop AMD-64 on an HP DV4-2000 laptop.

I have Docky running on the left side, desktop disabled and wallpapers for my four desktops.  I recently killed the bottom panel (yes, it's a poor-man's 11.04).

Those details, I don't think, will have any bearing on the problem at hand, but one never knows.

So, I have three different Firefox profiles I run-- the default, which has all the plugins, a stripped-down one which I use for my daily reading (I follow a number of sites using the Morning Coffee plugin), and another stripped one for my local WordPress install.

My problem is this-- I have created three separate launchers on my Desktop, one for each firefox profile.  They each have their own icons, and I have successfully imported them each into Docky.

By the way, if you have problems with getting a different icon to show in Docky, open up the launcher with a text editor such as gedit and make sure that *both* icon listings are pointing to the one you want to use.  Example:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/dngrs/Pictures/wordpress-icon-32.png
Name[en_US]=Dngrlog
Exec=firefox -no-remote -P WordPress
Name=Daily
Icon=/home/dngrs/Pictures/wordpress-icon-32.png
```

The first icon listing is what Docky uses, the second is what the Launcher file itself looks like.

Anyway, the problem-- When I click on the appropriate icon, I get an instance of Firefox under the correct profile.  However, Docky throws the window under the generic Firefox icon, so if I pull up the dock, there might be three instances of firefox running under the firefox icon and nothing under the icons of the other two profile launchers.

I want to be able to click on the Wordpress profile icon and get the Wordpress window that is already open (instead of getting a warning that Firefox is already running... I *know* that).

I found [this page](http://wiki.go-docky.com/index.php?title=How_to_Customize_Window_Matching) which tells me how to fix a Chrome problem of similar nature, however, when I try to use the command xprop I get nothing.  I left it running for fifteen minutes until I gave up and did a ^C to recover my terminal.

So, my problem, as I see it, is this-- I'm running Firefox in all three cases, which Docky correctly interprets.  This isn't a java implementation where I can point at the correct Java attribute.

So, is there any way I can tell Docky how to differentiate between different profiles?

---

### Post by Dngrsone on 2011-06-30
Okay, I figured out what I was doing wrong with xprop-- once I initiate xprop in terminal, I need to select the window in question with my mouse,

This helped me attach my Minecraft launcher to the actual program (so I didn't have two icons on the dock when running Minecraft).

Unfortunately, Firefox is Firefox, regardless of which profile I am using.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by Dngrsone on 2011-07-28
I found [this](http://superuser.com/questions/209771/how-do-i-use-chrome-linux-application-launchers-in-docky-alongside-regular-chro) answer for Chrome users, I just don't know how to use this information toward Firefox... [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by Dngrsone on 2011-07-28
Well, according to [this bug](https://bugzilla.mozilla.org/show_bug.cgi?id=496653) and [this one](https://bugzilla.mozilla.org/show_bug.cgi?id=494586), setting WM_CLASS through the command line is no longer available, no will it likely be.

However, I discovered that [Prism](http://prism.mozillalabs.com/), which is apparently a stripped-down firefox, is the perfect way to run my local WordPress installation.

That solves half of my problem, though I doubt it will work for my other profiles, dependent as they are on certain Firefox plugins...

---

### Post by shiraz dindar on 2011-10-29
Danger, did you ever figure this out? I'm in the same boat... I have two profiles, one for personal and one for work. I created a launcher for the second profile so i can at least have two different icons for *starting* the apps, but for switching, Docky treats them both as the same app as different windows under the first icon, so I have to use alt-tab instead of Docky.

---

### Post by Dngrsone on 2011-10-29
Unfortunately, no.  I've turned off Docky while troubleshooting some Update issues, but without the WM_CLASS I can't seem to find a solution.

Prism didn't work out for me, either.

---

