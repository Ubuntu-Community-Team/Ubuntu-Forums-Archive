---
title: "create xorg.conf using Ubuntu Live"
date: 2011-05-02
forum: Desktop Environments
---

### Post by cccc on 2011-05-02
hi

Howto create xorg.conf using Ubuntu 10.04 Live?

---

### Post by aphatak on 2011-05-12
I found these directions for creating an xorg.conf -
[LIST=1]
[*]Boot from the live CD, then select 'Try Ubuntu'.
[*]Switch to a terminal - **ctl-alt-F1**.
[*]Log in using a user-ID that can do 'sudo'.
[*]Stop the desktop manager - ```
sudo service gdm stop
```[*]Create a config file - ```
sudo Xorg -configure
```  If you do an 'ls ~ -l', the generated file should show up.  You might want to copy it to a thumb-drive at this point.
[*]Start gdm - ```
sudo service gdm start
```  This should send you back to the screen which gives you the option to try or install Ubuntu.
[/LIST]
You should find the file 'xorg.conf.new' in your home directory.

I have tried it using a USB drive, not a live CD.  However, it's worth trying.  The generated xorg.conf.new may not exactly match your hardware configuration, but should at least give you a good starting point.

---

