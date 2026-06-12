---
title: "Are you using Gnome 3 and would like to put icon on the Desktop. Do this."
date: 2011-05-18
forum: Desktop Environments
---

### Post by irv on 2011-05-18
[SIZE="3"]To show icons and be able to use right click on the desktop..

In a normal (non root) Terminal

 

```
gsettings set org.gnome.desktop.background draw-background true
gsettings set org.gnome.desktop.background show-desktop-icons true
```

And to reverse the process, replace true with false..[/SIZE]

I found this on the Internet @ [http://www.dnmouse.org/autoten/gnome-3-extra-tips/183-show-icons-show-on-desktop.html]("http://www.dnmouse.org/autoten/gnome-3-extra-tips/183-show-icons-show-on-desktop.html")

---

### Post by irv on 2011-05-18
Here is a couple of screen shots. One with the icons after running the commands.
[ATTACH]192538[/ATTACH]   [ATTACH]192539[/ATTACH]

---

### Post by wojox on 2011-05-18
I ran Gnome3 and the sHELL on Arch a few months back while it was still in testing. This was a good site if you don't already know [Customizing Gnome3 Shell]("http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html")

Pic's look good.

---

### Post by BigSilly on 2011-05-18
I just use the Tweak Advanced Settings tool. Go into the file manager options, and toggle the "Have the file manager handle the desktop" switch to on, and you're done. You don't have to go into gsettings.

---

### Post by irv on 2011-05-18
> **BigSilly said:**
> I just use the Tweak Advanced Settings tool. Go into the file manager options, and toggle the "Have the file manager handle the desktop" switch to on, and you're done. You don't have to go into gsettings.

I found that if I go into Unity then come back to Gnome 3 option quits working. I checked this setting in Tweak and it was set to on. I then tried to run the two commands again and nothing happen. (No change). I then logged off and back on again and everything worked again.

One other thing I find is the Alt +F2 key does not work in Gnome desktop. I am not sure if there is a place I can check this to see if something is off. Where does Gnome store and set keyboard short cuts?

---

