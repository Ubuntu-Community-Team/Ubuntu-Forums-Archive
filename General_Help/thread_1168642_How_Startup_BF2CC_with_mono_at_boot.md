---
title: "How Startup BF2CC with mono at boot"
date: 2009-05-24
forum: General Help
---

### Post by halvorls on 2009-05-24
Hi!
 
How can i automatlicy start bf2cd.exe with mono at boot time?
 
Now i run the command "mono /home/bf2server/bf2/bf2ccd/bf2ccd.exe" in the terminal but i will like to start i automatlicy at boot time.

Some Ideas?
 
Halvor.

---

### Post by halvorls on 2009-05-24
No answer?

---

### Post by directhex on 2009-05-24
Well, just add that to /etc/rc.local ?

---

### Post by halvorls on 2009-05-25
It dont work, can i add some script /etc/init.d/bf2.sh?

How make script?

Some another method?

Halvor

---

### Post by directhex on 2009-05-25
> **halvorls said:**
> It dont work, can i add some script /etc/init.d/bf2.sh?

How make script?

Some another method?

Halvor

/etc/init.d/skeleton is a demo script

Oh, and remember that stuff in /etc/rc.local would be running as root - unless you make it run as somebody else

---

### Post by halvorls on 2009-05-25
How Can i add it to /etc/rc.local?

And well it start? Can you publish whole the rc.local

---

### Post by directhex on 2009-05-25
Well, BEFORE the "exit 0", add something like 'su -c "mono /home/bf2server/bf2/bf2ccd/bf2ccd.exe" $USERNAME' where $USERNAME is the user you need to run the app as

---

### Post by halvorls on 2009-05-25
It this good?

su -c "mono /home/bf2server/bf2/bf2ccd/bf2ccd.exe" bf2


Is this correctly?

---

### Post by directhex on 2009-05-25
> **halvorls said:**
> It this good?

su -c "mono /home/bf2server/bf2/bf2ccd/bf2ccd.exe" bf2


Is this correctly?

As long as that's the correct username. Oh, and assuming that the app is not GUI based. You can't run an app which requires a GUI at boot. At login, then fine

---

### Post by halvorls on 2009-05-25
> **directhex said:**
> As long as that's the correct username. Oh, and assuming that the app is not GUI based. You can't run an app which requires a GUI at boot. At login, then fine

Most i run it as root?

or?

---

### Post by directhex on 2009-05-25
> **halvorls said:**
> Most i run it as root?

or?

Erm, no... a GUI based app can't run without a GUI to draw into - and running at boot, it would have no GUI to draw into

---

