---
title: "Firefox 32 bit, Address Not Found"
date: 2009-06-04
forum: General Help
---

### Post by JayStang on 2009-06-04
Hey Guys,
I have just finished downgrading firefox 64 bit to the 32 bit version (3.0.10) on 64 bit Ubuntu 9.0.4. I am a Flex developer and I NEED to have the flash debugger player installed which is only offered in 32 bit which is my reason for downgrading. Everything worked great out of the box with the 64 bit version of FF, but now that i've downgraded i cannot connect to ANY website. I get an "Address Not Found" "Firefox can't find the server at..." error. I DO have an internet connection (I can ping external sites just fine), and this was working fine before the downgrade. I have played with the firefox's proxy settings but nothing worked there. I followed the following guy to downgrade... [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)
 
Anyone have any idea's what could be wrong here? Any help would be appreciated.
 
Thanks!

---

### Post by JayStang on 2009-06-05
Bump.  Anyone?  I'm at a loss here!

---

### Post by JayStang on 2009-06-05
Ok problem solved.  In firefox had to change some settings.  Just for reference i'll post it up here.

Open Firefox.
Type in adderss bar "about:config"
Search for "network.dns.disableIPv6"
Set value to "true".

---

### Post by Lynch on 2009-08-18
Wow - I was searching for a solution like this for quite some time! Thanks a lot for posting this!

Do you have any idea why this is necessary?? Isn't there 32-bit support for IPv6 on 64-bit ubuntu?

Cheers, Flo

---

