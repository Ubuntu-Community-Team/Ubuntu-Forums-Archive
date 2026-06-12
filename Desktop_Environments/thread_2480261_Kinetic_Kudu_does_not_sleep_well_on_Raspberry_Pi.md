---
title: "Kinetic Kudu does not sleep well on Raspberry Pi"
date: 2022-10-23
forum: Desktop Environments
---

### Post by jordana2 on 2022-10-23
I had to set screen blank to never in order to use Kinetic Kudu on Raspberry Pi as whenever the screen went blank it stuck on black screen regularly when I was trying to log back in. I observed that switching tty to Ctrl + Alt +F[3-6] and back resurrected the session from black. I also observed that first login happened to tty2 but if I logged out that graphical interface login became available on tty1 and login there resulted in a session on tty7. I could not make sense this mess hence I disable sleep by never blanking the screen.

Otherwise I really enjoy Kinetic - and since I realised that browser versions do not lag behind like on Raspberry Pi OS there is no way back for me anymore... Thank you for supporting Raspberry Pi!

---

### Post by grahammechanical on 2022-10-24
I have no experience of Ubuntu on the Raspberry Pi. I may be wrong, but it is my understanding that Linux loads on tty1. At some point video drivers are activated and a display manager runs and a login screen appears. I would not be surprised if the login screen is running on tty2. I do know from past experiments that the Ubuntu desktop runs on tty7. When we shutdown then Ubuntu on tty7 shuts down and the system switches to Linux on tty1 for the final shutdown code to run.

Regards

---

### Post by ActionParsnip on 2022-10-24
What desktop environment are you using here please?

---

### Post by jordana2 on 2022-10-25
Thank you both for coming back to me.

My expectation is indeed that graphical interface is running on tty7 but with latest Kinetic Kudu on Raspberry Pi using GNOME 43 this is not the case! I suspect this is behind the issue with sleep also hence I detailed.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291179&stc=1[/IMG]

---

### Post by ActionParsnip on 2022-10-25
You may want to use something lighter like LxQT or XFCE. This will use fewer resources on the Pi and leave more free for your applications

---

### Post by jordana2 on 2022-10-25
Thank you for your advise but I quite a lot enjoy GNOME for now with sleep set never. Not to mention that official image from Ubuntu for Raspberry is also GNOME ;)
I will watch some parallel threads as others seem to also struggle with sleep on Kinetic Kudu

---

### Post by ActionParsnip on 2022-10-25
If you run the below, does it help? If so, make a script to run it
```

/usr/bin/gsettings set org.gnome.desktop.session idle-delay 0
/usr/bin/xset -dpms
/usr/bin/xset s off
/usr/bin/xset s noblank

```

---

### Post by jordana2 on 2022-10-25
Thank you for the advise and apologies in advance: I know this will be confusing - it is confusing for me too :(

When I tested these commands I got some freezing coming out of sleep but not stuck on black. Switch away by Ctrl+Alt+F[3-6] worked and switching back to Ctrl+Alt+F2 worked too - got out of freeze.

After I rebooted without running these commands now I can not make it to freeze or stuck on black...

Will keep trying - probably will also reinstall just for completeness sometimes soon.

---

