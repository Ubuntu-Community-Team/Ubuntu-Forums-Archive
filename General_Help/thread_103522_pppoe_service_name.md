---
title: "pppoe service name"
date: 2005-12-14
forum: General Help
---

### Post by kalin on 2005-12-14
Hi there,

My ISP requires setting a specific "service name" for the PPPoE connection, unfortunately the "pppoeconf" tool doesn't provide such a setting. I've looked in the generated configuration file (/etc/ppp/peers/dsl-provider), but there's no hint of such an option. There's nothing about it in the pppoeconf/pppd man pages also.

All solutions I've found on the web have you edit a config file - /etc/ppp/pppoe.conf, which is not present in my system. Additionally it seems to be used only by some Red Hat (I believe) tools - adsl-start and similar.

Does anyone know how/where should I put a pppoe service name?

I'm running Ubuntu 5.10 on an old iMac G3, ethernet is fine, the technician connected successfully to create my account, his account doesn't need the service name and it worked fine with pppoeconf.

---

### Post by looz44 on 2008-02-03
i don't know if it's even worth answering this since it dates 3 years ago :D
however, this is the exact problem i had, and i found a solution for it.

anyone interested? because if not, i won't bother explaining! :P

---

### Post by kalin on 2008-02-03
An old question indeed. At the time I installed [rp-pppoe]("http://www.roaringpenguin.com/products/pppoe"), which allowed me to use the "service name".

It's a separate app though, you need to login for it to start etc... not nice. Now I've got a Linksys router (WRT54GL) - works like a charm :)

Still, it'd be interesting to know... What's your solution?

---

### Post by looz44 on 2008-02-04
hehe that's indeed what i did!!! (but then i found smthg else)

eventhough the gui version of rp-pppoe didn't work at the beginning (because there was another package to install which i didn't notice right away, anyway when i got the gui working, it would give this error about write permissions eventhough i used sudo...)
however, the shell version worked fine, but still it didn't have the service name option!!!! so i went looking in the config file to find the explicit option for service name and add it manually, which made it finally work.
i suppose that in your case, the gui worked?

anyway that's not the other way i found out!!! :D
after reading some posts about the subject, one of them mentionned that this was easily done with the pppoe package.
so i installed it, and read the manual.
it said that it could be used from within the pppd command (which is the one that opens all network connections and doesn't directly support a service name, that's why it uses the pppoe command)
so i figured that i was supposed to add the pppoe command with the correct parameters in the configuration file that pppd uses to establish the pppoe connection (which is the /etc/ppp/peers/dsl-provider file)

the line          pty "/usr/sbin/pppoe -S 'Turtle4' -C 'Zoo'"              ( where Turtle4 is the service name, and Zoo is the account name)
should be added after the               pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"       line in order to work

plz recall that the guy in the post mentioned "easy" eventhough i didn't find this easy at all!!! :D

so this, i think, is the fastest and most direct way to make it work without using third-party software.
nevertheless, somebody should really really implement a decent graphical interface for configuring all internet connections in Ubuntu!!! it's still a headache to connect to the internet, without which Ubuntu is nothing!!!
it's essential for users (especially unexperienced) of Ubuntu to be able to easily connect to the internet, because most of ubuntu features requires you to be online :S
and of course, when/if they make a gui for this, they should remember putting a service name option for losers like me who don't have a router :D

cheers!

---

### Post by Snitz on 2008-03-27
> **looz44 said:**
> hehe that's indeed what i did!!! (but then i found smthg else)

eventhough the gui version of rp-pppoe didn't work at the beginning (because there was another package to install which i didn't notice right away, anyway when i got the gui working, it would give this error about write permissions eventhough i used sudo...)
however, the shell version worked fine, but still it didn't have the service name option!!!! so i went looking in the config file to find the explicit option for service name and add it manually, which made it finally work.
i suppose that in your case, the gui worked?

anyway that's not the other way i found out!!! :D
after reading some posts about the subject, one of them mentionned that this was easily done with the pppoe package.
so i installed it, and read the manual.
it said that it could be used from within the pppd command (which is the one that opens all network connections and doesn't directly support a service name, that's why it uses the pppoe command)
so i figured that i was supposed to add the pppoe command with the correct parameters in the configuration file that pppd uses to establish the pppoe connection (which is the /etc/ppp/peers/dsl-provider file)

the line          pty "/usr/sbin/pppoe -S 'Turtle4' -C 'Zoo'"              ( where Turtle4 is the service name, and Zoo is the account name)
should be added after the               pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"       line in order to work

plz recall that the guy in the post mentioned "easy" eventhough i didn't find this easy at all!!! :D

so this, i think, is the fastest and most direct way to make it work without using third-party software.
nevertheless, somebody should really really implement a decent graphical interface for configuring all internet connections in Ubuntu!!! it's still a headache to connect to the internet, without which Ubuntu is nothing!!!
it's essential for users (especially unexperienced) of Ubuntu to be able to easily connect to the internet, because most of ubuntu features requires you to be online :S
and of course, when/if they make a gui for this, they should remember putting a service name option for losers like me who don't have a router :D

cheers!

In the dsl-provider file under /etc/ppp/peers, I don't see the following line.

/usr/sbin/pppoe -I eth0 -T 80 -m 1452

How did it work for you?

---

### Post by jaithehulk on 2008-05-26
> **looz44 said:**
> hehe that's indeed what i did!!! (but then i found smthg else)

eventhough the gui version of rp-pppoe didn't work at the beginning (because there was another package to install which i didn't notice right away, anyway when i got the gui working, it would give this error about write permissions eventhough i used sudo...)
however, the shell version worked fine, but still it didn't have the service name option!!!! so i went looking in the config file to find the explicit option for service name and add it manually, which made it finally work.
i suppose that in your case, the gui worked?

anyway that's not the other way i found out!!! :D
after reading some posts about the subject, one of them mentionned that this was easily done with the pppoe package.
so i installed it, and read the manual.
it said that it could be used from within the pppd command (which is the one that opens all network connections and doesn't directly support a service name, that's why it uses the pppoe command)
so i figured that i was supposed to add the pppoe command with the correct parameters in the configuration file that pppd uses to establish the pppoe connection (which is the /etc/ppp/peers/dsl-provider file)

the line          pty "/usr/sbin/pppoe -S 'Turtle4' -C 'Zoo'"              ( where Turtle4 is the service name, and Zoo is the account name)
should be added after the               pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"       line in order to work

plz recall that the guy in the post mentioned "easy" eventhough i didn't find this easy at all!!! :D

so this, i think, is the fastest and most direct way to make it work without using third-party software.
nevertheless, somebody should really really implement a decent graphical interface for configuring all internet connections in Ubuntu!!! it's still a headache to connect to the internet, without which Ubuntu is nothing!!!
it's essential for users (especially unexperienced) of Ubuntu to be able to easily connect to the internet, because most of ubuntu features requires you to be online :S
and of course, when/if they make a gui for this, they should remember putting a service name option for losers like me who don't have a router :D

cheers!
hey whats the account name??
Is it the username??

---

