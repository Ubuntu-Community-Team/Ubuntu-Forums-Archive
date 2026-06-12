---
title: "SSH Warning Message (RSA host key has been changed)"
date: 2008-12-02
forum: Desktop Environments
---

### Post by Eric Boring on 2008-12-02
I have searched for information on this, but I can't seem to find anything that quite fits what I am experiencing. I appreciate any help you all can offer.

I have two Ubuntu boxes on my network. I have been using cygwin to ssh into these boxes now and then. From my personal XP laptop, I can still ssh in with no problem. From the work XP laptop, I get the scary message below.

The odd thing is that if I ssh into the local IP address instead of using the computer name, it seems to work fine. Also, the IP address is lists in the message below is an external address (not the address I use within the LAN). EDIT: Actually it seems to be an address associated with my employer! (according to an online ip lookup service). Coule this just be an odd confusion resulting from the VPN we use for work?

So my question is, am I really experiencing DNS Spoofing and/or a MITM attack, or did the upgrade this weekend simply change the RSA keys? 
[LIST]
I use WPA2 for my wireless, with a firewall on the router. I do not have any incoming ports open on the router. I only access these machines from within my LAN.[/List]
[LIST]I do not have firewalls or antivirus installed on the Ubuntu machines.  [/List]
[LIST]I do have firewalls and antivirus in use on the Windows machines
[/List]

Thanks for any help.

-Josh

```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for XXXXXX has changed,
and the key for the corresponding IP address XX.XX.XXX.XX
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
XX:XX:XX:XX:etc
Please contact your system administrator.
Add correct host key in /cygdrive/c/Documents and Settings/xxxxx/.ssh/known_hos
ts to get rid of this message.
Offending key in /cygdrive/c/Documents and Settings/xxxxx/.ssh/known_hosts:3
RSA host key for frankendevo has changed and you have requested strict checking.

```

---

### Post by Eric Boring on 2008-12-03
I wonder if I've posted this in the wrong forum? Any suggestions on where this would be a better fit?
Thanks,
-Josh

---

### Post by mannih2001 on 2008-12-03
I'm quite sure it's the wrong forum, but anyway:

Since you say it's working when directly using the IP address, I guess you really have a kind of dns issue. And since the address you get when using the hostname if part of your company network, it seems that you local host names are clashing with your company's and the company wins. 

You can easily tell ssh which IP to use for which hostname by creating a ~/.ssh/config file (not sure where to place this with cygwin):

```

Host foo
Hostname 127.0.0.3

```

This would associate the name 'foo' with the address '127.0.0.3'

---

### Post by kernelhaxor on 2008-12-04
I think the upgrade would have just changed the RSA key .. I ran into this problem sometime earlier .. I just deleted the entry for that IP/hostname in my ~/.ssh/known_hosts file .. then reconnected successfully

---

### Post by Eric Boring on 2008-12-04
Thanks for the responses. Naturally, my main concern is whether I have a security issue here. It sounds like it's probably not an actual attack?

Also, I found this thread: [http://ubuntuforums.org/showthread.php?t=243926](http://ubuntuforums.org/showthread.php?t=243926), and it occurred to me that I have installed Ubuntu through WUBI recently on this computer, so now it is a dual boot machine as well. Could this have created the confusion?

Thanks again,

-josh

---

### Post by mannih2001 on 2008-12-04
> **Eric Boring said:**
> ...so now it is a dual boot machine as well. Could this have created the confusion?


If the machine you are talking about is the one your are trying to ssh to, then yes, definitely. Each os will have a different finger print then.

---

### Post by Eric Boring on 2008-12-04
Actually, the Dual Boot machine in the client. The Host is only Ubuntu 8.10, which recently had a regular round of updates.

---

