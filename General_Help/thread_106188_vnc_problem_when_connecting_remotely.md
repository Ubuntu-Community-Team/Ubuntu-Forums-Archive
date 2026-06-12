---
title: "vnc problem when connecting remotely"
date: 2005-12-20
forum: General Help
---

### Post by zible on 2005-12-20
I got a strange problem. I've setup vnc to work, and works great for everyone on my local LAN. 

However, I need to acccess my box from work, and I'm getting strange results. 

I can hit the box fine, get the password prompt, enter it, and I see the vnc window (realvnc on a windows box) flash for a second then vanish. I know all the routing is good, as I'm getting the password prompt. (normally it would just time out trying to connect) but the window wont stay up. Is there some special consideration you have to take into account when accessing the Ubuntu box remotely? I am totaly stumped.

---

### Post by Gurgeh on 2005-12-20
Is there no software or hardware firewall interrupting the process? Is there any sort of log data you could provide.

---

### Post by zible on 2005-12-20
There is no firewall or software problems that I can think of, because this works fine when I boot into the windows partition, same port etc. 

Also, when there is a firewall/routing problem, ususally you don't get the password prompt, you just get an error message saying unable to connect. Plus it works fine locally. 

To be honest, I don't know where to look for a log. 

I used this [http://ubuntuforums.org/showthread.php?t=45565&highlight=Howto+VNC](http://ubuntuforums.org/showthread.php?t=45565&highlight=Howto+VNC) 

to get the vnc working.

---

### Post by ronmarley1 on 2005-12-20
Have you tried TightVNC [http://www.tightvnc.com/](http://www.tightvnc.com/) ?  I had issues with RealVNC, tried TightVNC and everything worked fine.

---

### Post by Gurgeh on 2005-12-22
Also have u installed VNC on ur ubuntu machine? I got the feeling it might come built in and the two are conflicting, just a theory...

---

### Post by zible on 2005-12-22
I've installed VNC as per the instructions in my previous link. It works fine localy no problem, just at work it was doing a weird issue, where the screen would come up for a second then disappear. I tried it again today, and it seems fine. I am not sure what the problem is, if it was asleep, or a screen saver was causing it problems, but it appears to be working. I'll have to see if I can replicate it.

---

### Post by baked on 2005-12-22
This doesn't have much to do with your problem, but you should use SSH to portforward your VNC connections from outside the network.  It keeps everything encrypted and its pretty easy to use.  It also may solve your problem because its like you would be connecting from inside your network because SSH would be tunneling it through.  

I really don't like sending anything unencrpyted across the net, and if someone got a hold of your vnc they would have pretty much total control...

Hope you solve your prob....

peace,

Tommy

---

### Post by zible on 2005-12-23
Can't use SSH as the port (22) is blocked on the network. Trying to get this to work through the firewall here is a bit of a pain, but works. 

Just tonight, been on the box via VNC just fine for hours, then all of a sudden I'm unable to connect. Well that's not accurate, I'm able to connect, get prompted for a password, then loose the connection as soon as I put in the password. 

Maybe instead of connecting to vnc on a strange port, I should change my SSH to an open port, and use that. As I could do alot more then just vnc through the SSH connection.

Realvnc just connects then disconnects after the password prompt. Tight gives a connection lost message, after I put in my password.

---

### Post by zible on 2005-12-23
I think I found the problem, I can't have more then one vnc connection to the box at a time. I'd rather it log out my (or any) old VNC connection and allow the new one.

---

