---
title: "Home LAN is not recognized"
date: 2009-04-22
forum: General Help
---

### Post by user1397 on 2009-04-22
I have 8.10 installed on my desktop, which is connected via ethernet to our wireless router.  For some reason, Ubuntu can't read my network when I go to Places -> Network -> Windows Network.  Instead it gives me this message: 'Unable to mount location - Failed to retrieve share list from server'

My windows partition reads the network fine, it's just Ubuntu not doing its job

---

### Post by Iowan on 2009-04-22
I presume there's an implicit question in there...
You have shared files on a Windows machine you can't see?

---

### Post by DGortze380 on 2009-04-22
> **ubuntuman001 said:**
> I have 8.10 installed on my desktop, which is connected via ethernet to our wireless router.  For some reason, Ubuntu can't read my network when I go to Places -> Network -> Windows Network.  Instead it gives me this message: 'Unable to mount location - Failed to retrieve share list from server'

My windows partition reads the network fine, it's just Ubuntu not doing its job

You're looking for SAMBA. Allows you to access Windows Shares on Linux.

---

### Post by Slim Odds on 2009-04-22
> **Iowan said:**
> I presume there's an implicit question in there...
You have shared files on a Windows machine you can't see?


Yah, the term "Home LAN" is actually pretty vague.

---

### Post by user1397 on 2009-04-23
Yup sorry, I am trying to access other windows computers considering it does see my windows network but it cannot access it for some reason.

Another important note I forgot to mention is that I used to be able to do this with 0 configuration before in previous ubuntu releases...only Intrepid does this to me.

But, I am upgrading to Jaunty right now, so I'll post after it is done to see if anything has changed.

---

### Post by paradigm2 on 2009-04-23
> **ubuntuman001 said:**
> Yup sorry, I am trying to access other windows computers considering it does see my windows network but it cannot access it for some reason.

Another important note I forgot to mention is that I used to be able to do this with 0 configuration before in previous ubuntu releases...only Intrepid does this to me.

But, I am upgrading to Jaunty right now, so I'll post after it is done to see if anything has changed.

I believe it does install the samba client by default, but not the server.  Might it be a workgroup name issue?  Or perhaps a problem with the username/password combination.

When you go to Places -> Network, if it doesn't work, try //IP.ADDRESS.OF.WINDOWS.MACHINE (actually it might be bakslashes instead, I forget. Try both).

---

### Post by user1397 on 2009-04-26
So I upgraded to jaunty, and it still didn't work, although I figured out all I had to do was install samba manually.  Now I see my home network, but it appears that my ubuntu desktop is on a different network than my windows computers (I forgot how to change that)

---

### Post by DGortze380 on 2009-04-26
> **ubuntuman001 said:**
> So I upgraded to jaunty, and it still didn't work, although I figured out all I had to do was install samba manually.  Now I see my home network, but it appears that my ubuntu desktop is on a different network than my windows computers (I forgot how to change that)

Are they on the same WORKGROUP?

What is you netmask?
IP Addresses of the Machines?

---

### Post by user1397 on 2009-04-26
> **DGortze380 said:**
> Are they on the same WORKGROUP?

What is you netmask?
IP Addresses of the Machines?
No, that's what I meant, they are not on the same workgroup.  netmask and ip addresses shouldn't matter...I just want to join the same workgroup, I think it has to do with samba settings but I can't remember exactly.  It used to be that ubuntu would install on my desktop with samba pre-installed and I would immediately be in the same workgroup as my other computers in my LAN, but oh well, things change :(

---

### Post by DGortze380 on 2009-04-26
> **ubuntuman001 said:**
> No, that's what I meant, they are not on the same workgroup.  netmask and ip addresses shouldn't matter...

Ok, if you're so sure you know the problem, good luck, go find the answer.

You said they aren't on the same network. Thats caused by 1 of 2 reasons. They are on different Workgroups, and/or they are on different subnets... 

and fyi, the subnet does matter, if the physical machines are on separate networks, the workgroup doesn't matter, you won't be able to talk without a domain controller.

---

### Post by user1397 on 2009-04-29
well all's good in the end, I just had to change my workgroup in my samba conf file.

---

