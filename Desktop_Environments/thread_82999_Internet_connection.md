---
title: "Internet connection"
date: 2005-10-27
forum: Desktop Environments
---

### Post by phil66 on 2005-10-27
I have installed Kubuntu Badger Breezy 5.1.0 on a duel boot system with Windows ME

I am now trying to establish a connection with my dial-up ISP using KPPP

First error was that /etc/resolv.conf file was missing and to make one.Made file and install in /etc error cleared.

Second error was that "the remote system is required to authenicate itself.
Found solution in Kppp handbook to add # in front of "auth" in /etc/ppp/options
Comments in options said not to disable "auth" and that the "call option" should be used (see manpages)

I cannot find a call command or an entry in the manpages to instruct me how to use the call option

I went ahead and put the # in front of "auth" and now when Kppp says It starting pppd it shuts down and gives me the following message:

pppd started by user
using interface ppp0
connect:ppp0 <--> /dev/ttyS0
remote message:request denied
pap authenication failed
connection terminated
modem hang up
Exit

Suggested fix is to checked username and password. These have been verified with ISP and also the usage of pap/chap. The password and user name is the same as the Windows ME and it works.

Where do I find instructions on using "call option" or do I need to change something in options to make Kppp work

Thanks in advance for the help
Ray

---

### Post by phil66 on 2005-10-29
Problem solved after talking to 5 tech's at ISP location it was determined they has inserted wrong password in my login sequence.

Thanks
Ray

---

### Post by greatshape on 2005-10-29
[QUOTE=phil66]Problem solved after talking to 5 tech's at ISP location it was determined they has inserted wrong password in my login sequence.

Thanks
Ray[/QUOTE]

Strange, then why did it work on wintendo with the same login credentials?
Just curious ;-)

Steve

---

