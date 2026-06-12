---
title: "Problem with apache2"
date: 2006-04-06
forum: Desktop Environments
---

### Post by rocarm on 2006-04-06
I accidently sudo apt-get install apache instead of apache2. 
now i've sudo apt-get remove apache. and sudo apt-get install apache2

but i can't get [http://localhost](http://localhost) to work. 

i've restarted the server, and also restarted apache itself. 
but no go. It just comes up with 
"the connection was refused when trying to connect to the local host"

anyone have any ideas?](*,)

---

### Post by amohanty on 2006-04-07
ALl this assumes that you did not mess with the default conf files .

First check whether the apache process is running at all using:
> ps aux | grep apache

If it is an everything is all right, check if port 80 is open, you can do so by:
> sudo apt-get install nmap
sudo nmap -vV -sS -p80 your_machine_ip

or 

> telnet your_machine_ip 80
If this just presents you with a blank screen it means the ports open.

If all of this is ok, then check to see if firestarter or some other firewall is not interfering.

HTH
AM

---

### Post by rocarm on 2006-04-07
thanks for replying, 
i couldn't get into port 80. i installed nmap and did what you said, but no go. 
i just realised i isntalled firestarter on my pc via automatix. 

i can't find it anywhere. the filesystem for linux is kindof confusing. where could i find the config file? The program itself doesn't appear in my menu structure on gnome

---

### Post by amohanty on 2006-04-07
Tutorial:
[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

I dont use it, but I believe you will find it under Applications->System Tools->Firestarter

Just make sure that you unblock port 80 and try again

AM

---

### Post by rocarm on 2006-04-07
thanks, i stopped the firewall from blocking any traffic. (i turned it off) and i still can't get to port 80. 

eh, i'm just going to reinstall ubuntu!
thanks anyway.

---

### Post by amohanty on 2006-04-07
Hold on there! dont reinstall ubuntu, just for this. The thing is if you dont figure out what happened, it might happen again and you still wont know how to fix it.

Try the following: (assuming you stopped firestarter/iptables
> apachectl restart
apachectl does a graceful restart
[http://httpd.apache.org/docs/2.0/programs/apachectl.html](http://httpd.apache.org/docs/2.0/programs/apachectl.html)

if its not runnign it will complain.
Then do the nmap thing again and see if port 80 is open only thi time check all ports using:

> nmap -vV -sS -p1-65535

HTH
AM

---

