---
title: "Help!"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Pedricko on 2005-11-03
Hi, for no apparent reason the following two things have happened to my Ubuntu 5.10 install

1. Mozilla programs *namely firefox* wont  load any more, I get the 'starting firefox' in the task bar but then nothing happens and the tab disapears. I tried installing Mozilla the browser to remedy this to no avail. Im now using Epiphany

2. I used to have just one panel, at the bottom of the screen and now whenever I log in, it reverts to the standard layout :( 

Help?

---

### Post by mlomker on 2005-11-03
You can try typing **firefox** at a terminal window instead of using the icon.  That'll often give you some error messages.

---

### Post by Pedricko on 2005-11-03
Entered firefox to no avail, looks like I need a reinstall anyhow

---

### Post by Ampersand on 2005-11-03
Try renaming the .firefox and .mozilla folders in your home directory to something like .firefox_ and .mozilla_ (you'll need to enable 'show hidden files' from the view menu in nautilus, or you can use a terminal with something along the lines of
```
mv ~/.firefox ~/.firefox_
```
This should reset the configuration files for firefox, and might remove the problem. If it works after that, you can remove the folders you renamed.

---

### Post by armar on 2005-11-03
I had the same problem when I had a plugin that didn't work correctly. I believe mozilla and firefox uses the same plugin folder--that's why neither one works. Did you recently install any plugins?

---

