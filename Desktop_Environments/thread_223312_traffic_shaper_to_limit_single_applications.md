---
title: "traffic shaper to limit single applications"
date: 2006-07-26
forum: Desktop Environments
---

### Post by F157 on 2006-07-26
hello,

i'm quite new to the world of linux and especially ubuntu, but till now everything works quite well...

at the moment there's just one question left: 
i'm searching for a tool to shape the network traffic, but everything i found is just able to limit the traffic of a network interface such as eth0... I need to limit the upload of applications, for example a ftp-uploader or p2p-program, so i can upload files and do a vnc session at the same time... 
without a traffic shaper, the vnc-session is reeeaaally slow..

---

### Post by tkiesel on 2006-07-26
Hi F157,

The ideal thing is to have an app that can limit its own traffic use. Most good p2p apps have one somewhere in their settings.  However, if there's no option like that, I'd say try trickle.

```
sudo apt-get install trickle
```

It can limit network traffic for individual applications.  The -u tag limits upload and the -d tag limits download. I usually keep my upgrades from hurting my or my wife's game performance like so:

```
sudo trickle -d 20 apt-get dist-upgrade
```

to limit apt-get to 20KB/sec speed. (Note: trickle comes AFTER sudo here.)

You just put trickle and then the -u or -d numbers you want.

To limit p2p-app to 65 KB/sec download and 55KB/sec upload, you'd:

```
trickle -d 65 -u 55 p2p-app
```

Once you have numbers that work with your setup, you can put this into the command launcher with the menu editor, and never worry about it again!

---

### Post by XomboX on 2007-02-16
Thank you for nice tip!
Please, tell me: how can I take all trickle settings back? I need to clear all my bandwith settings which I did using trickle :-(

---

