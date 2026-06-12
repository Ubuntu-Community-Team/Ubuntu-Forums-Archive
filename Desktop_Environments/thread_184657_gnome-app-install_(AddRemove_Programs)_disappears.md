---
title: "gnome-app-install (Add/Remove Programs) disappears"
date: 2006-05-30
forum: Desktop Environments
---

### Post by MattCarp on 2006-05-30
When I execute "Add/Remove Programs" from the ubuntu menu, it launches, and right after the dependency generation step, it disappears.  I do not get a prompt for my root password.

When I go to the terminal and run "sudo synaptic", it works.

When I go to the terminal as the normal user or as su and run the command "gnome-app-install"  I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 171, in __init__
    self.updateCache()
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 667, in updateCache
    progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 124, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 288, in refresh
    self._populateFromEntry(menu, progress=progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 346, in _populateFromEntry
    name = xmlescape(entry.getName())
  File "/usr/lib/python2.4/site-packages/AppInstall/Util.py", line 38, in xmlescape
    from xml.sax.saxutils import escape
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/saxutils.py", line 8, in ?
    import os, urlparse, urllib2, types
  File "/usr/lib/python2.4/urllib2.py", line 108, in ?
    import cookielib
ValueError: bad marshal data

```

I've tried reinstalling with:

sudo apt-get remove --purge gnome-app-install
sudo apt-get install --reinstall gnome-app-install

Both of those commands work successfully, but the problem remains.

Thoughts?  Or, is there a bug I need to report?

---

### Post by MattCarp on 2006-05-30
Also, update-manager gives me a similar result.

When I invoke it from the menu, it doesn't display anything.

When I invoke it from the command line, I'm able to capture this output:

```

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 44, in ?
    import urllib2
  File "/usr/lib/python2.4/urllib2.py", line 108, in ?
    import cookielib
ValueError: bad marshal data

```

---

### Post by MattCarp on 2006-05-31
Ok - I think the problem was caused by installing Firefox 1.5 (instead of 1.0.8)

[http://www.ubuntuforums.org/showthread.php?t=171114](http://www.ubuntuforums.org/showthread.php?t=171114)

But what about a fix?  Downgrading Firefox doesn't sound like a good idea.

---

### Post by MattCarp on 2006-05-31
Could the problem be related to installing Firefox 1.5?

[http://www.ubuntuforums.org/showthread.php?t=171114](http://www.ubuntuforums.org/showthread.php?t=171114)

Downgrading Firefox doesn't sound like a good idea.

---

### Post by bruce89 on 2006-05-31
Firefox is depended on by lots of programs - including gnome-app-install.  Installing a non-Ubuntu one on top of the original breaks stuff.

---

### Post by MattCarp on 2006-06-01
Is there a way for me to safely re-install Firefox?  I've tried doing it through Synaptic and it doesn't seem to fix my problem ("Mark for reinstallation")

It must be leaving the i686 files in place?

---

### Post by MattCarp on 2006-06-01
[QUOTE=MattCarp]Is there a way for me to safely re-install Firefox?  I've tried doing it through Synaptic and it doesn't seem to fix my problem ("Mark for reinstallation")

It must be leaving the i686 files in place?[/QUOTE]

Fixed!  Fixed!  Fixed!

Ok, I'm not sure how I originally broke it, and I'm not 100% certain how I fixed it, but here's what I did:

[I've been using Dapper Drake for about a month now, and have been applying a lot of updates that come across the wire as the 1-June release date arrived]

A while ago I downloaded and installed Firefox i686 1.5.0.3 directly from Mozilla.  I assumed that this broke something.  I was getting "ValueError: bad mashal data" in the console when I ran update-manager and gnome-app-install.  Given that I know ubuntu is an i386 app, I thought that there was a problem with the update manager or app installer calling the i686 Firefox code (I jumped to this by thinking about marshalling, and the old 16->32 bit marshalling days).

Despite using Synaptic to reinstall Firefox, I always saw i686 in the Help>About of Firefox, so I thought I was still using i686 code.  Duh, this is wrong.

To attempt to uninstall Firefox and reinstall from the ubuntu repositories, I just deleted /usr/bin/firefox and /usr/lib/firefox and then was in an hour of hell trying to reinstall from the firefox i386 debian package.  The short of it was that I had to apt-get remove yelp, gnome-app-install, firefox-gnome-support, libflash-mozplugin, and flashplugin-nonfree and then I was able to [apt-get] install firefox, and then put back the other packages I removed.

So, I was back to sqare one with the error.  I started to debug the Python code, first by commenting out the "import cookielib" in the /usr/lib/python2.4/urllib2.py.
Now update-manager and gnome-app-install ("Add/Remove Programs") worked!

However, urllib2.py is a common library, and somewhere something is going to want to use the cookie functionality of urllib2.  So, I put in a couple debugging statements ("import pdb"  "pdb.set_trace()") to see if I could see where the "bad marshal data" error was occuring.  First I tried the debugging statements in /usr/bin/update-manager and the right in /usr/lib/python2.4/cookielib.py directly.  Both times, no error!

I removed the debugging statements, then tested:  no error!!  So, the problem was fixed!

I did notice that cookielib.pyc and urllib2.pyc were modified about the same time as my debugging today.   For whatever reason, these libraries were recompiled.

So, I gather that I somehow screwed up /usr/lib/python2.4/cookielib.pyc
By simply touching it, it recompiled to byte code and now works fine.

very bizzarre....but I'm happy to have it fixed.

---

