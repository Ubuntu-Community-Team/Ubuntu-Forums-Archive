---
title: "Linux terminals to a windows terminal server"
date: 2008-10-29
forum: Desktop Environments
---

### Post by mrfr0g on 2008-10-29
I'm not even sure the best way to ask this, but, I am trying to find out if it's possible to have a central windows server which a bunch of linux machines connect to. Each linux machine gets the windows environment of the windows server.

This way each linux machine will have the same settings, and look like windows.

I did try to do a few google searches on this, but I'm just not sure the exact name of what I'm asking.

---

### Post by cryogenic on 2008-10-29
Sounds to me what you want is to have a Windows server running Terminal Services. Then use tsclient in Gnome to connect to them. They log in and they all get their own windows desktop on the server. Sound about right?

---

### Post by mrfr0g on 2008-10-30
That's exactly what I want. Is it that easy?

---

### Post by dad311 on 2008-10-30
> **mrfr0g said:**
> That's exactly what I want. Is it that easy?

Its that easy, use it every day.

---

### Post by mrfr0g on 2008-10-30
Sweet l, thanks very much. I'm going to run some tests and hopefully get this setup

---

### Post by mrfr0g on 2008-11-09
I can't believe how easy this was to setup. I just finished a work session using this program. Thanks again!

---

### Post by tbeehler on 2009-07-27
> **mrfr0g said:**
> I can't believe how easy this was to setup. I just finished a work session using this program. Thanks again!

I am in the middle of setting this up for my company.  I simply take some old pentium 3's and 4's, and make ubuntu boot up automatically with the terminal services client and they simply hit the "connect" button and they log in with their user names/passwords.

I put together a dual socket, quad core each (8 core total) xeon monster with 32 gig of ram and put about half my staff on it and it's working WONDERFULLY!  I HIGHLY recommend it for anyone who's trying to cut down on their costs.  I normally spend between $500 and $1,000 per person when they get an upgraded machine, and now, I can use a simple, unwanted computer as their main machine, and spent $4,000 on the server/licenses and put 15 people on it and counting (gonna be about 40 total when the project is complete)

---

