---
title: "[SOLVED] Sudo: unable to resolve hostname on Mini 9"
date: 2008-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by employeeno5 on 2008-11-22
Hi there.

I've got a Dell Mini 9, and it's pretty great despite a few kinks. So the custom install of 8.04 it comes with I noticed is doing something odd.

Any time I use sudo for root privileges, before it asks me for my password it outputs "sudo: unable to resolve host <myhostname>"

Obviously, <myhostname> is listed as my machine's actual hostname. It then does in fact ask for the password and appears to proceed as usual. I've never seen this before though and I'm hoping it won't cause any problems and am wondering if it's normal or can be fixed.

Thanks so much for any help!

---

### Post by palin_linux on 2008-11-22
Some thing is wrong with your hosts file. It not anything big, open a termial window and type *cat /etc/hosts* and past it here.

mine looks like this:

127.0.0.1	localhost
127.0.1.1	Jcook

---

### Post by ITAndrew on 2008-11-22
You can make a temporary change to your hostname by typing:

hostname 'new hostname'  Without single quotes.

You can make this change permanent by editing your /etc/hostname file.

Mine looks like:

EVILDEEDS

EVILDEEDS being my hostname. This is just a one liner file with your hostname. Reboot, and should be good to go.

Just as an FYI for your /etc/hosts file, this is like a permanent DNS pointer. I.g you can add to your hosts file

192.168.0.152 BLACKBOX

This means that instead of reaching out to your DNS server, your PC knows BLACKBOXs static location is at 192.168.0.152. As the poster above me stated, you want to make sure your PC resolves your hostname to your "real" host.

---

### Post by employeeno5 on 2008-11-22
> Some thing is wrong with your hosts file. It not anything big, open a termial window and type cat /etc/hosts and past it here.

Sweet. No need. Just putting me hip to that file solved it for me.

I had changed my hostname from the original by altering /etc/hostname. However, I did not know about /etc/hosts.

When I checked it out to paste it here, it still had the old host name. After updating that as well, I get no more problems "resolving host".

Thanks so much for the help to both of you! Fastest, easiest fix I've ever had here!

Cheers!

---

### Post by zmjjmz on 2008-11-23
I've had a similar problem on another computer, and I think it was because my hostname has a space.

---

