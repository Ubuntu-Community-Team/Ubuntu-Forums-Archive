---
title: "Network and Firestarter problems"
date: 2005-10-19
forum: Desktop Environments
---

### Post by nrwilk on 2005-10-19
I really need to learn to not mess with things that aren't broken.


I figured I'd run a firewall even if I didn't need to, and so I used synaptic to get firestarter last night.  This morning I started up the box and I see that the ntp sync fails during the start-up process.  When X starts, I get a dialog that tells me to enter my password to start up firestarter.  I enter the password, and firestarter does not start up.  I try to open firefox to see if my network connection is up, and it isn't.  I go to network settings and my eth1 port is disabled, so I highlight it and hit enable, but it flashes enabled for half a second and goes back to being diabled, and the enable button is grayed-out.  I removed firestarter with synaptic, and rebooted, but I still get a dialog to start firestarter.  I type in my password.  I try to enable the eth1 device again.  reboot.  still no network connection.

What can I do about this?  How can I get my connection back?  It will be hard for me to post any log, if it is needed because (of course) the box won't connect, and I'm using my other machine.

Thanks for any help!

---

### Post by cwaldbieser on 2005-10-19
[QUOTE=Fealos]I really need to learn to not mess with things that aren't broken.


I figured I'd run a firewall even if I didn't need to, and so I used synaptic to get firestarter last night.  This morning I started up the box and I see that the ntp sync fails during the start-up process.  When X starts, I get a dialog that tells me to enter my password to start up firestarter.  I enter the password, and firestarter does not start up.  I try to open firefox to see if my network connection is up, and it isn't.  I go to network settings and my eth1 port is disabled, so I highlight it and hit enable, but it flashes enabled for half a second and goes back to being diabled, and the enable button is grayed-out.  I removed firestarter with synaptic, and rebooted, but I still get a dialog to start firestarter.  I type in my password.  I try to enable the eth1 device again.  reboot.  still no network connection.

What can I do about this?  How can I get my connection back?  It will be hard for me to post any log, if it is needed because (of course) the box won't connect, and I'm using my other machine.

Thanks for any help![/QUOTE]

Well, since firestarter is just a GUI front-end for the system firewall, you should be able to disable the firewall with the following command:
```

$ sudo iptables -F

```
Then you should be able to use synaptic of apt-get to reinstall/reconfigure firestarter if you need to.

You also might want to try running the firestarter GUI from the terminal to see if it spits out any errors:
```

$ sudo firestarter

```

You can also use the "dmesg" command to look at the system log and see if there is any firewall-related message in there.

---

### Post by nrwilk on 2005-10-20
```
sudo iptables -F
```didn't work.  Still cannot connect to the internet.  I can't enable eth1 at all.  I guess I'll just reinstall tomorrow.  sucky.

Thanks for trying, cwaldbieser!

---

