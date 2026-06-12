---
title: "Problem with nameserver"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Albi on 2006-06-22
Hi,
Every time I boot up Ubuntu I have to fix the nameservers by editing resolv.conf, as they are always incorrectly put as 192.168.1.1.
Is there any way to stop the nameservers to stop automatically updating like this?

---

### Post by jvl on 2006-06-23
edit /etc/dhcp3/dhclient.conf and remove "domain-name-servers" from the following line:

request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, netbios-name-servers,netbios-scope;

so it looks like this:

request subnet-mask, broadcast-address, time-offset, routers, domain-name, host-name, netbios-name-servers, netbios-scope;

---

### Post by from_beyond on 2006-07-04
I believe that solving the problem of the resolv.conf is that a command needs to be issued to that file so it will not be overwritten.
Changing the dhclient.conf does not work for me.
Doe anybody know that unix command to stop a file from being overwritten?

---

### Post by from_beyond on 2006-07-04
"edit /etc/dhcp3/dhclient.conf and remove "domain-name-servers" from the following line:"

Does not work.

---

### Post by pksings on 2006-07-04
Are you in control of the dhcp server?  It's supplying the wrong nameserver address.. That should be fixed, and then you will automatically have the correct one..

---

### Post by from_beyond on 2006-07-05
I'm running a wireless router (DCHP server) which has the correct dns addresses. I don't know what you mean by being in control?
I tried (after creating a root account) the command "chattr +i /etc/resolv.conf" after manually editing the file with the dns numbers. I wanted to make the file immutable  . When I rebooted the DNS addresses dissappeared! I believe "chattr +i" is correct and thus resolv.conf should be immutable , but it is not.
Would like to know what to do to have control of my router.
Thanks

---

### Post by from_beyond on 2006-07-05
Got it working with "sudo chattr +i /etc/resolv.conf" . I shut down rather than restarted the system and now the DNS stays. Working good! I have to check the logs know to see if there are any errors or complaints, but this works.I don't think one should have to input nameserver addresses once a router is connected but maybe there is a good reason for it.

---

### Post by handy on 2006-09-16
> **from_beyond said:**
> Got it working with "sudo chattr +i /etc/resolv.conf" . I shut down rather than restarted the system and now the DNS stays. Working good! I have to check the logs know to see if there are any errors or complaints, but this works.I don't think one should have to input nameserver addresses once a router is connected but maybe there is a good reason for it.

In my situation, my ISP does change the DNS addresses quite often.  So, I will have to edit the /etc/resolv.conf file.

So, the following undoes it:

**sudo chattr -i /etc/resolv.conf**

Editing the /etc/resolv.conf every week or 2 is really not such a drag.

---

### Post by ofer_w on 2006-09-21
> **handy said:**
> In my situation, my ISP does change the DNS addresses quite often.  So, I will have to edit the /etc/resolv.conf file.

So, the following undoes it:

**sudo chattr -i /etc/resolv.conf**

Editing the /etc/resolv.conf every week or 2 is really not such a drag.


I also have the same problem also after editing this file
gksudo gedit /etc/resolv.conf

and updating the dns information 

after few mintues of work the dns is deleting and I need to update it again
and not sure what to do? anybody can help?  thanks

---

### Post by handy on 2006-09-26
> **ofer_w said:**
> I also have the same problem also after editing this file
gksudo gedit /etc/resolv.conf

and updating the dns information 

after few mintues of work the dns is deleting and I need to update it again
and not sure what to do? anybody can help?  thanks

Have a look at **post #6** in this thread?  Using the following:

**sudo chattr +i /etc/resolv.conf**

Seems to have worked for me...

---

