---
title: "GTK+ Themes/Apps Help"
date: 2005-01-27
forum: Desktop Environments
---

### Post by watchitman on 2005-01-27
I've installed a few GTK+ apps including XMMS. I have also installed several GTK+ themes as well as the old switch app. The problem is, I want to change the font in the GTK+ apps so it's smaller and fits in with the rest of my desktop but switch doesn't change it. It shows up in the switch preview window and I checked my .gtkrc file, it is writing the font changes to the file but the same old, giant-sized default font comes up in XMMS and other GTK+ apps. Anyone have any idea what the problem may be and how I can fix it?

P.S.: Please don't recommend GTK2 "alternatives" like Beep Media Player - I am aware of them and that wouldn't be answering my question.

---

### Post by watchitman on 2005-02-01
*bump*

---

### Post by valadil on 2005-02-01
There's a way to change GTK themes with switch via the commandline.  There might be a way to change fonts too.  man switch ought to tell you what that command would be and if it's possible to change fonts with it.  If it can change fonts you can put it in your .xinitrc, .xsession, or session manager.  If you don't know about .xinitrc or .xsession I recommend doing it through the session manager.  gnome should have an option for starting programs when you start gnome.

---

### Post by watchitman on 2005-02-13
I'm aware of switch, I already mentioned it in my original post. I've read man switch several times.

Anybody else have any ideas?

---

### Post by watchitman on 2005-02-26
*bump*

---

### Post by watchitman on 2005-03-01
*bump*

No one knows anything about GTK 1?

---

### Post by Ironi on 2005-03-01
It's been a while, but I'll try to figure it out later on... that is, if I can get GNOME to start (it didn't seem to want to a few days ago).

---

### Post by Ironi on 2005-03-01
Here's what I did. It worked for me; YMMV.

```

cd "$HOME"
rm -f .gtkrc
ln -s .gtkrc-1.2-gnome2 .gtkrc

```

Now you *should* be able to use gtk-theme-switch to change the GTK1 theme and font. The fonts look rather ugly though, so I would strongly recommend finding GTK2/KDE3 replacements for your GTK1 apps.

---

### Post by watchitman on 2005-03-15
.gtkrc-1.2-gnome2 is already in my home directory.

---

### Post by watchitman on 2005-03-19
Btw, there are still many GTK+ apps that have not been ported over to GTK 2.

---

### Post by Dromio on 2005-03-19
[QUOTE=watchitman]Btw, there are still many GTK+ apps that have not been ported over to GTK 2.[/QUOTE]
 Maybe [this](http://mail.gnome.org/archives/garnome-list/2002-November/msg00103.html) will help?

---

### Post by ozorba on 2005-03-20
Here is another problem.

I use ubuntu 5.04 preview. Everything installed well.

I selected Networking from the menu to set the network configuration in GNOME 2.10. I lost my Menu and all desktop somehow... I then tried to change the gtk theme using gtk-theme-swicth under Kubuntu. When I select the font I get

Gtk-CRITICAL **: file gtkentry.c: line 440 (gtk_entry_set_text): assertion `text != NULL' failed.

error and no fonts appear. Any ideas to change the font used by OpenOffice.org and Firefox in Kubuntu?

---

