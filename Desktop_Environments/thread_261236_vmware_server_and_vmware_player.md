---
title: "vmware server and vmware player"
date: 2006-09-20
forum: Desktop Environments
---

### Post by tomslopez on 2006-09-20
Can I use vmware server and vmware player both with diferent OS's on them, like one with windows xp home and the other with mac or xp pro, and if so can they run at the same time?

---

### Post by SishGupta on 2006-09-20
Can't you just run the 2 guests in server at the same time?

You will likely need a butload of ram as you'd then be running 3 os's at the same time.

---

### Post by Zyzzyx on 2006-09-20
> **SishGupta said:**
> Can't you just run the 2 guests in server at the same time?

You will likely need a butload of ram as you'd then be running 3 os's at the same time.

That's what I've done. Had XP Pro and Vista RC1 both running through VMware Server. And while the Linux side stays responsive with just one going, with both going, all three were darn slow.  (2.2ghz AMD, 1gb RAM)

---

### Post by SishGupta on 2006-09-20
Yes, i think as a general rule of thumb, to have each system run OK you would want at least 512mb of ram per OS running.

I have 512 and I run vmware/xp in ubuntu. When i run a memory intensive app both os's slow down a bit. I am sure that if i had 1gb the os's would be a lot more responsive. For 3 os's you'll absolutely want >1gb of ram in order to use all 3 at once.

---

### Post by Dr. C on 2006-09-20
I do not think you can have VMware player and VMServer running at the same time. 

As for Vista RC 1 and XP on different VMs RAM seems to me to be the limitation. I have run both Vista (768 Meg max)  and NT4 (512 Meg max ) with reasonable responsivness.  The system is a P4 1.8 GHz with 1.5 gig of RAM and the host OS is Ubuntu Dapper.

---

### Post by odinfromvalhalla on 2006-09-20
i'm running win2k3 server (both xp home and pro are crap unless hacked with nlite) in vmware server with dappers as host for my web development. i run a 3Ghz P4 with 1Gb DDR2 @ 667Mhz and i have noticed that making my VM to use less RAM actually makes it work much much better. By defaul when created the VM it sugested me to use 384MB or RAM, which i did. and everything worked fine and smooth until i have installed and started to run Dreamweaver. Everything went to chaos at this point: both VM and host were running incredible slow. After setting the VM to use 256RAM max everything works just great :).

i run the same time in vm dreamweaver, ie7 and firefox for web preview (ff has some webdev extensions that only work on win else i would just run it in host system :P) cuteFTP.

i have tested this on several vm's running windows and for all of them seems to add a performace boost.

i guess that it is in fact better to give the host system more resources to run the vm better.

---

