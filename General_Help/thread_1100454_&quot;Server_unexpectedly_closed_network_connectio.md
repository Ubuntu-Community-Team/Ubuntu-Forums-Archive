---
title: "&quot;Server unexpectedly closed network connection&quot;, putty, vmware"
date: 2009-03-19
forum: General Help
---

### Post by gkuser on 2009-03-19
Hi,

On Windows home computer I install vmware server 1.0.8, where I put the latest 8.10 ubuntu server with OpenSSH. In my local network, I can connect to server with putty without problem and also I can leave session open several hours. But in my work is different story.
I can connect and work with server, but if I leave session open let say 2 min (I don't work with server), putty give me message 
"Server unexpectedly closed network connection".

Why in my local network works, but from outside not?

I guess that I missed some "TimeOut" parameter, but where, ubuntu-server, vmware, router, ...

Regards,

Gregor

---

### Post by Nxion on 2009-03-19
I don't think you missed anything. It sounds to me like there is something on your work network that is causing it to disconnect. I believe it has to do the way they have everything setup at your work. I don't think that it is something misconfigured on your machines.

---

### Post by kryptikos on 2009-03-19
Hard to say without understanding your network configuration. Anything local on your home network with no firewalls, no DNS etc etc it makes sense that the server leaves the client alone. However when you go to work you traffic has to flow back across networks you don't own. 

Your ssh settings are in **/etc/ssh/ssh_config**. I would read the man pages on ssh_config as well. It will explain what each section does. Without seeing log files or a verbose debug of the ssh section (you could run ssh -vvv <host> to get a live debug) it's hard to say what's going on...but shooting from the hip I would look at adding **TCPKeepAlive** and **ClientAliveInterval**values. Don't forget to recycle the ssh daemon if you make changes to ssh_config.

---

### Post by gkuser on 2009-03-19
kryptikos, you give me some good points, I will play with them tomorrow at work.

I will be back, soon :)

---

### Post by fieroboom on 2009-03-19
On the work machine, have a look in /etc/ssh/sshd_config  and see if you have these variables set:
```
TCPKeepAlive yes
ClientAliveInterval 190
```
If not, add them. That's the setup on my colocated server, and mine never dies, no matter where I login from. You can change the 190; that's how many seconds the SSH server waits to send a keepalive packet 'asking' if you're still alive/connected.
:D
-Paul

EDIT:
I realize kryptikos already mentioned this, but it didn't look like what he said was very clear on where to look and what to do... :)

---

### Post by gkuser on 2009-03-20
HI,

I found the reason :P

It was putty setup. In putty setup under category Connection there is "Seconds between keepalives" option. It was "0" and I changed to 90. ( The same option is also in WINSCP program, I have problem also here )
In /etc/ssh/sshd_config I also add it "ClientAliveInterval 190", the "TCPKeepAlive yes" I already have it. But I have to say that connection was alive even without ClientAliveInterval, problem was as I said in putty.

Thank you for your time.

---

