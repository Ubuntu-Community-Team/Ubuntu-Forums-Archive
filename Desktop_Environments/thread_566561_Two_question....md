---
title: "Two question..."
date: 2007-10-03
forum: Desktop Environments
---

### Post by anarchist_hippy on 2007-10-03
Hi everyone. 
I used to use Suse 10.2 for 2 years. And for some reason, I try kubuntu now... But, I've problems a bit.

1. I install beryl..... It works OK. But, It won't start automatically and after I start it, when I rotate cube only one desktop shown correctly, others have %0 opacity... When I move a window here, I can do what I want, but there's no background. Once I see cube's curves. After that it becomes grey. But first desktop, there's nothing wrong. (Hope I can tell my problem :( )

2. I try to add repositories to my apt-get and want to do this how to: 

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

but, When I type terminal (root terminal or normal):

```
 kate /etc/apt/resource.list 
```

I receive this error:

```
 kate: cannot connect to X server 
```

What's the problem?? 

Some descriptions:
I Use Kubuntu 7.04 (are there newer one?) on laptop HP Compaq nx 7400, 1 gb ram, 1.66 Ghz Core2 Duo, 120 Gb hdd,  Intel GM945, bluetooth, wireless... etc... 

Thanks from now :popcorn:

---

### Post by taurus on 2007-10-03
2.  Instead of logging in as root, why not use sudo to edit /etc/apt/sources.list?

```
kdesu kate /etc/apt/sources.list
```

---

### Post by mexlinux on 2007-10-03
Beryl is deprecated, you should use compiz-fusion instead

---

### Post by anarchist_hippy on 2007-10-04
> **taurus said:**
> 2.  Instead of logging in as root, why not use sudo to edit /etc/apt/sources.list?

```
kdesu kate /etc/apt/sources.list
```

I was tried that from Root console... Now, I did it with normal konsole... Now, I can open it ;)

About beryl... I'll try the how-to... If still no change at state, I'm thinkin' about to install compiz-fusion... 

Is compiz-fusion work with Kde?

---

### Post by happysmileman on 2007-10-04
> **anarchist_hippy said:**
> Is compiz-fusion work with Kde?

Yes, Compiz-Fusion is just a merge of Beryl and Compiz, so it has all the features of both (AFAIK) and is much more actively developed

---

### Post by mexlinux on 2007-10-04
> **anarchist_hippy said:**
> 
Is compiz-fusion work with Kde?
Sure it does! I use have it runing.

I will recommend you to use the 3v1n0 (Treviño) repos

---

