---
title: "firestarter blocks ldp (cups) printer"
date: 2005-04-10
forum: Desktop Environments
---

### Post by bennettg on 2005-04-10
Hello....nOOb here. 3 months on suse linux and 3 days on ubuntu. I Love it and am so close from getting away from M$, BUT......

I have a samsung ml1430 printer attached to a linksys wireless print server. I use a laptop that connects wirelessly. No problem printing in xp.

in ubuntu, I went to system, administration, printing and configured my printer via lpd at abc.def.g.hij where the abc's are my local ip address for the print server. I could print in suse 9.2 without problems (including with the firewall on). In ubuntu, I can ply print with the firewall (firestarter gui) off.

I searched the ubuntu forums and linuxquestions.org for hours without success. I know I need to set rules (policy) in firestarter, but I havent had any success.

Please help this nOOb!

---

### Post by jonny on 2005-04-11
Try to print with Firestarter open.  When it fails, look at the Events tab; you'll see details of your blocked traffic.  Click on this and choose something like 'Enable traffic of this type'.  I can't engineer a blocked event to testgive you more precise instructions, but it worked for me.

---

### Post by bennettg on 2005-04-11
thanks....i tried your suggestion, but no events logged into firestarter.  any other ideas?

---

### Post by jonny on 2005-04-11
Odd.  If Firestarter's blocking something, it should tell you.  Are you sure it's the firewall that's to blame?

---

### Post by bennettg on 2005-04-11
I was able to see the log.  I tried what you suggested earlier, but had no luck.  I am asure it is me.  perhaps you could suggest a step by step description:

Time: Apr 11 19:07:54 Source: 192.168.1.101 Destination: 64.215.169.208 In IF:  Out IF: eth1 Port: 80 Length: 40 ToS: 0x00 Protocol: TCP Service: HTTP

---

### Post by somuchfortheafter on 2005-04-11
check the refresh button, I just setup a printer via samba today and it did the same thing.

---

### Post by bennettg on 2005-04-11
still no luck.  i am so frustrated. i want away from M$.  i went to the evetn and right clicked and allowed connections to destination, allowed outbound service for everypne and source.  i then clicked refresh and applied the rule. no luck.

the printer says:Ready: Attempting to connect to host 192.168.1.223 for printer L2

---

### Post by jonny on 2005-04-11
I've found the Firestarter logs to not always be complete unless you're actually watching when the trapped event occurs.  I guess there's a configuration setting somewhere that changes this, but life's too short...

Open Firestarter and view the Events tab; then try to print.  You should see a line appearing in the Blocked Connections box.  You need to click (maybe double-click or right click - I can't find any items in my log to check this) on the entry, and say that you always want to permit this type of traffic.

As I said earlier, it's how I fixed Firestarter myself.

---

### Post by bennettg on 2005-04-11
still no luck.  i am a dork.  i like ubuntu so much, more than suse and can be free of m$.  why cant i get this to work?

---

### Post by bennettg on 2005-04-12
anyone else having this problem??? help

---

### Post by bennettg on 2005-04-12
this is the error i get in the events tab:

Time: Apr 12 07:16:09 Source: 192.168.1.101 Destination: 64.233.161.99 In IF:  Out IF: eth1 Port: 80 Length: 40 ToS: 0x00 Protocol: TCP Service: HTTP

---

### Post by Darrena on 2005-04-12
[QUOTE=bennettg]this is the error i get in the events tab:

Time: Apr 12 07:16:09 Source: 192.168.1.101 Destination: 64.233.161.99 In IF:  Out IF: eth1 Port: 80 Length: 40 ToS: 0x00 Protocol: TCP Service: HTTP[/QUOTE]

First, stop firestarter and see if print works.

LPD is tcp port 515 I think, but IP Print which your windows box is probably using 9100 so unless I am missing something you shouldn't be using LPD to print to that printer just IP print.

I think (I don't have my box in front of me with a printer) but try using CUPS IPP to print

On a side note this forum isn't for questions so a mod will likely move it to the right place soon.

---

### Post by bennettg on 2005-04-13
printing works without the firewall on under lpd.  i entered 192.168.1.223 with L2 as the que.  i have also tried 192.168.1.1 as ipp, but perhaps i need to add something?  for example, should i be enterering ipp://192.168.1.223:631

---

### Post by shakin on 2005-04-13
I don't know much about reading firewall logs, so excuse me if I'm wrong, but your log doesn't look like it has anything to do with LPD.

Time: Apr 12 07:16:09 Source: 192.168.1.101 Destination: 64.233.161.99 In IF: Out IF: eth1 Port: 80 Length: 40 ToS: 0x00 Protocol: TCP Service: HTTP

Port 80 http? That's web traffic. IP 64.233.161.99 is Google.

Try this: In Firestarter under the policy tab, change the dropdown to edit your outbound traffic policy. It is permissive by default? In other words, permissive by default lets everything through unless you specifically block it. Do you have any blocking rules? If you have it set to restrictive by default, you can either change it to permissive or add an outbound rule to your print server (might be 192.168.1.1).

For LPD you should not need to allow inbound connections. I print to a Dell LPD server here and didn't need to touch Firestarter for it to work. Just in case, you can try adding an inbound rule from the print server IP to see what happens.

---

### Post by fire59 on 2005-04-13
I have the same problem. I even added a rule for lpp and open port 631 for everyone and it still doesn't work.  Gave up on it and now I have to disable my firewall each time i want to print.  Another weird thing is on some website it would block it to: for example go to [www.bensbargains.net](www.bensbargains.net) it would just spin till i disable firestarter.

---

### Post by Turin Turambar on 2005-04-20
I recommend you to update firestarter to 1.0.3. It solved for me the dictionary problem.

---

### Post by lsiden on 2005-04-27
[QUOTE=Turin Turambar]I recommend you to update firestarter to 1.0.3. It solved for me the dictionary problem.[/QUOTE]
 Where did you get firestarter?  "apt-cache search firestarter" turns up zip.

---

### Post by notzac on 2005-04-27
[QUOTE=lsiden]Where did you get firestarter?  "apt-cache search firestarter" turns up zip.[/QUOTE]

It's there - you just need to enable the Universe repository first. :)

---

### Post by jcohen on 2005-07-18
You probably want to allow port 631 (on the printer server) which is the port CUPS listens and broadcasts on. In firestarter right click in the Allow Service column and choose Add Rule. Then type 631 in the Port section and choose OK. this will allow incoming access. 

Nevermind- I read your original post again and noticed that you are using a linksys wireless print server. I've had problems myself with networked CUPS printers and firestarter. See [https://launchpad.ubuntu.com/malone/bugs/1492](https://launchpad.ubuntu.com/malone/bugs/1492)

---

### Post by dana_rea on 2007-07-16
I had some difficulty getting network printers to work & be detected with Firestarter 1.0.3 in Feisty (also using inbound and outbound policies).

Anyway, the work around I found was to give up on auto-detection and add the printer myself. If you need to figure out the printer settings to do this, use auto-detect with the firewall turned off to get the printer url (i.e. ipp://<cups server ip>:631/<printers>/<printer name>).

I suspect that Firestarter and the gnome-cups-manager firewall function don't play well in some way or another. My suspicion is that 'detect printers' doesn't (or is unable to) set all the necessary rules. Perhaps an iptables guru can look into this further.

---

