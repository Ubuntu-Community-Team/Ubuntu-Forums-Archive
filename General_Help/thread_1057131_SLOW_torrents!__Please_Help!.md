---
title: "SLOW torrents!  Please Help!"
date: 2009-02-01
forum: General Help
---

### Post by M_Portiss on 2009-02-01
Hey guys.  I have searched for a suitable answer for this, but I have not found one.

This is my issue.  I have recently switched over to 8.10 after dual booting for about 6 months with XP.  While on XP I had used uTorrent to get my daily feed of Opie and Anthony.  When I would download it using XP and uTorrent, I would get around 500-600kbs down.  Now, using kTorrent -or- Transmission, I do not see over 140kbs.  Actually, more times than not, I am only seeing 5-10kbs.  I have a 10mbps connection, so there should be no issues!  

The other thing that I find odd is that I am connected to 45-50 seeders, and I am still only getting these speeds..

I have used this command to ensure the port was open correctly:
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

I KNOW my issue is not throttling.  Please do not suggest this.  I am not behind a router.  And my ports show as being free and clear.

PLEASE HELP ME!!  :)

Thanks
Matt

---

### Post by cb951303 on 2009-02-01
that command opens the port for firewall. but you should also do forwarding from router settings. the reason its working with utorrent but not with transmission or ktorrent may be the difference between automatic port forwarding features such as upnp.

---

### Post by M_Portiss on 2009-02-01
> **cb951303 said:**
> that command opens the port for firewall. but you should also do forwarding from router settings. the reason its working with utorrent but not with transmission or ktorrent may be the difference between automatic port forwarding features such as upnp.

Thanks for the quick answer.  

Are there linux-based torrent progs that do automatically forward ports?

I have considered running uTorrent under wine, but that seems like a last-resort answer.

Thanks again

---

### Post by skyshark88 on 2009-02-01
Dude, 

    Deluge is best for ubuntu and all I do is set desktop to DMZ in router if I use one ......No problems wicked fast..

    I download about 50 to 80 gigs a month...

---

### Post by M_Portiss on 2009-02-01
Thanks for the info.  Is Deluge the prog that used to be Azereus (sp.)?  I remember years ago I used to use Azureus.  I was not really a fan of it then.  I'll give it a go.

anyone have any other info?

Thanks again

---

### Post by cb951303 on 2009-02-01
no relation with azureus. it's called vuze now.

---

### Post by hajbal92 on 2009-02-01
> **M_Portiss said:**
> Hey guys.  I have searched for a suitable answer for this, but I have not found one.

This is my issue.  I have recently switched over to 8.10 after dual booting for about 6 months with XP.  While on XP I had used uTorrent to get my daily feed of Opie and Anthony.  When I would download it using XP and uTorrent, I would get around 500-600kbs down.  Now, using kTorrent -or- Transmission, I do not see over 140kbs.  Actually, more times than not, I am only seeing 5-10kbs.  I have a 10mbps connection, so there should be no issues!  

The other thing that I find odd is that I am connected to 45-50 seeders, and I am still only getting these speeds..

I have used this command to ensure the port was open correctly:
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

I KNOW my issue is not throttling.  Please do not suggest this.  I am not behind a router.  And my ports show as being free and clear.

PLEASE HELP ME!!  :)

Thanks
Matt

I had the same problem, and I've downloaded Azureus... With azureus everithing is fine\\:D/
You can still donload azureus with  apt-get

---

### Post by M_Portiss on 2009-02-01
Thanks for the help, guys.  I have since downloaded Deluge, and my speeds are almost back to where they were.  Where I use to get 700-800kbs, and I now getting 600-700kbs.  This is satisfactory IMO.

Thanks!

**edit**  As a forum owner, I truly appreciate the quick and professional matter this question was resolved.  I am new to this community, but I can already see it is a very good and informative community!

Best Regards! 
/edit

---

