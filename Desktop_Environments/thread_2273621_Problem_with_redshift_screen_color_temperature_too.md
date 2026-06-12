---
title: "Problem with redshift screen color temperature tool"
date: 2015-04-14
forum: Desktop Environments
---

### Post by chaaderf on 2015-04-14
Hello dear *buntu users!

I would like to try a color temperature tool like redshift. It looks like I can install it via software center or terminal, there are no problems in that part. I.e.

```
sudo apt-get install redshift redshift-gtk
```

This creates a menu entry but once I click it, the lamp icon shows up on the system tray but it disappears after some seconds. There is no any indication that the program would work either. I mean, the screen colors won't change. Any hints how to set up the redshift tool properly? I'm using Lubuntu 14.04.

Thank you for your help! ^^

//EDIT Few days later: It seems that the redshift itself works, but it just needs to be configured manually by adding the file ~/.config/redshift.conf with suitable content.

---

### Post by Rex Bouwense on 2015-04-14
There is a bug that goes back to Oct 2011.  [https://bugs.launchpad.net/ubuntu/+source/redshift/+bug/868904](https://bugs.launchpad.net/ubuntu/+source/redshift/+bug/868904)  and apparently is still in 14.04 unless I read the last posts incorrectly.

---

### Post by chaaderf on 2015-04-15
Thank you, Rex Bouwense.

Is there a text based way to configure it then? I read something, that the configuration file should be located in ~/.config/redshift.conf. But how is in this case? Is the installation working even though the GUI is clearly not? Or should I look for somewhere else to adjust the color temperature?

Thank you again! ^^

---

