---
title: "Cant connect to my gnump3d server."
date: 2009-04-01
forum: General Help
---

### Post by redonwhite on 2009-04-01
Hello,

I am trying to set up a audio streaming server as my first task with my server box I just built.  I installed gnump3d after some googling on what to use for streaming mp3s.  But when i type in [http://ipaddress:8888](http://ipaddress:8888).  There is a Page Load Error.  Is there something i need to configure on the server to get this working?  Thanks for your help.

Im using ubuntu server 8.10
Gigabyte GA-MA74GM-S2 mobo

---

### Post by ryanhaigh on 2009-04-02
Is this server located on the same local network as the computer you are trying to use to access it or over an internet connection?

If it is the internet connection then I would guess that the port is blocked by the host. 

Can you access the web page using a terminal based browser like links,lynx or w3m running on the server? eg. [http://locahost:8888](http://locahost:8888)

---

### Post by hyper_ch on 2009-04-02
you need to portforward that port from your router to your computer/server

---

### Post by redonwhite on 2009-04-02
Thanks for the replies guys.  I just had to reset my Router to gain access to it.  I will mess with the port forwarding.  I think your right because my webmin wasn't connecting either.  Thanks!

---

### Post by redonwhite on 2009-04-02
I set port 8888 to forward and it still wont connect.  Is there another ports i need to forward?

---

### Post by ryanhaigh on 2009-04-02
Have you actually been able to verify that gnump3d is running and accessible on that port from inside the firewall? As I said previously you could use a console based browser running on the server and try and access the site via localhost:8888 to verify it is running.

---

### Post by redonwhite on 2009-04-02
> **ryanhaigh said:**
> Have you actually been able to verify that gnump3d is running and accessible on that port from inside the firewall? As I said previously you could use a console based browser running on the server and try and access the site via localhost:8888 to verify it is running.

Tried to access it from the server.  Didnt work. =(.  Failed to connect.  What would be your recommendation for starting to fix this?  Ill try and find the link to the guide i followed for installing.  maybe that will help figure it out.

---

### Post by ryanhaigh on 2009-04-03
As I said its been some time since I ran gnump3d. I would suggest running the program directly to see if it reports any errors. Having a look at the readme for the program [http://www.gnu.org/software/gnump3d/README](http://www.gnu.org/software/gnump3d/README) indicates that you can do this by running just gnump3d. Before you do this make sure there are no other instances running and if neccessary kill/stop them:
```

ps aux | grep gnump3d
sudo /etc/init.d/gnump3d stop
OR
killall gnump3d (may need to run using sudo)

```
The readme also mentions that you need to build an index first, have you run gnump3d-index yet?

---

