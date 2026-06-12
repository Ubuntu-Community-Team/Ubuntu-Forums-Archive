---
title: "How to restart X-server? I try everything..."
date: 2010-03-03
forum: Desktop Environments
---

### Post by felix-leg on 2010-03-03
I've a work which involves a lot of editing **xorg.conf**, so I wish to be able to apply my confs as quick as possible. But I can't restart X in my ubuntu :(. I've try:[I]
[LIST]
[*] init 3
[*] telinit 3
[*] gdm restart
[*] killall gdm
[*] Ctrl+Alt+Bks
[/LIST]
[/I]Of course everything under root ("su" command). But the server doesn't react at all T_T. Terminal also doesn't show any messages (like if a command was ran properly)

---

### Post by karthick87 on 2010-03-03
Try..

```
/etc/init.d/gdm restart
```

---

### Post by felix-leg on 2010-03-03
This is exactly the 3th point on my list... :(

---

### Post by karthick87 on 2010-03-03
Log in to tty1 (ctrl+alt+F1) and then run the command.

```
/etc/init.d/gdm restart
```

---

### Post by warp99 on 2010-03-03
In keyboard setup you can enable the ctrl-alt-backspace command to restart x-server. Go to System > Preferences > Keyboard. Click on "Layouts" then at the bottom of the dialog click on "Layout Options". Scroll down until you see "Key sequence to kill the X server" and check the box.

Another way is to switch to a terminal with ctrl+alt+f1 then the following:

```
sudo service gdm restart && exit
```

That will restart X and close the terminal. Another method:

```
killall5 && exit
```

This will kill all programs that are running under your user id. It doesn't allow for a graceful closing of programs and cleanup so it should be avoided unless all other options fail.

---

### Post by felix-leg on 2010-03-08
It works! :D Thanks.

---

### Post by akand074 on 2010-03-08
You could also go to system > preferences > keyboard (or keyboard layout can't remember) and then go to layout and reactivate "shortcut to kill the X server" which is ctrl+alt+backspace, I find that more convenient personally.

---

