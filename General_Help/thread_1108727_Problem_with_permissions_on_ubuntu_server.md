---
title: "Problem with permissions on ubuntu server"
date: 2009-03-28
forum: General Help
---

### Post by cb_papi on 2009-03-28
Hello all,
Yesterday I installed an ubuntu 8.10 server on a computer. Firstly, I will use it as a file server and print server and then expand it to mail server.I followed the guide found [here]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") and I am on page 3.As you can see on the picture below, I am loged in as root. Then, I write the command */etc/network/interfaces* and it pops out a message -bash: /etc/network/interfaces: Permission denied

Please help me, what else can I do?

---

### Post by ubersolid on 2009-03-28
Edit means you have to *edit* the file. Use nano.
```
nano /etc/network/interfaces
```

---

### Post by ubersolid on 2009-03-28
Also, if you are new to ubuntu or linux in general, I suggest you use *nano* instead of *vi* that is used in that guide. Personally I find nano easier to use.

---

