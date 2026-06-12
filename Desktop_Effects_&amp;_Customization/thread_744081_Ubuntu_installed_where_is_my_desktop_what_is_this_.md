---
title: "Ubuntu installed where is my desktop what is this sudo stuff"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by UbuntGivesmeheadaces on 2008-04-03
hello guys i wanted to try out linux Ubuntu verison so i heard it was free so i burn it on a cd and installed it this is my first time using it so i install it i get to this screen which is black and tells me to log in, so i log in with my user name then my password i didnt understand why i cant see my password as i type but i  figured it out but anyways i did that and then it says all this stuff about SUDO and ROOT let me just say i have no idea what so ever about this stuff i tought i just burn it on an cd and install it and put my username and pass and go to desktop and install my drivers and wow, what is this sudo stuff i dont understand thanks if u can help.


NOTE: I been up all night trying to get a fresh clean OS on my new COmputer please help

---

### Post by njparton on 2008-04-03
It sounds like you've installed the server edition rather than the desktop edition?

---

### Post by UbuntGivesmeheadaces on 2008-04-03
yes sir thats true, is something wrong with that verison?

---

### Post by stefangr1 on 2008-04-03
> **UbuntGivesmeheadaces said:**
> hello guys i wanted to try out linux Ubuntu verison so i heard it was free so i burn it on a cd and installed it this is my first time using it so i install it i get to this screen which is black and tells me to log in, so i log in with my user name then my password i didnt understand why i cant see my password as i type but i  figured it out but anyways i did that and then it says all this stuff about SUDO and ROOT let me just say i have no idea what so ever about this stuff i tought i just burn it on an cd and install it and put my username and pass and go to desktop and install my drivers and wow, what is this sudo stuff i dont understand thanks if u can help.


NOTE: I been up all night trying to get a fresh clean OS on my new COmputer please help

Wow, that's one very long sentence!

The server version of Ubuntu does not have a desktop environment installed. It is for servers that run as a deamon. If you want the desktop version of Ubuntu, you can just execute:

sudo apt-get install ubuntu-desktop

The root user is the system administrator. A normal user can only execute commands as if he were root if he puts "sudo" before the command.

---

### Post by njparton on 2008-04-03
No, there's nothing wrong with the server edition per se other than it doesn't have a desktop installed by default as the last poster says.
 
You could execute the command above or download the desktop edition and try again, it's up to you.
 
The command above will install gnome plus a bunch of other apps such as firefix, openoffice etc etc but I would only do that if you have a broadband connection as it will need to download quite a few packages.

---

### Post by aysiu on 2008-04-03
Read this:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

