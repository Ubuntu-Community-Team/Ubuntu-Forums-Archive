---
title: "Does apt-cacher-ng work offline?"
date: 2009-06-14
forum: General Help
---

### Post by expelledboy on 2009-06-14
I went to install 200 computers at one of these african education aid projects that my dad seems to be keen on at the moment and apt-cacher-ng didnt do what I wanted it to do! I needed it to serve the files that I had cached earlier to a net-boot-installer all preseeded. The installer tried to get the release file and then timedout. It seems apt-cacher-ng was waiting for the internet.

There is a option in the conf file that I thought would work so I didnt even bother checking before I left.. :oops:

If apt-cacher-ng doesnt work offline I will probably need to add another proxy that does. A transparent squid proxy? More overhead on a already overworked previously retired pc. :(

---

### Post by KhurramM on 2009-06-14
u can use a local ftp, http, samba or nfs server/share to install apts using apt-get on a local network, using the netbootCD mode.

Hope this helps.

---

### Post by expelledboy on 2009-06-14
> **KhurramM said:**
> u can use a local ftp, http, samba or nfs server/share to install apts using apt-get on a local network, using the netbootCD mode.

Hope this helps.

That would be perfect! :KS I must have missed this in my reading on the whole thing. Do you have a link I could follow up on?

---

### Post by cong06 on 2010-03-16
apt-cacher also has offline support.

There are a few features that apt-cacher has, that if apt-cacher-ng would include, would make me switch over. For now though, I'm stuck using a slower piece of software.

---

### Post by zazuge on 2010-11-09
well i stembled on this problem myself
you can force apt-cacher-ng to work offline by adding a proxy in it's config file (don't forget to stop the proxy if you have one)
and using apt-get with the -m or --fix-missing argument 
it will make it upgrade without forcing apt-cacher-ng to download anything
remmeber that ignoring packages can break your system specialy if you upgrade the distro

---

### Post by cong06 on 2010-11-09
Actually, apt-cacher-ng (0.4.6) has an option in it's config:
```

#offlinemode:1

```
1 = true, offline
0 = false, online (and commented is also offline)

I have noticed that it doesn't work perfectly though. If I update behind apt-cacher-ng (with this option enabled), it claims that the packages it wants to install are unverified.

(actually, I'm trying to get it to do it now, but can't. I'm not sure why. Maybe it's fixed?)

---

