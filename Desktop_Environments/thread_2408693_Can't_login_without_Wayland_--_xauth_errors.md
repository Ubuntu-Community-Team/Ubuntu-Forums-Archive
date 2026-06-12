---
title: "Can't login without Wayland -- xauth errors"
date: 2018-12-21
forum: Desktop Environments
---

### Post by pixbuf on 2018-12-21
Never used Ubuntu before but have been using Linux for 22 years. I just installed 18.04 LTS. I prefer WindowMaker so I installed it but when I select it from the settings gear on the gdm3 login screen it fails, with messages like this:

[FONT=courier new]Dec 21 10:22:05 xxxx /usr/lib/WindowMaker/wmaker[1638]: (real_main(main.c:763)): fatal: could not open display ":0"[/FONT][FONT=courier new]Dec 21 10:22:05 xxxx /usr/lib/gdm3/gdm-x-session[1529]: Invalid MIT-MAGIC-COOKIE-1 key/usr/lib/WindowMaker/wmaker(real_main(main.c:763)): fatal: could not open display ":0"[/FONT]

I tried [FONT=courier new]xhost + [FONT=arial]but that didn't help.

Then I noticed that the login sessions possible were Ubuntu, Ubuntu on Wayland, and WindowMaker. When I selected plain Ubuntu (without on Wayland), it failed and I got similar errors:
[/FONT][/FONT][FONT=courier new]Dec 21 12:58:26 xxxx gnome-session[19698]: Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused[/FONT]
[FONT=courier new]Dec 21 12:58:26 xxxx gnome-session-c[19772]: cannot open display: :0[/FONT]
[FONT=courier new]Dec 21 12:58:26 xxxx gnome-session[19698]: Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused[/FONT]
[FONT=courier new]Dec 21 12:58:26 xxxx gnome-session-c[19773]: cannot open display: :0[/FONT]
[FONT=courier new]Dec 21 12:58:26 xxxx gnome-session[19698]: gnome-session-binary[19698]: WARNING: software acceleration check failed: Child process exited with code 1[/FONT]
[FONT=courier new]Dec 21 12:58:26 xxxx gnome-session[19698]: gnome-session-binary[19698]: CRITICAL: We failed, but the fail whale is dead. Sorry....[/FONT]

I also tried uncommenting the line in /etc/gdm3/custom.conf [FONT=courier new]#WaylandEnable=false [FONT=arial]but that just prevented me from logging in at all. 

Any help will be appreciated.[/FONT][/FONT]

---

### Post by pixbuf on 2018-12-24
I figured it out. After I installed Ubuntu, I restored my previous user directory from backup. There must be something in there that is screwing things up, because when I log in as a completely new user it works fine. Now I just have to find out what the problem directory is.

---

