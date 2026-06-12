---
title: "gnome-cups-icon 100% cpu"
date: 2006-08-27
forum: Desktop Environments
---

### Post by the_0ne on 2006-08-27
I've found plenty of posts on this and there seems to be no answer.  I have a problem where my laptop (Dapper Drake 6.06) starts a gnome-cups-icon process and consumes 100% of my cpu until I kill it.  It starts after several hours of being booted.  (Seems to always be running when I wake up in the morning.)  I don't even print from this machine, although I do have a printer or two defined.

Google produces several results, but nobody with a resolution to the problem.  Ubuntuforums produces several results also, but no resolution.

Am I missing something?  Is there a fix to this?  The posts I speak of are from July, we're almost in September.  :(  I have a laptop and use it 24/7 at home.  I can't have my cpu running 100% for several hours like that for no reason, the thing starts to smoke.  :)

Thanks in advance for any help...

---

### Post by lagagnon on 2006-08-27
I would start by looking through all your logs hunting for error messages when that problem acutally occured (/var/log/messages and /var/log/cups/error_log and /var/log/cups/access_log), also try to duplicate it by launching cups (locahost:631 in your browser). look also at ~/.xsession-errors and send all the relevant details you can find to Ubuntu bug reports. But FIRST search the Ubuntu bug reports and see if there has been a solution posted already.

---

### Post by the_0ne on 2006-08-27
I checked all my logs and nothing so far.  Nothing in /var/log/messages and nothing in the cups logs either, they are blank.

I checked bug reports and there is one with no resolution.  :(

[https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/44196](https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/44196)

I did find one thing useful.  A person that posted to the bug report said that they added a printer that ubuntu can not connect to and the problem showed up again.  I do have an old printer set up that I do not have hooked up anymore.  I removed the printer from the System -> Administration -> Printing section.  We'll see if that helps.  I'll be hitting the sack soon and it's usually there in the morning.  :)

---

### Post by emperor on 2006-08-29
I have been experiencing the fanthom gnome-cups-icon 100% CPU usage problem as well.  You can kill it from a terminal.

ps -A  (to get "pid" or run "top")

<then>

kill -9 "pid#"

I do not see any log errors in "/var/log" or /var/log/cups" files.

---

### Post by nimrod_abing on 2006-10-16
I experienced this just a while ago. This is on a desktop machine but like the_One, I used to have  a printer connected, but now I don't have one. I read the Launchpad bug entry for this and it looks like this bug has already been fixed before. Somehow, the fix did not end up in Dapper. Right now they have not decided on fixing this on Dapper yet :confused:

Like the_One I also removed this non-existent printer from my configuration using the Printers GUI. I hope this indeed fixes it.

---

### Post by 3rdalbum on 2006-10-17
Happened to me for the first time today (that I know of), just a minute after login. I only noticed it because I have the CPU monitor in my Gnome panel, so it may have happened a month or more ago when I didn't have the CPU monitor.

---

### Post by mschering on 2006-10-21
Same problem here on a toshiba laptop. Don't know how to solve it yet.

---

### Post by lefteyecc on 2006-11-06
Ok I found a fix.

Edit /etc/cups/cupsd.conf and change HostNameLookups from Double to On

Set the SystemGroup to whatever the group for /var/cache/cups is.

Check your /etc/hosts and make sure localhost is associated with 127.0.0.1.

Restart with CUPS /etc/init.d/cupsys restart and enjoy.

---

### Post by cash1981 on 2006-11-29
I don't have a HostNameLookups in my /etc/cups/cupsd.conf

---

### Post by BeBoxer on 2007-02-13
> **lefteyecc said:**
> Ok I found a fix.

Edit /etc/cups/cupsd.conf and change HostNameLookups from Double to On

Set the SystemGroup to whatever the group for /var/cache/cups is.

Check your /etc/hosts and make sure localhost is associated with 127.0.0.1.

Restart with CUPS /etc/init.d/cupsys restart and enjoy.

My cups.conf doesn't have a HostNameLookups stanze, so I skipped that
I changed SystemGroup to be 'lp' instead of 'lpadmin'. 'lp is the group owning /var/cache/cups

Localhost is properly configured.

Simply restarting cupsys did not quickly fix the problem, so I did a 'killall gnome-cups-icon' as well. We will see how long it lasts. I'm guessing I hit this particular bug at least once a week or so. We'll see if the group 'fixes' it.

---

### Post by BeBoxer on 2007-03-12
The steps above did not fix the problem. After more searching, it appears the bug is actually in cupsys. Or at least Debian has a fix there. As mentioned in [https://launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/44196]("https://launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/44196")

The actual patch is [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=377640;msg=64;filename=65_detect_http_shutdown.dpatch;att=1")

I haven't tried this yet, but I did just rebuild the cupsys .deb file and will be installing it shortly. The cups package actually built a whole host of .deb files. I only tried installing cupsys_1.2.2-0ubuntu0.6.06_i386.deb since I think that is where the patched code is.

---

### Post by jppaynesr on 2008-01-13
For me this just started after the Ubuntu January 11 cups upgrade which changed the following;

Upgraded the following packages:
cupsys (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2
cupsys-bsd (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2
cupsys-client (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2
cupsys-common (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2
libcupsimage2 (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2
libcupsys2 (1.2.8-0ubuntu8.1) to 1.2.8-0ubuntu8.2

Anybody else have the same experience.?????

---

### Post by jppaynesr on 2008-01-13
SOLVED - for me anyway.

I ran sudo top and and killed (k) the pid's that show  "socket" and  "gs". Each was taking 100% of each processor (dual core).

Tested printing and everything was OK. Processor use (as measured by System Monitor 2.18) dropped to my more normal 2%.

---

