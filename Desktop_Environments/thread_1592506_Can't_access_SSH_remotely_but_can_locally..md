---
title: "Can't access SSH remotely but can locally."
date: 2010-10-10
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-10-10
I've got an SSH server setup on my box which is running locally fine. I can connect to it through my local laptop but when I try to connect through the internet either via my IP or using the DynamicDNS I have setup both get an operation timed out message.

I've got firestarter running with an inbound policy to allow connections from any host to port 22. I've also gone into my Netgear router and selected to forward any inbound connections to port 22 to the IP of the box that's got the SSH server on it.

Even with all this the connection just isn't being made. I've also tried temporarily setting the DMZ option on the router to forward all inbound connections to the IP of the Ubuntu box but still get the same Operation time out. 

Is there any other options that wouldn't allow remote connections via SSH? Or am I missing something hugely obvious here? Maybe it's possible to connect to SSH via a different port or something?

I'm running Ubuntu 10.4 and have installed openssh-server via Synaptic. Would be great to get this working so I can use it as a tunnel from work and access the VNC, which I've been told should be done via SSH anyway.

Anyone know what might be going wrong here?

---

### Post by cinohpa on 2010-10-10
First, reset everything on your router back to how it was before you started screwing around with things and ONLY configure the appropriate port forwarding. That is all that is necessary and anything else might just interfere.

Second, make sure you are doing whatever your router requires to actually apply setting changes. It could be as simple as just hitting apply, but you might have to actually reboot your router. 


What do you mean you can "connect locally" with your laptop? That means your server and the laptop are getting internet from the same router? Then are you using the same IP to connect to your server when you connect locally and when you connect over the web? I have a similar set up and in mine everything uses the same ip (the ip of my router) and then my router does the port forwarding. If this is the same in your setup as your setup and you still can't connect to your server from "non-local" machines it is kind of strange.

Also what sort of set up are you using for connecting non-locally? Are you still using your laptop? What is the internet connection you are using to connect in the non-local setup? If you are trying to connect from work, it might be a security thing that there is a proxy along the way which is specifcally dropping ssh packets.

Also, are you absolutely sure you need firestarter? It might be what is interfering with things. You may need to double check your configuration for it if you can't just remove it. Somewhere along the way between your server and your external machine something may be disallowing connections to your server from the internet (as opposed from over wlan).  

Finally, make sure to restart your ssh server after making any changes with:

```

sudo /etc/init.d/ssh restart

```

Also keep in mind that you can do:

```

sudo /etc/init.d/ssh COMMAND

``` 

Where command can also be things like start, stop. 

Let us know if you figure out what was wrong. It is probably something unnecessary

---

### Post by juliushibert63 on 2010-10-11
hey chinopa

Thanks for the comprehensive reply. I'll give all the suggestions a try when I'm back at my house latter but just to clarify a few points. 

The laptop and server are connected to the same network via Wifi on the same router on 192.168.0.1/254 range. They both can access the internet and when I have my laptop say 192.168.0.100 try and connect to the server at 192.168.0.110 there's a 10s pause, it connects and asks for my PW and then connects via and I can issue terminal commands via SSH. The laptop runs OS X 10.6 and I've tried everything via Terminal. However what make the situation more puzzling, is I have a SABnzbd/HTTP server running on the machine. This I can access absolutely fine from my iPhone when on the go (so from an remote IP). So clearly the router and firestarter are able to handle those ports correctly as it works via my IP and the DDNS I have setup.

When I'm trying to connect non-locally, for SSH I have just been using my laptop on the same network but instead of putting

```
shh user@192.168.0.110 
```

I've been using 

```
shh user@external IP for router

or 

shh user@mydydns.dyndns.org
```


I've tried connecting from work but this doesn't seem to work either to the SSH or my SABnzbd/HTTP server at all which I would think means what you said. Some firewall or proxy is stopping the connection somewhere.

---

### Post by juliushibert63 on 2010-10-11
Stupidly reviewing the settings in firestarter it was clear that I'd just not allowed inbound connections on port 22 other than local IP's

I feel like such an idiot.

For security should I setup a special user account just for remote SSH access?

---

### Post by pricetech on 2010-10-11
So it's working now ??

---

### Post by juliushibert63 on 2010-10-11
Yep all working fine now.

Should I setup a user who just has SSH access or just continue using the same user I have to login to the machine as normal?

---

### Post by cinohpa on 2010-10-12
The short answer is: No, just log in with your normal account.

What I would recommend for additional security is: changing the port on your router that listens for ssh connections. There are 65356 ports. Pick a random one and check it isn't being used for anything else on your system. It takes a long time to scan all of the ports and look for an ssh server. 

Also, if you are logging in from public machines this might not be an option, but setting up key based authorizations instead of typing in passwords could add additonal security in some cases and also keep you from having to type your password in each time you log in. 

Longer answer about making an ssh user:

So the use case for creating a special ssh user is really more for when you have many people logging into the server and you want fine grain control over what they have access to. If you want access to most of the things you usually access from your normal account it really probably isn't worth it.

With that said, there is a pretty detailed thread which talks about different things you can do if you want a user with limited access: [www.ubuntuforums.org/showthread.php?t=367573](www.ubuntuforums.org/showthread.php?t=367573)

---

### Post by juliushibert63 on 2010-10-13
I've changed the port for SSH so it's not on a default 22. All's working fine here except for at work. I'm guessing the port I'm using for SSH is being blocked at work.

Is there any quick way to determine what ports might be open at work so I can reconfigure the SSH server to listen on one of them?

---

