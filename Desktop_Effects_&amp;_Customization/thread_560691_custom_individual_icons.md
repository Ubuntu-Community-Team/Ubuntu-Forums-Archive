---
title: "custom individual icons?"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by mailbox on 2007-09-26
I have a couple movies in VOB format,  and I'd like to have a custom icon for each individual one, like so:

[http://i69.photobucket.com/albums/i72/dissonance_ms/moviefolder.jpg](http://i69.photobucket.com/albums/i72/dissonance_ms/moviefolder.jpg)

i'm using xfce, so going into properties and clicking on the icon there doesn't do anything.
is there any way to do this at all, or am i dreaming?

---

### Post by mailbox on 2007-09-26
bump

---

### Post by mailbox on 2007-09-27
bump

---

### Post by mailbox on 2007-09-29
bump

---

### Post by Rupertronco on 2007-09-29
What file manager are you using? I forget which comes by defualt in xfce.

---

### Post by mailbox on 2007-09-30
> **Rupertronco said:**
> What file manager are you using? I forget which comes by defualt in xfce.Thunar.

---

### Post by violagirl23 on 2008-02-19
bump

I'm having the exact same problem, I have a bunch of shell scripts to open folders with pcmanfm since I dislike Thunar (so like the Home script says pcmanfm /home/violagirl23), but since to me Xfce manages the Desktop better I am still having it manage the desktop.  So I want to make each icon look like a folder icon, even though they are really shell scripts, but it is just these particular shell scripts, not ALL shell scripts.  IS there any way to edit icons individually in Thunar?  It sure would make things easier!

---

### Post by PCMan on 2008-02-19
> **violagirl23 said:**
> bump

I'm having the exact same problem, I have a bunch of shell scripts to open folders with pcmanfm since I dislike Thunar (so like the Home script says pcmanfm /home/violagirl23), but since to me Xfce manages the Desktop better I am still having it manage the desktop.  So I want to make each icon look like a folder icon, even though they are really shell scripts, but it is just these particular shell scripts, not ALL shell scripts.  IS there any way to edit icons individually in Thunar?  It sure would make things easier!

Use *.desktop files for this instead.
You can see the *.desktop files in /usr/share/applications to know the format.
Use this you can get customized icons and descriptions.
That's what it's designed for.

---

### Post by violagirl23 on 2008-02-21
Can one not use absolute path names?  I tried this:

/usr/share/applications/Home.desktop:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Home
Exec=/home/violagirl23/Desktop/Home
Icon=/usr/share/icons/Rodent/scalable/filesystems/gnome-fs-home.svg
Terminal=false
```
to no avail. Changing the Icon= line to Icon=gnome-fs-home.svg also did not work. :confused:

Oh no wait, I see, it put it into the main menu for programs with that icon.... but how would I use .desktop files just to display this icon when viewing the shell script in a folder?

---

### Post by PCMan on 2008-02-22
> **violagirl23 said:**
> Can one not use absolute path names?  I tried this:

/usr/share/applications/Home.desktop:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Home
Exec=/home/violagirl23/Desktop/Home
Icon=/usr/share/icons/Rodent/scalable/filesystems/gnome-fs-home.svg
Terminal=false
```
to no avail. Changing the Icon= line to Icon=gnome-fs-home.svg also did not work. :confused:

Oh no wait, I see, it put it into the main menu for programs with that icon.... but how would I use .desktop files just to display this icon when viewing the shell script in a folder?

Here:

<ANY NAME YOU LIKE>.desktop

```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=<ANY NAME YOU LIKE>
Exec=<YOUR SHELL SCRIPT>  <-- This should be a full path unless you put the script under $PATH
Icon=gnome-fs-directory
Terminal=false
```

Put this on your desktop, and you'll get a folder icon with the name you like which executes your shell script when double clicked.

Cheers!

---

### Post by violagirl23 on 2008-02-22
Aha! It all makes sense now! I think part of me just wasn't full grasping the concept of a .desktop file. But thanks you to, now I do! Thanks a bunch! I'm definitely not forgetting how to do this one. :KS

---

