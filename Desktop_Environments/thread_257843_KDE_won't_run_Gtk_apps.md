---
title: "KDE won't run Gtk apps"
date: 2006-09-15
forum: Desktop Environments
---

### Post by lowey23 on 2006-09-15
Already posted this on the Kubuntu forums to no avail. I thought perhaps someone here may be able to help.

Using Kubuntu Dapper 6.06.1

I have tried, a couple of times, to give Gnome a try. Decided to stay with KDE and followed the instructions for Pure KDE on Aysiu's excellent site

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

The first time I did this, I needed to reinstall a couple of gtk apps (synaptic, swiftfox, thunderbird etc) and succeeded.

For various reasons, I installed ubuntu-desktop again. Still didn't like it as much as KDE so I followed the psychocats instructions again and this time it uninstalled my KDE as well. No problems, reinstalled Kubuntu desktop and synaptic etc and all was good.

This time (I know, I know) I reinstalled Ubuntu-desktop and this time when I try to start Ubuntu I only get half way through metacity, a blank status bar and thats it. Went into the KDE d/top and found that my Gtk apps no longer work. Can't get them to start with command line, either. When I try synaptic with cli I get the following error message

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault

Tried reconfiguring xserver (on advice from google) but no go.

The apps I want to start are all installed but just won't go.

Just wondering if I'm the only one silly enough to get myself in this bind or if I've broken it properly this time. I don't want to reinstall. Wondering if upgrading to Edgy may help (not yet, though, when it's released).

Thanks in advance

Lowey

---

### Post by lagagnon on 2006-09-15
Way too much installing and uninstalling of desktop environments. No wonder you have problems. IMHO the easiest way out is to first of all make a final decision as to what desktop you really want and then re-install Kubuntu, xubuntu or Ubuntu.

---

### Post by Tim.thelion on 2006-10-18
I had this. I fixed it with
cd ~/
rm .gtk*

---

### Post by lowey23 on 2006-10-18
Thanks for the reply Tim. I fixed it by upgrading to Edgy. Didn't want to do that so soon, but so far so good. Still holding my breath till the final release, though.

---

