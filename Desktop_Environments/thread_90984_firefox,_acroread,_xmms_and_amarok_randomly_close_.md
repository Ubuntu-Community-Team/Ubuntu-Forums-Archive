---
title: "firefox, acroread, xmms and amarok randomly close - possibly because of sound?"
date: 2005-11-16
forum: Desktop Environments
---

### Post by katu on 2005-11-16
(for all my faithful readers, an update as to what's going on ;)  and sorry for the tabloid topic ;>)

I've had random apps crash on random for sometime now, this was usually firefox, acroread, xmms, the bottom gnome panel and I think also the terminal (not sure). Since this was a system that I upgraded from hoary to breezy via dist-upgrade I thought this could be the reason. So I did a clean reinstall (leaving the home directory intact). The problem is still there.

Mind you, this  is basically a clean system with universe and multiverse packages (no backports or marillat), only w32codecs and libdvdcss installed as in the wiki, and the kadu messenger (which also sometimes crashes, but I've never had problems with it otherwise). 

**The symptoms**
As I said, most of these apps crash without giving any kind of error messages. They just dissapear. I tried running them from the command line and this is what I got:
firefox:
```
The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

acroread gives no output whatsoever, but the curious thing is I can crash it by pressing the left mouse button, and wiggling quickly up and down (I'm serious). It usually takes about 3 seconds of this to go down.

xmms
```
Gdk-ERROR **: X connection to :0.0 broken (explicit kill or server shutdown).
```

other apps, that I got some output from:
amarok:
```
amarok: Fatal IO error: client killed

``` 
This is from a standard disappearance. 
What I also get with amarok is a slightly different bahaviour in the sense, that at some point it just stops playing but sits there. If I try to push play or stop, it stops responding and then it's force quit country.

from these I get as window warnings (usually together):

show desktop
window list
worskpace switcher   --- has quit unexpectedly.

reloading them makes it fine.

**What I tried**
I tried the **export GTK_IM_MODULE=xim** hack both for firefox and acroread and disabling PANGO for firefox. Didn't help.

**the unexpected turn of events** 
Ok. At first I thought this may have been caused by sound. But another thing is that my usb mouse after the startup of the computer doesn't have the scrolling wheel function. If I unplug and plug again, the scrolling wheel works, but also the apps begin to close. Without the "replugging" it essentialy seems to be stable - except for amarok, which still hangs as described above. 
(before) dmesg |grep usb ```
[4294675.689000] usbcore: registered new driver usbfs
[4294675.689000] usbcore: registered new driver hub
[4294676.886000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294678.562000] usbcore: registered new driver hiddev
[4294678.573000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:02.1-1
[4294678.573000] usbcore: registered new driver usbhid
[4294678.573000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
```

after replug:
```
usb 2-1: USB disconnect, address 2
[4308705.113000] ohci_hcd 0000:00:02.1: wakeup
[4308705.386000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[4308705.530000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:02.1-1

```


**additional info**
I'm running 32bit ubuntu/breezy on a compaq R3340 laptop, AMD64 processor,nforce3 audio. 
xmms is running on alsa output (was on oss). amarok is using the xine engine.  
And of course, I never had these problems with hoary or on my main machine (which is kubuntu though). 

Sorry for the long post. I will be very grateful for any help. If this is a bug I'll gladly submit, but I need help to diagnose, what is actually going on.
Edit: And I hope more people will read it now ;]. 
cheers,
Katu

---

### Post by alikilaij on 2006-06-07
Did you ever get this resolved? 

I am having similar problems with Ubuntu Breezy amd64. When I run xmms with xmms-liveice enabled it closes xmms with the Gdk error.  If I disable the plugin, all seems to operate fine.

Haven't had much luck finding any information about this issue.

---

