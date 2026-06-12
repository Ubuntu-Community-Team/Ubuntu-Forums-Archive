---
title: "vsftpd I am confused"
date: 2009-04-02
forum: General Help
---

### Post by jigglywiggly on 2009-04-02
Here is what I want to do: Use FTPS to access a folder located in /home/administrator/webroot/warkid
I want this to be accessible under the account "warkid" with a password of my choice. So to first make an account for this user and I want him locked into that warkid folder... I did
sudo useradd warkid
sudo passwd hispasswd

but how do I lock him in that warkid folder?

Next part uhm what next part I got confused D:

So I went into the config file by sudo gedit /etc/vsftpd.conf
I disabled anonymous access and I thought that should be it?
Well when I try to connect under the account of warkid with that password I set under port 22 it just says connection timed out on filezilla, then I also tried 21, and 20. I want to connect using ftps and I don't want any unsecure ftp if possible.
So how do I lock the user warkid in his folder? Howcome it won't connect? What am I doing wrong D: (PS why is there no gui under webmin or something? I mean setting a ftp server in IIS or filezilla is 100000x times easier)

---

### Post by jigglywiggly on 2009-04-02
Oh wait I got the user account warkid setup correctly in that folder, it was under administration yay for GUI :D 
But why is vftpds or w/e so annoying to use... I still need help on that D:

---

