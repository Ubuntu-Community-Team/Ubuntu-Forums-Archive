---
title: "Hl2 dedicated server root?"
date: 2011-03-01
forum: Gaming &amp; Leisure
---

### Post by tailwhipm on 2011-03-01
Hello, im running a hl2 server and i want to know why i have to run it as root putting sudo before the command to start it up. When i do i get this message.
************** WARNING ***************
Running the dedicated server as root
is highly discouraged. It is generally
unnecessary to use root privileges to
execute the dedicated server.
**************************************

Im curious as to why, running the dedicated server as root is not such a good idea?And if so how can i run it without using sudo?

---

### Post by Perfect Storm on 2011-03-02
Because your server will properly be compromised really really quickly by ill-intended hackers etc.

---

### Post by tailwhipm on 2011-03-02
It wont permit me to run it if i dont use sudo, so how do i run it without sudo?

---

### Post by gmargo on 2011-03-02
What errors do you get if you run it without sudo?

---

### Post by tailwhipm on 2011-03-02
I believe it say's i am not permitted.

---

### Post by gmargo on 2011-03-02
> **tailwhipm said:**
> I believe it say's i am not permitted.

It is simply due to permissions on the binary?  Or does it need to open TCP ports below 1024?

Where did your hl2 server come from?

---

### Post by tailwhipm on 2011-03-02
I believe its from the binary. I just want to be able to run it without using root

---

### Post by dfreer on 2011-03-02
You probabyl installed it as root, so all of the files and permissions are set for root. I would recommend creating a new user just to run the server as. You can check the permissions of the files using this command:
```
ls -l
```
To change the ownership of the all the files and folder in a given directory use this:
```
sudo chown username:usergroup -Rv /path/to/srcds
```
Replacing the username:usergroup with the name/group of the user you want to own the files, and replacing /path/to/srcds with the path to your SRCDS install.

Source: running several SRCDS servers in linux for a year.

---

### Post by tailwhipm on 2011-03-03
Fixed!!!!Thanks you i appreciate your help allot!!

---

