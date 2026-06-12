---
title: "DHCP fails but static IP works....why?"
date: 2006-01-02
forum: General Help
---

### Post by jennhi on 2006-01-02
Hi guys! I'm running 5.10 with a motherboard embedded ethernet chip (82562EZ 10/100). I also have a wireless card (Intersil ISL3890 Prism) and get a very strong signal to the network, and today, both chip and card stopped connecting to DNS servers until I used the ethernet chip with a static IP address. Since I don't know the IP address of the wireless network, I can't enter that as a static IP when I want to switch over, but I do want to use the wireless network soon, solely. However, if the DHCP is a problem, then switching to wireless will be a big problem.

Any reason DHCP would fail when trying to find the IP address of, say, yahoo.com, but do okay when you manually try to ping the numerical IP address? Along the same lines, why would it fail until I manually entered a static IP address in network admin?

I know this is a software and not a hardware problem, so didn't post in the hardware>network forum. But if there's a different forum, please let me know, and I'll ask to move it.

Thanks!
jennHi

---

### Post by ape on 2006-01-03
Is there a difference in the DNS server(s) that are configured when using DHCP vs. when using a static IP?  Are you trying to override the DNS servers given to you from the DHCP server?

---

### Post by jennhi on 2006-01-03
[QUOTE=ape]Is there a difference in the DNS server(s) that are configured when using DHCP vs. when using a static IP?  Are you trying to override the DNS servers given to you from the DHCP server?[/QUOTE]
Hi Ape!

No, I've never tried to override the DNS servers that were there. The ones that were there are the closest servers to me. I did add two more that were a little further away in to the bottom of the list as an alternative in case the closest ones didn't work, but didn't delete the closest ones. It didn't work anyway. That was before entering my static IP into the network admin tool.

One thing: my static IP address for the ethernet chip's network changed over the weekend. But it did work for a while after the change (for only about a half hour). And the change should not have affected the wireless network.

Does this make a difference?

---

### Post by chocolatetoothpaste on 2006-01-03
I had problems too with dhcp and dns gibberish.  Heres the scoop, and we'll see if our probs are similar.  I had a DSL modem that assigned ip's to the computer via dhcp.  Now, after I installed ubuntu for the first time, I went to connect to the internet and, nothing.  I looked at my network configuration, and the modem had assigned it's own ip address as one of the DNS servers, which obviously didn't work.  so I asked on the forum, and someone suggested to open the file /etc/resolv.conf.  It was there that I entered the correct infomation and saved it.  Then I typed ```
sudo chattr +i /etc/resolv.conf
``` into the terminal to lock the file so my modem wouldn't overwrite it again.  After that, success!  Internet!  Also, someone told me that when you lock the file, the system creates a new one called /etc/resolv.conf.dhclient-new.  Simply duplicate the contents of the file and lock this one too by ```
sudo chattr +i /etc/resolv.conf.dhclient-new
``` and you should have it.  If this doesn't work, then maybe I misunderstood the problem.  hope this helps!

---

### Post by ape on 2006-01-03
As chocolatetoothpaste has mentioned, this could very well be something to do with whatever dhcp server you are using.  Does your /etc/resolv.conf file get overwritten when using DHCP?  

Also, if you are having problems with those DNS servers (since you mentioned that you have failures on both the wired and wireless NICs) have you tried any others?  Give this IP a shot:  69.67.108.10.  It is a public DNS server that is very responsive.

---

### Post by jennhi on 2006-01-05
wow -- sorry for taking so long to get back. I was waiting for the email saying this thread was replied to.

I'll check those things out tonight and get back to you. Thank you so much for helping!

---

### Post by jennhi on 2006-01-07
Inexplicably, it's working again. I think it may have to do with my IP address changing and DHCP not catching up. I believe the file is updated regularly. When this happens again, I will lock the file. Thank you so much for your help!

---

