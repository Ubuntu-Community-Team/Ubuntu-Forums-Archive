---
title: "Huge dualboot problem - formatting HD"
date: 2008-12-12
forum: General Help
---

### Post by coldcut on 2008-12-12
Hi you guys

Okay here's my story. I installed Ubuntu 8.10 when it came out and created 4 partitions (/, swap, /boot and /home) which filled up my 500gb SATA-II HDD.
I was always planning on dualbooting after the christmas exams but when I tried, my XP install wouldn't load up.
I am told that the problem is the crappy XP installer and after trying many different things to install XP i have given up.

Now I just want to install XP first and then set up Ubuntu but since my XPinstaller doesn't load I cant format the whole HDD.

So my question is...How can I format the whole HDD so I can begin to dualboot?
Is the LiveCD's partition editor a possibility or can I somehow factory reset the HDD?

greetings from the land of the ice and snow,
Coldcut

---

### Post by jteb on 2008-12-12
Doesn't really sound like an *nix partitioning issue. From my experience it's quite the opposite. You install Windows without specifying some advanced options, it will take your drive, format it, (it already hijacked your MBR before you knew it, as a user-service). 

But you're not really clear. If I understand correctly, you've dedicated your entire disk to *nux, with 4 partitions?

If so, it;s no wonder the XP installer can not dedicate some space, as it can not resize *nix partitions (it can hardly resize windoze partitions). 

Which leads me to the next question .. 

Are you using LVM on your *nix installation? If so, (and if you do have enough free space) you could probably use the LVm tools to free up some space and use parted/(c)fdisk to resize your partition to make some room for Windoze and have grub chainload it?

Hope I'm understanding your question right.

Regards,
Jan

---

### Post by jteb on 2008-12-12
--

---

### Post by caljohnsmith on 2008-12-12
Actually you don't need to format the whole HDD, instead if you just delete the MBR (Master Boot Record), that will make the entire drive appear unformatted. To do that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Red"]sda[/COLOR] count=1
```
And make sure you get the correct drive if it isn't sda like above. Then the drive will appear unformatted to XP, and XP should hopefully install.

---

