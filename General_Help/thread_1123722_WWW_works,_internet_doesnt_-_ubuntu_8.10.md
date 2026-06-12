---
title: "WWW works, internet doesnt???? - ubuntu 8.10"
date: 2009-04-12
forum: General Help
---

### Post by cougar4u on 2009-04-12
Cheers linux community,

I am new here and have been using ubuntu 8.10 for about 6 months now. Most every problem I encounterd was solved via google, however, this one has me pulling my hair out. 

Right now, when I open firefox, my home page will load perfectly, however none of my add-ons connect (foxmarks, forecastfox, etc...). Moreover, I can go to any website from the address bar..for example google.com, however, once there, I cannot submit a query in any way. 

Same goes for applications, Pigdin does not connect properly nor does gFTP. 

The last thing I did before this started was attempt to install a VPN client my university requires to connect. 

Has anyone experienced this or have an idea of what's going ?!?

Any help would be much appriciated.

Regards,
Travis from Chicago


I'm using wireless internet on a Dell Inspiron 1520 with a dual-boot on xp & ubuntu 8.10. xp works fine, only ubuntu is giving me issues.

---

### Post by Darkade on 2009-04-12
It could be that you can't go to "The internet" and for example you have google in your offline sites.
Clean your personal data in firefox (Tools>clear private data) make sure not to delete your saved passwords ;)

Just to make sure you really have internet access what happens if you time this in a terminal?

```
ping http://google.com
```

---

### Post by Tony Flury on 2009-04-12
> **Darkade said:**
> It could be that you can't go to "The internet" and for example you have google in your offline sites.
Clean your personal data in firefox (Tools>clear private data) make sure not to delete your saved passwords ;)

Just to make sure you really have internet access what happens if you time this in a terminal?

```
ping http://google.com
```

Try just : 
```

$ ping -c5 www.google.com

```
The command Darkade gave you wont work - ping does not understand full URIs - it just uses host names.

---

### Post by Darkade on 2009-04-12
> **Tony Flury said:**
> Try just : 
```

$ ping -c5 www.google.com

```
The command Darkade gave you wont work - ping does not understand full URIs - it just uses host names.
True. As I read the quote I went like... "Why did I wrote that http" LOL Thanks Tony

Anyway, as I said before that will tell us if you have internet conection or just local network.

---

