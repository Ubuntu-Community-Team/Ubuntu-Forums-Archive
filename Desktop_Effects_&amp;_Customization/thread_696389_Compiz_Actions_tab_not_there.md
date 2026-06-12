---
title: "Compiz Actions tab not there"
date: 2008-02-14
forum: Desktop Effects &amp; Customization
---

### Post by Metallinut on 2008-02-14
I had some problems with compiz after updating screenlets to 0.0.12...I wound up having to reinstall compiz...then I couldn't get ccsm working.  I commented out the "idle" line from /usr/bin/ccsm as suggested in another thread, and that got ccsm working again...

However, I went to set Scale Windows to the top right screen corner, but my General section in CCSM has no actions tab!  I cannot change or set any key/mouse/screen bindings for Compiz.

Has anyone seen this, or know what might be going on?  As far as I can tell, Compiz is running just fine...I just don't have the Actions tab in CCSM anymore...

---

### Post by Metallinut on 2008-02-17
Bump?  No one knows?  I couldn't find anything in the forums about this.  I cannot reset my screen corner actions!!!

---

### Post by Metallinut on 2008-02-20
One more bump.  NOBODY's seen this?

---

### Post by chavanak on 2008-02-20
No as far as i know, no one running screenlets 0.12 is facing this problem. What is the output of compiz when you run from terminal.

---

### Post by Metallinut on 2008-02-21
```
jp@lappy3000:~/dvdrip$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Everything runs fine.  But there's just no way for me to change the key bindings or screen edges, etc. for any of the plugins....

Frustrating!  I use screen corners all the time, and now I can't!

Here's the screen grab of the general settings in compiz
[IMG]http://jpandrobyn.homelinux.com/settings.png[/IMG]

---

### Post by fuzzalex on 2008-03-15
Hi people!

Looks like finally I've found the traces of what I've been looking for 2 days - absolute same problem with Actions Tabs! :)

Actions tabs just disappeared from ccsm's plugins. I can't really say what I did for that... I was just playing around with extra plugins installation, when some fine moment ooops happened. 

my compiz output in the terminal looks like says all OK:
pineapple@pineapple:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

All effects are working fine by default but one most wanted I cant set up: Windows Scaling... 
Computer is running under Gutsy Gibbon, and still I haven't found a place in the filesystem where I could fix those ccsm setings manually

---

