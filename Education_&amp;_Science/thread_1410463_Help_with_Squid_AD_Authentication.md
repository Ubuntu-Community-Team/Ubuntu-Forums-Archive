---
title: "Help with Squid AD Authentication"
date: 2010-02-18
forum: Education &amp; Science
---

### Post by mcp200 on 2010-02-18
Hi There,
 
I have setup squid to authenticate with active directory and managed to authenticate successfully however i need to make sure when particular ad user group authenticate to the internet they get access denied to youtube for example while other group is granted access. could someone assistt how i can go about it please?
 
 
Thanks

---

### Post by lunatico on 2010-03-18
> **mcp200 said:**
>  
I have setup squid to authenticate with active directory and managed to authenticate successfully

Hi,

Could you tell me how you did this? I'm trying to setup squid to authenticate against AD but there seems to be no easy way of doing this.
Any howtos you followed? Links?

Any info appreciated.

---

### Post by jermf810 on 2010-03-18
Please give us a little more details. From what I understand, you are looking to deny user groups access to certain websites. I think your best bet would be to look into the squid.conf file. Check out SquidGuard: [http://www.squidguard.org/](http://www.squidguard.org/) 

"SquidGuard is a URL redirector used to use blacklists with the proxysoftware Squid. There are two big advantages to squidguard: it is fast and it is free. SquidGuard is published under GNU Public License. "

Does this help?

---

