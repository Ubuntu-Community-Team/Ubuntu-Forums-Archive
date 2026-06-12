---
title: "Internet not working"
date: 2010-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goofynewf on 2010-08-22
I know many have asked about and I apologize in advance for repeating a topic.

Yesterday, I posted about an issue with not being about to view the desktop.   Nothing worked.  I read post after post and nothing worked.  I decided to take drastic measures and reinstalled Ubuntu.  I was using 10.4 and just reinstalled it.  

I used the USB still install.  The install worked and it seemed everything works.  However, I cannot access the my wireless network.  

I entered a few commands and they indicated there was no wireless connection.  

[B]iwconfig
[/B]lo     no wireless extensions
eth0  no wireless extensions
pan0 no wireless extensions
 
Any thoughts on what I can do to get my internet working?? I am using Dell Mini 9 and use it primarily for the internet and need to get this fixed.

Thanks.

---

### Post by jaymoolay on 2010-08-22
This is from another post but I had a similiar issue to the one you are describing when I installed Ubuntu Netbook Remix on my Mini 9. 
 
> **iponeverything said:**
> Go to:
 
System -> Administration -> Hardware Drivers 
 
 
To see if has a proprietary driver available.
 
I did this and it detected two drivers. I activated the "free" one first and then activated the proprietary driver second. After a restart, I was good to go. Good luck!

---

### Post by mörgæs on 2010-08-23
A reinstall is a good beginning. After that: Have you installed all available updates using a wired internet connection?

---

### Post by goofynewf on 2010-08-23
It worked.  I used a wired internet connection and installed updates.  Then, I installed the drivers.  I could only install the free one, not the proprietary one.

The internet is working so, not sure if I should be concerned about the proprietary one.  When I tried to activate it, I received the following error: 
SystemError: Failed to lock  /car/cache/apt/archives/lock  

What does that mean?  Is this something I really need?

---

### Post by mörgæs on 2010-08-23
Just stick to the open source version; then you will not run into problems if some day the manufacturer chooses not to support the net card.

---

