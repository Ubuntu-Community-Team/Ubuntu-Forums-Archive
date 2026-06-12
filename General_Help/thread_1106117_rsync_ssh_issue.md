---
title: "rsync ssh issue"
date: 2009-03-25
forum: General Help
---

### Post by bstras21 on 2009-03-25
I was hoping some one could help me out. I intalled rsync and ssh on my "target" server and "source" server. I added:
 
AllowUsers brian
AlowUsers *@192.168.*.***

to my sshd_conf file on the "source" folder.

Now when I try to rsync them together I get prompted for a password and I use the pwd that I created when I set up Ubuntu but that doesn't work, am I missing something? This is the command I enter: (content has been changed for protection)

rsync -avz -e ssh brian@192.168.*.***:/home/test1/test2/*   /home/test1/test2

I hope someonce can help.

---

### Post by vanadium on 2009-03-25
First make sure you can login using plain ssh:

```

ssh brian@192.168.*.***

```

the password you need to provide is the password of user "brian" on the remote computer (192.168.*.***).

If it works, you will be returned to a command prompt. However, it is a prompt controling the remote machine. If it won't work, you will get an error message and be returned to the command prompt of your local system. Provide the precise error message you get if it does not work.

---

### Post by igor. on 2009-03-25
Unless you mistyped it for this post, your second "Allow" is missing an L.

---

### Post by bstras21 on 2009-03-25
I entered the ssh brian@192.168.*.*** on the "target" server and it prompted me for a password, and I entered it but it said Permission denied, please try again.

When I set up Ubuntu I set the user to: brian and lets say I set the PWD to: admin

admin is the password I am entering.

Also, thank you for taking the time to help me.

---

### Post by bstras21 on 2009-03-25
I did just mispell it in my previous post, It is spelled right in the file.

---

### Post by igor. on 2009-03-25
What happens if you change the password and try authenticating with the new one?

---

### Post by bstras21 on 2009-03-25
Ok I created a new user and password and now I can connect but when I run my rsync I get an error that says: failed: no such file or directory.

I double checked the paths and they are correct.

---

### Post by igor. on 2009-03-25
What is the exact rsync command (with args) you are running?

---

### Post by bstras21 on 2009-03-26
Here is the rsync I am using:

rsync -avz -e ssh brians@192.168.123.456:/home/test1/test2/*  /home/test1/test2

I am doing this from the target server not the source server.

---

### Post by vanadium on 2009-03-26
remove the /* from the source path.

---

### Post by bstras21 on 2009-03-26
Thank you everyone, I figured it out. I accidentally typed in a capital letter in my path.

---

