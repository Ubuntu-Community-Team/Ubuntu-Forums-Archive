---
title: "blocked SSH solution"
date: 2009-03-10
forum: General Help
---

### Post by WolfLust on 2009-03-10
Hello all,

I cannot access my Ubuntu server since SSH and telnet are blocked at work. Is there a solution for this? I need to ssh to my server and they wouldn't unblock the port.

Thanks.

---

### Post by skymera on 2009-03-10
Is it the port thats blocked?

You can change the SSH port on your Ubuntu server, 22 is default i think.
Changing it will also make it more secure :) (So i'ver read)

---

### Post by Peter09 on 2009-03-10
This is not a good idea, presumably your work has blocked this for a reason (or a security policy) - whether it is right or wrong, circumventing this could leave you in a lot of trouble.

I also know that the moderators on here will not like any discussion which could be construed as condoning a security breach.

---

### Post by WolfLust on 2009-03-10
I don't need to connect to one of their servers, I just need to connect to my home pc through ssh.

I cannot ftp or ssh into it.

I don't see how it will affect the work network security if I ssh somehow to my home pc. What did I miss?

Thanks Peter09 and skymera.

---

### Post by skymera on 2009-03-10
Yes, but opening the SSH port will allow any other person to try and access the system.

It's understandable that it's not open

---

### Post by WolfLust on 2009-03-10
I don't need to open the ssh port here, I was just wondering if there's another option of ssh-ing into my own machine from work. 

ssh tunneling, a web based alternative...

I didn't say that I'm trying to unblock the closed port.

---

### Post by skymera on 2009-03-10
Change the port that your server uses?

---

### Post by WolfLust on 2009-03-10
That is what you proposed above and what I will try later on once my shift's over but I was trying to see if there's a quick fix that I can try now since I needed to do something asap.

Thanks again.

---

### Post by Peter09 on 2009-03-10
The problem is that (with due respect)
a) we do not know your motives for wanting to be able to transfer files
b) we do not want to give others directions to do the same.

---

### Post by WolfLust on 2009-03-10
Point taken, no worries Peter09 that's quiet understandable :)

Have a good day.

---

