---
title: "messed up gnome pannel, broke system"
date: 2009-12-02
forum: Desktop Environments
---

### Post by pearldrums on 2009-12-02
I was fooling around with the gnome panel settings and ended up making my system inoperable. I realized that if you had two panels oriented at the top of the screen one would be right below the other. I decided this would be a cool way to make a quit start menu if I had the lower panel auto-hide and put launchersn on it. When I made it auto-hide it "hid" on top of the other panel and the panels locked up. I went to shut down and it said that the gnome panel was unresponsive. I was hoping that a restart would allow me to right click and delete that panel, but now when I try to start up the system locks up before the login screen.

Can anyone help me boot up. If not I can access recovery mode and uninstall/reinstall it, but I don't know exactly what its name is, or if i need to do  a special command to delete the package and its settings. Is this a major bug that I should fill a bug report out for? Thanks.

---

### Post by VCoolio on 2009-12-02
Try to login to your account with console and then:
gconftool --recursive-unset /apps/panel
to reset all your panel settings to default. If it works that better then a reinstall, right? Don't know if it's a huge bug, I'm not going to test it ;). Also reinstalling ubuntu or gnome-panel won't help if you don't erase your /home partition too (if you're right in assuming the problem is in the user settings).

Edit: closer reading learned me that your system locks before login screen. That suggests the problem is not in the user settings and the above doesn't apply. Sorry.

---

### Post by pearldrums on 2009-12-02
thanks, that got me back up and running again! I decided to try it one more time before I got everything set the way I like it and if any one is ever interested, you can do it if you make the panel closes to the edge of your screen auto-hide.

---

