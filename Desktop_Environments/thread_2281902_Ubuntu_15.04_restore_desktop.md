---
title: "Ubuntu 15.04 restore desktop"
date: 2015-06-10
forum: Desktop Environments
---

### Post by nlee2 on 2015-06-10
My Ubuntu 15.04 desktop got messed up. How do I get back to the default Unity desktop without a complete system reinstall?

edit:

Changing theme to Ambiance gets it closer to the original but no wallpaper, just black screen. Cannot change in settings or tweak-tool.

---

### Post by ajgreeny on 2015-06-10
Got messed up how?  What did you or someone else do?  Have you added or removed any essential packages or is this just some bad setting in you own home?

Can you please login to the **Guest** account from the login screen and see if that works as you expect.

---

### Post by nlee2 on 2015-06-10
Thank you for your help with restoring my Ubuntu 15.04 unity desktop.
The Guest account has the same messed up unity desktop with default Adwaita theme. I have customized mine to be a little more like a fresh install by change to Radiance theme.

Just one of those days. Started with trying to install CoreOS as vm. One installer complained with messages shown. I installed some pertinent gtk2 packages and when they did not help I purge removed them. Things got unstable. I reinstall ubuntu-desktop and unity. Somehow ended up with extra (not needed/unwanted) gnome-classic and gnome (default) on lightdm greeter. Next time I will use a docker container.

Other things I have tried.

setsid unity
dconf reset -f /org/compiz/

Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"
Gtk-Message: Failed to load module "canberra-gtk-module":  libcanberra-gtk-module.so: cannot open shared object file: No such file  or directory

edit
All fixed. I kept switching themes and logging off a few times. The missing wallpaper was wierd until I enabled desktop icons. Just need to uninstall gnome and gnome-classic.

---

### Post by ajgreeny on 2015-06-11
I am glad to hear that you have apparently solved your problem.
Please mark as SOLVED from the Thread Tools menu at the top.

---

### Post by nlee2 on 2015-06-11
I spoke too soon. My background wallpaper will not stick. If I logoff then logon, my initial desktop background is a black screen. To fix. I use tweak tool to toggle Desktop->Icons on Desktop to see my wallpaper.

edit
Fixed by using dconf-editor and reset Background to default settings.

---

