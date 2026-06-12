---
title: "Can't sudo due to postfix error"
date: 2009-02-18
forum: General Help
---

### Post by adcwoef on 2009-02-18
Hello,

Suddenly *sudo*  stopped working because of some postfix error. I have no idea at all how this is possible since sudo should not relay on sending mail and I haven't touched a *postfix* or *send-mail* configuration file since June last year. This is the error I get:

```

erikw@compton:~$ sudo ls
[sudo] password for erikw: 
[COLOR="Red"]send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75
Segmentation fault[/COLOR]
erikw@compton:~$ 

```

The great problem is that I can't fix anything either since I cant use *sudo*..... So what do I do?

All help is much appreciated!

---

### Post by adcwoef on 2009-02-19
No ideas? This is really annoying since I don't have physical access to the machine (atm) and I have disabled root login over SSH.

---

### Post by insineratehymn on 2009-02-19
Hmm... have you tried gksudo? Have you tried opening a new bash prompt? Have you tried putting in your install CD and using the "repair broken ubuntu" thingy? Have you tried asking it very politely? Never seen this problem... sorry!

---

### Post by wowbagger53 on 2009-02-19
Don't know about the sendmail problem, but I do know that sudo sends mail if the person doing the sudo is not authorised. Try doing a *sudo -l* which gives a list of authorised sudoers.  *man sudo *will give more information about how sudo works.

Hope this helps.

---

### Post by adcwoef on 2009-02-19
OK. I will try those things. Thanks!

---

### Post by adcwoef on 2009-02-19
I booted the PC with the install CD and started the rescue mode. With the root shell I created the file /etc/postfix/main.cf. When I try to log in now (both normal user and root) it just kicks me out after I have logged in - but this time with no error messages :S

---

### Post by piovisqui on 2009-02-25
The same absurd happens here. No idea why. "sudo" starts to malfunction for no reason. I never touched the postfix/sendmail config, they are as the default installation of Ubuntu 8.10 puts them.

sudo -l
[sudo] password for pio:
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75
Segmentation fault
 
:confused::confused::confused::(

Edit: I filled a bug report. [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/334410](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/334410)

Well, I restared the system and it got almost useless!! I can't log in anymore!! The unique way I can use my laptop now is if I start Ubuntu in recovery mode, log in as root and type "startx". I can not switch users. I can't open some graphical administrations tools, even as root! No network config and bluetooth :(

Do you believe me!?

---

