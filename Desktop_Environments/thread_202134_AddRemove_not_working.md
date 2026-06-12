---
title: "Add/Remove not working"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Vegas on 2006-06-22
This is gnome's "Add/Remove" feature.

I am a complete Linux novice.  If I have to show you any sort of reports, gotta tell me what I need to type in.


I've been messing around with Automatix mainly, however I decided to look in Add/Remove.  Add/Remove worked great, however I installed quite a few programs from Automatix. 

Now, whenever I try to open Add/Remove, the progress bar appears, stating that it's seeing what programs I have et cetera, then when it completes, it just shuts down.  I had the proccess viewer open and I saw it actually terminate.

When I type the in "gnome-app-install", it pops up, the progress bar goes across.  But when all the "Criticals" pop up it shuts down (right when the progress bar is finished).

Thanks in advance, I'm sure I've done something wrong, but the help would be appreciated.

This is what the console outputs.




```
Introspect error: The name org.freedesktop.AppInstall was not provided by any .s
ervice files
no listening object (The name org.freedesktop.AppInstall was not provided by any
 .service files)

** (gnome-app-install:5013): WARNING **: return value of custom widget handler w
as not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:5013): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `s                                                    tream->cancel_func != NULL' failed

(gnome-app-install:5013): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `s                                                    tream->cancel_func != NULL' failed

(gnome-app-install:5013): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `s                                                    tream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in                                                     __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

```

---

### Post by jccj7 on 2006-07-02
I'm having the same problem as well.  Hopefully someone will reply.  I'm still looking through search results though.....probably a common issue.

---

### Post by jccj7 on 2006-07-02
I got it working by running Automatix, installing something, and then when it prompts you about reinstalling or reverting back to some list (warns you that if you that if you hit ok, it will overwrite) well, I think we've been hitting cancel...it sould be 'ok'.  After that, I've got the Add/Remove command back.

---

### Post by YourDoom123 on 2006-07-02
yea, you need to overwrite the sources.list file when prompted, otherwise, add and remove programs won't recognize the new file. i'm fairly sure that automatix recommends that u hit ok (and overwrite), going so far as to say not to hit cancel unless you know exactly what you're doing. could be wrong about that tho. haven't run automatix in quite a while. one other thing you could try is opening up a terminal, and typing in
```

sudo aptitude update

```
that may fix the problem, but again, i'm not sure. last tip, asap, learn to install and remove programs from the terminal, or at least synaptic (found in system --> administration --> synaptic package manager). either way, you'll find you have a lot more control over what goes on your system, and what doesn't. do you have to do it this way? nope, you'll be perfectly fine sticking to the gui. but the power of linux resides in the terminal. the sooner you learn to use it, the more control you'll have over your system. entirely up to you though.

---

### Post by jccj7 on 2006-07-02
Doom...Thanks for confirming

---

