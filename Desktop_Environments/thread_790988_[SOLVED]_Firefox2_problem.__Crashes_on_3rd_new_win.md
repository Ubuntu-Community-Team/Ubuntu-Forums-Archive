---
title: "[SOLVED] Firefox2 problem.  Crashes on 3rd new window"
date: 2008-05-11
forum: Desktop Environments
---

### Post by iKevin on 2008-05-11
Hi All

I am not sure where to start debugging this one.   I am using Ubuntu 8.04 and downgraded to firefox2 due to add-on issues with Firefox 3-beta 5.  Everything is working fine but I can crash firefox2 every time by opening a third new window.  Is there some kind of log to look into?

Thanks
Kevin

---

### Post by corevette on 2008-05-11
try running 
```
firefox
```
in the terminal (after you have closed all sessions of firefox)
try repeating your steps to make firefox crash and see if anything appears in the terminal

also

try running firefox in safe mode from the terminal (again after you have closed all sessions of firefox)
```
firefox -safe-mode
```
if it doesn't crash, it's probably a problem with an extension, theme, plugin, or change in about:config

---

### Post by iKevin on 2008-05-11
Thanks. There abnormal in the terminal windows but it ran fine in safe mode.    That was a great tip.  I went through my three add-ons and it was "google toolbar".  I was able reproduce the error by turning it back on.  So, away goes the tool bar.  Unfortunately, I love that tool bar.

Thanks
Kevin

---

### Post by iKevin on 2008-05-11
I also found the link below. It has information related to this problem in Ubuntu.

Thanks


[http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/3c694a05d2752f9/e6738e686a352bbe?lnk=gst&q=crash+firefox#e6738e686a352bbe](http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/3c694a05d2752f9/e6738e686a352bbe?lnk=gst&q=crash+firefox#e6738e686a352bbe)

---

