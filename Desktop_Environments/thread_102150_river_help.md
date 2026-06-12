---
title: "river help"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Akya on 2005-12-11
hey my bro told me about a program that creats a river on the bottom part of the screen sadly i dont know what its called or how to get it, if some one could tell me what the neame, and help me install it it would be very appreciated

---

### Post by taurus on 2005-12-11
[QUOTE=Akya]hey my bro told me about a program that creats a river on the bottom part of the screen sadly i dont know what its called or how to get it, if some one could tell me what the neame, and help me install it it would be very appreciated[/QUOTE]
I think he means Enlightenment window manager!!!  I remember playing with it back then and there was an option to make your background, a river flowing in a forest, waving like a real river...

---

### Post by Akya on 2005-12-11
cool so how would i get it?

---

### Post by taurus on 2005-12-11
Okay, you need to include these two lines to the end of your /etc/apt/sources.list,

# Enlightenment...
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

You can do that by using a text editor,

sudo gedit /etc/apt/sources.list

Save it and then update it with

sudo apt-get update

Now, fireup synaptic and in the search field, type in "enlightenment" and install everything that has to do with enlightenment.  Now, you better spend sometimes playing with it since you have to configure it the way you want to...

---

### Post by Akya on 2005-12-11
what two lines do i need to ad? could you just make something i can copy and paste in please?

---

### Post by taurus on 2005-12-11
# Enlightenment...
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

---

### Post by Akya on 2005-12-11
its telling me this

Fetched 39.8kB in 4s (8563B/s)
Reading package lists... Done
W: GPG error: [http://soulmachine.net](http://soulmachine.net) unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BC95B8B5CF6984C
W: You may want to run apt-get update to correct these problems

---

### Post by taurus on 2005-12-11
Don't worry about that...

---

### Post by Akya on 2005-12-11
ok now that i have it installed how do i do anything with it?

---

