---
title: "Firefox causes crashes when playing videos"
date: 2009-01-23
forum: General Help
---

### Post by Mzwo on 2009-01-23
hi all,

hardy studio, kernel 2.6.24-23 rt, gnome 2.22.3, firefox 3.0.5.

i'm not even certain if the term "crash" is applicable here. what happens is: every now and again when i play flash video content firefox will not only freeze for a handful of moments, more annoyingly, i'm presented with a black screen sporting a number of message, followed by ok. (Something about timidity, and alsa, and other things - keep meaning to write down the details, sorry). i can then enter a terminal pressing ctrl-alt-f1-9. however: starting x or gnome doesn't seem to work. the only thing i can do is sudo shutdown and reboot. this is a little annoying, since all data is lost.

how can i get back to my desktop when this happens? what could cause firefox to misbehave? 

i tried to be as precise as possible, will add any info missing.

thanks for any help.

Mzwo

---

### Post by Mzwo on 2009-01-23
i should add that i'm mostly presented with a black screen as described above when closing tabs *within* firefox. haven't had this problem yet when closing windows and only rarely without taking any action what so ever. 

Mzwo

---

### Post by Mzwo on 2009-01-24
bump

---

### Post by dcstar on 2009-01-24
> **Mzwo said:**
> hi all,

hardy studio, kernel 2.6.24-23 rt, gnome 2.22.3, firefox 3.0.5.

i'm not even certain if the term "crash" is applicable here. what happens is: every now and again when i play flash video content firefox will not only freeze for a handful of moments, more annoyingly, i'm presented with a black screen sporting a number of message, followed by ok. (Something about timidity, and alsa, and other things - keep meaning to write down the details, sorry). i can then enter a terminal pressing ctrl-alt-f1-9. however: starting x or gnome doesn't seem to work. the only thing i can do is sudo shutdown and reboot. this is a little annoying, since all data is lost.
........

What video hardware do you have?

---

### Post by jure1873 on 2009-01-24
did you try changing from flash10 to 9 or from 9 to 10?
when you enter the terminal during what is the output of 
tail /var/log/messages 
dmesg 
tail .xsession-errors

---

### Post by Mzwo on 2009-01-26
@dcstar: 

mobility radeon HD 2400 



@jure1873:

haven't changed recently. i think. how do i find out which flash i've got (sorry, stupid user)?

```
mzwo@Mzwo:~$ tail /var/log/messages
Jan 26 15:45:05 Mzwo -- MARK --
Jan 26 16:05:05 Mzwo -- MARK --
Jan 26 16:25:05 Mzwo -- MARK --
Jan 26 16:29:44 Mzwo kernel: [15147.722164] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 26 16:29:52 Mzwo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jan 26 16:29:52 Mzwo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jan 26 16:29:52 Mzwo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jan 26 16:29:52 Mzwo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jan 26 16:45:07 Mzwo -- MARK --
Jan 26 17:05:07 Mzwo -- MARK --
mzwo@Mzwo:~$ 
```

"dmesg" gives me a list about 12 pages long ...


```
mzwo@Mzwo:~$ tail .xsession-errors 
(npviewer.bin:1000): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:1000): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:1000): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:1000): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

** (gnome-system-monitor:2141): WARNING **: SELinux was found but is not enabled.

mzwo@Mzwo:~$ 




```

that what you wanted to know?

thanks,

Mzwo

---

### Post by philinux on 2009-01-26
Run firefox from a terminal in safe mode to see what happens. Addons can cause problems.

```
firefox -safe-mode
```

Post any errors if it crashes.

---

### Post by Mzwo on 2009-01-26
hi, 
did that. firefox froze, this is what i got:


```

GCJ PLUGIN: thread 0x621d10: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621d10: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621d10: NP_GetValue
GCJ PLUGIN: thread 0x621d10: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621d10: NP_GetValue return
GCJ PLUGIN: thread 0x621d10: NP_GetValue
GCJ PLUGIN: thread 0x621d10: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621d10: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3929): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:4015): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Message timeout
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(npviewer.bin:4071): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:4071): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:4071): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:4071): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
mzwo@Mzwo:~$ 
```


another problem: my bookmarks have dissappeared(all of them: rss, toolbar, folders.) restore won't work. where can i find them?

Mzwo

---

### Post by Mzwo on 2009-01-26
bookmarks are gone. not only that: i can't add any either. not even after completely removing and reinstalling firefox. 

help?

---

### Post by Mzwo on 2009-01-26
update: can't go back and forward either - history seems to be disabled. how do i switch everything back on?

Mzwo

PS: stop and reload won't work either (icons remain "unclickably" grey)

PPS: gone back to firefox 2 and removed 3. can't live without bookmakrs and "back-button". how to i upgrade to 3?

---

### Post by Mzwo on 2009-01-27
help?

---

### Post by Linuxdork on 2009-01-27
Okay, I could be wrong but I think this is due to libflashsupport.  What Ubuntu version are you on?

---

### Post by Mzwo on 2009-01-28
64 bit 8.04 studio, 2.6.24-23-rt.

how does libflashsupport make my bookmarks go away and prevent firefox 3 from working properly (even after the third complete removal and reinstall), while firefox 2 works a treat?

still don't know how to upgrade, by the way ...

Thanks,
Mzwo

---

### Post by Linuxdork on 2009-01-28
Because you said it happens when you play flash video.  libflashsupport has been causing firefox crashes and mis-behavior.  Like I said, I could be wrong.  If you have libflashsupport installed, it wouldn't hurt to remove it and see if the problems continue.

```
apt-cache search libflashsupport
libflashsupport - Support library for sound output of Flash 9 with pulseaudio
```

Btw, I didn't realize that Ubuntu Studio 8.04 didn't come with firefox 3.  Also, what instructions did you follow to install flash; there isn't native 64 bit flash support.  I'm wondering if it is install incorrectly.  Just some ideas.

---

### Post by Mzwo on 2009-01-28
hi, 

thanks, will try that.

8.04 came with firefox 3 - alas, after i did what philinux suggested above, namely to start firefox in safe mode, my bookmarks dissappeared, back and forward buttons stopped working, reload wasn't an option anymore - and completely removing and reinstalling firefox 3 didn't solve the problem. hence i installed firefox 2, since i need a working browser. i'd love to get back to firefox 3, but don't know how. merely instaling it form the repos ain't getting me a working browser.

i'm a bit of a noob, so i haven't got a clue how i isntalled flash. i assume it was installed with the restricted extras package? 


what i really need at this stage is a working "copy" of firefox 3 - then i will sort out the flash problem.

many thanks,

Mzwo

---

### Post by Mzwo on 2009-01-29
bump

---

### Post by khedron on 2009-01-29
Ok, first try deleting your profile directory (well, actually just moving it somewhere else so firefox can't find it):
```
temp="$(mktemp ~/profileXXX)"
mv ~/.mozilla/firefox/*default "$temp"

```This should force Firefox to create a new profile for you. If this fixes the problem, you should be able to copy back the bookmarks.html file from your old profile to ~/.mozilla/firefox/????????.default to keep your bookmarks.

If this doesn't, try fully reinstalling Firefox:
```
sudo aptitude purge firefox
sudo aptitude install firefox

```

---

