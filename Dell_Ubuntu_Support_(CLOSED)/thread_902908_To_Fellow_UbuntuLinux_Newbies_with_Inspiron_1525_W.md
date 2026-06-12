---
title: "To Fellow Ubuntu/Linux Newbies with Inspiron 1525 Wireless Problems!!!"
date: 2008-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ostamb on 2008-08-27
I thought I would post a new thread here, because I had an Inspiron 1525 running Windows, and wanted to try switching over to Ubuntu, with no previous Linux experience (gasp!). Well, I tried, and almost quit when I couldn't get the wireless working, even after hours of reading through different threads and trying different things like ndiswrapper, downloading different broadcom drivers, and more... Well, as is usually the case, I found a ridiculously easy solution that worked for me, so I wanted to share.

First of all, I used the Dell reinstall image for 1525n's that come preloaded with 8.04 (Hardy) from [http://linux.dell.com/files/ubuntu/hardy/iso-images](http://linux.dell.com/files/ubuntu/hardy/iso-images)

Then, here's the key... the ONLY thing I needed to do was connect to the internet with a regular old Ethernet cable, and **do the recommended update** (an icon showed up in the top right corner of the screen to tell me to update), which for me was over 100 updates that took over an hour to download and install. Once it all completed, viola, wireless worked! Apparently, the update included all the proprietary Broadcom drivers that I needed and took care of it automatically. 

I hope this helps other newbies out there like myself who are completely unfamiliar with this foreign world called Linux :)

---

### Post by wgarider on 2008-08-27
Well, at least I know I'm not alone!! LOL

I did the same - using the Dell Ubuntu install, I did the updates like you but I still seem to have no wireless.......:(

**[COLOR="Red"]EDIT: [/COLOR]**A day later, after pouring through the forum messages, I'm up and working with wireless. I had to go the NDISWRAPPER route and do a fair amount of work bbut it's working now. oddly enough,it won't work with WPA2 personal but works with no security (thanks to my neighbors.... ;-) ) Oh, and WEP seems okay too.

---

### Post by myradio on 2008-08-27
hi there

i've just bought an Inspiron 1525, unfortunately, it'll be here not before 4 weeks from now.

so, i'm looking how linux works on it. i don't know which wireless hardware it has, i've recently helped a friend of mine installing ubuntu on her laptop. she has a acer aspire with atheros wireless hardware. solution was to get windows drivers (yes, the same drivers you 've for your win) and installing them with NDISwrapper.

i hope this help you, at least to know what to look for.

---

### Post by myradio on 2008-08-27
there is an ''oficial dell ubuntu ISO'' out there, you should probably check that too

---

