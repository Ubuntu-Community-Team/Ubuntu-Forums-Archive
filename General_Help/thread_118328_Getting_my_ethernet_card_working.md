---
title: "Getting my ethernet card working"
date: 2006-01-16
forum: General Help
---

### Post by steveland? on 2006-01-16
I have Ubuntu installed on my laptop but can't get my ethernet card working

It's a Dell Latitude CPx J650GT, upgraded to 320MB RAM and 20GB HDD (originally 64MB and 10GB HDD)

I've got a Xircom PCMCIA ethernet adapter, RE-100.

When I run ifconfig it just shows lo and eth0 doesn't appear... Unknown Device > Networking Interface shows up in Device Manager but doesn't show up when running ifconfig from the terminal

I've read up on the card and know I have to use the xirc2ps_cs driver which is there in /lib/modules/2.6.12-9-386/kernel/drivers/net/pcmcia

Does anyone else have a similar setup and know how to get it to show up and be useable?

Any help is greatly appreciated

---

### Post by steveland? on 2006-01-16
Man these posts pop off the frontpage quick...

Sorry about bumping this thread up... it's fairly important I get this sorted soon.

I've an exam in real time systems on Thursday and want to get a Unix environment set up quickly so I can study some of the stuff online

---

### Post by Lambert on 2006-01-16
Try this.

Run from terminal this command.

sudo lshw -C network

You should see your ethernet driver. Look for a line configuration: should say driver= in that line. If you don't see that then try this.

sudo modprobe xirc2ps

run this to make sure module is running

lsmod | grep xir

then run lshw command again to see if driver is bound to device. If yes try to configure.

last, go to networking section of this forum. There is a sticky there on troubleshooting ethernet.

---

