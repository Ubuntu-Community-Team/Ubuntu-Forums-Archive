---
title: "[SOLVED] Mupen64 joystick axis problem (Wingman64 plugin)"
date: 2008-03-22
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2008-03-22
Anyone here tried using the Wingman64 controller plugin?
I'm using a very cheap Chinese joystick and am having axis problems in apps like ePSXe and Mupen64. For ePSXe, I switched to pSX which rocks and has awesome controller support. Mupen64, no such luck. The blight input plugin can't read from the joystick axes and here's the problems I'm having with the Wingman64 plugin:

I can get it to compile and everything but when I try to run it from mupen64, GTK throws out a ton of errors:

```
cojones@tipping-point:~/Games/mupen64-0.5$ ./mupen64 
Using calibration file `wingman_libjswconfig'.
Reading values from `/dev/input/js0'.
Joystick has 7 axis
Joystick has 12 buttons

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(mupen64:3800): Gtk-WARNING **: invalid cast from (NULL) pointer to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 433 (gtk_signal_lookup): assertion `gtk_type_is_a (object_type, GTK_TYPE_OBJECT)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: gtk_signal_connect_object(): could not find signal "clicked" in the `(null)' class ancestry

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 433 (gtk_signal_lookup): assertion `gtk_type_is_a (object_type, GTK_TYPE_OBJECT)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: gtk_signal_connect_object(): could not find signal "clicked" in the `(null)' class ancestry

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 433 (gtk_signal_lookup): assertion `gtk_type_is_a (object_type, GTK_TYPE_OBJECT)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: gtk_signal_connect_object(): could not find signal "clicked" in the `(null)' class ancestry

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 433 (gtk_signal_lookup): assertion `gtk_type_is_a (object_type, GTK_TYPE_OBJECT)' failed.

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: gtk_signal_connect_object(): could not find signal "clicked" in the `(null)' class ancestry

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-WARNING **: invalid cast from `(unknown)' to `(unknown)'

(mupen64:3800): Gtk-CRITICAL **: file gtksignal.c: line 725 (gtk_signal_connect): assertion `GTK_IS_OBJECT (object)' failed.

```

Any ideas or experience with this?

---

### Post by acoustibop on 2008-03-22
Since you have pSX running, cisforcojo, you must have libgtkglext1 installed: try installing the -dev package, as well.

---

### Post by cisforcojo on 2008-03-22
Unfortunately it doesn't do a thing. There are no red flags raise during either the configure or the make parts of the compile. Only once I load the plugin through Mupen64. I'm wondering if it's an inconsistency with libgtk? I believe the plugin was written in 2004. I saw some posts from the author from around that time. 
I would venture to say it's no more recent that at the soonest 2006. 

It's a little frustrating because jscalibrator and jstest work perfectly. I saw the post you added where jscalibrator can actually interfere with joystick operations (it was a post about nexuiz) so I removed it but that didn't work either.

---

### Post by cisforcojo on 2008-03-23
Bump! I can't even seem to find a way to contact the author 'hjc'.

---

### Post by cisforcojo on 2008-03-25
Could someone please try and compile this Mupen64 plugin?

I've attached it to this post, if you don't trust it, the website is:
[http://www.headspace.uklinux.net/wingman64.html](http://www.headspace.uklinux.net/wingman64.html)

I can get it to compile without errors but when I load the plugin in Mupen64, I just get a VERY small dialog window with no content (and critical GTK errors).
Any ideas???? I think it might be an inconsistency with GTK and older versions.

---

### Post by forrestcupp on 2008-03-25
When you used the Blight plugin, did you actually set it to use your controller?  In the configuration for blight, you have to click the box to the right of the word 'Device' and choose your controller from the list.  By default, it's not going to use it.

---

### Post by cisforcojo on 2008-03-25
Yeah I've tried that. I had the same problems when using ePSXe. Whatever pSX does, it works perfectly. I was hoping for better luck with the Wingman64 plugin. I'd like to know if anyone else has any luck compiling it.

As for blight, I think it's a problem with SDL and my joystick. All the buttons work, just nothing from the D-Pad or Analogs.

---

### Post by forrestcupp on 2008-03-25
I had the same problem after I installed jscalibrator.  Before I installed that and used it, my axes worked fine.  Then I installed jscalibrator and calibrated my gamepad, and the axes stopped working in Mupen64.  The buttons worked, but the joystick part didn't.  I purge removed jscalibrator, and the axes started working again in Mupen64.

---

### Post by cisforcojo on 2008-03-26
acoustibop said something similar in another thread.
I tried it but didn't have any luck. I'll try it again and let you know.

EDIT: Alright! Apparently the --purge was the trick that needed to be done. I got it to config and games seem to be working pretty well. The d-pad up and down buttons don't seem to be being assigned. I'm not sure however because when I press up or down, the input box closes but nothing is entered into the key assigned field. Both left and right have been given "W Axis +" for the axis. It's just blank for up and down. I haven't played enough to have this affect me yet. Do you know what would cause this? I really appreciate your help!

---

### Post by forrestcupp on 2008-03-26
Yeah, if you don't purge remove it, it just leaves those settings on your system that was messing things up.  I'm glad that worked for you.  Jscalibrator should be banned.

I don't really know about your new problem, though.  On my game pad, I have an analog stick and a digital 4-directional pad.  I can only use one or the other, but mine is made like that.

---

### Post by cisforcojo on 2008-03-26
Have you ever had problems with your controller just stopping responding? I'll be playing for about 5 minutes and then the controller just goes. If I stop the ROM and go to the config, Mupen64 crashes.

---

### Post by acoustibop on 2008-03-26
> **forrestcupp said:**
> Yeah, if you don't purge remove it, it just leaves those settings on your system that was messing things up.  I'm glad that worked for you.  Jscalibrator should be banned.

Agreed, forrestcupp _ I keep telling people about jscalibrator, too.  And almost every time, it *is* the problem...

---

### Post by cisforcojo on 2008-03-27
Agreed. I'll sign that petition. It was pretty frustrating.

---

### Post by cisforcojo on 2008-03-28
I'm marking this thread as SOLVED because I fixed the axis problem, the topic of this thread. My joypad still has problems with not responding after 5 minutes but that's a problem for another thread, and it probably has a lot more to do with it's Chinese and costs about the same as a bottle of Coke in America. 

Bottom line: GET RID OF JSCALIBRATOR IF YOU HAVE IT!!!

---

