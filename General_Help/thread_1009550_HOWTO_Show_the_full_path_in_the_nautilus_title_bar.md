---
title: "HOWTO: Show the full path in the nautilus title bar."
date: 2008-12-12
forum: General Help
---

### Post by zuserm on 2008-12-12
Note: The following instructions work for Intrepid only.

Nautilus normally displays only the name of the current directory in the title bar. To get nautilus to display the full path, you need to update the source and rebuild it. Luckily this is easy to do in Ubuntu.

First you need to get the packages needed to build nautilus.
```

$ sudo apt-get install libx11-dev
$ sudo apt-get install libgtk2.0-dev
$ sudo apt-get install libeel2-dev
$ sudo apt-get install librsvg2-dev
$ sudo apt-get install intltool 

```

Next download the source. I suggest downloading it to /usr/src/nautilus/
```

$ mkdir /usr/src/nautilus/
$ cd /usr/src/nautilus
$ sudo apt-get source nautilus

```

Put the following in a file named nautilus-full-path-diff (in the same folder where you downloaded the source).
```

1197c1197,1198
<   char *full_title;
---
>   char *full_path;
>     char *full_title;
1206c1207,1212
<       full_title = g_strdup_printf (_("%s - File Browser"), slot->title);
---
>         full_path = g_file_get_path (slot->location);
>         if (full_path) {
>             full_title = g_strdup_printf (_("%s - File Browser"), full_path);
>         } else {
>             full_title = g_strdup_printf (_("%s - File Browser"), slot->title)
>         }
1211a1218
>         g_free (full_path);

```

Back up the file and then patch it.
```

$ cd nautilus-2.24.1/
$ sudo cp src/nautilus-navigation-window.c  src/nautilus-navigation-window.c.bak
$ sudo patch src/nautilus-navigation-window.c  ../nautilus-full-path-diff

```

Finally, rebuild nautilus and install the new version.
```

$ sudo ./configure
$ sudo make
$ sudo make install

```

Killing nautilus will cause it to automatically restart running the new version.
```

$ pkill nautilus

```

---

### Post by bluefrog on 2008-12-13
some would click on the button called "toggle between button and text-based location bar". 
takes one second to view the path.

---

### Post by juamez. on 2008-12-14
> **bluefrog said:**
> some would click on the button called "toggle between button and text-based location bar". 
takes one second to view the path.

That brings along the hassle to have to focus every window to click on the toggle button, which can be avoided by using the above workaround. When I, for example, have 3 directories with each of them identically named (one on my usb stick, one on my hard disk and one on the network) and all three of them are opened and visible in the task bar of gnome, I cannot know which one is which just by looking at the name of the button of the task bar, because it shows only the current directory. Cycling through every window which is hidden behind those buttons just to make sure your are in the right one is unacceptable.

---

### Post by juamez. on 2009-01-08
I feel reluctant to apply such a hack to Nautilus and recompiling it. I suppose you cannot safely "uninstall" the self compiled installation with a package manager like Synaptic, am I right? If so, how then could I uninstall the altered version of nautilus?

In human language: if this hack screwes up my nautilus, is it repairable in a safe and simple way?

---

### Post by Ergates on 2009-02-13
I'm having trouble installing the patch. As I'm not familiar with coding, can you advise me how to proceed? When I typed the command
sudo patch src/nautilus-navigation-window.c ../nautilus-full-path-diff

I got this response:

patching file src/nautilus-navigation-window.c
Hunk #1 FAILED at 1197.
Hunk #2 FAILED at 1207.
2 out of 3 hunks FAILED -- saving rejects to file src/nautilus-navigation-window.c.rej
jch@dv5z-Dec-08:/usr/src/nautilus/nautilus-2.24.1$ cd src
jch@dv5z-Dec-08:/usr/src/nautilus/nautilus-2.24.1/src$ cat nautilus-navigation-window.c.rej
***************
*** 1197
-   char *full_title;
--- 1197,1198 -----
+   char *full_path;
+     char *full_title;
***************
*** 1206
-       full_title = g_strdup_printf (_("%s - File Browser"), slot->title);
--- 1207,1212 -----
+         full_path = g_file_get_path (slot->location);
+         if (full_path) {
+             full_title = g_strdup_printf (_("%s - File Browser"), full_path);
+         } else {
+             full_title = g_strdup_printf (_("%s - File Browser"), slot->title)
+         }

---

### Post by dcstar on 2009-02-13
> **juamez. said:**
> That brings along the hassle to have to focus every window to click on the toggle button, which can be avoided by using the above workaround. When I, for example, have 3 directories with each of them identically named (one on my usb stick, one on my hard disk and one on the network) and all three of them are opened and visible in the task bar of gnome, I cannot know which one is which just by looking at the name of the button of the task bar, because it shows only the current directory. Cycling through every window which is hidden behind those buttons just to make sure your are in the right one is unacceptable.

So you set the following key using **gconf-editor** and **EVERY** Nautilus windows opens up in Location mode (without recompiling anything):

```
/apps/nautilus/preferences/always_use_location_entry
```

---

### Post by monguin61 on 2009-02-14
dcstar: The issue is that some people, myself included, have grown accustomed to using the task bar and application switcher as a significant source of information when editing many files or working with many applications. Maybe its picky, but theres absolutely no reason it shouldn't an option in preferences. Changing the display bar within the window is not helpful.

Ergates: I got the same problem, and I noticed that I have nautilus 2.22.5.1, not 2.24.1, so I wonder if that is the reason?

---

### Post by dcstar on 2009-02-14
> **monguin61 said:**
> dcstar: The issue is that some people, myself included, have grown accustomed to using the task bar and application switcher as a significant source of information when editing many files or working with many applications. Maybe its picky, but theres absolutely no reason it shouldn't an option in preferences. Changing the display bar within the window is not helpful.

If you want a new Nautilus feature (or in this case, an easier way to enable an **existing** feature), then contact the package maintainers and/or request the feature.

There is no need to write a patch for something that is already there and then have people stuffing around doing totally unnecessary package compilations.

---

### Post by monguin61 on 2009-02-16
I'm sorry, one of us must be misunderstanding, or we're using different versions. My always_use_location_entry is checked, and I do NOT see the full path in the title bar or the task bar. For me, this entry is described as follows:

If set to true, then Nautilus browser windows will always use a textual input entry for the **location toolbar**, instead of the pathbar.

So for me this option has no effect on the **titlebar**, nor is it intended to. Unless I am misunderstanding, or I have a different version, this is not a solution to the problem. If it is indeed already an existing feature, great, but I still don't know how to enable it - can someone explain further? If it is not an existing feature, then can we get back on topic and does anyone know why Ergates and I are getting this error?

To clarify, dcstar, you are proposing an improvement to bluefrog's suggested solution, and it is a good improvement to that suggestion. However, bluefrog's answer does NOT actually solve the problem at all.

---

### Post by dcstar on 2009-02-16
> **monguin61 said:**
> 
.......
To clarify, dcstar, you are proposing an improvement to bluefrog's suggested solution, and it is a good improvement to that suggestion. However, bluefrog's answer does NOT actually solve the problem at all.

Yes, I was responding to the person who didn't want to go to every window to then select the toggle for the location bar - the setting I found does nothing to the Title bar.

---

### Post by monguin61 on 2009-03-21
zuserm: I finally got around to trying out your patch. I made the changes in the .c file, no problem, but I don't have the necessary libraries to compile it. When I try ./configure, it checks for a bunch of things and eventually errors out, seems like at this line:
```

checking for ALL... configure: error: Package requirements (
	glib-2.0		>= 2.19.0
	gnome-desktop-2.0	>= 2.25.5
	gthread-2.0
	gio-unix-2.0
	gio-2.0
	pango			>= 1.1.2
	gtk+-2.0		>= 2.13.0
	libxml-2.0		>= 2.4.7
	gail			>= 0.16
	unique-1.0
	dbus-glib-1
) were not met:

Requested 'glib-2.0 >= 2.19.0' but version of GLib is 2.16.6
Requested 'gnome-desktop-2.0 >= 2.25.5' but version of gnome-desktop-2.0 is 2.22.3
Requested 'gtk+-2.0 >= 2.13.0' but version of GTK+ is 2.12.9
No package 'unique-1.0' found


```

And none of these packages seem to be available through apt-get. Can you give me some pointers as to how I might compile this?

Thanks

---

### Post by Duranxl on 2009-03-21
huh? the full path is in the address-bar already??

---

### Post by monguin61 on 2009-03-21
> huh? the full path is in the address-bar already??

The address bar is not the same thing as the title bar:

> **bluefrog said:**
> some would click on the button called "toggle between button and text-based location bar". 
takes one second to view the path.

> **juamez. said:**
> That brings along the hassle to have to focus every window to click on the toggle button, which can be avoided by using the above workaround. When I, for example, have 3 directories with each of them identically named (one on my usb stick, one on my hard disk and one on the network) and all three of them are opened and visible in the task bar of gnome, I cannot know which one is which just by looking at the name of the button of the task bar, because it shows only the current directory. Cycling through every window which is hidden behind those buttons just to make sure your are in the right one is unacceptable.

The problem is very simple. I want the full path to display in the TITLE bar, which is not the same as the ADDRESS bar. Evidently, zuserm has figured out how to make a simple patch for one file in the nautilus source that does this. I am asking him (or anyone else who knows) for assistance on getting that to work.

I'm sorry that other people aren't as picky about this particular issue as I am, but isn't that the point of these forums? I want linux to do something that it does not currently do. I might be the only person in the world that wants it, and maybe that makes me crazy. But I want it, and the fix should be simple. so what is the problem?

---

### Post by dcstar on 2009-03-21
> **monguin61 said:**
> .........
The problem is very simple. I want the full path to display in the TITLE bar, which is not the same as the ADDRESS bar. Evidently, zuserm has figured out how to make a simple patch for one file in the nautilus source that does this. I am asking him (or anyone else who knows) for assistance on getting that to work.

I'm sorry that other people aren't as picky about this particular issue as I am, **but isn't that the point of these forums**? I want linux to do something that it does not currently do. I might be the only person in the world that wants it, and maybe that makes me crazy. But I want it, and the fix should be simple. so what is the problem?

No, these forums are **not** a place to complain about the features of applications that this particular distro uses, these forums are to assist the users of Ubuntu to either get things working or find out how to use their systems.

Individual applications all have their own development forums, if you want new features you use those.

---

### Post by mc4man on 2009-03-22
I'm assuming your talking about what's in screenshot?

Just use the repo source and the build-deps are easily satisfied (also i'd suggest building packages vs. a make install

@ Ergates -  you need to manually edit the patch in.

I forgot that I'd disabled intrepid-updates so built from the intrepid source (2.24.1-0ubuntu1, instead of 2.24.1-0ubuntu2

Will try the updated source tomorrow and also ck. if there are any unintended issues...

Edit: no problem with 2.24.1-0ubuntu2

---

### Post by monguin61 on 2009-03-22
mc4man: Sorry, I know basically nothing about what I'm trying to do. Can you elaborate on "just use the repo source" and "building packages vs a make install" ? I tried downloading nautilus source from here: [https://launchpad.net/ubuntu/+source/nautilus/1:2.24.1-0ubuntu2](https://launchpad.net/ubuntu/+source/nautilus/1:2.24.1-0ubuntu2), because it matched your filename. Using that, I still got this:

Requested 'eel-2.0 >= 2.24.0' but version of eel is 2.22.2
Requested 'glib-2.0 >= 2.17.5' but version of GLib is 2.16.6
Requested 'gtk+-2.0 >= 2.13.0' but version of GTK+ is 2.12.9

I tried to find newer source for gtk, and every package I tried to install required some other library (gtk, gtk dev, cairo, libxcb-render-util). I finally got libxcb-render-util and then the gdebi "package installer" (which I've never seen or used before) told me the "dependency is not satisfiable". I can't help but feel like I'm missing something very simple here.



dcstar: I'm not here to complain about Nautilus. I just have a few questions about how to acquire libraries and compile source in linux. I'm a new linux user, I've never compiled application source before, I don't really know what I'm doing. The best result on google for my problem is this thread, which presents a solution that seems complete, but doesn't work for me for some reason. I'm just hoping I can get some assistance learning how to fix these dependency problems, and it makes more sense to start with this thread, where somebody has already tackled my problem, rather than trying to start from scratch.

---

### Post by mc4man on 2009-03-22
@monguin61
Noting that this is for a 8.10 install run this in a terminal, should pick up your dep's (also make sure your updated overall to current intrepid-updates versions in update manager

Also install the package fakeroot

```
sudo apt-get build-dep nautilus
```

Then go here for the source, diff, and dsc (you probably don't need the dsc for this use

[http://packages.ubuntu.com/pt-br/intrepid-updates/nautilus](http://packages.ubuntu.com/pt-br/intrepid-updates/nautilus)

Then you'd simply extract the source, apply the diff, edit your nautilus-navigation-window.c and build off of the /debian/rules with any of several build commands

For help with building you may want to post here
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

Here's basically how I did it (corrections welcome

Made a dir. in home named nautilus2, extracted the source in it and placed the nautilus_2.24.1-0ubuntu2.diff.gz inside the *nautilus2 folder* (not extracted, not inside the nautilus_2.24.1 folder

Cd'ed to nautilus2/nautilus-2.24.1 and ran 
```
zcat ~/nautilus2/nautilus_2.24.1-0ubuntu2.diff.gz  | patch -p1


```
To make clear, at this prompt
> doug@doug-desktop:~/nautilus2/nautilus-2.24.1$ zcat ~/nautilus2/nautilus_2.24.1-0ubuntu2.diff.gz  | patch -p1

Then
```
chmod +x ./debian/rules

```
Then edited the scr file for the patch and built
```
dpkg-buildpackage -rfakeroot -b -uc
```

or
```
fakeroot debian/rules binary
```

That will build 5 packages, you only need the nautilus one (nautilus_2.24.1-0ubuntu2_i386.deb

The advantage here is it installs as the same ver. as the current ubuntu intrepid-updates package, to revert back simply go to synaptic and reinstall nautilus.

The disadvantage is that any update to nautilus, if applied, will obviously not have the patch. (either don't update or build again, only takes 5 min. or so, patch should be good for any minor update to nautilus

screen shows what you should end up with, only the nautilus deb needs to be installed

---

### Post by juamez. on 2009-06-17
Does compiling the gnome-taskbar myself and using that altered version instead the default one erase the application launchers and applets I have on my current gnome-taskbar? Will I lose my current configuration? Will the new gnome-taskbar be blank or will it have everyhing I ever put on it?

---

### Post by mc4man on 2009-06-17
> Does compiling the gnome-taskbar myself and using that altered version instead the default one erase the application launchers and applets I have on my current gnome-taskbar? Will I lose my current configuration? Will the new gnome-taskbar be blank or will it have everyhing I ever put on it?

This really has nothing to do with the 'taskbar', I'd refer you back to the screenshot in post #15.
It's only enabling the full path in the "title bar", and when a window(s) are minimized to lower panel.

It's usefullness is limited to certain senarios but I may say I've gotten to like it.

Building a patched nautilus doesn't alter or affect anything else, nor is anything 'lost'

---

### Post by juamez. on 2009-06-17
> **mc4man said:**
> This really has nothing to do with the 'taskbar', I'd refer you back to the screenshot in post #15.
It's only enabling the full path in the "title bar", and when a window(s) are minimized to lower panel.

It's usefullness is limited to certain senarios but I may say I've gotten to like it.

Building a patched nautilus doesn't alter or affect anything else, nor is anything 'lost'

WOW, I'm sorry, I'm posting in the wrong thread here, I was confused because of the need to compile this, which is a similar approach to the problem I just confused this with. I was actually talking about the need to recompile the gnome-taskbar to be able to have more than 5 bookmarks or removable drives without the menu cascading - which is also something VERY stupid: that threshold number is hardcoded, seriously, HARDCODED! Why should I recompile something to change something as simple as that? Gnome sucks, from time to time.

---

### Post by mc4man on 2009-06-17
> was actually talking about the need to recompile the gnome-taskbar to be able to have more than 5 bookmarks or removable drives without the menu cascading

Yeah that's something different, but also could be useful. Went ahead and did on my hardy desktop install where I have 10 partitions plus whatever else may be connected.

I don't see it changing anything but the places menu so you should be ok.

I say should because I did slightly differently, more like as for nautilus except I used debuild.

6 packages where built, the only one to be 're-installed' was the gnome-panel one.

I prefer this way, then it's just a re-install of same package operation (only difference is this one is patched

Used the define to patch
for hardy it was line 61
```
#define NAMES_DIR               "/apps/nautilus/desktop"
#define HOME_NAME_KEY           "/apps/nautilus/desktop/home_icon_name"
#define COMPUTER_NAME_KEY       "/apps/nautilus/desktop/computer_icon_name"
#define MAX_ITEMS_OR_SUBMENU    [COLOR="Blue"]20[/COLOR]
```

---

### Post by juamez. on 2009-06-18
Thank you for that information!

---

### Post by tulcak on 2010-09-02
FOR THE LOVE OF GOD!! WHY DO PEOPLE THINK THEY HAVE TO DO A LOT OF COMMAND LINE BULLCRAP?

HERE'S THE DAMN ANSWER:  [http://www.liberiangeek.net/2010/06/linux-beginner-how-to-display-the-full-folder-path-in-the-title-bar-with-nautilus/](http://www.liberiangeek.net/2010/06/linux-beginner-how-to-display-the-full-folder-path-in-the-title-bar-with-nautilus/)

What a freakin moron...

---

### Post by monguin61 on 2010-09-03
> **tulcak said:**
> FOR THE LOVE OF GOD!! WHY DO PEOPLE THINK THEY HAVE TO DO A LOT OF COMMAND LINE BULLCRAP?

HERE'S THE DAMN ANSWER:  [http://www.liberiangeek.net/2010/06/linux-beginner-how-to-display-the-full-folder-path-in-the-title-bar-with-nautilus/](http://www.liberiangeek.net/2010/06/linux-beginner-how-to-display-the-full-folder-path-in-the-title-bar-with-nautilus/)

What a freakin moron...


Although this is no longer an issue for me personally, I shall repeat myself since twice is apparently not enough for some people. This time I will use more text formatting so the explanation is easier to follow:

The problem is very simple. I want the full path to display in the **_*[SIZE="6"]TITLE[/SIZE]*_** bar, which is not the same as the **_*[SIZE="6"]ADDRESS[/SIZE]*_** bar.

Thanks for your helpful suggestions and constructive criticism, though!

---

### Post by carlo.pellegrini on 2010-12-28
Well, I found a way to show the  current uri on the title bar WITHOUT recompilation, using a python extension.
It's a bit of a hack,  but works for me using:
nautilus 1:2.32.0-0ubuntu1.1
python-nautilus   0.6.1-1

Simply unzip the attached file in ~/.nautilus/python-extensions and restart nautilus.

---

### Post by ragavendra_bn on 2011-01-01
Do CTRL + L

---

### Post by carlo.pellegrini on 2011-01-03
As they said in a previous post...
The problem is very simple. I want the full path to display in the **_*[SIZE=6]TITLE[/SIZE]*_** bar, which is not the same as the **_*[SIZE=6]ADDRESS[/SIZE]*_** bar.

---

### Post by seawolf167 on 2011-01-03
For other versions (10.04, 10.10) in case they stumble here looking for a solution, to show the full path in the **address bar **just do:

[Alt-F2] -> gconf-editor -> apps -> nautilus -> preferences -> check the box for display full path

---

### Post by carlo.pellegrini on 2011-01-03
As they said in a previous post...
The problem is very simple. I wanted the full path to display in the **_*[SIZE=6]TITLE[/SIZE]*_** bar, which is not the same as the **_*[SIZE=6]ADDRESS[/SIZE]*_** bar. It arises from the necessity to identify my nautilus windows directly by the window TITLE displayed in the window list.
The address bar preference I do know.  It's among the first customizations I apply to a new installation.

---

### Post by richardbrucebaxter on 2011-05-06
I previously listed this deficiency in customisation here;

[http://live.gnome.org/Nautilus/Ideas/Elaborate/Power%20users]("http://live.gnome.org/Nautilus/Ideas/Elaborate/Power%20users")

This is a critical issue with Nautilus, along with the length of the location bar (see [http://ubuntuforums.org/showthread.php?t=187795](http://ubuntuforums.org/showthread.php?t=187795)). For people who have been using file managers for over 15 years (since Windows 95 / 98, Linux file browsers appear always deficient for one or more reasons. Terminals are OK for many operations, but they are not always the most efficient mechanism for browsing files on Linux (or any operating system). The inability of the Linux development community to recognise this is a serious failure on their behalf and adds to the list of obstacles in corporate uptake.

I have developed a number of File Manager revisions based on principles of traditional file management (Thunar and PCman - eg [http://bugzilla.xfce.org/show_bug.cgi?id=6412](http://bugzilla.xfce.org/show_bug.cgi?id=6412)), and may be forced to develop one for Nautilus also. 

Alternatively, it would be better if the Linux development community could adopt a policy of customisablity over constraint. Unfortunately, forcing UI constraints has become popularised with Adobe (eg navigation panel), Microsoft (eg IE7 search panel), and sadly even Google (eg sidebar, fade-in [we have fixed that], preview images, sample images, enormous search box, auto-complete), in recent years.

---

