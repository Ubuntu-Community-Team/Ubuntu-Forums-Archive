---
title: "Can I make AMP available to one uder only?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Steveire on 2006-07-12
I recently discovered the power and ease of loading multiple sessions.

I currently have a partition separate to my regular one which I installed LAMP and a window manager on. I use it as a test server, but it is inconvenient for me to have to reboot to use it. I would prefer to be able to start a new session, log in as a different user, and be able to switch over and back at will.

I don't want to be running a web server under my regular username, and I don't want the new username to be able to access any web services.

Is this possible?

I think apache starts up before anyone logs in, so I'll have to change that at least.

Thanks.

PS:
I haven't been here in a while, and I think the skin is ugly. I checked in my userCP to change to the old one, but it doesn't look like I can. Am I missing something, or is there no way I can change this?

---

### Post by Steveire on 2006-07-13
I'm gonna modify ports.conf, and see if that works for me. I'm still open to other ways of doing something like this though...

---

### Post by Ramses de Norre on 2006-07-13
Edit /etc/apache/httpd.conf and search the lines User and Group (253 and 254 here) to the user you want to run apache with. (this is for apache 1.3, I'm sure you can do this for apache 2 too, do a grep `user_name` /etc/apache2 to find out in which file it is configured and edit it, change `user_name` to your username)

For the webservices thing, you mean you don't want the apache user to be able to use ssh for example?

---

