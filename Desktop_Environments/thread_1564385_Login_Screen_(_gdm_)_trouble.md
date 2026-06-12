---
title: "Login Screen ( gdm ) trouble"
date: 2010-08-30
forum: Desktop Environments
---

### Post by ccc2007chaos on 2010-08-30
Hi!

I'm trying to change my login screen, where i select *username* and enter *password*. I 've read many tutorials but i can't find any solution for my problem. The problem is that in System->Administration->Login Screen the window that appears has no options to change theme or anything. Anyone knows what can i do?

Attaching the screenshot of that window.

---

### Post by sisco311 on 2010-08-30
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by ccc2007chaos on 2010-08-30
Ok! Thanks!

That worked, but how can i install a gdm theme? i tried to install by clicking the "Install" button in the window but it failed to install. Is there any solution or the version does not support the themes? I ask because i read something about it.

Thanks again!

---

### Post by sabenfox on 2010-08-30
Please take my message with a grain of salt since i am new to linux as well....
From what i've been able to read, Themes on ubuntu is /fail....
 
there are some themesthat look ok, but nothing cool like what you're probably looking for. Mind you this is on Gnome

---

### Post by ccc2007chaos on 2010-09-02
Thanks for the replies. I wonder if someone that knows more can say something more specific. Sabenfox, i think the same but nothing is clear to be trusted 100%.

So can anyone tell us in order to close this thread?

---

### Post by sisco311 on 2010-09-02
[noparse]The new GDM (>=2.28) is not compatible with the old themes. You can change the GTK theme, background, mouse cursore, etc... But not the UI of the greeter window & panel, oh well, until you manually edit the /usr/share/gdm/gdm-greeter-login-window.ui file with glade [/noparse]:).

---

### Post by ccc2007chaos on 2010-09-02
Thank you very much. I 'll try to customize it. The thread is [SOLVED] ! :D:D):P

---

