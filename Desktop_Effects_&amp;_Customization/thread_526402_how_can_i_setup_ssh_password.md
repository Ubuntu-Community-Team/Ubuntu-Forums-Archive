---
title: "how can i setup ssh password"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-08-15
how can i setup ssh password so that when i ssh to the same server, it does not prompt me for password everytime?

Thank you.

---

### Post by buntunub on 2007-08-15
You need to share rsa keys with the server. Its sorta complicated to do so follow the ssh or sshfs wiki that will walk you through the steps.

---

### Post by petit.padavoine on 2007-08-15
You should post in the Networking & Wireless forum but anyway...

On the client:
```
ssh-keygen -t rsa
``` # Generate a key
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote_host
``` # Add the key to the server's list of trusted keys

---

### Post by yinglcs2 on 2007-08-15
Thanks. I did your steps, 

But i stil need to type in mypassword when I ssh to the same box.

And I only have these files in my .ssh directory:

-rw-------  1 scheung scheung 1679 2007-08-15 12:17 id_rsa
-rw-r--r--  1 scheung scheung  404 2007-08-15 12:17 id_rsa.pub
-rw-r--r--  1 scheung scheung  810 2007-08-14 15:35 known_hosts

Can you please tell me what am i missing?

---

### Post by petit.padavoine on 2007-08-15
Hmm that's weird...
Since you have these files, it means that you managed to generate your key.
What output did you get when running
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote_host
```?

(Just checking: you did replace username with your username and remote_host with the ip address or name of the remote machine, right?)

---

### Post by yinglcs2 on 2007-08-15
output:

$ ssh-copy-id -i ~/.ssh/id_rsa.pub scheung@65.169.134.3
29
scheung@65.169.134.3's password: 
Now try logging into the machine, with "ssh 'scheung@65.169.134.3'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.


And in my remote host 65.169.134.3, the '.ssh' directory under my account.
i do see the file authorized_keys.

---

### Post by petit.padavoine on 2007-08-15
> **yinglcs2 said:**
> output:

$ ssh-copy-id -i ~/.ssh/id_rsa.pub scheung@65.169.134.3
29
scheung@65.169.134.3's password: 
Now try logging into the machine, with "ssh 'scheung@65.169.134.3'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.


And in my remote host 65.169.134.3, the '.ssh' directory under my account.
i do see the file authorized_keys.

Well ssh-copy-id seems to think it worked... Did you generate the key from the user from which you're sshing?

Other than that, I'm stumped... Sorry.

---

### Post by buntunub on 2007-08-15
I simply followed the ssh wiki and all worked like a charm. Posting here just wasted some of your time. I suggest you follow that wiki carefully.

---

### Post by petit.padavoine on 2007-08-16
[https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba](https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba) This is the wiki you mean.

BTW I finally figured out why you still need to enter a password. What you're entering is the passphrase you set when generating your key, not your password.

If you want not to enter anything, generate the key again, and this time, when prompted for a passphrase, just press Enter.

---

### Post by buntunub on 2007-08-16
Exactamundo dude. There are many ways to share keys as well. I used to spend time posting questions to forums too and usually ended up more frustrated then when I started. I found that simply following posted guides/wiki's worked 99.999999999999999999999999999% of the time, and thus avoided all further frustration from the process. Additionally, you learn things about linux where you typically do not by having someone else figure things out for you.

---

