---
title: "How to get back &quot;right click open folder with&quot; 14.10?"
date: 2015-02-06
forum: Desktop Environments
---

### Post by hopelessone on 2015-02-06
Hi,

Googled and googled, closest thing I found is not supported in 14.10 which is frustrating :(

[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open)

Anyone tell me how I can bring this back in Nautulis? tried Nemo, but don't like the layout

Thanks,

---

### Post by mc4man on 2015-02-06
I've no use for 14.10 but anyone who wants open with back is ok with me. Ck. the ppa in about an hr. or so
(- make sure you update all your currently installed nautilus packages, typically 3 (libnautilus-extension1a,  nautilus, nautilus-data

---

### Post by hopelessone on 2015-02-10
Hi :)

Thanks for the add, I'll never install another .10 ubuntu version... this one got me good ;)

I updated software today, and can't install. Am I doing this right?
I ran a sudo apt-get update
then:
```
blade@unicorn:~$ sudo apt-get install nauty-open
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nauty-open
```

---

### Post by mc4man on 2015-02-10
No, that's not going to work - 

To add ppa - 
```
sudo add-apt-repository ppa:mc3man/nauty-open
```

Then this should suffice
```
sudo apt-get update  
```
```
sudo apt-get upgrade
```

Or just upgrade manually from your package manager

---

### Post by hopelessone on 2015-02-10
Thanks alot for this mc4man :)

worked a treat.

Typically how often you upgrade Ubuntu? I'm thinking of the .04's only once a year...

Cheers for the help :)

---

### Post by mc4man on 2015-02-10
> **hopelessone said:**
> 

Typically how often you upgrade Ubuntu? I'm thinking of the .04's only once a year...

Cheers for the help :)
I used to just go directly to the next dev version but as of 14.10 no more. Now the non lts releases are more a point in time than a release & only good for 9 months.
Myself want to stick with unity7 & compiz so will stay on 14.04 until I see what 16.04 is bringing. 
(- though I'll have the current dev installed on another drive so I can keep in contact with what's changing & what I want to change & how to do those changes, ect.

---

### Post by hopelessone on 2015-02-12
That's Great, and Thanks again you made my day :)

Catch you 'round,

---

