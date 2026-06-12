---
title: "Transferring files and remote desktop"
date: 2009-03-10
forum: General Help
---

### Post by jdelasalas on 2009-03-10
I was just wondering, I got this question while playing with remote desktop, is there any way I can transfer files using remote desktop.  I just installed linux on my other laptop and I wanted to move over most of my documents.

---

### Post by yther on 2009-03-10
I don't think you can do it directly, but if you set up SSH on one machine, then you can open a SFTP session to the other and move files securely from one to the other over an encrypted connection.  Check the Ubuntu documents (help.ubuntu.com) for steps on setting up SSH service.  (Hint, don't leave it on port 22 or you will get hundreds of people trying to crack it all day.  Set a strong password and put it on some random port that isn't listed in /etc/services.)

I do this and it works nicely, whether I'm moving files across the room or across the city.  :)

---

### Post by jdelasalas on 2009-03-10
Could you crash course how to get that up and running?

---

### Post by yther on 2009-03-10
help.ubuntu.com -> Search -> ssh -> [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by HermanAB on 2009-03-10
Install ssh-server on one machine.

Then log in from another machine using Nautilus 'File menu, Connect to server', select SSH and type in the IP address and user name and click OK, then type the password when asked.

Now open another instance of Nautilus and click-drag-drop files between the two machines.  It really cannot be easier.

You can also use FileZilla client to connect from a Windows machine.

Yes, it really IS that easy!

Cheers,

Herman

---

