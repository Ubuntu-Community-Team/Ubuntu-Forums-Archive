---
title: "How do i remotely  use my linux on my vista ?"
date: 2009-06-06
forum: Desktop Environments
---

### Post by L.J on 2009-06-06
Hi, I am looking for some help on remotely using my linux desktop computer on my vista laptop, I am relatively new to linux and a full tutorial would help me do what i would like to do. Linux has already gotten me off xp and the only reason i am using vista on my laptop is because i would like a better laptop for my linux, Sorry for using the word "Vista" as i am sure it is a dirty word, for all you avid linux users :lol:. Any help would be very appericiated. Thanks.

---

### Post by orange-wedge on 2009-06-06
The easiest thing to do is to setup a VNC server on your linux machine.  If you are using Ubuntu all you have to do is go to System->Preferences->Remote Desktop to setup the VNC server.

Then on Windows you will need a VNC client.  I typically use RealVNC and UltraVNC for a portable client.

---

### Post by L.J on 2009-06-06
ok i will try this and get back to you :D

Thanks.

---

### Post by L.J on 2009-06-06
Haha i am liking the UltraVNC !  Thanks every so much, i have it all set up and working fully :p. Many thanks for all the help.

---

### Post by L.J on 2009-06-06
P.S could you use this for remote wlan desktop control ? and if not what i could get to do that ? thanks.

---

### Post by jamesrfla on 2009-06-06
You could do it over a WLAN.

---

### Post by L.J on 2009-06-06
Sorry what i meant to say was WAN, from another network over my friends house, sorry.

would you still be able to do it, if not what could i use ?

cheers

---

### Post by jamesrfla on 2009-06-06
You can do it over the WAN it will just be laggy. If you turn down the some of the graphics and quality you can do it. When you connect there should be a option in their about changing from LAN to WAN speeds. You need to forward the VNC port in your router which is 5900. Then find out what your world ip address is by going to this site [http://www.ipaddressworld.com/](http://www.ipaddressworld.com/) If you have cable or your ISP blocks hosting sites this might be harder to do or you might have to pay more to allow you to host a server at your house.

---

### Post by L.J on 2009-06-06
ok well i cannot test the WAN connection right now so i will post to let you know how it goes, thanks for all the help.

cheers

---

### Post by L.J on 2009-06-08
I have try to make the connection via WAN but amnot able to still, i checked on UltraVNC and it does not have an option for it just for the speed of the connection. Any help on how to do this anyone ??

---

### Post by tilerwen on 2009-06-08
I was trying to do the same thing you are and have a very dirty way to do it. It is easy, just strange and unusual. You would need a windows computer installed on your network OR a virtual copy of windows installed on your computer through virtual ware. You would also need an app called: NoMachine installed ony our linux computer(the client, node and server). You would need the client for windows installed on your windows computer. You would also need to get logmein installed on your windows computer.

In the end you would be logging into your windows computer through logmein. From your windows computer you would use nomachine service. It works really well for me. I can't do some graphic stuff, but i use it to browse installation packages and program with netbeans software. 

Here are the links:
[http://www.nomachine.com/](http://www.nomachine.com/)
[www.logmein.com](www.logmein.com)

If you need any help with this, I would love to explain more thoroughly. It is confusing, but hey it works!

---

### Post by L.J on 2009-06-08
right, i understand the logmein and nomachine but not the virtual windows :S, can you elaborate and also there is a problem with me using logmein as i am not willing to pay for it...cheapscate i know

cheers

---

### Post by L.J on 2009-06-08
scrap the last part, i just found a free version, sorry :lol:

---

### Post by tilerwen on 2009-06-08
Logmein = Free (me too)

Virtual Windows: copy of windows installed virtually on your copy of linux.
Here is the website:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

It is very cool, especially if you have rotating desktop. You can have one of your desktops as a copy of windows.

You will have to have a valid copy of windows and liscence key which sucks. However it is nice to have a copy of windows inside linux instead of having to dual boot.

---

### Post by L.J on 2009-06-08
is the virtual windows a must have to use this ??

---

### Post by orange-wedge on 2009-06-10
If you want to use VNC remotely via the Internet, you will need to forward the port to your PC.  The most secure way is to tunnel the VNC through an SSH connection.  So you would need to setup an SSH server, then forward port 22 to your Linux box on your broadband router, and finally setup the SSH tunnel.

---

### Post by L.J on 2009-06-11
Ok, i think i understand you, but i am relatively new to linux and networking so is there any tutorials that you would recommend to help me set this up? I would love to learn about all this networking as i already know the basics, thanks for the reply
 
cheers

---

