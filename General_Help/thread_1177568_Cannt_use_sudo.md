---
title: "Cannt use sudo"
date: 2009-06-03
forum: General Help
---

### Post by Harry2 on 2009-06-03
Okay, Upon installing I was asked to create a username and password... I was very tired and forgot the password. So that was it, I couldnt get onto ubuntu and ran in recovery mode, then made a new user from that. But here is my problem, I am not root admin or w/e so I cannot install any packages/plugins etc.

What can/should I do?
(I am new to linux/ubuntu)


Thanks.

---

### Post by BslBryan on 2009-06-03
Hello, Harry2. :-)

First, Turn your computer on.  While GRUB is loading, press Esc.
Then, press ```
e
``` to edit.

Highlight the line that begins kernel ........., and press ```
e
```.
Then, go to the very end of the line, and add ```
rw init=/bin/bash
```

Next, press ```
enter
```, then ```
b
``` to boot your system.

**Your system will boot up to a passwordless root shell**.
**[COLOR="Red"]This is a completely root shell! It is possible to damage your system if not careful![/COLOR]**
Type in ```
passwd <username>
```, replacing <username> obviously with your username. :p

Finally, set your password to what you want.

To reboot, type ```
reboot now
```

I hope this works for you! :-)  Good luck.

---

### Post by Harry2 on 2009-06-03
Ok thanks, But I think I tried that and said rw was not recognised or something, I will retry anyway ^^

oh, And do I need to know my root admins login name?

---

### Post by michy99 on 2009-06-03
The easiest way to reset the password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Harry2 on 2009-06-03
ooh, Thanks!

I will try that one now!

Edit:
Wow, It was that easy??

Thanks

---

