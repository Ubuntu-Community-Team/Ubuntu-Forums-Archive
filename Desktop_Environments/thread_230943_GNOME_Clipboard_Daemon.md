---
title: "GNOME Clipboard Daemon"
date: 2006-08-06
forum: Desktop Environments
---

### Post by srunni on 2006-08-06
I tried to install the GNOME Clipboard Daemon using the instructions at ubuntuguide.org, but when I restarted, it didn't work. Also, when I was restarting, "PCMIA services" failed to start, and continues to do so. Is it even important? Does anyone know how to fix this?

Thanks

---

### Post by srunni on 2006-08-07
Any ideas?

---

### Post by RajivNair on 2006-08-07
i dont know about the PCMCIA part but better install Klipper,it works in GNOME.

---

### Post by Anduu on 2006-08-07
If you are using a laptop pcmcia is important.It manages your swappable memory/network/etc cards.

Desktops have no use for it.

Are you sure gnome-clipboard-daemon isnt working?It doesn't work with certain apps.Firefox for example...if you ctrl+c something in Firefox then close it you will lose the copied stuff.

Open your system monitor and check to see if an instance of gnome-clipboard-daemon is running.If not you may not have added it to your startup programs under session properties.

---

### Post by srunni on 2006-08-07
I'm running a desktop, so I guess I'm OK as far as that goes. I'm going to try Klipper instead.

---

### Post by srunni on 2006-08-07
Well, I tried Klipper, and it turned out to be horrible. It caused major slowdowns during login and logout, and when I was turning my computer on and off. I think I'll just get used to keeping a window open until I paste what I need to, seeing as the GNOME Clipboard Daemon doesn't work universally.

---

### Post by LordSavage on 2006-08-07
Just use glipper. Its much better.

[http://prdownloads.sourceforge.net/glipper/glipper_0.86-1_i386.deb?download](http://prdownloads.sourceforge.net/glipper/glipper_0.86-1_i386.deb?download)

---

### Post by dentaku65 on 2006-08-07
try Glipper :-)

[http://www.gnomefiles.org/app.php/Glipper](http://www.gnomefiles.org/app.php/Glipper)

unfortunately it is not in the repo.

---

### Post by srunni on 2006-08-07
Are there any speed problems with Glipper like there are with Klipper?

---

### Post by LordSavage on 2006-08-08
No, there are no problems. Glipper is made for Gnome.

---

### Post by srunni on 2006-08-08
I downloaded the Glipper tarball, but when I ran
```
./configure
```
I got
```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```
I think I'm missing a dependency.

---

### Post by LordSavage on 2006-08-08
Why don't you just download the deb?

---

### Post by srunni on 2006-08-08
Didn't see that :D
I went to the second link, and it was to a tarball, not a deb. I'll try out the deb now.

---

### Post by srunni on 2006-08-08
Well, Glipper doesn't seem to be causing any slowdowns (at least on login/off; I still have to test on startup/shutdown). However, it, like the GNOME Clipboard Daemon, doesn't seem to work with Firefox. Is this true?

EDIT: Well, I can paste from other programs into Firefox, but anything I cut/copy from it doesn't appear in other programs.

---

### Post by Anduu on 2006-08-08
> **srunni said:**
> Well, Glipper doesn't seem to be causing any slowdowns (at least on login/off; I still have to test on startup/shutdown). However, it, like the GNOME Clipboard Daemon, doesn't seem to work with Firefox. Is this true?

EDIT: Well, I can paste from other programs into Firefox, but anything I cut/copy from it doesn't appear in other programs.

Firefox is funny tha way...dunno why.

---

### Post by srunni on 2006-08-08
On Kubuntu (which comes with Klipper installed and running at startup by default), Klipper is able to work just fine with Firefox.

---

### Post by Anduu on 2006-08-08
Ookey...just did a little experiment.

Copy some text in Firefox then close it.If you try to paste into a document nothing happens.With Glipper all you have to do is click the Glipper icon in the tray and select the text from the Glipper history thinger.

It will then paste.

I don't know about KDE but Firefox in Gnome must be left open to copy/paste even when using gnome-clipboard-daemon.

---

### Post by Frem on 2006-08-08
> **Anduu said:**
> I don't know about KDE but Firefox in Gnome must be left open to copy/paste even when using gnome-clipboard-daemon.Aren't most Linux apps like this?

---

### Post by Anduu on 2006-08-08
> **Frem said:**
> Aren't most Linux apps like this?

If you use gnome-clipboard-daemon you can paste after the app is closed.

No clipboard-daemon no paste after close with any app.

---

### Post by srunni on 2006-08-08
What's up with this problem with Firefox? What exactly causes it?

---

### Post by LordSavage on 2006-08-10
I can paste from firefox even when its closed if glipper is installed.
are you sure glipper is running?

---

### Post by srunni on 2006-08-10
Yeah, it's installed, I see the little G on the clipboard in the system tray. I found out that if you just click on the G, you can see your cut/copy history, and using that method, it works even with Firefox. I guess that'll work. I'm not even going to be using this Ubuntu computer anyway, just want to make it easy for others. On Kubuntu (which I run), Klipper works with everything.

---

### Post by SentientFluid on 2007-07-20
> **Anduu said:**
> Ie you sure gnome-clipboard-daemon isnt working?It doesn't work with certain apps.Firefox for example...if you ctrl+c something in Firefox then close it you will lose the copied stuff.

When I ran Dapper and Edgy, Gnome Clipboard Daemon always worked fine with Firefox, whether it was open or closed. *shrug*

Either way, it doesn't seem to work in Feisty so I'll try out Glipper.

---

### Post by crazy ivan on 2007-10-30
Well I switched to ubuntu 7.10 from suse recently and missed my good old klipper  (or something similar) in the add to panel menu. Now I got it via synaptic and still couldnt add it. Executing "klipper" in console got it um to the systemtray, where it sort of works. I cant move it and it has all KDE-looks. It works with firefox, but only if I press "ctrl+c", not if I simply select text. But thats ok, since I sometimes just mark text to emphasize.
Any tricks how to improve looks and feel? Are there some alternative repositories including glipper.deb?

---

### Post by crazy ivan on 2007-10-30
Forget the second, question. I just found glipper in the community supported list.

Another question I have, is wether there is a gnome alternative to xmms-kde, since what I get is:  "wmxmms
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 141 error_code 8 request_code 62 minor_code 0"

---

### Post by srunni on 2007-10-30
You should try Kubuntu, the KDE version of Ubuntu - it comes with Klipper installed and I find it to be a lot better than Ubuntu (with GNOME).

---

### Post by ice60 on 2007-10-30
you could try out Desktop Data Manager too, it's pretty cool.  it displays thumbnails of graphics in the clipboard, can take screenshots and might do something else too, i can't remember now.
[http://data-manager.sourceforge.net/](http://data-manager.sourceforge.net/)
i found this -
[http://onlyubuntu.blogspot.com/2007/04/desktop-data-managerddm-for-ubuntu.html](http://onlyubuntu.blogspot.com/2007/04/desktop-data-managerddm-for-ubuntu.html)

i'm using it now, i had one configuration problem with it - it saves data from both the clipboards, but with the default config only one of them was working, it was really easy to fix in the preferneces though, just selected one of the other options.

---

### Post by crazy ivan on 2007-10-30
@srunni, well I just came from SUSe, now I think Ill stick with Gnome for a year

@ice60: Thanks for the hint. Always wanted to take screenshots with klipper. But unfortunately DDM is not in repo + has some issues with 7.10: 
[http://forum.ubuntuusers.de/topic/123678/#997239](http://forum.ubuntuusers.de/topic/123678/#997239)

Now I got it working via Autostart in sessions. Also I had to install
```
 libmono1.0-cil 
 gtk-sharp2 
 libmono-system-runtime2.0-cil
```

via Synaptic prior to installing the .deb package.

Anyhow any such good ideas for multimedia control in the panel?

---

