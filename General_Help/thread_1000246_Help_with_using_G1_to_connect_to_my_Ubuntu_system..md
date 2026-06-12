---
title: "Help with using G1 to connect to my Ubuntu system."
date: 2008-12-02
forum: General Help
---

### Post by redonwhite on 2008-12-02
My Cellphone has an app called connectbot (SSH).  I was wondering if anyone could explain how i use this to connect to my Ubuntu system or if they can recommend any tutorials on this.  I have searched the net for using SSH and cant seem to find anything meant for beginners like myself.  Thanks for your help in advance.

---

### Post by chronus_aurelius on 2008-12-22
I setup an ssh server on you desktop using apt-get.  From the command prompt do:

sudo apt-get install openssh-server

Then get Connectbot from android market.  Start the app and type 

username@hostname

enter password, and you have shell access from your phone to your computer.  I have tried it, it is pretty cool.

sources:
[https://help.ubuntu.com/7.10/server/C/openssh-server.html](https://help.ubuntu.com/7.10/server/C/openssh-server.html)

---

### Post by sonhadorpr on 2009-04-18
Yeah, but what I want to know is how to successfully mount G1 to Ubuntu, to transfer files to the MicroSD card?
the G1 recognizes that I connected it to my PC/Ubuntu using USB, it told me to mount it(The G1 did), but I still can't find the G1 on Ubuntu.
Any ideas?

---

### Post by redonwhite on 2009-04-23
> **sonhadorpr said:**
> Yeah, but what I want to know is how to successfully mount G1 to Ubuntu, to transfer files to the MicroSD card?
the G1 recognizes that I connected it to my PC/Ubuntu using USB, it told me to mount it(The G1 did), but I still can't find the G1 on Ubuntu.
Any ideas?

G1 mounts fine into ubuntu for me.  After you choose mount from the phone go to your terminal and type "lsusb" and copy paste the output.

---

