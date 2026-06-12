---
title: "No window borders no virtual desktops"
date: 2006-05-05
forum: Desktop Environments
---

### Post by xcarol on 2006-05-05
I have Kubuntu 5.10 installed with multiple users login screen. Sometimes (around 50%), when I (or another user) log in, there's only one virtual desktop although I have the default four virtual desktops configured. Also, when I open any application, the application window has no border, so I cannot move, maximize, minimize and so. This issue is easily solved, only need to logout and login again and then everything is ok. 
Can anybody help me with that? Any clue where to begin to investigate?

Thanks.

---

### Post by localzuk on 2006-05-05
I have had the exact same issue. It appears to occur after running any K app with sudo. Sometimes it doesn't start working until I have ran 'sudo chown user:user /home/user/* -R' which re-owns all files in my user to me.

---

### Post by GeneralZod on 2006-05-05
Not sure what the absolute, root cause of it is, but the most immediate cause is that kwin is probably not running.

If you can open up a terminal, type

```

kwin &

```

and you should be good to go.  Logging in and out shouldn't be necessary.

[QUOTE=localzuk]I have had the exact same issue. It appears to occur after running any K app with sudo.[/QUOTE]

Always use the graphical 
```

kdesu

```

with KDE apps instead of "sudo"

---

### Post by xcarol on 2006-05-08
Thank you localzuk and GeneralZod for your contributions.

I have this problem also at the first login after boot. And also with users that have no sudo rights, so they cannot sudo. 

I have tried to run *"kwin &"* in a terminal window and it brings up borders and virtual desktops, but if I exit the terminal window, borders and desktops go away. 

So, I would like to know why *kwin* doesn't always run at login. Any idea will be appreciated.

thanks again.
regards.

---

### Post by alysson.ferrari on 2008-05-23
Same thing happens to me. At the first login after boot up, kwin is dead. If I type "kwin &" in a konsole, it comes back to life and works normally, but if then I log off and login again, I have the same problem. If I restart X with CTRL-BACKSPACE, the problem also persists. 

As far as I explored so far, the problem disappear *only* if I log off *without calling kwin*, and login again. Then everything works just fine. Quite odd, I think, this is what I noticed after several experimentations.

I have this issue in two computers running Kubuntu 8.04, one that were upgraded from a previous 7.10 installation, the other with a fresh new installation. In both computers, I use NVIDIA's proprietary drivers, but I don't think this is the source of the problem, since it happens even with the nv Xorg free driver. Also, I tried to turn off the desktop effects, and the problem persists.  So far, I have no clue of what is happening.

If you think it might help, I could include here any configuration or log files... I tried to look at the system's logs and Xorg's logs, and found nothing noticeable.

Hope someone finds the source of this behaviour!

Best regards,

Alysson Ferrari

---

