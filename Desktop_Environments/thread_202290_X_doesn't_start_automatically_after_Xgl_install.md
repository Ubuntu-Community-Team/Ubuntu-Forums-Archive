---
title: "X doesn't start automatically after Xgl install"
date: 2006-06-23
forum: Desktop Environments
---

### Post by knn on 2006-06-23
I finally managed to get Xgl and compiz to work, using the howtos here. There is still one minor problem: X doesn't start on bootup, Usplash finishes, then I have to press Ctrl-Alt-F1, log in and type sudo gdm. Everything else works fine. I modified /etc/gdm/gdm.conf-custom like the howtos said (I have an Nvidia card, so 0=Xgl should work):
```
[servers]
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv 
flexible=true

```

I've tried aptitude reinstall xserver-xorg, then xserver-xgl, then gdm, but it didn't help.
Both gdm and kdm are supposed to start at runlevels 2, 3, 4 and 5. However, neither one starts at all, because kdm should display "not starting kdm it's not the default window manager"

Edit: Disabling Usplash fixed the problem, but I wouldn't like to keep usplash disabled. Has anyone else had this problem?

Edit2: Nevermind I figured it out. I borked my usplash installation while experimenting with fbsplash, and it's missing /etc/init.d/usplash. The script which starts gdm kills usplash using this file.
```
# if usplash is runing, make sure to stop it now, yes "start" kills it.
	        if pidof usplash > /dev/null; then
			/etc/init.d/usplash start
		fi
```

I have no clue why several reinstalls of usplash didn't install this file, but reinstalling it manually helped

---

