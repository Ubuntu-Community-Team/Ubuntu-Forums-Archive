---
title: "user authentication from server?"
date: 2009-04-17
forum: General Help
---

### Post by senor_smile on 2009-04-17
I have been googling for a little while and haven't found a real solution.  I found some solutions for other distros that probably do that and much, much more.  But I have really grown fond of my linux servers and linux desktops.  Just to clarify, this is what I want to do:

(1) central ubuntu server to handle the central store or user names/passwords
(5) ubuntu desktops being able to be logged in by the same 3 people on all five desktops.  Because we're all paranoid, or do something silly and reinstall one of the os's every few months, this would be very helpful.  

So, can anyone point me to a general how to or the name of a server/client software pair that would be appropriate to accomplish such a seemingly easy task?

thanks,
--shaun

---

### Post by tornadof3 on 2009-04-18
OpenLDAP would appear to be what you're after. An older and less secure technology would be NIS but I wouldn't recommend this.

(forgive me if you know this) but OpenLDAP will run as a service on your ubuntu server and will maange usernames/passwords as well as other directory services (Eg central store of people's email address etc but obviously not so important with only 5 users).

Here is a great howto: [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

LDAP is a pain to set up, but once it is up and running it makes life *so* much easier and is the modern 'professional' way to do this. One thing you will need to decide is are you going to have any windows machines logging on using this? (they would need to be win xp pro or vista pro to get a domain login) in which case you will also need to look up how to configure a Samba PDC with LDAP.

---

### Post by senor_smile on 2009-04-18
Thank you very much tornadof3.  I had seen ldap tutorials, but only in reference to setting them up with samba and authenticating windows boxes.  In fact, it seemed that that's all it could authenticate(windows boxes).  I have no windows boxes.  In fact, I have persuaded all of my roommates that Ubuntu is far superior to Windows.  So, my entire house of college age guys are all running ubuntu.  

Now I have something tangible to figure out.  Having 0% experience with LDAP, would you say that walking through that page's informatin a few times would be sufficient to figure it all out in say a weekend?

---

### Post by tornadof3 on 2009-04-18
I never used that exact howto, but I'm sure within a weekend you should be OK. I used LDAP with a CentOS-based network using LDAP for authentication and NFS to share out home drives and it all worked fine. Just make sure your server has a permanent IP address, but then I guess it probably already does. I *think* it's port 389 that needs to be open on your firewall for LDAP to receive requests. Oh, and change the "bind" policy to 'soft' on your clients, otherwise you will add about 2 mins to your boot time on occasions when the server is unreachable. To do this change the line "bind_policy hard" to "bind_policy soft" and uncomment it in the /etc/libnss-ldap.conf file.

---

