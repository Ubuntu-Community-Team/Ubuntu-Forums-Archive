---
title: "sudo kate problem"
date: 2005-04-11
forum: Desktop Environments
---

### Post by deadlands on 2005-04-11
Hi, I'm new to Kubuntu (just installed it yesterday) but not to Linux ... I'm also not an expert by any means.

Whenever I try to start kate from konsole with
```
sudo kate /some/file
```

I get this output:
```
Error: "/var/tmp/kdecache-travis" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
```

Kate will run as a regular user, but crashes when being ran as root. 

I deleted /var/tmp/kdecache-travis and killed the kate process, but I still get the same error. I'm not sure where to go from here. I have gotten used to using Kate for file editing, but without being able to use it as root is rather pointless.

Thanks in advance for your help. I just need to be pointed in the right direction. This funkiness started today after I got Ndiswrapper and my Wireless card working -- prolly a coincidence.

---

### Post by brandonyoung on 2005-04-12
I'm getting the same problem, too.

I am able to work around the problem by running kate by running it from the Run Command option from the menu and choosing run as another user and choosing to run it as root, and entering my root password.

It is a real pain not being able to run it from the command line though.

This is on a fresh install of kubuntu.

--Brandon Young

---

### Post by crvendramini on 2005-04-12
I have the same problem here. Maybe, be necessary to report as bug?

 :neutral:

---

### Post by dmh-bidlah on 2005-04-12
You can just 
```

kdesu kate
```

---

### Post by deadlands on 2005-04-12
[QUOTE=brandonyoung]I'm getting the same problem, too.

I am able to work around the problem by running kate by running it from the Run Command option from the menu and choosing run as another user and choosing to run it as root, and entering my root password.

It is a real pain not being able to run it from the command line though.

This is on a fresh install of kubuntu.

--Brandon Young[/QUOTE]


I can't even run Kate as root from the run command. Amazingly, though, running 'sudo kate' from the run command works. Weird.

It's a relief to see that it's not just my system. (I'm also getting frequent Konquerer crashes like many other people are getting -- maybe Kubuntu isn't ready for primetime??)

---

### Post by deadlands on 2005-04-12
[QUOTE=dmh-bidlah]You can just 
```

kdesu kate
```[/QUOTE]


Thank you!!! That works great. Would this be the preferrable command for running KDE apps as root?

---

### Post by dmh-bidlah on 2005-04-12
[QUOTE=deadlands]Would this be the preferrable command for running KDE apps as root?[/QUOTE]


[QUOTE=Ubuntu Wiki]
If you need to give a graphical application root privileges use either
...
The kdesu in ubuntu has been patches to use sudo.
Using sudo as opposed to gksudo/kdesu can sometimes lead to file ownership problems.[/QUOTE]
 :wink:

---

