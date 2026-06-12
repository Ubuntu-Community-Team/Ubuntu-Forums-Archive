---
title: "Firefox refuses to download VirtualBox"
date: 2009-05-02
forum: General Help
---

### Post by calvinps on 2009-05-02
Hello!

I am trying to download VirtualBox, but for some reason, Firefox doesn't seem to download it when I click on the link.

[http://download.virtualbox.org/virtualbox/2.2.2/virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/2.2.2/virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb)

Test that link, and if it works for you, I will restart my computer.

---

### Post by zvacet on 2009-05-02
It doesn´t work.You can get Virtualbox from repos.[Here]("http://ubuntuforums.org/showthread.php?t=1074160") is a guide for Intrepid but it should work for Jaunty too.

---

### Post by delcypher on 2009-05-02
There seems to be some sort of redirect on the links on the virtual box. I was going to suggest try downloading it from a repository instead but their repository seems to be down too.

The instructions are on [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") anyway.

You want to choose ```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

``` 

I get ```
Err http://download.virtualbox.org intrepid/non-free Packages
  302 Moved Temporarily
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-i386/Packages.gz  302 Moved Temporarily

``` So looks like the sites being modified in someway. Hopefully it'll be up and running soon.

---

### Post by kestrel1 on 2009-05-02
Yes, same issue here. The Windows version will download, but couldn't get the Ubuntu ones to. I am going to try via Windows & see if that works, Can't see why it would, but I will post back with result.

---

### Post by kestrel1 on 2009-05-02
It will download in Windows. I am using Google Chrome to do this, but it is working.
Strange

---

### Post by Tipped OuT on 2009-05-02
Strange...works for me:)

---

### Post by codeseer on 2009-05-02
Better to use the repos anyway, they will keep you up to date.

---

### Post by Pom2122 on 2009-05-02
Try it again, they just got the downloads working again. :)

---

### Post by kestrel1 on 2009-05-02
Looks like a glitch then.

---

### Post by Pitel on 2009-05-03
Hmm, I still got 302 error in apt-get update
```
W: Selhalo stažení [http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-amd64/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-amd64/Packages.gz)  302 Moved Temporarily
```

---

### Post by bluemars63 on 2009-05-03
same applies to me. Each suggested "mirror" leads only to original download server.
Oh SUN!

---

### Post by kc109 on 2009-05-04
I have had the same thing for the last 3 days or so, the APT update manager has failed to get through to the VirtualBox depository. Looking for some help I came across this thread but no one has found the answer yet.
I started to look around the VirtualBox site using Firefox and now the APT update manager is working but I don't know why.
The only thing that I can think of is that it is some form of DNS or Sun redirect problem I by-passed by navigating one level at a time from:-
[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
cut and paste the following from the Debian-based Linux distributions list on that page:-
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)
Navigate down to:-
[http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-2.2/](http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-2.2/)
then back tracked and navigated to:-
[http://download.virtualbox.org/virtualbox/debian/dists/hardy/non-free/binary-amd64/Packages](http://download.virtualbox.org/virtualbox/debian/dists/hardy/non-free/binary-amd64/Packages)
at this point I re-tried  the APT update manager and it worked (but will it tomorrow when various caches have timed out?) . Others seem to be having related problems but no fix. See:-
[http://www.pubbs.net/debian/200905/67523/](http://www.pubbs.net/debian/200905/67523/)

---

### Post by Pitel on 2009-05-04
It seems fixed now.

---

