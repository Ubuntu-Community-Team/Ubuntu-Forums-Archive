---
title: "Ubuntu Hosts File?"
date: 2008-12-07
forum: General Help
---

### Post by ToyotaGuy23 on 2008-12-07
Back in the windows days, I used a modified hosts file to prevent connection between ad servers, and my computer.  It worked SO WELL, the ONLY THING in windows that worked well!  haha 

Anyway I would like to do this in Ubuntu, but I'm still learning as I go along.  

Windows hosts file, and general hosts information here:  
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

How can you accomplish this in Ubuntu?

---

### Post by binbash on 2008-12-07
/etc/hosts

---

### Post by ToyotaGuy23 on 2008-12-07
> **binbash said:**
> /etc/hosts

can i just download that same hosts file and copy into that directory then?

---

### Post by eBoxNet on 2008-12-07
no, but your can easily edit your ubuntu host file add your hosts from your windows host file

---

### Post by ToyotaGuy23 on 2008-12-07
> **eBoxNet said:**
> no, but your can easily edit your ubuntu host file add your hosts from your windows host file

ok so I will just copy / paste the addresses (adserver.net) to the existing ubuntu hosts file via gedit?

---

### Post by eBoxNet on 2008-12-07
yes something like that : 127.0.1.1 HOSTNAME

---

### Post by geirha on 2008-12-07
You might want to give adblock plus a try. It's an add-on to firefox that makes it easy to filter out ads on websites. Easier than editing the hosts file at least. You'll find it in the repo.s.

---

### Post by ToyotaGuy23 on 2008-12-08
Adblock did what I wanted it to do.

The only difference is that it did NOT fix the problem in ALL browsers.
I don't need to use more than Firefox anyway, now.  

In Windows, IE was so awful that you had to get Firefox for windows, yet keep IE for things that may not work. 

Now, I'm all set!

Thanks!

---

