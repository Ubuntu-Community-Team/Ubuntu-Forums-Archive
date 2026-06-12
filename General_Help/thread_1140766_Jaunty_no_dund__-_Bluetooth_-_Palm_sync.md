---
title: "Jaunty no dund?  - Bluetooth - Palm sync"
date: 2009-04-27
forum: General Help
---

### Post by shane2peru on 2009-04-27
Hmm, I had my Palm Treo 650 syncing via bluetooth with Ibex, and it seems that these guides are no longer accurate. 

Guide 1:
[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

Guide 2:
[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)

Both require dund or use dund or something, and dund no longer exists in Jaunty!  

Here is what my system says:
```

sudo sh startbluetooth.sh
dund: no process killed
startbluetooth.sh: 15: dund: not found
user@sane-desktop:~/bin$ locate dund
user@sane-desktop:~/bin$ 

```

Here is the startbluetooth.sh script I got from somewhere and worked with my laptop.
[PHP]
#!/bin/bash

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -A FORWARD -i ppp0 -j ACCEPT

iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

killall -v dund

sleep 1

dund --listen --persist --msdun call treo[/PHP]

Any ideas, thoughts or help on this would be appreciated.  Thanks

Shane

---

### Post by shane2peru on 2009-05-14
Well, I seem to have the dund problem fixed.  I think I re-installed the final jaunty as there were some issues with the RC or Beta I had installed.  At any rate, it still doesn't work. :)  Dund works, and my script works, however my palm doesn't connect to the computer.  I had this working great in Intrepid, but have been through the guides a few times and nothing.  If anyone knows what has changed in Jaunty and how to get my palm back connected to my computer I would greatly appreciate the help!  I'm still looking for my sync cord since I can't seem to get bluetooth functional in Jaunty.  

Shane

---

### Post by shane2peru on 2009-05-16
I found my cable and it wouldn't work either!  Frustration was climbing.  Then it turns out that pilot-link and pilot-manager were not installed either. After installing them I'm able to sync at least via cable, will have to play with the bluetooth later.

Shane

---

### Post by ihutch on 2009-06-23
In Jaunty, bluetooth is apparently incorrectly installed such that dialup networking is disabled and can't be enabled without a hack. Because there is a major move to a new daemon, several scripts are changed and in fact the needed programs are not installed by default. Consequently past helpful discriptions are incomplete. Here is what you have to do instead.

1. Do not edit anything in /etc/default/bluetooth
2. Do edit the /etc/ppp/peers/treo file to include your information about addresses etc, per prior instructions.
3. Everything on the Palm is the same as before.
4.Obtain the bluez-compat package:  apt-get install bluez-compat
5. When bluetoothd is already going (check e.g. with ps ax) #> dund --listen -p --msdun call treo
     [here treo is the name of the file you editted or created in 2. You must be root (sudo)]
6. Test to show that this works. :D
7. Hack some script (e.g. /etc/init.d/bluetooth) to execute dund after bluetootd is started, and to kill it
    (killall dund || true) just before bluetoothd is stopped. [This is the part that's most annoying.]

The alterations to /etc/default/bluetooth are irrelevant because the current script /etc/init.d/bluetooth
pays no attention to anything like DUND=.

---

### Post by shane2peru on 2009-06-28
> **ihutch said:**
> In Jaunty, bluetooth is apparently incorrectly installed such that dialup networking is disabled and can't be enabled without a hack. Because there is a major move to a new daemon, several scripts are changed and in fact the needed programs are not installed by default. Consequently past helpful discriptions are incomplete. Here is what you have to do instead.

1. Do not edit anything in /etc/default/bluetooth
2. Do edit the /etc/ppp/peers/treo file to include your information about addresses etc, per prior instructions.
3. Everything on the Palm is the same as before.
4.Obtain the bluez-compat package:  apt-get install bluez-compat
5. When bluetoothd is already going (check e.g. with ps ax) #> dund --listen -p --msdun call treo
     [here treo is the name of the file you editted or created in 2. You must be root (sudo)]
6. Test to show that this works. :D
7. Hack some script (e.g. /etc/init.d/bluetooth) to execute dund after bluetootd is started, and to kill it
    (killall dund || true) just before bluetoothd is stopped. [This is the part that's most annoying.]

The alterations to /etc/default/bluetooth are irrelevant because the current script /etc/init.d/bluetooth
pays no attention to anything like DUND=.

Ok, I gather you know what you are talking about here.  Can you give me an example of #7.  I think I got everything but that one.  Seemed a little complex.

Shane

---

### Post by shane2peru on 2009-07-06
I was tinkering around with this again, and skipped step #7 and this seems to be working for me.  Thanks for the info!!!

Shane

---

