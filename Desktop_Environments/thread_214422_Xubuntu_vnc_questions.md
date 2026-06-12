---
title: "Xubuntu vnc questions"
date: 2006-07-12
forum: Desktop Environments
---

### Post by mykrob on 2006-07-12
I have Xubuntu installed on a server machine, and have a vncserver working on it. However, to access it in the broswer, i have to go to [http://machine_address:5801](http://machine_address:5801)

The vncserver is starting another X-session.. I would prefer it to use the existing session and desktop :0..

What have i done wrong? Typically, you should go to [http://machine_address:5800](http://machine_address:5800)


Thanks,
-myk

---

### Post by sefs on 2006-07-12
I dont think its possible to export the existing desktop with a regular vnc server 

you would need to run probably x11vnc server instead, that one does export the existing desktop for sure.

x11vnc is in the repos.

---

### Post by mykrob on 2006-07-12
thank you, i will give that a try.

on a side note, how do i make sure this server runs on startup and accepts uninvited requests so long as the correct password is provided?

Thanks,
-myk

---

