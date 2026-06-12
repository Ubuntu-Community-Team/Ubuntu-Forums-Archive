---
title: "How to uninstall the kde desktop? and some fonts question"
date: 2009-12-19
forum: Desktop Environments
---

### Post by frantzsong on 2009-12-19
i had installed the kde desktop, and my ubuntu is  9.10.  
&#25105;&#24050;&#32463;&#23433;&#35013;&#20102;KDE&#26700;&#38754;&#65292;&#25105;&#30340;Ubuntu&#31995;&#32479;&#29256;&#26412;&#26159;9.10

now my start logo is kubuntu,and soon it turn GNOME .
&#29616;&#22312;&#25105;&#30340;&#24320;&#26426;logo&#26159;KUBUNTU&#30340;&#65292;&#28982;&#21518;&#36805;&#36895;&#30340;&#21464;&#25104;gnome&#30340;&#30028;&#38754;

i wont uninstall the KDE desktop ,but i don't know how
&#25105;&#24819;&#21368;&#36733;KDE &#26700;&#38754;&#65292;&#25105;&#19981;&#30693;&#36947;&#24590;&#20040;&#21150;&#12290;


also have a question is about the fonts. i had use the Hiragino San GB as the system fonts,BUT there still some software fonts not use it,like Synaptic Package Manager.
&#25105;&#20173;&#28982;&#26377;&#19968;&#20010;&#38382;&#39064;&#26159;&#20851;&#20110;&#23383;&#20307;&#30340;&#12290;&#25105;&#24050;&#32463;&#20351;&#29992;Hiragino San GB&#20316;&#20026;&#25105;&#30340;&#31995;&#32479;&#20351;&#29992;&#30340;&#23383;&#20307;&#65292;&#20294;&#26159;&#20173;&#28982;&#26377;&#19968;&#20123;&#36719;&#20214;&#30340;&#23383;&#20307;&#19981;&#20351;&#29992;&#37027;&#20010;&#23383;&#20307;&#12290;&#27604;&#22914;&#26032;&#31435;&#24471;&#36719;&#20214;&#21253;&#31649;&#29702;&#22120;&#12290;

then gave you some Screenshot.

---

### Post by 3Miro on 2009-12-19
To uninstall kubuntu-desktop, go to Syneptic-Package-Manager and search for KDE, then all then tell it to uninstall all the selected packages (if it is green, click on it and select uninstall or purge).

For the system fonts, you changed the fonts so that all applications under your username would run with your fonts, however, Synapti runs as root (i.e. not you). You need to open Terminal (Applications -> Accessories -> Terminal) and then type
```
gksudo gnome-appearance-properties
```
Then you can change the fonts for Synaptic and all applications that run under root.

---

### Post by frantzsong on 2009-12-19
> **3Miro said:**
> To uninstall kubuntu-desktop, go to Syneptic-Package-Manager and search for KDE, then all then tell it to uninstall all the selected packages (if it is green, click on it and select uninstall or purge).

For the system fonts, you changed the fonts so that all applications under your username would run with your fonts, however, Synapti runs as root (i.e. not you). You need to open Terminal (Applications -> Accessories -> Terminal) and then type
```
gksudo gnome-appearance-properties
```Then you can change the fonts for Synaptic and all applications that run under root.
(gnome-appearance-properties:5880): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5881): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

i can open it and change it
but there is 2 failed 
why?

---

### Post by 3Miro on 2009-12-19
> **frantzsong said:**
> (gnome-appearance-properties:5880): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5881): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

i can open it and change it
but there is 2 failed 
why?

I don't know. It works for me and I don't know enough to figure out the errors.

You can try to reboot (restart) and then try the command again.

If this doesn't work, then try to copy paste the message in Google to see if someone knows what the problem is.

---

### Post by frantzsong on 2009-12-19
> **3Miro said:**
> I don't know. It works for me and I don't know enough to figure out the errors.
 
You can try to reboot (restart) and then try the command again.
 
If this doesn't work, then try to copy paste the message in Google to see if someone knows what the problem is.
 uh..
 
i uninstall all the kde software
 
and now i cant login into my desktop
 
there is black screen with little text like
 
ubuntu 9.10 song-desktop tty2
song-desktop login:
 
 
 
:(

---

