---
title: "Different Wallpapers"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by Ceemee on 2007-04-26
Is there a way in Fiesty to have different wallpapers on the different Desktop workspaces?

the default wallpaper switcher changes both to be the same.

---

### Post by raja on 2007-04-26
All workspaces have the same wallpaper in gnome. You can have different wallpapers in KDE.

---

### Post by doriard on 2007-04-26
Is there a way to get Gnome to support having wallpaper show up on each of dual monitors, instead of in the center -- half the wallpaper on each monitor.  What about Kubuntu (KDE), will it work on that desktop?

---

### Post by ubuntu27 on 2007-04-26
> **Ceemee said:**
> Is there a way in Fiesty to have different wallpapers on the different Desktop workspaces?

the default wallpaper switcher changes both to be the same.

You can put different wallpapers with [mybackground-properties]("http://www.gnomefiles.org/app.php/mybackground-properties")

Here: download the deb from: [http://www.gnomefiles.org/app.php/mybackground-properties](http://www.gnomefiles.org/app.php/mybackground-properties)

---

### Post by cogadh on 2007-04-27
That page only had a source tarball, is there a precompiled package somewhere?

---

### Post by ubuntu27 on 2007-04-27
> **cogadh said:**
> That page only had a source tarball, is there a precompiled package somewhere?

What?? But there was a Deb for Edgy and Feisty there when I posted 42 minutes ago!!?? What happened?

Well, it's no use crying now. You will have to compile it fro source.

Here, the guide:

[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by dracule on 2007-04-27
when i attempt to install i get this:Library requirements (gtk+-2.0 >= 2.3.0 gconf-2.0 libgnomeui-2.0 >= 2.2.0 bonobo-activation-2.0 libbonobo-2.0 libglade-2.0 libwnck-1.0) not met;

i have searched for these packages but they are installed

NVRM i had to install the dev files

now it installed ok, but how do i run the program?

---

### Post by orb9220 on 2007-04-27
There is a wallpaper plugin in beryl 0.3.0 svn which does this.
For Feisty
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html)
For Edgy
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

### Post by Scheater5 on 2007-04-27
I'm not familiar with this program, but if you have succesfully compiled and installed it, and if it is a stand-alone app, then you can simply enter
```
mybackground-properties
```
at a terminal.  If this works I'll help you create a button for it.

---

### Post by dracule on 2007-04-28
i already typed that in, but it doesnt launch a window or anything... so i have no idea how to actually change the wallpapers

---

### Post by Scheater5 on 2007-04-28
Then it must be an addition to another program.  Check under the usual Desktop menu (under the System tab) and see if anything has changed.

---

### Post by Rinzwind on 2007-04-28
It says in the installation file that mybackground-properties is a replacement for gnome-properties. But I haven't figured out what that means yet :P

---

### Post by Scheater5 on 2007-04-28
I've got nothing.  I had a similar problem when I installed the KDM Theme Manager.  Once I finally found the thing and installed it, I couldn't find what it had done.  I eventually found it under KControl.  Try browsing Gnome's menus.

---

### Post by ubuntu27 on 2007-04-28
> **dracule said:**
> i already typed that in, but it doesn't launch a window or anything... so i have no idea how to actually change the wallpapers

> **Rinzwind said:**
> It says in the installation file that mybackground-properties is a **replacement** for gnome-properties. But I haven't figured out what that means yet :P

Try right clicking on your descktop and select properties or change wallpapers... 
See if you have a option to add it to multiple desktops/work places


> **Scheater5 said:**
> I've got nothing.  I had a similar problem when I installed the KDM Theme Manager.  Once I finally found the thing and installed it, I couldn't find what it had done.  I eventually found it under KControl.  Try browsing Gnome's menus.



@Dracule: Install Debian Menu, it might be in there.
Debian Menu is a menu that shows ALL installed application in your computer.

```
sudo apt-get update
```
```
sudo apt-get install menu
```
```
sudo update-menus
```

Then you should see a new Menu called Debian, under Applications Menu. 
If it is not there, or if it is there but doesn't have anything in it.

Try:

```
sudo dpkg-reconfigure menu
```
```
sudo dpkg-reconfigure menu-xdg
```

Good Luck!

---

### Post by dracule on 2007-04-30
didnt help, surely someone must have used this

---

