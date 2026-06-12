---
title: "Jailbroken iPod touch: SSH » Host key verification failed."
date: 2009-01-10
forum: General Help
---

### Post by Masquerade on 2009-01-10
Hey everyone,
I have jailbroken iPod touch, first gen, FW 2.2. Because of some configuration errors, i had to restore and rejailbreak the device.
So whenever i want to ssh, i get the following errors:

in the terminal
```
benjamin@moser-linux:~$ ssh root@10.4.24.118
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
9e:2d:0b:a3:32:5c:5a:c7:f3:2e:87:9e:7c:13:ac:67.
Please contact your system administrator.
Add correct host key in /home/benjamin/.ssh/known_hosts to get rid of this message.
Offending key in /home/benjamin/.ssh/known_hosts:2
RSA host key for 10.4.24.118 has changed and you have requested strict checking.
Host key verification failed.

```

We dont have to think about the man-in-the-middle-attack; its an internal network i am in; so its something with the host keys. the problem is that i dont have a clue what they are^^

Using Nautilus, i get the following error (freely translated, german screenshot is attached):
> Error checking the server/host keys. Please select another viewer and try again.

Can someone help me with this? Thanks a lot!

---

### Post by Masquerade on 2009-01-16
no one can help me?

---

### Post by Nepherte on 2009-01-16
```
Add correct host key in /home/benjamin/.ssh/known_hosts to get rid of this message.
Offending key in /home/benjamin/.ssh/known_hosts:2

```
You either add the correct host key to known_hosts or you remove the offending key. If you choose to do the latter, the next time you try to ssh in your ipod, it will prompt you with the host key verification screen. Press Y to accept.

---

### Post by Masquerade on 2009-01-16
Thanks a lot.  I simply removed the line that was wrong. And you have to type "yes" ^^

---

