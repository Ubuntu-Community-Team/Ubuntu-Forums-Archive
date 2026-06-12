---
title: "receive files over bluetooth needs settings??"
date: 2022-10-04
forum: Desktop Environments
---

### Post by dwater on 2022-10-04
Hi,

The only way I've managed to transfer files from my phone to my ubuntu laptop via bluetooth is by opening the bluetooth settings.

It seems quite obtuse to have to do this, so I'm wondering if there is some other way that I'm missing.

Anyone know?

Max.
Ubuntu 22.04.1 LTS

---

### Post by TheFu on 2022-10-04
Why use slow bluetooth when you can use wifi at 100x the speed and more security using the sftp protocol?  
Why do people do things the hard and slow way?

Or with a USB cable, there are a number of pretty connection tools that do more than just xfer files, but allow remote control of the device, screen sharing, installations and more from a computer.  KDE Connect is one. There's a Gnome version too.

To use sftp, your laptop will run Linux and be the sftp-server.  On ubuntu, just run this command:
```
$ sudo apt install ssh fail2ban
```
That sets up the ssh client and ssh server on the system, along with a brute for fighting tool to prevent brute force password attacks.  With the ssh server, we get scp, sftp as well.  With ssh, we can also use rsync and sshfs and use the system as an encrypted SOCKS5 proxy too.  ssh is crazy powerful and really not complex.

On Android, there are a number of file managers with sftp support built in.  
* ghost commander
* Ghisler's total commander file mgr
* mosh
* Solid Explorer
* Cx File Explorer
* LYSESOFT AndFTP
* MiXplorer 

I use ghost commander from the F/LOSS loving F-droid store. I guess it may be in google's store too. Should be $0.

ssh is how Unix systems communicate.  BTW, nearly every Linux file manager supports the sftp:// URL, so you can transfer files using strong encryption between any 2 Linux systems really easy - drag-n-drop easy.  ghost commands is a 2-pane file manager. You'll figure it out. Is is a client-only, so not an ssh server. That helps with security, a bit.  Just have the Linux workstation and android device on the same subnet to do the transfers.  These days, you should see 500 Mbps transfers using ssh/scp/sftp on the same wifi LAN in a typical house.   The fastest that bluetooth can do is 1-3Mbps, which was slow for wifi in 2001. Plus, all bluetooth has terrible, terrible, security. Claims that they've fixed it are untrue.

---

### Post by dwater on 2022-10-05
The length of your reply is in itself an answer to why...it is actually easier to send a file with BT due to the capability being built in. It isn't fast, but it is easy - well, it should be.

Anyway, you don't answer the question, which is essentially, "Is it actually the intended UX to have to open the BT settings in order to receive a file?"

---

### Post by TheFu on 2022-10-05
> **dwater said:**
> The length of your reply is in itself an answer to why...it is actually easier to send a file with BT due to the capability being built in. It isn't fast, but it is easy - well, it should be.

Anyway, you don't answer the question, which is essentially, "Is it actually the intended UX to have to open the BT settings in order to receive a file?"

Sorry for being complete.  BT is such a security failure that it shouldn't be used.  But we can only bring the horse to the water. We cannot get the horse to drink.

If the two systems (Linux and android) are already on the same LAN, sftp is trivial to use. Sorry, if you misunderstood THAT part.  Most of the post was about how awesome ssh is and not just for the specific file transfers. ssh does so much more that entire books have been written about those capabilities.

BTW, you did ask, 
>  It seems quite obtuse to have to do this, so I'm wondering if there is some other way that I'm missing.
Yes. Use sftp.

---

### Post by dwater on 2022-10-05
I'm very familiar with sftp, thanks. I've been using that for many years - decades even.
I'm not looking for a different way to do the same thing. I'm after a way to use BT without opening the settings. I thought I was clear, but it seems not. Never mind then. I'll assume not.

---

