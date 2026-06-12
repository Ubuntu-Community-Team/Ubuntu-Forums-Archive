---
title: "How can I stop annoying notification popups"
date: 2016-08-12
forum: Desktop Environments
---

### Post by dealy663 on 2016-08-12
Hi

i have a relatively new computer that has a fresh install of Ubuntu 16.04. Several weeks ago I started getting all of these pop-up notifications when network events happen. So I'm constantly getting notified whenever another wifi access point goes in or out of range, when network interfaces have changed, when ip addresses have changed. This happens all the time throughout the day. I have no idea what changed and made this start happening.

Also I just don't see how there isn't some straightforward way to fix this. I've been searching all over the internet and haven't found anything.

Does anyone know how to fix this? I'd simply like to turn off all network notifications.

Thanks, Derek

---

### Post by grahammechanical on 2016-08-12
I do not get any of that and never have done. I do get notification if the connection to my WiFi access point drops out. Or I load Ubuntu and forget to switch on the router. Then I get notified that there are other WiFI access points in range. But that is as far as it goes.

Have you ever tried to access any of these WiFi access points? Are they listed as WiFi connections? We can delete connections and the Network manager will not try to establish an connection with them. 

Regards

---

### Post by dealy663 on 2016-08-12
The wifi networks show up inside of the Network configuration settings. But I've only connected to one of these networks. The rest are just the other wifi networks that happen to be nearby.

Even if I kill notify-osd, something restarts it again a few minutes later and all the notification pop-ups return.

---

### Post by #&amp;thj^% on 2016-08-12
> **dealy663 said:**
> Hi

i have a relatively new computer that has a fresh install of Ubuntu 16.04. Several weeks ago I started getting all of these pop-up notifications when network events happen. So I'm constantly getting notified whenever another wifi access point goes in or out of range, when network interfaces have changed, when ip addresses have changed. This happens all the time throughout the day. I have no idea what changed and made this start happening.

Also I just don't see how there isn't some straightforward way to fix this. I've been searching all over the internet and haven't found anything.

Does anyone know how to fix this? I'd simply like to turn off all network notifications.

Thanks, Derek

Either open dconf-editor or install it by 
```
sudo apt-get install dconf-editor
```
And after opening dconf-editor navigate to <org> <gnome> <nm-applet> .
From there it should be straight forward.

---

### Post by dealy663 on 2016-08-12
I tried using dconf-editor. It certainly looks like the options there would be able to stop all of the pop-ups but it didn't make any difference. They are still occurring. well I guess I didn't try rebooting after using the dconf-editor maybe I'll see what happens then.

---

### Post by #&amp;thj^% on 2016-08-12
You can restart nm-applet with this command from terminal:

```
killall nm-applet; nohup nm-applet &
```

or by restart network-manager service (witch will restart nm-applet):

```
sudo service network-manager restart
```

---

### Post by dealy663 on 2016-08-12
Grrr, nope that didn't work either, not did rebooting.

This is a really persistent PITA.

---

### Post by #&amp;thj^% on 2016-08-12
> **dealy663 said:**
> Grrr, nope that didn't work either, not did rebooting.

This is a really persistent PITA.

So Sorry to hear that:(...but like grahammechanical i am not seeing that on my system.
Kind Regards

---

### Post by wildmanne39 on 2016-08-12
Is it possible that your internet connection is going on and off line that is the only thing I know that would cause you to see messages like that.

---

### Post by vasa1 on 2016-08-12
> **dealy663 said:**
> ... Does anyone know how to fix this? I'd simply like to turn off all network notifications.
...
Take a look at [How to intercept (kill) only specific notifications, using dbus-monitor]("http://askubuntu.com/a/773886/"). You may need to modify stuff to suit your needs.

---

### Post by dealy663 on 2016-08-13
It doesn't seem like my internet connection is turning on and off. I'm constantly browsing the web while this is happening and don't ever see any hiccups. Is there anything I should be looking for in syslog that would indicate this?

---

