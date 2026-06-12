---
title: "IP address banned??"
date: 2012-06-15
forum: Forum Feedback &amp; Help
---

### Post by scorp123 on 2012-06-15
@admins:

Whenever we try to access [http://www.ubuntuforums.org](http://www.ubuntuforums.org) from our workplace we're informed that ubuntuforums.org has banned our IP ... !?

Is there any way to resolve this? Or at least get information on *why* exactly our IP range was banned?

Could please any forum admin get in touch with me?

Thanks.

---

### Post by valvegrid on 2012-06-15
It is probably your workplace firewall blocking, I have the same I'm on a large network, if you have a word with your IT department they might unblock it, but unless it impinges on your work I doubt if they will.

---

### Post by nothingspecial on 2012-06-15
Moved to Forum Feedback & Help

---

### Post by scorp123 on 2012-06-15
> **valvegrid said:**
> It is probably your workplace firewall blocking  We are in total control of all firewalls and we don't block any outgoing traffic or protocol whatsoever.

---

### Post by scorp123 on 2012-06-15
> **nothingspecial said:**
> Moved to Forum Feedback & Help How can I get help for this? We could really use access to the Ubuntu Forums from time to time; not being able to access them sucks very much for our jobs ... :(

---

### Post by SeijiSensei on 2012-06-15
I suggest a little testing is in order.

First, can you ping [www.ubuntuforums.org](www.ubuntuforums.org) or its IP address, 91.189.94.12?  If not, try running a traceroute to see where the connection times out.

If you can ping the server, try:

```

[COLOR="blue"]telnet 91.189.94.12 80[/COLOR]
Trying 91.189.94.12...
Connected to 91.189.94.12.
Escape character is '^]'.
[color=blue]GET / HTTP/1.1
Host: ubuntuforums.org
[hit enter]
[hit enter again][/color]

```

Type the entries in blue. What happens?  You should see the HTML source for the forums home page.

---

### Post by scorp123 on 2012-06-15
> **SeijiSensei said:**
>  First, can you ping [www.ubuntuforums.org](www.ubuntuforums.org) or its IP address, 91.189.94.12?   I can read the message right inside my browser. So the reachability should be there ... or how else would I see the message?

Screenshots:

[http://dl.dropbox.com/u/1614648/tmp/Ubuntuforums_IP-banned.jpg]("http://dl.dropbox.com/u/1614648/tmp/Ubuntuforums_IP-banned.jpg")

[http://dl.dropbox.com/u/1614648/tmp/Ubuntuforums_vBulletinMessage.jpg]("http://dl.dropbox.com/u/1614648/tmp/Ubuntuforums_vBulletinMessage.jpg")

I tried with different OS (Solaris 10, Windows 2003, Windows 2008, Windows 7, RHEL 5, Ubuntu 11.10, Ubuntu 12.04) from different subnetworks and with different browsers (Safari, Chrome, Chromium, various versions of Firefox ...) and the message above is always the same.

I also logged in and filled out a contact form ... but it's nearly been a week now and no reaction so far. And yes, I left my real name, my real phone number, my real company e-mail, my real company homepage URL ... 

As for your questions:

- nslookup resolves correctly
- ping works, average answer time is around 21 ms
- telnet to port 80 doesn't work, after *"GET / HTTP/1.1"* telnet hangs forever, I need to use *"killall telnet"* to get rid of it again.


I just tested your telnet command with other web sites that are known to work (e.g. Google, Oracle, Microsoft, Facebook, etc.) too and it also fails there. So I'd have to guess that the syntax isn't correct.

---

### Post by spynappels on 2012-06-15
What exactly do you see when you try to access ubuntuforums?

Are you on a static or dynamic IP? I'm wondering if the address was blocked for spamming when someone else had it, and now that it has recycled to you, you're stuck with the blocked ip. you could try to recycle the ip again by rebooting the router if this is the case.

---

### Post by CharlesA on 2012-06-15
scorp123: Can you go to whatismyip.com and PM me what IP address it says.

Thanks,
Charles

---

### Post by scorp123 on 2012-06-15
> **CharlesA said:**
> scorp123: Can you go to whatismyip.com and PM me what IP address it says.  PM containing all the details sent. Thanks in advance :)

---

### Post by CharlesA on 2012-06-15
> **scorp123 said:**
> PM containing all the details sent. Thanks in advance :)
I passed it along to the admins.

Thanks!

---

### Post by coffeecat on 2012-06-15
@scorp123, thanks for sending the information. You should be OK now. If you have any further problems, please let me or any of the staff know.

Sorry for the inconvenience. I'm afraid this is just one more case where spammers cause problems for all of us.

---

