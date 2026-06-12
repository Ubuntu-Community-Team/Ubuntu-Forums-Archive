---
title: "Using red hat Package Manager?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by shade11 on 2006-01-07
I have been trying for ages to get alien installed. It caused too much trouble so I decided to get Red Hat Package Manager. I got it off Synaptic and now I need to know how to use it.

Unless you know a website with a valid .deb file of alien (Other than the Debain webste [Not working at the moment])

Can someone please tell me how do I de-package an RPM file with Red Hat Package Manager?

And dont tell me to install kpackage (it doesnt reckognise my root password.)

---

### Post by aysiu on 2006-01-07
What's wrong with ```
sudo apt-get install alien
```?

---

### Post by ardchoille on 2006-01-07
I installed alien from the main repo for Ubuntu 5.10 and did:
```

sudo alien --to-deb packagename.rpm

```
and then did :
```

sudo dpkg -i packagename.deb

```
and it worked fine.

---

### Post by shade11 on 2006-01-07
It is because I cannot set my repositories to universe and multiverse. So I cannot apt-get alien or get it off of synaptic. 

Now can someone please tell me how to use red Hat Package Manager?

---

### Post by aysiu on 2006-01-07
[QUOTE=shade11]It is because I cannot set my repositories to universe and multiverse. So I cannot apt-get alien or get it off of synaptic. [/quote] [alien is not in Universe or Multiverse.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alien&searchon=name&subword=1&version=all&release=all) It's in the standard repositories. Why can't you set your extra repositories? Do you not have an internet connection?

---

### Post by shade11 on 2006-01-07
I have an internet connection and someone on this forum told me that in order to apt-get alien then I had to add universe and multiverse in my repositories.

Can you just please tell me how to use Red Hat Package Manager?

EDIT: Never mind I downloaded it finally and got it working.

I am going to put this in the Wiki so noobs like me will be able to install this stuff.

---

### Post by aysiu on 2006-01-07
[QUOTE=shade11]I have an internet connection and someone on this forum told me that in order to apt-get alien then I had to add universe and multiverse in my repositories.[/quote] It's in the regular repositories, and you still haven't explained why you are unable to add those extra repositories anyway.

> 
Can you just please tell me how to use Red Hat Package Manager? You don't. You use alien for .rpm files. Otherwise, you use .deb files. Otherwise, you use Mandriva, Fedora, or some other RPM-based distro.

> 
EDIT: Never mind I downloaded it finally and got it working.

I am going to put this in the Wiki so noobs like me will be able to install this stuff. Why don't you put the explanation in this thread of both what you're trying to do, what exact obstacles you face, and what exactly you did to get it to work? I still don't understand what the problem was.

---

