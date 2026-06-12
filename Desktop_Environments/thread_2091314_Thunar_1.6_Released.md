---
title: "Thunar 1.6 Released"
date: 2012-12-04
forum: Desktop Environments
---

### Post by Toz on 2012-12-04
As per [http://forum.xfce.org/viewtopic.php?pid=28190#p28190]("http://forum.xfce.org/viewtopic.php?pid=28190#p28190"), **Thunar 1.6 has been released**.
> 

Yesterday a new stable version of Thunar was released. It features a whole bunch of stuff that's been missing for most users:

- Tabs.
- Multiple file properties.
- A lot of speed improvements.
- New shortcuts sidepane. Including support for remote bookmarks and more volume/mount types.
- Permanent delete option in the context menu.
- Ctrl+right-click will show directory context menu in details view.
- Better file progress dialog.
- Select problems have been fixed.
- Interface cleanups.
- Various thumbnailing improvements.
- Settings stored in Xfconf.
- Fix sorting of non ascii characters.
- Tons of bug fixes.
- Gtk 2.24 and Glib 2.30 (required for some changes).

You can download the required exo 0.10 release and thunar 1.6.0 here: [http://archive.xfce.org/src/xfce](http://archive.xfce.org/src/xfce)


Some interesting enhancements, especially regarding remote bookmarks. Currently, you'll have to build from source, but hopefully it will available via a PPA soon.

---

### Post by SantaFe on 2012-12-04
> **Toz said:**
> As per [http://forum.xfce.org/viewtopic.php?pid=28190#p28190]("http://forum.xfce.org/viewtopic.php?pid=28190#p28190"), **Thunar 1.6 has been released**.


Some interesting enhancements, especially regarding remote bookmarks. Currently, you'll have to build from source, but hopefully it will available via a PPA soon.

Sure HOPE so, right now I can't right click anything. Thunar just closes without error message. Otherwise it works like it should, if I don't want to move, copy, delete, rename files...... ;)

Anyone know how to revert to Thunar 1.4.0, which Synaptic Package manager still shows as installed.  Thought about completely removing Thunar in Synaptic & reinstalling it, but when I select that option, it wants to remove other things like Xfce4 & Xubuntu-Desktop for example.


Forgot to say I'm running Xubuntu 12.10 & Xfce 4.10.  And I did see these lines in .xsession-errors.

```


(thunar:9722): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(thunar:9747): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

```

If that helps. ;)

---

### Post by LewisTM on 2012-12-04
See this Webupd8 [post]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html") for the 1.6 PPA.
If you already had the 1.5.1 development PPA installed, it's the same (and the same post, they just edited the version number...). They just pushed 1.5.1 -> 1.5.3 -> 1.6.0

Thunar 1.6 is awesome. The only bug I found (and reported) is that [FONT="Courier New"]sudo thunar[/FONT] freezes. Can anyone confirm that?

Cheers!

---

### Post by Toz on 2012-12-04
> **LewisTM said:**
> The only bug I found (and reported) is that [FONT="Courier New"]sudo thunar[/FONT] freezes. Can anyone confirm that?

Works fine here, but I'm building from source. Does:
```
gksu thunar
```
...provide different results?

---

### Post by Toz on 2012-12-04
> **SantaFe said:**
> Sure HOPE so, right now I can't right click anything. Thunar just closes without error message. Otherwise it works like it should, if I don't want to move, copy, delete, rename files...... ;)

Anyone know how to revert to Thunar 1.4.0, which Synaptic Package manager still shows as installed.  Thought about completely removing Thunar in Synaptic & reinstalling it, but when I select that option, it wants to remove other things like Xfce4 & Xubuntu-Desktop for example.


Forgot to say I'm running Xubuntu 12.10 & Xfce 4.10.  And I did see these lines in .xsession-errors.

```


(thunar:9722): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(thunar:9747): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

```

If that helps. ;)

32-bit or 64-bit? If 64 bit, what do the following return?
```
ls -l /usr/lib/thunarx-2
ls -l /usr/lib/x86_64-linux-gnu/thunarx-2
```

---

### Post by SantaFe on 2012-12-04
> **LewisTM said:**
> See this Webupd8 [post]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html") for the 1.6 PPA.
If you already had the 1.5.1 development PPA installed, it's the same (and the same post, they just edited the version number...). They just pushed 1.5.1 -> 1.5.3 -> 1.6.0

Thunar 1.6 is awesome. The only bug I found (and reported) is that [FONT="Courier New"]sudo thunar[/FONT] freezes. Can anyone confirm that?

Cheers!
Thank you! :)  This worked! :D  Still wonder why the compiled Thunar didn't work right.  Go figure.

---

### Post by SantaFe on 2012-12-04
> **Toz said:**
> 32-bit or 64-bit? If 64 bit, what do the following return?
```
ls -l /usr/lib/thunarx-2
ls -l /usr/lib/x86_64-linux-gnu/thunarx-2
```
Just used the PPA LewisTM posted and it works now.  Of course I can't mark this thread solved because I didn't start it. :D

And for what it's worth, I tried gksu thunar in xterm, and I didn't notice Thunar 1.6.0 freezing. ;)

The O/S is 32 bit.  I know, but that's what I had installed when I started with Xubuntu 8.04, and have been upgrading to every new version since.  ;)

Anyhoo..... it's running now.  Funny, never had problems compiling other programs, like SpaceFM.  ;)

---

### Post by DukeOfMixture on 2012-12-04
Does Thunar support multiple panes?

Multiple tabs are OK but you have to switch between them.

I get three panes that I can view simultaneously and have different display properties for each with Xfe File Manager.

[IMG]http://roland65.free.fr/xfe/images/screenshot-s5.png[/IMG]

I'm asking because I want a light application, but i also want it to be handy.

With Xfe I can have one pane display hidden files if needed and the other pane without hidden files if not needed for "convenience".

I know that PCmanFM and Thunar are very popular. Why?

---

### Post by Toz on 2012-12-04
> **SantaFe said:**
> Still wonder why the compiled Thunar didn't work right.
I found that if you compile thunar over an existing packaged installed thunar, the thunarx libraries conflict and you need to make sure you are using the correct libraries. This thunarx library conflict caused the crash on right-click.

---

### Post by SantaFe on 2012-12-04
Ah.  Didn't know that.  ;)

---

### Post by LewisTM on 2012-12-05
I can confirm that on 4 different machines, all running 64-bit Xubuntu 12.10, Thunar 1.6 freezes when run as superuser. gksu makes no difference. Sometimes you don't see it right away, you have to click a few of folders. It only happens when the tree view is active.

Another small bug that I've seen is that the Send To context menu is broken for folders. It only displays 'Desktop (Create link)', no other target.

---

