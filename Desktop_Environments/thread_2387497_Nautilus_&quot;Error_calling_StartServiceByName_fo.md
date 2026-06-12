---
title: "Nautilus &quot;Error calling StartServiceByName for org.gtk.vfs.MTPVolumeMonitor&quot;"
date: 2018-03-19
forum: Desktop Environments
---

### Post by PABlanche on 2018-03-19
Nautilus is very slow at opening a first file manager window, or to save a file with "save as".

When opening a fist file manager window using nautilus in terminal I have the following error message that appears after 20 seconds: 
'Error creating proxy: Error calling StartServiceByName for org.gtk.vfs.MTPVolumeMonitor: Timeout was reached (g-io-error-quark, 24)
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)'

The process still run (no new command line), and I have to exist with Ctrl+c, which close the window

If I open a window first, then go in the terminal and type 'nautilus', the window open immediately, and the  terminal get me back to a new command line.

To be thorough, my /home is formated using Btrfs.

This error is really annoying and I would really appreciate any help.

---

### Post by PABlanche on 2018-03-21
Could this error be related to the mtpfs package?
I reinstall that package in order to connect an android cellphone 'sudo apt-get install go-mtpfs', and it solve the file management problem. 
One stone, two birds.

---

