---
title: "Delay startup programs"
date: 2009-05-19
forum: General Help
---

### Post by Luffer on 2009-05-19
Is it possible to delay a program from loading so quickly on start-up? I like to have Thunderbird and Emescene open when I boot up, but currently they load so quickly that they can't access the Internet because the network connection hasn't set up.

I juts need to put a slight delay on those two applications so the network is established fully before they attempt to connect to the Internet. It's never been a problem in WinXP because it's so slow :-)

Thanks in advance!

---

### Post by lovinglinux on 2009-05-19
Add "sleep" to the command in the "Startup Application" (aka Session) . Like this:

```
sleep 30 && firefox
```

---

### Post by Luffer on 2009-05-22
Doing this didn't work, I changed the Command line is the "Startup Applications" as described above. When I restarted, the two applications I had altered never opened.

---

### Post by KhurramM on 2009-05-22
Try this:

xterm -e 'sleep 30 && firefox' 

alter 30 as required.

instead in the startup.

I hope this works. But the xterm opens and remains open will be a little annoying. U can push it to the non-used virtual screen.

Hope this helps.

---

