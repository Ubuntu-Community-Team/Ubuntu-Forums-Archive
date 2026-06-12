---
title: "Is it possible... [remote desktop question]"
date: 2009-06-10
forum: General Help
---

### Post by cody7002002 on 2009-06-10
to control my desktop from my netbook when my netbook runs ubuntu and my desktop windows vista? If so how do I go about it, is there a tutorial specific for linux->windows?

---

### Post by cariboo on 2009-06-11
Have a look [here]("http://orum.ultravnc.info/viewtopic.php?p=57666"). It has step by step instructions. Where ever you see Debian, substitute Ubuntu, as Ubuntu is based on Debian.

---

### Post by akakingess on 2009-06-11
> **cariboo907 said:**
> Have a look [here]("http://orum.ultravnc.info/viewtopic.php?p=57666"). It has step by step instructions. Where ever you see Debian, substitute Ubuntu, as Ubuntu is based on Debian.
I was actually interested in this, but the link did not work, it may be my wifi here at the office ( I've had this sort of issue before, but they claimed it was fixed), can anyone confirm that the link posted is still active?

akakingess

---

### Post by H2SO_four on 2009-06-11
[http://forum.ultravnc.info/viewtopic.php?p=57666](http://forum.ultravnc.info/viewtopic.php?p=57666)

heres the link

---

### Post by cody7002002 on 2009-06-11
That's confusing to me. So i install ultra vnc on my vista computer? What do I do on ubuntu to connect to the computer?

---

### Post by akakingess on 2009-06-11
> **H2SO_four said:**
> [http://forum.ultravnc.info/viewtopic.php?p=57666](http://forum.ultravnc.info/viewtopic.php?p=57666)

heres the link
Thank you for the quick response, that link worked for me.

akakingess

---

### Post by cody7002002 on 2009-06-11
Is there anyone else that can help me with this?

---

### Post by Jose Catre-Vandis on 2009-06-11
> **cody7002002 said:**
> Is there anyone else that can help me with this?

Where are you stuck?

Install UltraVNC on your Vista PC and get it serving
(for a decent view set to 800x600)

Run Vinagre on your ubuntu netbook and connect to the Vista PC
by typing in its IP address and port number, e.g.
```
192.168.0.12:5901
```
Enter password info and you should be connected
(Vinagre can scale the Vista desktop so you may not need to set Vista to 800x600)

---

### Post by cody7002002 on 2009-06-11
oh thanks, that got it working =))

---

### Post by LKjell on 2009-06-11
Another ting you might consider is it is also possible to connect linux => linux which is in my opinion a bit more powerful. Then you can forwards heavy programs and all calculation is done by server (Desktop) while you can enjoy your work on the client (Laptop/netbook). The bottleneck is of course your network connection.

---

### Post by cody7002002 on 2009-06-11
Just wondering, is it possible to transfer files to/from either computer using this kind of connection?

---

### Post by LKjell on 2009-06-11
> **cody7002002 said:**
> Just wondering, is it possible to transfer files to/from either computer using this kind of connection?
Hi, if you go to application => internet => terminal server client. Under local resources you can add your local hdd to the remote machine. Assuming you are using that program.

---

