---
title: "How do I use Ubuntu passwords and encryption keys for remote SSH?"
date: 2011-05-01
forum: Desktop Environments
---

### Post by usalabs on 2011-05-01
I just recently upgraded from 10.10 to 11.04, but using the classic desktop instead of unity, mainly because unity sucks big time, but that's a different story, anyway, when I used 10.10 I had a key setup for access to my remote SSH server, but now when I try to set up a new key using passwords and encryption, I get:- "Couldn't configure secure shell keys on remote computer", followed by:- '** (process:2532):WARNING **:couldn't open fd 27:Bad file desciptor' 3 lines of this with different process numbers then I got ''** (process:2535):WARNING **:couldn't open fd 27:Bad file descriptor: Permission Denied. Please try again'

I have not changed anything on the remote server at all.  I can access SSH using PuTTy sucessfuly, but I want to set up a key using the ubuntu passwords and encryption key program, but since ugrading to 11.04 I can not do that for some reason.

---

### Post by Tankety on 2011-05-24
I am also having this exact issue with 11.04.  I downloaded the recent one off and installed it and also got the permission denied error when trying to add it to the remote server.  I am fully upgraded.  I dont have any other issues then that.

---

### Post by bdaman80 on 2011-05-30
I also am having this issue since i have moved to 11.04.  was on a mix of 10.04 / 10.10 across 1 laptop, 1 netbook, 2 desktops and 1 home server.  As soon as everything got taken up to 11.04 ~ Unable to log in via any GUI application. I have full access via terminal, but nothing on any Gui application

```

** (process:7239): WARNING **: couldn't open fd 31: Bad file descriptor
Permission denied, please try again. 

** (process:7240): WARNING **: couldn't open fd 31: Bad file descriptor
Permission denied, please try again. 

** (process:7241): WARNING **: couldn't open fd 31: Bad file descriptor
Permission denied (publickey,password). 

```

---

### Post by Herman on 2011-07-24
I encountered this problem too, nearly three months later. 

It turns out to be Bug #78563.
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/785632](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/785632)
Can you guys please add a comment to the bug report to add heat to this bug so it will be more likely to get some attention? 

I think SSH is really cool and it's also really cool to be able to use Seahorse (aka 'Passwords and Encryption Keys') to generate the RSA key and install it in the remote server for us. I wanted to be able to update my how-to for this in the SSH Page in my website but now it looks like I'll just have to wait around till this gets fixed. :sad:

---

### Post by Herman on 2011-07-24
:D At least Seahorse makes the RSA keys for us. It's just not able to copy the public key to the server.

I tried an scp command and that wouldn't work either.

The workaround that I ended up using is surprisingly simple. 
I decided to simply copy the id_rsa.pub file from the .shh directory in the client operating system and paste it into a USB flash memory stick.

Then I plugged the USB into my SSH Server and pasted into the /home/username directory and ran,
```
cat id_rsa.pub >> .ssh/authorized_keys
```

---

