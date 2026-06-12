---
title: "Your session only lasted..."
date: 2006-03-10
forum: Desktop Environments
---

### Post by th3gh05t on 2006-03-10
Hi, 

I recently installed Ubuntu on my laptop which is also running Win XP Pro. 

Everything was working fine, but then when I shutdown the computer, I choose "Save Session", and choose shutdown.

Now, when I try and log back in, I get an error message saying:

"Your session only lasted for 10 seconds...You may want to try a failsafe session to see if that works,"

(That last part I kind of forgot. :???: )

Has anyone seen this error? It seems like it could be easily fixed by editing some file. I can go back into the OS to get more detail of the error message if no one knows what I am talking about.

Thanks for your time and help!

th3gh05t

---

### Post by V4Vendetta on 2006-03-10
see what the error is, it might be .ICEauthority

if so, go to fail-safe terminal and type sudo rm -r ~/.ICEauthority

---

### Post by kickaha on 2006-03-10
Check the permissions on the /tmp directory. It is most likely not writeable by the id you're loggin in as.

If it's not 777, you can't open/use the gconf or mcop entries that are placed there when you log in, and you are forced out, with that message.

---

### Post by th3gh05t on 2006-03-11
[QUOTE=V4Vendetta]see what the error is, it might be .ICEauthority

if so, go to fail-safe terminal and type sudo rm -r ~/.ICEauthority[/QUOTE]

Hi, 

Thank you so much!

That command worked! 

Will I get this session error each time I reboot? or log out?

---

