---
title: "Wallpaper turn blanck ond retur all icons to desktop"
date: 2011-11-16
forum: Desktop Environments
---

### Post by grusty on 2011-11-16
In my nev xubuntu 11.10, since clean installation, if i open Thunar, all works great, but if I open nautilus, all desktop turn black without background, all black and come to desktop all icons in desktop folder. I prefer my background/wallpaper and no icons.

What can I do?

---

### Post by Copper Bezel on 2011-11-17
Run it instead as nautilus --no-desktop. I can't find any way to set it permanently this way, other than possibly to edit /usr/share/applications/nautilus.desktop with --no-desktop at the end of the "exec" line (I haven't tried this - Gnome's my only installed DE at the moment.)

What's happening is that Nautilus is trying to draw the desktop wallpaper, because it performs this function in Gnome (although it shouldn't be doing this under Xubuntu and didn't before Gnome 3, and you should probably file a bug on it.)

---

### Post by grusty on 2011-11-17
Hi, thanks for answer.

I did that, i change the exec line as you say, unfortonoully it didn't work, still at open nautilus, the wallpaper dissaper and all background turn to black, and the desktop icons appear at screen, i don't like have the icons files at desktop.

I have no idea about what is happend.

---

### Post by Copper Bezel on 2011-11-17
What happens if you run nautilus --no-desktop from a terminal?

---

### Post by grusty on 2011-11-17
Thanks by be here.

I run "nautilus --no-desktop" in guake and in a normal terminal, run perfect. The background don't change and don't come the icons at desktop.

Just, as normal, at run in terminal or guake i see this lines instructions, I know are not importants but, I show it.

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:19: Themeing engine 'adwaita' not found

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:620:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:626:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:632:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:639:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:645:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:651:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:657:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:663:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:669:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:675:27: Whitespace between 'url' and '(' is deprecated

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:716:32: Expected an identifier

(nautilus:23149): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:716:32: Expected an identifier

---

### Post by Copper Bezel on 2011-11-17
Okay, try this: run dconf-editor and navigate to org.gnome.desktop.background, and make sure draw-background and show-desktop-icons are unticked. If that works, file a bug on it, because Xubuntu should have already set those keys to disable the Gnome desktop when Nautilus is run (and it did indeed do so in prior versions, when the keys were in gconf instead of dconf.)

If it doesn't work, see _[here]("http://askubuntu.com/questions/69485/stop-nautilus-managing-my-desktop-xfce-desktop")_ about using Gnome Tweak Tool to do it - the drawback being installing most of Gnome to make it happen. Yuck.

---

### Post by scottbomb on 2011-11-17
Or you can just use Thunar (comes with Xubuntu). The only time I use Nautilus is with Dropbox.

---

### Post by Copper Bezel on 2011-11-17
In that case, if you're just using it to get public links, you can use something like this:

```
dropbox puburl %f | parcellite
```

as a Thunar custom action (appearance conditions set to everything but folders.) It'll ask Dropbox for the URL and copy it to the clipboard. Of course, you'll need parcellite installed, but it won't interfere with whatever clipboard manager you're using (I've used this both alongside Glippy and without a clipboard manager at all with no problems.)

---

### Post by grusty on 2011-11-17
Copper Bezel, it works!!

I didn't have dconf-editor, I just installed and unstick the background issue. It works. 

For install, i did in a terminal: 
sudo apt-get install dconf-tools
and its all.

Thanks for you help. Xubuntu and XFCE is great, I use this system in my netbook, but at last, in had there Kubuntu netbook with fat-settings, to get a system for minor procesors. At my desktop I had linux mint, but, with the future change to Gnome 3, my computer will be slow. So, I change to Xubuntu 11.10; great system, I really like it.

Thanks again for your patient and help. Now I only need to figurate how change to SOLVED.

---

### Post by grusty on 2011-11-17
Yes Scottbomb, Thunar is good and I use it, but I'm very familiarize with panel at F3 options in Nautilus, and by ow Thunar don't have it implementation. But, yes I use too. Thanks.

---

### Post by Copper Bezel on 2011-11-17
Very cool - I'm glad that worked for you. = )

[QUOTE=grusty]Now I only need to figurate how change to SOLVED.[/QUOTE]
You can mark the thread Solved from the Thread Tools link at the upper right.

---

