---
title: "software crossover issue"
date: 2010-09-20
forum: Desktop Environments
---

### Post by Detroit_Bad_Boy on 2010-09-20
A friend of mine works as an independent rep for a well known flower sales company in the U.S. Her computer recently blew up so I sold her a computer with a linux OS installed on it.
  She works as a home telephone rep for this company and needs to use the Nectar dialpad interface to make and receive calls while on the job.
  My concern is that Nectar may not work on linux. Any help with this issue?

---

### Post by LinuxPhreak on 2010-09-21
If it is a Windows based program you can try using WINE. You can check the Wine HQ archives to see if it has been done successfully yet. An alternative would be to install ekiga. 

[Install Here]("apt://ekiga")

Or type the following in the terminal. 

```
sudo apt-get install ekiga
```[URL="apt://ekiga"]
[/URL]

---

### Post by Detroit_Bad_Boy on 2010-09-27
> **LinuxPhreak said:**
> If it is a Windows based program you can try using WINE. You can check the Wine HQ archives to see if it has been done successfully yet. An alternative would be to install ekiga. 

[Install Here]("apt://ekiga")

Or type the following in the terminal. 

```
sudo apt-get install ekiga
```[URL="apt://ekiga"]
[/URL]


 I installed that program, but it turns out to be a dialer that can be used through ubuntu. What I need to know is :Will Citrix run on ubuntu and will the Nectarphone dialer work on ubuntu also?

---

### Post by macanudo on 2010-09-28
The citrix client will work on Ubuntu: [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo). Not sure about the other app. One other solution.. if you have a XP install laying around just get a virtualization app like VirtualBox or VMWare running. I use VirtualBox for a work app and it works fine.

---

