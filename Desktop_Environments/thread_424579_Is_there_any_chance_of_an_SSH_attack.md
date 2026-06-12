---
title: "Is there any chance of an SSH attack?"
date: 2007-04-26
forum: Desktop Environments
---

### Post by DeathOnJuice on 2007-04-26
Hey, everyone. I just set up SSH on a machine in my house, but I'm a little worried about security. I'm only going to need it for a couple of 30-minute periods, and I'm behind a router. I simply installed openssh-server through apt-get and did not configure it. Will this be safe, or is there risk of attack? I'm logging with the default account (it has permission to use sudo). If there has already been an attack in this past 30 minutes of running the server, how will I know? How can I fix it (OK, really general...)

And although I seriously doubt this, is the client machine in any danger?

Thanks so much!

---

### Post by qpieus on 2007-04-26
I can't answer all your questions because I'm not an ssh pro by a long shot. But I have done some reading on securing ssh. Here is a link where you can read up on the topic. I have done a few of the suggested changes - change the port, use protocol 2 only, use key authentication, disallow root logins, to name a few. As far as finding out if you've been attacked, the article says ssh makes a log and in there you might see illegal user attempts. There's tons of other info on the web for securing ssh. I think if you follow some of the basic advice, and you are behind a router, you should have no problems.
[http://www.debian-administration.org/articles/455]("http://www.debian-administration.org/articles/455")

---

### Post by DeathOnJuice on 2007-04-26
I just did a complete removal of ssh, so the logs are gone :(. However, I was behind a router, had it running for about half an hour, and the password is a 6-lowercase-letter long sequence (it's my wireless-leeching friend's, not mine, so it's not too secure). Do you think there was any chance for attack, or should I stop worrying?

As you can see, I'm paranoid :) . Thanks again.

---

### Post by PilotJLR on 2007-04-26
Unless you specifically forwarded port 22 from the router to Ubuntu, then there is nothing to worry about. Even if you did forward the port, you would need to be both unlucky and have a terrible password to be hacked in 30 minutes.

Check /var/log/secure for security related messages, like dictionary attacks.

I have a Fedora machine exposed on port 22 for about 6 months once... it WAS attacked several times, but they never got in. Based on logs, it seems their script was checking random usernames like "john" "bob" etc. So keep a watch on the logs and use good passwords.  :-)

---

### Post by az on 2007-04-26
In /var/log/auth.log you will see all ssh log ins and sudo activity since the beginning of time...

---

### Post by qpieus on 2007-04-26
I don't think you have anything to worry about. I have a file and print server that runs 24/7 running ssh and I've never had any problems.

---

### Post by dbott67 on 2007-04-26
Leaving ssh running on port 22 will subject you to all sorts of "internet radiation" of scanners and bots looking for easy-to-crack passwords & such.

As mentioned, changing ssh to some arbitrary port number helps, as does using authorized keys, etc.

Another useful tool is [DenyHosts]("http://denyhosts.sourceforge.net/").
```
sudo apt-get install denyhosts
```

Hey, az... looky what I found!  The other 'z':
[IMG]http://www.julen.net/cfp/alphabet/digital/img/real.z.gif[/IMG]

---

### Post by DeathOnJuice on 2007-04-26
Thanks, everyone! It has been a really informative thread. I'm going to set it up again.

---

### Post by DeathOnJuice on 2007-04-27
OK, I set the SSH server up again, and I'm trying to run a diagnostics program on the remote computer. The problem is, it's a graphical program (it has terminal output, though, so I can still see the results through SSH). When I try to open it, it says it can't open the display and the program doesn't run at all. When I connect using the -Y argument (ssh -Y user@0.0.0.0), the window opens on my computer and obviously runs very slowly since it has to go through the network to be processed on his machine. How can I make the window open on the remote computer?

Thanks in advance!

---

