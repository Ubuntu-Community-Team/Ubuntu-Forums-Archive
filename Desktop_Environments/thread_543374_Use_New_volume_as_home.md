---
title: "Use New volume as /home ?"
date: 2007-09-05
forum: Desktop Environments
---

### Post by gtdaqua on 2007-09-05
I have a question.

I installed Kubuntu on a 4.6GB partition and have 2GB as swap on a different partition.

I freed up my other 13GB NTFS drive and formatted as an extended partition using gparted and mounted using 'fstab'. Its an Ext3 volume. It is listed as /dev/sda5. 

I was not able to write to it and did 'chmod 777 /dev/sda5' and got it as writable.

Now I want this new 13GB drive to serve as my /home. How do I do it? I store a lot of things on my desktop and I dont want use my 4.6GB partition (which is the default "/" and /home)

Because I want to access it, I have to navigate to 'media' and then select 'sda5'. I am sure there is a simpler way.

---

### Post by banewman on 2007-09-05
I found this to be really helpful - [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by gtdaqua on 2007-09-05
thank you. 

the link says i must move the /home data. What if I dont have any data on my /home (it is empty because this is a new installation)? Can I just do 

```

sudo mount /dev/sda5 /home

```

and make changes accordingly in the 'fstab' entry? Will this simply work?

---

### Post by banewman on 2007-09-05
Yep. It is even easier for you then most because of it being a new install. With no data to move just go to the next step. :)

---

### Post by gtdaqua on 2007-09-05
ok thanks! Its encouraging!

Let me try this today and shall let you know tomorrow. This setting is for my home computer.

---

### Post by scrooge_74 on 2007-09-05
This can also help

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by gtdaqua on 2007-09-06
I did it successfully.

All I had to do was add the appropriate entry in the /etc/fstab file and rebooted the machine. The entry in fstab file ('sda5' is my new /home)

```

/dev/sda5 /home ext3 nodev,nosuid 0 2

```

But write access was disabled and couldnt see the files already there! So i opened terminal - changed to root user and did 
```

chmod 777 /dev/sda5

```

that's it! my existing files in that volume showed up along with 'Desktop' folder and had write access to it. 

Thanks all.

---

### Post by banewman on 2007-09-07
Well done! :lolflag:

---

