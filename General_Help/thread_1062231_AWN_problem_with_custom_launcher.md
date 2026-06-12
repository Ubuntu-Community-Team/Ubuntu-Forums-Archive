---
title: "AWN problem with custom launcher"
date: 2009-02-06
forum: General Help
---

### Post by VitaminCPP on 2009-02-06
I have added custom launcher to my AWN, one which invokes "nautilus" command. The problem is that when I start my PC, the launcher doesn't work. It responds on mouse (jumping effect), but doesn't open nautilus. However, when I restart AWN (manually close and open from Accessories), it works. So, how do I fix it so I don't need to restart AWN manually each reboot?

I have AWN, compiz and Fusion Icon autostart in Sessions.

---

### Post by Tim Sharitt on 2009-02-07
Try the command
```
nautilus --no-desktop
```

I'm not sure if it will help any, but nautilus can do some weird things when evoked with just nautilus.

---

### Post by VitaminCPP on 2009-02-07
I've tried --no-desktop, didn't help :-(

---

### Post by kawaji on 2009-02-07
> **VitaminCPP said:**
> I have AWN, compiz and Fusion Icon autostart in Sessions.

Your problem seems the same on cairo-dock.
[http://ubuntuforums.org/showthread.php?t=968168](http://ubuntuforums.org/showthread.php?t=968168)

How about the following commands ?
```
nautilus .
nautilus /
nautilus ~/  
```

---

### Post by VitaminCPP on 2009-02-07
"nautilus ." worked for me, thanks!

---

### Post by jklick on 2009-11-15
"nautilus ." also worked for me, thanks!

---

