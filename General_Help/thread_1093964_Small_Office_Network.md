---
title: "Small Office Network"
date: 2009-03-12
forum: General Help
---

### Post by AndyXS on 2009-03-12
I am looking to put together a new small office network. We will be using 4 desktop PCs, all running Vista Business. We were looking at getting Windows Server 2008 until someone suggested Linux. Would an Ubuntu Server do what we wanted Windows Server 2008 to do? This would be: User access, Share files, Private files for each user, Share and restricted internet, Share printers, Backup for all files.

How easy would a server be to setup for someone who is new to Linux? If we could use Ubuntu it would save us almost £510.

Thanks for your help.

---

### Post by Peter09 on 2009-03-12
Most (All?) of what you want is available out of the box, there are reasons why most servers run Linux/Unix. However you will need to expect a learning curve and some teething problems.

Edit - I would suggest that you install the 64 bit desktop edition - unless your server is highly stressed. Then you have the Gnome GUI to assist you in setup. It will not really impact performance too much.

---

### Post by AndyXS on 2009-03-12
After installing ubuntu server, what services do i need to look at?

I am told squido for the proxy server and samba for shared folders and printers.

How can we get the my documents folder in vista to be stored on the server so users files can be accessed from any pc?

---

### Post by Hobgoblin on 2009-03-12
> **AndyXS said:**
> 

How can we get the my documents folder in vista to be stored on the server so users files can be accessed from any pc?

When you have samba set up, Windows will see the shared folders just like a Windows share.  You do the rest on the Vista end....

And, I assume it's a typo but the proxy is called Squid.

---

### Post by AndyXS on 2009-03-13
After a default install of Ubuntu Server, I will go ahead and install/configure samba and squid.

I believe there were problem connecting Vista Business to linux networks. Has this Vista authentication process been fixed yet?

As adding windows users as simple as running the useradd or is there a little more to it than that? If anyone has a good tutorial could you post up the links.

Thanks

---

