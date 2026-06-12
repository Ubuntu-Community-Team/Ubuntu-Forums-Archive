---
title: "How do I allocate more memory to Java?"
date: 2012-11-02
forum: Gaming &amp; Leisure
---

### Post by Alvina on 2012-11-02
RuneScape client runs slow on Ubuntu 12.04. Would allocating more memory to Java increase it's frames/per/second? How do I do this?

---

### Post by StephGbzh on 2012-11-03
I'm not familiar with any Runescape client but concerning java you can specify the amount of memory allocated like this:
```
java -Xmx256m ...
```
You'll have to find the launching script and edit it to include the Xmx part.

---

### Post by Dlambert on 2012-11-03
don't use the client.

---

### Post by holastickboy on 2012-11-03
> **Alvina said:**
> RuneScape client runs slow on Ubuntu 12.04. Would allocating more memory to Java increase it's frames/per/second? How do I do this?

What graphics card are you running, and have you installed the correct drivers? For example, if you are using an AMD graphics card, are you using the Catalyst drivers, or the open source Radeon drivers?

---

### Post by HikariKnight on 2012-11-06
depends on which client you use.
are you using the windows client in wine or are you using the native port?

for the **windows client** you should look in
~/.wine/drive_c/jagexlauncher/jagexlauncher/runescape

and open the file named runescape.prm

then edit the line saying
-Xmx256m

and change it to -Xmx512m
that will change the memory allocated to java 512mb, which is more than enough in most cases, an absolute max would be 1024mb but that may cause odd issues on some computers.
----

If you use the **native port** of the client then just launch the "Runescape Client Settings" and just change the memory in the "Client Settings" tab

[IMG]http://i.imm.io/KCQD.png[/IMG]

---

### Post by Opokiolio on 2012-11-08
I have a related/unrealated problem actually... I've downloaded the newest version of IcedTea that I can find, and don't know where the hell to put it lol I just extracted it to the desktop, I'm just trying to update, Runescape bugs out on me too... Really not too familiar with Linux based systems yet, but I'm workin' on it.:guitar:

---

### Post by Carpentr on 2012-11-09
Check out the RSU Client:
[http://services.runescape.com/m=rswiki/en/Linux_Native_Clients](http://services.runescape.com/m=rswiki/en/Linux_Native_Clients)

It works great on 32-bit Ubuntu. There are some errors with 64-bit, though, which can lead to some lag issues. All the instructions can be found at the link above. All I did was install the wrapper and I was able to get Runescape running great with my installation of Java 7.

Edit:
Look at that, didn't notice that HikariKnight replied above. Thumbs up for the client.

---

