---
title: "Broadband Firewall Router (Linksys)"
date: 2006-03-16
forum: Desktop Environments
---

### Post by giddy1945 on 2006-03-16
I just bought a "broadband firewall router" with 4-port switch/VPN Endpoint.  One of the minimum requirements is "Internet Explorer 5.0 or Netscape 6 for web-based configuration".  I called one of my friends before I bought it and brought that little detail to his attention, but he told me to ignore that part, because it is their "easy set up" disk that requires that.  How do I install it?  My connection is DSL, and my brouser is Debian Sensible Browser.

---

### Post by eyebrowman92 on 2006-03-16
linksys probably has some connection to m$ who wants you to use those.  you dont need to install any software, ubuntu will detect it automatically. to connect to it in your browser just type the nat ip(ex: mine is, 192.168.1.1) and a prompt should appear. to login it should just be username:admin pass:admin, and you can change stuff from there.

---

### Post by Dragineez on 2006-03-16
What he said. The only reason they list IE5 and NS6 is because they both support the javascript linksys uses in their web interface. Just about any browser you'll have in ubuntu will work just fine. It certainly does on mine.

---

### Post by giddy1945 on 2006-03-16
thank you.

---

### Post by giddy1945 on 2006-03-16
So, I just hook it up, and restart my computer?  Wher do I type the nat ip?  In a terminal?  What is a nap ip, and how do I find out what mine is?  Thanks for your help.

---

### Post by eyebrowman92 on 2006-03-16
For hooking it up im not so sure. i use comcast and have a modem and a CAT cable connects my modem to my router, and another CAT cable goes from my router to my computer. since you have dsl, it might be different.  if you have any CAT cables, plug one into the slot on the router that says Internet (it should be off to the side by itself) and plug the other end into an ethernet port on your computer (i dont know if its the same for dsl)  then take another cat cable and put in slot one of the router, and connect it to the modem (or the dsl thingy you use). after that restart your computer,  open a terminal and type:

```
ip route
```

for me, the last ip adress it lists is my nat ip. type this into your web broser, and a prompt should appear.  to login try username:admin and password:admin
this should take you to the web setup where you can configure your router.  

again im not positive this is 100% correct because i dont have dsl.  this is just the way i hooked mine up.

---

### Post by _bacon_ on 2006-03-16
I don't think theres any configuration necessary at all. If your broadband connection worked before and you plug in the router properly, it _should_ work out right away. Wireless is going to be another thing. With most browsers and with a linksys router, you go to [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1) (correct me, it's in the manual anyway). It connects to the internal web server on your router and you configure it this way. Linksys gives "installation cd" but IMHO it's pretty useless, even on Windows.

(default u/p for linksys routers : user : <blank> password : admin)

Edit AGAIN: sorry eyebrowman92, didn't see your post!

---

### Post by giddy1945 on 2006-03-17
Thanks again.  This forum is very informative.  Maybe I'll be able to contribute someday.

---

