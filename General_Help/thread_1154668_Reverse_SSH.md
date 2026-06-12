---
title: "Reverse SSH"
date: 2009-05-10
forum: General Help
---

### Post by Boynas on 2009-05-10
I am trying to do the following:

I have no problems opening and closing ports in my computer. I have no problems fixing boxes using SSH or anything. 

I know that there is a way that, using SSH, you can create a reverse connection so the person that wants you to help them to type a command so they can open a connection for me.

It works like ssh in listening mode in my computer, and they will open the connection so I have a terminal (SSH) of their box.

I remember that I was helped by a digium guy like that.

Any ideas????

---

### Post by Boynas on 2009-05-10
I read that doing this in the remote computer:

sh -f -N -R 10000:localhost:22 username@ip_address_of_laptop

and this in my computer

ssh username@localhost -p 10000

will allow me to control my friends computer, since he is opening a tunnel in port 1000 of my localhost to port 22 on the remote network.

This doesn't work.. Plus, my home ISP blocks port 22, so I have to specify a port like 2222 in my router... this will slightly change the command in my friends computer to:

sh -f -N -R 10000:localhost:22 username@ip_address_of_laptop -p 2222

Well, it sounds really cool, but it doesn't work for us...
my friend receives a warning message saying that couldnt make the tunnel in port 10000. I tried other ports with no luck.

Thanks...

---

