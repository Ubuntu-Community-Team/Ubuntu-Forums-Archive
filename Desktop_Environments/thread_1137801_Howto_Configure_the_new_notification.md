---
title: "Howto Configure the new notification ?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by Wanas on 2009-04-25
I want to configure the new ubuntu notification that it can appear while playing a video, because while am playing a video via totem pidgin notification dont appear so when my friends go online or offline I cant see them.
Can any body help me to configure this ?
Can I change the place that the notification appear ?
Is it easy to change the notification to the old one ?

---

### Post by DevSherif on 2009-04-28
I you are talking about the new ubuntu 9 black top right notificaiton....

I think that you can install it from synaptic by searching for "Notify-osd" and install it.

Hope it is the thing that you need, also i hope that my reply is helpgul.

Try and feedback.......

BR,
Sherif

---

### Post by Wanas on 2009-04-28
1st thank for trying to help
2nd I think your talking about something els far from my questions :(

---

### Post by kpkeerthi on 2009-04-28
> **Wanas said:**
> 
Is it easy to change the notification to the old one ?
Yes. You just have to uninstall **notify-osd** package.
```
sudo apt-get purge notify-osd
```

---

### Post by Wanas on 2009-04-28
> **kpkeerthi said:**
> Yes. You just have to uninstall **notify-osd** package.
```
sudo apt-get purge notify-osd
```

I have tried this command, it removed the new one and it didnt replace it with the old one, now I dont have any notification working :(
I have tried to restart after but the same results :(

---

### Post by kpkeerthi on 2009-04-28
> **Wanas said:**
> I have tried this command, it removed the new one and it didnt replace it with the old one, now I dont have any notification working :(
I have tried to restart after but the same results :(

My bad. You need the old notification system.
```
sudo apt-get install notification-daemon
```
I suggest you reboot your PC after installing the package.

---

### Post by Wanas on 2009-04-28
Thanks works great ;)
I love the old notification than the new one 
I think the new one is just in the alpha :D, it need so much updates :(

---

