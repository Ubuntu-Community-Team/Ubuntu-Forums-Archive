---
title: "(startup) User's $HOME/dmrc is being Ignored....."
date: 2009-01-14
forum: General Help
---

### Post by carl99fan on 2009-01-14
Please help.
I am using Ubuntu 8.04 64 bit. on a 250gig SATA drive
I have a 8.04 32 bit that I like more on a smaller drive.

So I have decided to move back to 32 bit Ubuntu for now.
I bought a 200gig IDE drive and have installed it on the second cd/dvd rom cable. I just installed 32 bit 8.04 on it using my friends name to install it as after I am finished I will be giving him the 200gig IDE drive to run his computer.

I am trying to MOVE MY HOME FOLDER to his desktop.
I will then install 32bit Ubuntu on MY 250gig SATA drive.
I have heard from others that I can move my home directory and I will basically have everything I used to have.

My computer froze during the transfer so I decided to boot using the new install on the 200gig IDE and move them from that side, but it was only transferring at 1.2mbs and was going to take 24hrs. I canceled the file operation and now when I boot up my 64 bit 250gig SATA I get the following message:

[B]User's $HOME/dmrc is being Ignored Files should be owned by user and have 644 permissions..............
User's $HOME directory must be owned by user and not be writable by other users.[/B]
I click OK and I boot up normally.

can some help me out? have I corrupted a file? It will not let me do it using sudo nautilus

---

### Post by taurus on 2009-01-14
Assuming your login name is carl, boot into recovery mode from GRUB menu and run

```
chown -R carl:carl /home/carl
chmod -R 755 /home/carl
chmod 644 /home/carl/.dmrc
shutdown -r now
```

---

### Post by carl99fan on 2009-01-14
That worked great.
thank you.

Could you tell me?.... am I going about this all wrong?
Is there a better way to move all my files to the new install?
I wish I had an external hard drive but I don't.

---

### Post by taurus on 2009-01-14
Maybe this would give you some hints.

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

---

### Post by carl99fan on 2009-01-14
> **taurus said:**
> Maybe this would give you some hints.

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

cool.
good stuff.

---

### Post by carl99fan on 2009-01-20
I don't remember how to mark as [SOLVED]

---

