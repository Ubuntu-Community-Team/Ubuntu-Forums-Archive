---
title: "ports"
date: 2006-02-23
forum: Desktop Environments
---

### Post by pacificdrums on 2006-02-23
I need to have certain ports open all the time. I have them open on my router but i think they are closing on ubuntu. What happens is when I first start the program and it sends out traffic on those ports it will work fine for a while and I can connect to the computer. If i leave it sit with no traffic for a while then it will not work any more. I am pretty sure that the router is not my problem and I have the computer set static that the port is being forwarded to.
I am plain out of ideas :confused:  any help would be GREATLY appreciated!! thanks

Edit: OK this is really wired. I started the server and every thing works. Then a bit later I cant connect from the wan. OK now I check back again later and it works again. Now this is just plain wacky.

---

### Post by lamego on 2006-02-23
Could you be a little more specific ?
What programs are you using, from and to are you doing the connection ?
Ubuntu has nothing which closes ports or connections based on inactivity, the applications you use may do.

---

### Post by echo $USER on 2006-02-23
maybe your firewall is blocking the ports?

---

### Post by pacificdrums on 2006-02-23
ok im sorry.

I am running a team speak server and it uses port 8767. It works fine if I stop and start the program but if it sits for a while then i can not connect to it from the wan anymore. I cant still get on it from the LAN but that's it. Should I try some other Linux distro or is there just something i missed?
I just think it is so wired that I have gotten people on it before but if I do not use it for a while the port gets closed it seems like. I am using [this site]("http://ts2test.planetteamspeak.com/index.php") to test my connection.

---

### Post by pacificdrums on 2006-02-23
[QUOTE=echo $USER]maybe your firewall is blocking the ports?[/QUOTE]

Well if ubuntu has a firewall then yes but my router is all set up correctly. I did not add a firewall to ubuntu.

---

### Post by lamego on 2006-02-23
The firewall wouldn't suddently start rejecting the packets...
Are you sure it is everything ok with the router when the connections get lost ?
If you can connect from the LAN the ports are not closed, and I doubt its the firewall, because the connections from the router to your server are just LAN connections also.
When you have such problems, how do you solve them ? Restarting the service ?
If you try to use some other service at that specific time, like SSH do you have the same problem ?

---

### Post by pacificdrums on 2006-02-23
OK so yes if i restart the server then it works again. I had it also hooked in to a hub but i took that off for now and it seems to stay open longer now.
With the router well I can not think of any thing that i did not put in correctly and when the connection gets lost nothing seems to change in the router.
Actually i just thought of something i read that i never got a chance to try. I will change the port that it uses because it is a default port that I am using (8767).

---

### Post by pacificdrums on 2006-02-23
OK that did not work it still stops excepting incoming from the wan after a while.

---

### Post by pacificdrums on 2006-02-23
OK it is my router I think. Because it was all working fine and then later I tried again to check and it would not work. So then I restarted my router and it worked fine again. I have a Dlink DI-524. Any ideas?

---

### Post by LordBug on 2006-02-23
Might want to check for firmware updates.  I use a DI-524 here and have not had any issues like this with WAN traffic.

---

### Post by pacificdrums on 2006-02-23
[QUOTE=LordBug]Might want to check for firmware updates.  I use a DI-524 here and have not had any issues like this with WAN traffic.[/QUOTE]
The firm ware it is up to date. It actually works fine for the internet and everything it is just this one program that it dose this with.

---

