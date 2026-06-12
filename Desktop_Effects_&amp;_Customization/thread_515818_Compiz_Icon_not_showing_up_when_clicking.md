---
title: "Compiz Icon not showing up when clicking"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by SkippyIsForYou on 2007-08-02
When I run Compiz, it loads but the icon doesnt show up in the panel. So I go to 'Applications>System Tools>Compiz Fusion Icon' and I click that. Again, the icon doesn't show up.

Can anyone help me with this?

THANKS!

Btw, I LOVE Compiz. It's amazing...

---

### Post by atomkarinca on 2007-08-02
can you type 

compiz-tray-icon

in the terminal and copy-paste the output?

---

### Post by SkippyIsForYou on 2007-08-02
(compiz-tray-icon:6418): Wnck-WARNING **: Unhandled action type (nil)

(compiz-tray-icon:6418): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6418): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:6418): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6418): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by SkippyIsForYou on 2007-08-02
It repeats that first command about 10 times

---

### Post by atomkarinca on 2007-08-02
you can try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by SkippyIsForYou on 2007-08-02
Ok trying that now

---

### Post by SkippyIsForYou on 2007-08-02
Ok, is there a guide on how to use that?

I'm thoroughly confused using that command. 

 &#9474; No X server known for your video hardware                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; There is either no video hardware installed on this machine (e.g. serial  &#9474;  
 &#9474; console only), or the "discover" program was unable to determine which X  &#9474;  
 &#9474; server is appropriate for the video hardware.  This could be due to       &#9474;  
 &#9474; incomplete information in discover's hardware database, or because your   &#9474;  
 &#9474; video hardware is not supported by the available X servers.               &#9474;  
 &#9474;                                                              

So I choose ATI in the next window and it identifies the card as "Generic Video Card".
Its an ATI X1800XT.

---

### Post by SkippyIsForYou on 2007-08-02
Anybody?

---

### Post by zavaletaster on 2008-02-14
> **SkippyIsForYou said:**
> When I run Compiz, it loads but the icon doesnt show up in the panel. So I go to 'Applications>System Tools>Compiz Fusion Icon' and I click that. Again, the icon doesn't show up.

Can anyone help me with this?

THANKS!

Btw, I LOVE Compiz. It's amazing...

hey i had the same problem, try this:

right click to the panel bar > properties >

change the pixels to 26

---

### Post by oderus on 2008-04-17
Changing the panel bar to 26 helps but then other icons look too large and ugly. Is there a way to get it to work with the default 24 pixels?

---

