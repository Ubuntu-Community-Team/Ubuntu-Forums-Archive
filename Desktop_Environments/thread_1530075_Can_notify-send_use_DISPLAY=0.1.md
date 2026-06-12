---
title: "Can notify-send use DISPLAY=:0.1 ?"
date: 2010-07-13
forum: Desktop Environments
---

### Post by Sander.H on 2010-07-13
I use Ubuntu 9.10 for one of my MythTV frontends, which have a plasma screen connected using VGA as display :0.0 and a projector connected using HDMI as display :0.1.
 
How do I send notifications using notify-send to the projector? The following doesn't work, i.e. it still displays on the plasma screen:
```
DISPLAY=:0.1 ; notify-send "This will still display on :0.0"
```

---

### Post by stinkeye on 2010-07-13
Try
```
export DISPLAY=":0.1"; notify-send "This will still display on :0.1"
```

---

### Post by prshah on 2010-07-13
> **Sander.H said:**
> 
```
DISPLAY=:0.1 ; notify-send "This will still display on :0.0"
```

If you put a semicolon, the environment variable will have no effect on the following command; Either do it the "export" way, or remove the semicolon, eg:
```
DISPLAY=:0.1 notify-send "This will still display on :0.0"
```

---

### Post by Sander.H on 2010-07-29
Thanks for both your reply,
 
which unfortunately does not work.
 
Prshah, I know how you normally have to export your variables, but apparently (some or all?) programs supporting the DISPLAY variable are able to read the parent environment, as you can verify with
 
```
DISPLAY=:0.0 ; gedit
```
which opens gedit on display :0.0.
 
```
DISPLAY=:0.9 ; gedit
```
which displays the error message:
```
Gtk-WARNING **: cannot open display: :0.9
```
 
I have given up using notify-send and instead I'm now using gxmessage which support multiple displays.

---

