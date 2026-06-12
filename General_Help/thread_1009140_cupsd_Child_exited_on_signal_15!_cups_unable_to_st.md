---
title: "cupsd: Child exited on signal 15! cups: unable to start scheduler."
date: 2008-12-12
forum: General Help
---

### Post by slambrick on 2008-12-12
Help. No cups server even though it's installed - also removed reinstalled - regressed nothing. Print menus are missing. no longer there.
Cups service not there.
I have no idea what to do next. or where to look for clues as to why.
Please help!!

---

### Post by slambrick on 2008-12-14
C'mon guys please refer me to someone with some idea. I have none. I have just recompiled Cups 1.4b1 but with no success still getting:
cupsd: Child exited on signal 15!
cups: unable to restart scheduler.
Still don't know how to get the menus back.
Surely I don't have to rebuild the entire OS to fix this????

---

### Post by slambrick on 2008-12-16
[SOLVED] Thanks to Michael over at the Cups forum for giving me a clue. I then found that the conf file for cups was completely empty. this was easily corrected by adding the contents of a slightly older conf file and voila! my cups scheduler started.
I must comment on the lack of responses here. It would have been a bit easier if some-one had at least made a suggestion as to the error logs to look at and pointed me to the cupsd.conf file that was the cause of the problem.

---

### Post by sancho panza on 2008-12-16
I'm having the same error message, which is stopping me from adding a pdf printer to the system. Could you provide more details as to how you fixed it?

Thanks,

---

### Post by lenooh on 2009-05-21
> **sancho panza said:**
> I'm having the same error message, which is stopping me from adding a pdf printer to the system. Could you provide more details as to how you fixed it?

Thanks,
if you have an old conf file that worked, this should make your printer work again:
```
sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
```

---

### Post by studiogrynn on 2009-09-15
Thanks for the assist!

---

### Post by chaanakya_chiraag on 2009-10-04
Thank you so much!!!  I couldn't figure out what was going on!  Apparently, my root partition became full **while** I was printing something for school, and my whole system started going bonkers!  If there is one thing you should **never** do while using Ubuntu, it's running it with no space left on the root partition :D

---

### Post by lnxguit on 2009-10-06
note that it's cupsd.conf.O (capital "O", not zero)

---

### Post by khughitt on 2009-10-09
Hey thanks for the solution!

Any idea what caused the file to be blanked?

---

### Post by ponchomx on 2009-12-09
Thank's

A mi tambien me sirvio

Salu2

---

### Post by gigahz on 2010-02-17
> **chaanakya_chiraag said:**
> If there is one thing you should **never** do while using Ubuntu, it's running it with no space left on the root partition :D

A quick "fix" for full root is to "sudo apt-get clean" or at least "sudo apt-get autoclean".

That will take out unused, cached .deb files from your root. In my case it took off 2.2GB of stuff just sitting there.

As always, read the manual before running any command you see on the net, especially "sudo <something>" :)

---

### Post by sasagundul on 2010-06-01
maybe you could try to reconfigure the cups package.
try :

sudo dpkg-reconfigure cups

this worked for me :P

---

### Post by snowveil on 2010-08-19
> **sasagundul said:**
> maybe you could try to reconfigure the cups package.
try :

sudo dpkg-reconfigure cups

this worked for me :P

worked great for me as well!  Thanks :)

---

### Post by zohar995 on 2011-01-10
I don't know if this is the same problem. Mine is that the computer stopped the cups service and since my version of Ubuntu doesn't have a service menu anymore there is no way I can start the cups service. I tried many things and have now tried this conf thing with no result:
sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
mv: no se puede efectuar «stat» sobre «/etc/cups/cupsd.conf.O»: No existe el archivo o directorio

If you have any suggestions I would love to hear them

---

### Post by Luke490 on 2011-06-06
> **lenooh said:**
> if you have an old conf file that worked, this should make your printer work again:
```
sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
```

You might also try:
```
sudo mv /etc/cups/cupsd.conf.default /etc/cups/cupsd.conf
```[/QUOTE]
or just type an "ls" of the cups folder and see what other config backups might be in.

---

