---
title: "Cron Job Erasing DNS Entries"
date: 2007-05-08
forum: Desktop Environments
---

### Post by chronister on 2007-05-08
I have 6.01 Installed with Apache, Mysql & PHP. I have several v-hosts set up and all is working fine. 

I am using a 2wire 2700 modem/router issued by my ISP Qwest. I am just learning Linux and am having an issue. The 2wire 2700 has a DNS resolve so I can make local sites available on my whole network without having to resort to hosts files. The problem is that there is a CRON job running every 45 hours or so that is causing the 2wire to erase DNS resolve entries. I am working with 2wire to resolve this, but could someone shed some light on what may be causing this to happen?

When looking at the syslog at the time the DNS resolve settings are erased on the 2wire, there seems to be a sendmail cron job running that is appearing every time the router erases the settings. Also when I restart the machine it is removing user defined entries. 

I also have a windows xp machine running XAMPP, and it's entries are never modified. So the problem is something on the Ubuntu Box that is making this happen. Any Ideas??

I will be more than happy to provide any additional information to get to the bottom of this.

Thanks in Advance,

Nathan

---

### Post by Zelut on 2007-05-08
If a cron job is actually deleting your DNS entries (somehow via the DHCP service I would assume) you can set it to prepend a list of DNS entries to always be used.

Try looking at the /etc/dhcp3/dhclient.conf, uncomment the line beginning with #prepend and add your known good DNS servers to that list.

If it is going to continue to wipe those addresses it'll atleast prepend the good ones when it restarts.

---

### Post by chronister on 2007-05-09
Well, I guess that the cron jobs are not actually erasing the entries. A cron job runs and something about what it is doing is making the router erase the dns entries. This also happens when I reboot my Ubuntu machine.

I have a windows xp machine running XAMPP, and the DNS entry I have for that stays no matter what.

I have uncommented the prepend line and set the IP to 192.168.0.1, which is my modem/routers IP address, so we will see if that helps at all.

What cron jobs run by default? 

I noticed that everytime this happens, there is a line that says something like gethostbyaddr 192.168.0.13 failed. Any Idea what this means?

I would like to eventually make the move from Windows to Linux for my day to day system, but I got a long way to go before I can do that.

Thanks for your help.

---

### Post by chronister on 2007-05-09
I rebooted the machine and it happened again. There is something that runs in a cron job, and something that runs on startup that I *think* is making the router think that the machine no longer exists. Is there a way to see what is happening behind the Ubuntu "loading" screen?

If I can drop that screen and take note of what is happening, maybe I can find exactly which line makes this happen.

I tried looking at the logs in my 2wire modem, but they are pretty useless.

thanks

---

### Post by chronister on 2007-05-09
I have traced the problem down to the DHCP request. I set the machine to a static IP and when I reboot the DNS entries in the 2wire router stay put. So I am guessing that the cron job that was causing this was simply refreshing the IP address.

Why would the machine simply refreshing the IP address cause the router to delete user defined DNS entries?

---

### Post by chronister on 2007-05-10
anyone got any ideas why DHCP would make my router's custom DNS entries disappear?

---

### Post by Zelut on 2007-05-10
That is the way that DHCP works.  It receives an IP address, DNS addresses and often hostnames from the DHCP server.  If you've customized your DNS addresses they'll be reset when your machine re-retreives it's addresses.

Again, as above, use the prepend function in the file to force it to prepend DNS addresses you want it to use every time.... either that or tell it to use static addressing.

---

