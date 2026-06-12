---
title: "connect remotely to ubuntu"
date: 2009-01-02
forum: General Help
---

### Post by thingy87654321 on 2009-01-02
i have a ubuntu laptop and so does my friend, my friend live about 5 minutes away but i was wondering if i could just connect to his computer and fix problems for him? i mean with him at his house and me at my house,aka without being on the same network.

---

### Post by dcstar on 2009-01-02
> **thingy87654321 said:**
> i have a ubuntu laptop and so does my friend, my friend live about 5 minutes away but i was wondering if i could just connect to his computer and fix problems for him? i mean with him at his house and me at my house,aka without being on the same network.

Depending on the type of Internet connection, you will need to open up an incoming port to allow access to the remote computer.

You should be able to search out detailed instructions.

---

### Post by rumli on 2009-01-02
First, in order to do any administrative stuff on his computer, you will need a username and password that gives you administrative privileges to his machine -- either your friend's username and password, or, better yet, a separate user account with administrative privileges on his machine created especially for you.  You can create such a user account by going to System / Administration / Users and Groups.

Secondly, you will need to install OpenSSH server on his computer to securely access his machine (see [http://www.funnestra.org/ubuntu/intrepid/#openssh-server]("http://www.funnestra.org/ubuntu/intrepid/#openssh-server")).  This is a must for security reasons.

If you just require command-line access for the things you want to do, then that's all you need to do.  If, in addition, you need to remote desktop into his machine (i.e., take over his graphical GNOME session while he is logged in), you will need to use VNC (see [http://www.funnestra.org/ubuntu/intrepid/#vnc]("http://www.funnestra.org/ubuntu/intrepid/#vnc")).

---

### Post by thingy87654321 on 2009-01-03
i cant install ssh server i get this error message:

openssh-server:
  Depends: openssh-client (=1:4.7p1-8ubuntu1) but 1:4.7p1-8ubuntu1.2 is to be installed

---

### Post by thingy87654321 on 2009-01-06
do you have to pay to make a static dns thingy?

because i went to the site and it says you have to pay to create the account for the static dns thingamagiger

---

### Post by rumli on 2009-01-20
You don't need static DNS (not sure what that even is); you just need the free dynamic DNS service:
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

---

### Post by thingy87654321 on 2009-01-23
ok thanks for the advice

---

