---
title: "Terminal server client - please explain"
date: 2009-05-05
forum: General Help
---

### Post by eekfonky on 2009-05-05
I'm in Australia and I need to access an ubuntu machine overseas. My friend and i have a VNC client installed from Synaptic so the VNC pull-down is accessible in Terminal Server Client. My question is do we have to sign-up for install anything else. Please help as we need to access each other computers. Is there a simple howto:

Thanks

---

### Post by stretch427 on 2009-05-06
Well it sounds like you know what Terminal Server client is just use that. 

Applications -> Internet -> Terminal Server Client

Just get the login information from your friend enter it in the specified boxes and you should be set. 

Hope this helps!

Edit: If you don't already have TSC you can go to synaptic and install it from there.

---

### Post by eekfonky on 2009-05-06
Thanks but my problem is what information? How and where is it obtained? Sorry for being stupid but it's bothering me.

I need an idiots guide, everywhere I look on line assumes I know more than I do.

---

### Post by stretch427 on 2009-05-06
No problem. Your going to need the Ip address of your friends computer. This can be obtained by typing in ```
ifconfig
``` 
into terminal. 

You will also need the login name of your friends computer as well as the password. 

Just as an example. Lets say that your friends computer's ip address is 192.168.1.1 and his username  to login is "bob" and his password is "password"

Open up Terminal Server Client and under the "General" tab, enter that information. And you will also probably need to chose "RDPv5" as the "Protocol" setting and than click "Connect" at the bottom. 

Also the default screen size of TSC is 640x480, That is really small so if you want a bigger screen, under the "Display" tab click "use specific screen size" and adjust according to your preferences.

---

### Post by eekfonky on 2009-05-06
Will this work over the internet and not just a LAN. As he is in France and I'm in Australia?

---

### Post by stretch427 on 2009-05-06
Theoretically, Give it a try. Just for the record I'm trying to get it work here at my house on two separate computers, and I'm having a little trouble I think with authorisations.  Best of luck. I'm workin on it right now.

---

### Post by stretch427 on 2009-05-06
And just to check if you have the right computer Ip. Go into terminal and type
```
ping -c 3 friends_ip_address
```

and if that works you know you have the right computer.

---

### Post by eekfonky on 2009-05-06
Nothing I'm afraid. I fear this only works on a local network. Any other suggestions anyone. Thanks for trying though.

---

### Post by Grenage on 2009-05-06
It will work, I've configured and used countless remote RDC connections.  You will need to make sure that your friends router is configured to forward the right ports to his machine, assuming he is using a router.

---

### Post by eekfonky on 2009-05-06
So I get the correct IP? His Ip is dynamic though, does that effect it? I know I can go to whatismyip.com to find the one I'm using or do I need the IP his router gives him e.g. 192.168.0.2
From there I need him to forward the ports is it 5900? I'm sometimes on a usb mobile broadband. Does that make a difference?
Also which protocol do I use? Is it RDPv5 or VNC?

Thanks

---

### Post by Grenage on 2009-05-06
You'll need to use his external IP address, so whatismyip.com is fine.  If you want a more convenient solution (if you're using this connection a lot and he isn't at the PC) then you can look into DyDNS etc.  For now, stick with whatismyip.com.

On the router he will need to add a rule to forward port 3389 (RDP port) to 192.168.0.2.  If you opt for VNC instead of RDP, then simply forward whatever port you configure VNC to use.  The default port is 5900 for VNC.

So, to summarise:

For using VNC, his router needs to forward port 5900 to 192.168.0.2
For using RDP, his router needs to forward port 3389 to 192.168.0.2

For connecting via RDP you need to use RDPv5 as the protocol
For connecting via VNC you need to use VNC as the protocl

I hope that clears things up a little.

---

### Post by eekfonky on 2009-05-06
We're going to try it tomorrow, I'll let you know how it goes

Thanks

---

### Post by stretch427 on 2009-05-06
To answer you question above about dynamic ip, that will only change if he is switching around his computers onto different ethernet cables from the router. For the most. It's not just gonna randomly change. So follow Grenege's instructions and you should be ok. Good luck 

And about the USB mobil broadband. That shouldn't matter either. The internet is the internet.

---

### Post by eekfonky on 2009-05-07
Ok I put in:

Computer: 1110.2222.22 etc for my friends Ip address
Protocol: RDPv5
User Name: Bob
Password: xxxxx
Domain:
Client Hostname:
Protocol File:


Then I hit connect and am told it cannot connect?
What's wrong

---

### Post by stretch427 on 2009-05-07
could you tell me what error you get?

---

### Post by albinootje on 2009-05-07
> **eekfonky said:**
> I'm in Australia and I need to access an ubuntu machine overseas. My friend and i have a VNC client installed from Synaptic so the VNC pull-down is accessible in Terminal Server Client. My question is do we have to sign-up for install anything else. Please help as we need to access each other computers.

Before you continue with a vnc viewer or tsclient using a VNC session, this is gonna be all un-encrypted, your username and password will go as plain text over the internet. Personally I wouldn't want that at all.

If you want a quick and easy, and safer solution try the free-of-charge NX from Nomachine : [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

Install the server on the Ubuntu machine that you want access to, and use NX client on the client machine.

---

### Post by eekfonky on 2009-05-07
I'll try that, thanks but I do want to get either RDP or VNC working. The RDP I tried just says couldn't connect to (IP address). I may try VNC next. I'll port forward 5900.

---

### Post by ranie on 2009-05-12
Thanks for letting me know that tsclient is un-encrypted

---

### Post by eekfonky on 2009-05-12
got it working with vinagre, however due to slow connection speed it's pretty useless, can I lower the grpahics to increase the speed?

---

### Post by albinootje on 2009-05-12
> **ranie said:**
> Thanks for letting me know that tsclient is un-encrypted

Hmm, well, sorry, I should have said instead that by default VNC and XDMCP connections are unencrypted, but I'm not sure about the various MS Terminal services or Remote Desktop Administration, see e.g. here :
 [http://www.eggheadcafe.com/forumarchives/windowsserversecurity/Jul2005/post23156202.asp](http://www.eggheadcafe.com/forumarchives/windowsserversecurity/Jul2005/post23156202.asp)
Where someone says :
> 
Terminal Services in Windows 2003 Service Pack 1 (finally) supports RDP over SSL

I guess it's a matter of testing it with a password sniffer.

FreeNX (which I use myself) uses ssh exclusively, and on top of that you can even add SSL.
Apart from that, FreeNX is unbelievably fast.

---

### Post by eekfonky on 2009-05-12
I'll try it thanks

---

### Post by Grenage on 2009-05-13
Windows RDP is encrypted, can use 128bit...

---

### Post by ranie on 2009-05-14
rdesktop uses encryption (Microsoft RDP), and it's already installed (on Jaunty).
Looks interesting. It is possible to define up to 128 bit encryption, but I have no idea of how to do it(PLEASE HELP).


open terminal
man rdesktop for help
rdesktop -f ip 
    or 
rdesktop -f my.site.com

-f is for fullscreen
CTRL+ALT+Return escape full screen

---

