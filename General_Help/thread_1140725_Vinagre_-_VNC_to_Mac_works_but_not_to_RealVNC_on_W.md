---
title: "Vinagre - VNC to Mac works but not to RealVNC on Windows"
date: 2009-04-27
forum: General Help
---

### Post by heitjer on 2009-04-27
All,

I have multiple Windows machines on my local network running **RealVNC 4 Server**. I am trying to connect to them from my ubuntu machine. 

At first I tried **Vinagre** (2.24.1), then **tsclient** (0.150) but nothing worked. Then I tried to install **RealVNC** on ubuntu but it tells me that I am missing **"libstdc++-lib6.2-2.so.3:"**. Interestingly I get the same error on tsclient when I click on details. 

So I spend the last two days trying to get the **"libstdc++-lib6.2-2.so.3:"** but nothing is out there that helps.

Then I figured that I use **Vinagre** to vnc into my wifes Mac with OSX and that worked nicely. But it still shows the error on **tsclient**. 

Any thoughts on 

a) why I am getting the error **"libstdc++-lib6.2-2.so.3:"**?
b) why I can get into the Windows machines? 

Thanks!

---

### Post by heitjer on 2009-04-28
anyone....?

---

### Post by max_power on 2009-04-28
try tightVNC server for windows.

---

### Post by heitjer on 2009-04-29
I close this topic out for me.

I have got **vinagre** working now after fiddling with the firewall settings on the windos machines. For some reason this got changed (I assume through an automatic windows update). 

I also have the windows version of **RealVNC** working under WINE. 

I still have the same error messages **tsclinet** and **RealVNC** (linux)

---

### Post by greatscott on 2009-05-02
> **heitjer said:**
> I close this topic out for me.

I have got **vinagre** working now after fiddling with the firewall settings on the windos machines. For some reason this got changed (I assume through an automatic windows update). 

I also have the windows version of **RealVNC** working under WINE. 

I still have the same error messages **tsclinet** and **RealVNC** (linux)

This should fix the error messages.
[http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2)

Edit:
I just tested it on my Ubuntu 8.04 and now I can run RealVNC viewer.

---

