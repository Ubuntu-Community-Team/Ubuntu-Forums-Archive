---
title: "SSH , need some help getting this working"
date: 2009-06-18
forum: General Help
---

### Post by Slimzee on 2009-06-18
I have a Windows XP and Ubuntu box on my LAN, they can ping each other no problems.

I installed SSH:

sudo apt-get install ssh

Modified the config file etc/ssh/sshd_config

Listen Address 192.168.0.3

On the GUI network connections I assigned the above static private I.P.

At this stage ssh localhost worked, ssh login@192.168.0.3 worked, and from the Win XP machine using Putty I could ssh using the 192.168.0.3, felt great!

Next stage I couldnt Putty in from my dynamic public I.P address was saying connection refused, ultimately I went to ssh remotely using DynDNS, but for some reason I have gone back to square 1, i cant ssh locally or ssh username@I.P it says connection refused on port 22! 

I dont know why, i havnt altered anything apart from NIC settings as the static I.P wasnt saving on there but it does now.

Any suggestions?

---

### Post by LepeKaname on 2009-06-18
> Listen Address 192.168.0.3

You don't need to specify this. That is why you can't access from "outside", because the IP you are using to connect is a different one.
Just remove that.

I recommend you to change the port in /etc/ssh/sshd_config to what ever you want (e.g., 8822, 222, 2212, 2222, etc.)

In that way, you will improve the security of your box.

Don't forget to use Firewall... if you use UFW, just do this:

sudo ufw allow 8822/tcp 
(just an example if you use 8822 as port)

And that it!

---

### Post by Slimzee on 2009-06-18
Ok
-changed to random port number
-took off the listen address just commented the line
-done sudo ufw allow portnumber/tcp  it said rule added

When I do SSH localhost still says connection refused port 22

---

### Post by sanemanmad on 2009-06-18
That is not entirely correct. If your box is behind a router then it will just forward to the correct LAN IP, hence 192.168.0.3 or whatever.... Do you have any sort denyhosts running? How about a firewall? 

In order to reach ports inside your network you will need to forward them from your router to your pc. 
check /etc/hosts.deny for your remote IP address.

---

### Post by sanemanmad on 2009-06-18
You do not need to change sshd ports.

---

### Post by nikhilk on 2009-06-18
> **Slimzee said:**
> 
When I do SSH localhost still says connection refused port 22

Your SSH client is still trying to connect to the SSH server on the standard port 22. You need to specify the new random port that you have configured the server to use.
Not sure how to do that via Putty but the OpenSSH ssh client accepts the "-p <port number>" command-line option which can be used to override the default port 22.

---

### Post by .nedberg on 2009-06-18
Putty can be configured for any port in the settings panel.

I also use fail2ban to stop brute force attempts.

---

### Post by Slimzee on 2009-06-18
> **sanemanmad said:**
> 
In order to reach ports inside your network you will need to forward them from your router to your pc. 
check /etc/hosts.deny for your remote IP address.

If im doing ssh on putty to a local private I.P address then no I dont need port forwarding.

When this was working earlier via the private I.P my router logs showed no inbound access for the SSH rule I created, but when i was trying to SSH on my public WAN I.P it did hit my router logs and showed which machine was trying to access it. So no need for changes in my router as it will route internally fine without any changes.

If I do ssh localhost on the linux box itself, do I still need to specify the port number because I have changed it in the config file?

so SSH localhost -p portnumber ?

ive tried putty on the port number I changed it to, it still doesnt work.. Once im back home im going to change the ssh config file back to 22 for now, once this is all working then I can change port.

I havent installed any firewall, dont know if one is running there atm. This was all working fine for 1 eveningi locally and remotely via private address, so not sure whats changed..

---

### Post by Peter09 on 2009-06-18
If you are trying to ssh into a local machine on your LAN from an external location (say work) you will need to configure port forwarding on your router. Have you done that?

---

### Post by Slimzee on 2009-06-18
> **Peter09 said:**
> If you are trying to ssh into a local machine on your LAN from an external location (say work) you will need to configure port forwarding on your router. Have you done that?

Yes! but if you read my post, its all gone wrong, and I cant ssh locally on the machine or from another machine on the LAN, we need to address that first, before trying to SSH in remotely :)

---

### Post by .nedberg on 2009-06-18
Did you restart the ssh server after changing port?

sudo /etc/init.d/ssh restart

---

### Post by Peter09 on 2009-06-18
OK - just wanted to clarify this.

If you have changed the default port number (22) then you will need to use your new port number whenever you make the connection.

On the Ubuntu machine you are trying to get to try the line

```
ssh -X <yourusername>@<the Ubuntu machine name> xterm
```this should allow you to connect to the machine that you are already logged into. (note substitute into the brackets the information thats relavent.)

---

### Post by Slimzee on 2009-06-29
Right, made some adjustments found what the issue was but that doesnt matter now.

ssh localhost works fine
ssh private LAN i.p works from from another machine.

So next thing is I want to SSH in from the internet, port forwarding is working correctly as router logs show rule match and succesfull forward.

I have installed firestarter because it shows blocked attempts on the logs, when i SSH in from my WAN public I.P it comes up on firestarter in red and the connection on putty times out from my windows machine. So that tells me Ubuntu is blocking inbound internet requests for SSH but yeh LAN requests are fine.

So I added a rule to firestarter to allow SSH, when i try SSH from internet again, no red flag up in the blocked list, so that tells me the firewall is not blocking it now, but Putty is still timing out...

Any suggestions?

---

### Post by Slimzee on 2009-06-30
bump

Any advice?

---

### Post by LepeKaname on 2009-06-30
Try:

"nmap your-public-ip-address" (from a computer outside your LAN) and see what it returns (which other ports are listed?).
You can also compare it when you do: "nmap localhost"

If it shows it filtered, then something (software) may be blocking the access. If it is not listed then it is possible your router is blocking it? But you said your logs showed an access attempt from outside and that you router setup was correctly... 

Also check in your /etc/sshd_config file what you have in "ListenAddress". If it is commented, then its ok... if not, it should have your local IP and also other one with your public IP as well. If you modify this file, don't forget to restart your ssh server.

I suggest you to try first with no firewall at all. Be sure you turn it off instead of "deny all". 

If it works, then start playing with your firewall.

---

