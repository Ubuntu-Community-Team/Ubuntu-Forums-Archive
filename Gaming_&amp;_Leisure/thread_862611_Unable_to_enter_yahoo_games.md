---
title: "Unable to enter yahoo games"
date: 2008-07-17
forum: Gaming &amp; Leisure
---

### Post by C0oli069 on 2008-07-17
Hi I've ready many other posts on this issue and none were clear.

I've installed java and it's enabled, but everytime i click to join a room it loads to a page telling me my current browser settings will not let me access games.

Either enable java or download it if you havent already...

So i went to the options and disabled the java and java script and re-enabled and it loads further this time 

It looks like it's loading then i get the messages-
You were not able to enter games because
1-behind a firewall
2.stale cache
3-server is down

I disabled it re-enabled a couple times and it finally let me in.

But when i tried to enter another room again it would either bring me back to the first error page or the second.

Anyone know why this is happening? Should i reinstall java? if so what the heck is the command.

Just curious as to what the problem might be as it's annoying the heck out of me. I'm a new user to Linux and it's been nothing but hectic.

Thanks and hopefully i'll get atleast a reply this time!

---

### Post by niceguy78 on 2008-07-18
Please tell us what browser do you use? Try to use other browsers; maybe you will be able to enter games.

---

### Post by Archmage on 2008-07-18
Did you enable cookies?

---

### Post by evets25 on 2008-07-18
Ok, so I just checked yahoo games, and it uses flash, not java (and it works for me). No worries though, firefox should be able to automagically detect this and download the plugin for you. if you type this in the address bar of firefox...

```
about:plugins
```

...then you should be able to see what plugins are installed. If it's not installed, and firefox doesn't autmagically install it for it, there are several other ways to install it: 

 - go to the abobe page, and manually install it, OR
 - add another (non-free) repository that has flash player in it, then install it through synaptic OR
 - go to getdeb.net as see if it's there, then download and install

---

### Post by tuxxy on 2008-07-18
> about: plugins

You are looking for the java web plugin I use GCJ, and also non-free-flash plugin.

---

### Post by ewan86 on 2009-11-09
Hi,

I had exactly the same problem today when trying to play pool on Yahoo games](*,)] I couldn't solve the problem so I'd thought I'd try opera which I downloaded and then it worked! So why it is not working in firefox I don't know!!

---

### Post by ewan86 on 2009-11-10
Well I solved my problem..Java was installed on my computer but no plugin in firefox...I followed the advice on this page and now it works

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

---

