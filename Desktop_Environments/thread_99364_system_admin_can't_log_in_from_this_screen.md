---
title: "system admin can't log in from this screen"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Hunter761 on 2005-12-05
i need to log in as root.  I've created a password, but can't log in when I start up....  how do I log in as root?  

Also, where is the firewall?

And where is a good place to start to learn how to use ubuntu from a total linux newbie?

---

### Post by Hunter761 on 2005-12-05
ok, so I figured out that I log in as a regular user then goto applications system tools run as different user.  But it keeps telling me my password is wrong
..    now what?

---

### Post by Hunter761 on 2005-12-05
deleted

---

### Post by ipn1nj4 on 2005-12-05
Ubuntu uses sudo

run 

> sudo passwd root 

---

### Post by kosmic on 2005-12-05
[quote=Hunter761]never mind. I'm just gonig to install another distro over it. its hung several times in the first 1/2 hour of using it. and I can't get root privilages no matter what, and I can't find documantion anywhere. total waste of a decent amout of my time[/quote]
 
Did you click in the WIKI theres lots of documentation there, did you go to the Tricks section of this Forum ??? theres also a lot of documentation.
 
If you are tryng to login as root with GDM it is not possible if you do not confiure GDM to allow root login 
 
To become Root in the shell first you need to activate the root password with a comand like this
 
sudo passsword
 
and now you can enter as root.
 
 
Waste of time ? If you searched a little bit you soon find out why this problems appears to you.
 
If you want to use another linxu distro go for it nobody where is apointing a gun at your head to use Ubuntu...oh and my 0.02 cents try lindows it should be perfect for someone that want to do things a La windows way.

---

