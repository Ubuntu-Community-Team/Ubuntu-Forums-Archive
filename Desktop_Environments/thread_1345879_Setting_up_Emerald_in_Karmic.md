---
title: "Setting up Emerald in Karmic"
date: 2009-12-04
forum: Desktop Environments
---

### Post by bunk3rk1ng on 2009-12-04
I'm very new to Ubuntu (about 5 days in) and I'm just figuring out how different programs work together. 

Anyways, I wanted a sweet new look for my desktop and found the Emerald program.  I installed it, but when I try to run the program the terminal sends me this error.
```
paul@skeeter:~$ emerald
emerald: Screen 1 on display ":0.1" already has a decoration manager; try using the --replace option to replace the current decoration manager.
```I've tried using:
```
paul@skeeter:~$ emerald --replace &
```With no luck.

I also went to System -> Preferences -> Startup Applications, clicked add and typed emerald --replace

I can go into the Emerald Themer and view the theme I want, but nothing happens.

What do?

---

### Post by chrisinspace on 2009-12-04
Install Compiz, then open the CompizConfig Settings Manager.  In the 'Filter' field, type "Window Decoration", then click the 'Window Decoration' icon in the right pane.  Look for the 'Command' field and type:

```
emerald --replace
```

Restart the X server and you should be good to go.

---

### Post by bunk3rk1ng on 2009-12-04
> **chrisinspace said:**
> Install Compiz, then open the CompizConfig Settings Manager.  In the 'Filter' field, type "Window Decoration", then click the 'Window Decoration' icon in the right pane.  Look for the 'Command' field and type:

```
emerald --replace
```Restart the X server and you should be good to go.

Thanks for the reply.

For those really new to Ubuntu (karmic koala) like me.  Compiz is already installed.  But the compiz config settings manager is not.  So you have to download it.

I used:
> sudo apt-get install compizconfig-settings-manager

Then follow chrisinspace's directions after that.

Cheers

---

