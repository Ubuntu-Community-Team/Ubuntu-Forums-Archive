---
title: "ubuntu totally unresponsive"
date: 2008-12-14
forum: General Help
---

### Post by azathrael on 2008-12-14
I posted a thread under scim problem but now it's more than that so I'm strting a new thread

I just turned my laptop on and I get 0 response.  All I can do is flip around to my cube desktops and barely manage to get system monitor open.  Last time stopping or killing the scim-bridge process made my laptop a little more responsive but now even scim-launcher is taking all my CPU and nothing works, including the terminal.

Can some please advise me on how I can go about fixing this problem, such as doing a system restore that even Vista offers but for some reason I can't find for Ubuntu.

Thanks

---

### Post by tuskenraider on 2008-12-14
id say use the live cd and reformat.  but thats just me.

---

### Post by hikaricore on 2008-12-14
I'd really like for everyone to please avoid giving the standard windows solution for any problem.

Here on the Ubuntu forums we try and solve users problems, not replace their operating system if all all possible.

---

### Post by azathrael on 2008-12-14
Ok, so I managed (after 2 hours at that) to open up my Synaptic Package Manager and uninstall SCIM.  Trying to get to that with 100% CPU usage is a pain in the ***.

Currently, I'm typing from my laptop so everything is dandy, right?

NO.

I DON'T HAVE SCIM.  Now I am unable to type in Chinese, Japanese, and Korean.  All of which I use on a daily basis.

So, I tried reinstalling SCIM and the 3 language support files from scratch.

Same problem repeated.

I saw that the SCIM-launcher's files were originating from the Chinese support files.

I deleted the Chinese support files.

Now SCIM-bridge is lagging.

So I delete Japanese and Korean language support.

SCIM-bridge continues to lag.

I have to delete SCIM all over again.

This is as "technical" as I can be with computers.  Does anyone have any idea why installing other languages makes my SCIM-bridge and SCIM-launcher go nuts with CPU usage?  Installing just SCIM without any other languages does not create this problem.  So I think I've isolated the problems to the language support files or of that sort.

Please, any help would be appreciated.

---

### Post by Sef on 2008-12-14
1) What version of Ubuntu do you have?

2) What are your system specs?

If you have Ubuntu,  Check Applications > Accessories > Disk Usage Analyzer to see if you can spot a problem.

---

### Post by azathrael on 2008-12-15
1. I have the latest version of Ubuntu (Hardy Heron)

2. I have a Toshiba Satellite X205-SLi5
Intel Core2Duo T8300
Nvidia SLI Dual GeForce 8600M GT
2x 160GB HDD
3072MB RAM

3. I tried messing with Disk Analyzer and I couldn't understand what it said:

Total filesystem capacity: 426.9GB (used: 258.4 GB available 168.5 GB)
The circle that shows up from using "Scan Filesystem" says I used a total of 129.3GB in my "/" folder.

Thanks for the response!

---

