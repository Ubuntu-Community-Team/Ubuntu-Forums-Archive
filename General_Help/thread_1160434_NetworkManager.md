---
title: "NetworkManager"
date: 2009-05-15
forum: General Help
---

### Post by reggler on 2009-05-15
Hi There,

I got a shell script that analyzes if a ping google.com is returning any succesful results, if too many tries failed, I want to restart my network connections. To do that I do a 'killall NetworkManager; sleep 5; NetworkManager' which should start a new instance of NetworkManager 5 seconds after its been killed. The kill seems to work succesfully but It doesn't get restarted. When I type 'NetworkManager' on a shell manually it starts it perfectly back up - any ideas what may be my problem?

Thanks,
Ron

---

### Post by soro2005 on 2009-05-15
Try
```
killall NetworkManager && sleep 5 && NetworkManager
```

---

### Post by reggler on 2009-05-15
> **soro2005 said:**
> Try
```
killall NetworkManager && sleep 5 && NetworkManager
```

Nope doing the same :(, my script looks like this:
```
#!/bin/bash
ping -c 10 192.168.1.1 | grep % > /root/result
awk '{if ($4 <= 5 ) {print system("killall NetworkManager && sleep 5 && NetworkManager")}}' /root/result
```

some one may have a better idea - I decided to ping the gateway instead of google as the reponse count varies too much with google...

Any clues, ideas, suggestions?

Thanks!

---

### Post by hexanol on 2009-05-15
How about
```
sudo /etc/init.d/NetworkManager restart
```

And I'm not sure to understand how restarting NetworkManager can help your connection...

---

### Post by reggler on 2009-05-15
> **hexanol said:**
> How about
```
sudo /etc/init.d/NetworkManager restart
```

And I'm not sure to understand how restarting NetworkManager can help your connection...

That unfortunately doesn't help, neither does a stop/start because the NetworkManager actually doeesn't disconnect from the network - i need something to re-establish my wifi connectivity...

---

### Post by michy99 on 2009-05-15
This works for me:

```
sudo /etc/init.d/networking restart
```

---

### Post by reggler on 2009-05-15
> **michy99 said:**
> This works for me:

```
sudo /etc/init.d/networking restart
```

Really? Well a restart doesn't re-establish...and then on stop i'm getting this:```
/etc/init.d/networking stop
 * not deconfiguring network interfaces: network file systems still mounted.

```

---

### Post by hexanol on 2009-05-15
You could also try to communicate with the NetworkManager process via it's dbus API. The only problem is, I know it exist, I just don't know where you can find the correct information about it (I guess the best source of information would be the source code). Also, since I have a low experience with dbus, I won't be able to help you more.

EDIT: oh well, guess it wasn't that hard to find. [http://projects.gnome.org/NetworkManager/developers/spec.html](http://projects.gnome.org/NetworkManager/developers/spec.html)

---

### Post by reggler on 2009-05-15
> **hexanol said:**
> You could also try to communicate with the NetworkManager process via it's dbus API. The only problem is, I know it exist, I just don't know where you can find the correct information about it (I guess the best source of information would be the source code). Also, since I have a low experience with dbus, I won't be able to help you more.

EDIT: oh well, guess it wasn't that hard to find. [http://projects.gnome.org/NetworkManager/developers/spec.html](http://projects.gnome.org/NetworkManager/developers/spec.html)

Well but I'm sure this should with just bash work - don't you think?

---

### Post by hexanol on 2009-05-16
Well, you can use the "dbus-send" command to send message. That means you don't have to write any special application and you can do it from a bash session. But then... since my experience with dbus is really small... can't help you more.

---

### Post by reggler on 2009-05-16
> **hexanol said:**
> Well, you can use the "dbus-send" command to send message. That means you don't have to write any special application and you can do it from a bash session. But then... since my experience with dbus is really small... can't help you more.

I found that application cnetworkmanager that's offering all the comands i need on the shell! This seems to resolve my issue! :)

---

### Post by lswb on 2009-05-16
What version of ubuntu (8.04, 8.10, etc) are you using? There are some differences in the startup scripts for NM between these versions.

---

### Post by reggler on 2009-05-16
> **lswb said:**
> what version of ubuntu (8.04, 8.10, etc) are you using? There are some differences in the startup scripts for nm between these versions.

9.04

---

