---
title: "Unable to open Adept Manager / Sudo errors"
date: 2009-03-05
forum: Desktop Environments
---

### Post by Red Rhino on 2009-03-05
I recently installed Kubuntu 8.04, within the past week, and have just now starting having a problem with opening the Adept Manager or using Sudo. Both of these programs were working fine yesterday. When I try to open Adept Manager, the program attempts to start then closes. When I try to issue a sudo command line, I get the following error:

>>>sudoers file: syntax error, line1 <<<
sudo: parse error in /etc/sudoers near line 1

It does not matter what command I use with sudo it returns the same error. The last thing I setup on my machine was Smb4k, this probably has something to do with it, but not sure what. The Smb4k is working fine so I hope I don't have to uninstall this to get sudo working as I do need to access Samba shares.

As someone that is still new to Linux, any help would be appreciated.

---

### Post by taurus on 2009-03-05
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Red Rhino on 2009-03-05
I tried your suggestion and here is what happened:

Case #1 - adduser says that I am already a member of admin
Case #2 - unable to run sudo commands due to problem stated above
Case #3 - returned no errors, but problem still exists.

Thanks

---

### Post by taurus on 2009-03-05
According to your error message from your OP, there is something wrong with /etc/sudoers, near the top.  Did you check your /etc/sudoers while you were in the recovery mode?

Otherwise, post it here.

---

### Post by Red Rhino on 2009-03-05
I was eventually able to get into the /etc/sudoers file and found that on the first line was the word PASSPROMPT

I do not know what this command or word represents, but when I removed it and saved the file the sudo command began to work again, including Adept Manager.

Thanks for the help!

---

