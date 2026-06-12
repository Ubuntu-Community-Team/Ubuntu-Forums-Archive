---
title: "SSH trouble"
date: 2005-02-23
forum: Desktop Environments
---

### Post by Jonathan Drain on 2005-02-23
When ssh-ing into a server, it stalls once I've entered my password. I'm connecting to the server, because if I enter an incorrect password it gives me an error as usual, but once I enter the correct password it just stalls instead of bringing up the shell like it should. I'm using Warty.

This problem occurs on all three servers I have accounts on, and I can ssh in to them normally from a Windows machine on the same network. I'm using password authentication, not keys.

Can anyone suggest a solution to this?

---

### Post by alastair on 2005-02-23
You could try adding the debug flag to sshd on the linux side i.e. edit :

/etc/default/ssh

and make :

SSHD_OPTS="-d"

then restart sshd (/etc/init/d/ssh restart) and check the logs.

It might be something simple like reverse DNS lookup (or something) - perhaps try adding your NT hostname/IP to /etc/hosts.

---

### Post by Jonathan Drain on 2005-02-24
I don't have access to the linux side, it's not my server.

Edit: and both sides are linux.

---

### Post by alastair on 2005-02-24
Well, there's also a "-v" option to ssh (man ssh) - perhaps that would help.

---

### Post by Jonathan Drain on 2005-02-24
[QUOTE=alastair]Well, there's also a "-v" option to ssh (man ssh) - perhaps that would help.[/QUOTE]
 I've used -vvv, it spews a bunch of debug data at me, getting as far as before it stalls:

```
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
```

Someone else tells me that theirs has this line after that:

```
debug2: channel 0: rcvd adjust 131072
```

---

### Post by p!=f on 2005-02-24
Don't you have any firewall running on your desktop?

---

### Post by Jonathan Drain on 2005-02-24
[QUOTE=p!=f]Don't you have any firewall running on your desktop?[/QUOTE]

Not on the Ubuntu box, I would assume. My Windows machine, which can ssh, might or might not be running ZoneAlarm.

As for my network layout, though, it's something of a mess, but I'll describe it in case it's relevant. I have this little green five-port network hub into which plugs two Win2k boxes, my Ubuntu box and a D-Link 300T DSL modem. One Win2k box has its IP on "get IP from from network", the other Win2k box and my Ubuntu box have had their IPs and whatnot set manually, using the modem's address as a gateway.

---

### Post by Jonathan Drain on 2005-02-25
Another fun thing is that PuTTY under WINE works perfectly, but ssh doesn't.

---

### Post by jdodson on 2005-02-25
by default ssh passes the username you are using in gnu/linux to the server you are logging in to.  so if you have on your home machine the user "frankg" and the server has your username to be "fgrimes" then you will be attempting to login as "frankg" when you have no "frankg" account.  check to see if your username is different.  if it is, then you can pass in a argument to change the user account via:

ssh -l [login name]

---

### Post by Jonathan Drain on 2005-02-27
Tried it, even though it shouldn't matter because I'm the same username on all three servers as well as my own box.

---

### Post by Jonathan Drain on 2005-03-06
I wonder if this qualifies for the "Stumper Questions" board yet.

---

### Post by alastair on 2005-03-07
Probably qualifies! But that firum looks pretty dead.

How long have you waited after giving your password?

It's obviously doing something - I suspect some sort of reverse DNS lookup, but can't explain why windows putty works here. I have a vague recollection that I have had this problem a long time ago - but it would get in after a long wait.

I know it is not your server, but is there no help/support at the server end? At least someone you can ask to look at the log file?

---

### Post by Jonathan Drain on 2005-03-13
[QUOTE=alastair]Probably qualifies! But that firum looks pretty dead.

How long have you waited after giving your password?

It's obviously doing something - I suspect some sort of reverse DNS lookup, but can't explain why windows putty works here. I have a vague recollection that I have had this problem a long time ago - but it would get in after a long wait.

I know it is not your server, but is there no help/support at the server end? At least someone you can ask to look at the log file?[/QUOTE]
 Just now I tried it and waited ten or fifteen minutes and it hasn't connected yet. **Edit:** After waiting some longer I get ```
Read from remote host akarihosting.net: Connection timed out
Connection to akarihosting.net closed.

```

None of the admins at the three servers hae any idea what the problem is. They could most likely check their logs, but I'm not sure they'd know what they are checking their logs *for*.

---

### Post by alastair on 2005-03-13
I had an odd problem at work a week ago. A mailserver machine could not send mail to a particular mail server - I tried a "telnet" to port 25 from this host - and nothing (it timed out). Other hosts worked fine.

It turned out to be "explicit congestion notification" (ecn) being ON. This is very obscure - but perhaps worth a look. Ofcourse, it could be something else enabled in your IPV4 stack.

Check :

cat /proc/sys/net/ipv4/tcp_ecn

If it is "1", try and "echo" a "0" to it.

---

### Post by Jonathan Drain on 2005-03-13
It is a "0".

---

### Post by admp on 2005-03-21
I have the same problem. :(
What's not funny at all, I tried GTK build of putty, and it works! I have also tested few different distros (warty, older hoary, knoppix) and they all have failing ssh client.
I suppose this has to do something with NAT that my router does, but why putty works then?

---

### Post by admp on 2005-03-23
Finally, it works now. This appears to have been problem of my ISP.
However, it is quite strange why putty worked.

---

### Post by Jonathan Drain on 2005-03-28
Any idea why it works for you and not me, then?

I still cannot get it to work.

---

### Post by admp on 2005-03-28
I'm not sure whether I'm correct (possibly I am not), but there might be something with MRU&MTU (maximal receive/transmit unit) values. However, I tried to change both of these on my router, and on my own computer, but neither helped.
Most strangely, SMTP didn't work for me then; but next day everything was just fine -- connections over SSH were fine, thus I decided this was ISP's problem.
No hints here. Sorry ;-)

---

### Post by Jonathan Drain on 2005-05-04
I still haven't found a solution to my problem, other than installing PuTTY which isn't as good as the command-line "ssh". Can anyone suggest a solution to problem?

---

### Post by Jonathan Drain on 2005-06-16
It's June, now, and I have upgraded to Hoary, to no luck. It's been a month and a half since my last post to this thread and I decided to ask again.

Please, can someone help me getting ssh to work? PuTTY under Windows never had this trouble, why does 'ssh' in Linux have it?

---

### Post by Jonathan Drain on 2005-07-01
It's July, now.

Please, can someone help me getting ssh to work? PuTTY under Windows never had this trouble, why does 'ssh' in Linux have it?

---

