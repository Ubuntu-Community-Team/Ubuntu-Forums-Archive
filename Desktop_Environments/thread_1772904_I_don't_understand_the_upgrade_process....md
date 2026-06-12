---
title: "I don't understand the upgrade process..."
date: 2011-06-01
forum: Desktop Environments
---

### Post by Mariane on 2011-06-01
I just did 

```

sudo apt-get update
sudo apt-get upgrade

```

and I was told I was up to date. Then up pops the notification saying I have 3 packages to update. Something like 5 seconds later. How can this be possible? Which information should I believe? 

Mariane

---

### Post by TBABill on 2011-06-01
Is your update manager set to notify you once per day at a set time? If so, could it be coincidence that you did it manually right before your system was set to advise you that it had updates?
 
I would always trust your terminal output before an automated tool, assuming you issued commands correctly (and it appears you did).

---

### Post by snowpine on 2011-06-01
What were the 3 packages?

It is possible you need to:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

"sudo apt-get upgrade" only does a partial upgrade; it will skip any upgrades that require adding or removing a package.

---

### Post by Mariane on 2011-06-02
They were about core... 2.6.26 or something like that... I don't remember. 

I don't know if the reminder is set for any particular time, it must be on default settings because I never changed it. 

As for dist-upgrading, I'll wait a few months before doing this. 

Mariane

---

### Post by snowpine on 2011-06-02
> **Mariane said:**
> They were about core... 2.6.26 or something like that... I don't remember. 

I don't know if the reminder is set for any particular time, it must be on default settings because I never changed it. 

As for dist-upgrading, I'll wait a few months before doing this. 

Mariane

2.6.26 would be the Linux kernel. You need to use "dist-upgrade" to get new kernels. Not sure why you feel the need to wait a few months to get bug fixes and security patches to the most important part of your operating system, but it's your computer after all. :)

---

### Post by Mariane on 2011-06-02
dist-upgrade might get me Ubuntu 11.04 which is too recent to work properly. 

Mariane

---

### Post by snowpine on 2011-06-02
> **Mariane said:**
> dist-upgrade might get me Ubuntu 11.04 which is too recent to work properly. 

Mariane

No it will not give you 11.04, I promise. You can type "man apt-get" if you don't believe me. Or use the Update Manager if you are unfamiliar with terminal commands. :)

---

### Post by Mariane on 2011-06-02
I chose to trust you and... You're right! It didn't! It just told me I was up-to-date. 

Now I'm really confused. Did this change or was it always like that? And what is the CLI command for getting the next version of Ubuntu, then? 

Mariane

---

### Post by snowpine on 2011-06-02
> **Mariane said:**
> I chose to trust you and... You're right! It didn't! It just told me I was up-to-date. 

Now I'm really confused. Did this change or was it always like that? And what is the CLI command for getting the next version of Ubuntu, then? 

Mariane

Always like that as far back as 2008 when I started. 

According to [http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade) the command for a release upgrade is:

```
sudo do-release-upgrade
```

---

### Post by Mariane on 2011-06-02
Thank you very much snowpine. 

Mariane

---

