---
title: "Transmission Web Client"
date: 2009-03-26
forum: General Help
---

### Post by Epidural on 2009-03-26
I recently figured out that I could play around with my downloading of torrents on my Ubuntu box located at home from anywhere with an internet connection.

But I can't figure out HOW. I've set it up with all defaults on the Ubuntu box, IP 127.0.0.1 , and when I press "open" it shows me the page, loads fine, works fine, everything's good.

But I can't access it WITHOUT using that "open" button. Firefox simply gives me this:

Failed to Connect


Firefox can't establish a connection to the server at 127.0.0.1.        

"Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing."

I'm using port 9091, and it's open. But even when useing the exact same URL or [http://localhost:9091](http://localhost:9091) or whathave you, I can't connect from the internet alone.

What am I doing wrong/overlooking? Because it's new to me, I'm sure there's something. xD Any more info that's needed, I shall provide.

Thanks in advance. (:

---

### Post by aeiah on 2009-03-26
127.0.0.1 and localhost are only local to the computer you're issuing them on. every computer has its own 127.0.0.1 and 'localhost'. if you're on a LAN you'll need the internal IP address of the computer you're trying to connect to, and if you're trying to access it over the internet, you'll need its external IP, the IP that everyone sees (the IP of your router that everyone sees that is). you'll need to forward requests sent from the outside world to your router on port 9091 to the computer on your lan that has transmission running.

---

### Post by lovinglinux on 2009-03-26
> **Epidural said:**
> I'm using port 9091, and it's open. But even when useing the exact same URL or [http://localhost:9091](http://localhost:9091) or whathave you, I can't connect from the internet alone.

The address [http://localhost:9091](http://localhost:9091) will work only on the machine where Transmission is installed and configured to use the Webui. This address is basically for testing.

If you are connecting from another computer on your local network, then you must replace* localhost* with the internal IP of the remote machine (something like 192.168.1.x)

If you are connecting from another computer outside your lan (from work for example), then you must replace *localhost* with the IP of your router (external IP). In this case, the router must be configured to port-forward the connection on port 9091 to the IP of the machine running Transmission.

---

### Post by Epidural on 2009-03-26
Got it. xD Seemed like a stupid thing, most definitely was. But hey... I suppose now anybody else who knows ZIP about networking can figure this out, as well. (: Thanks guys, perfect answers.

---

### Post by jerrycrabb on 2009-09-22
I have a simillar yet different issue (I think)

My home machine is set to a static ip and my router forwards port requests for 9091 to that machine.

When I set everything up I tried to access it though the web browser on my blackberry phone. It asked me for the user name and password, and loaded the web client to the best of its ability but was (for the most part) unusable. THIS IS WHAT I EXPECTED

Oh well, I didn't think that would work anyway, but at least I've got the port forwarding set-up correctly.

BUT

When I try from any other computer (outside of my home network)
Explorer says: Internet Explorer cannot display the webpage
Firefox says: The server at 69.255.xx.xxx is taking too long to respond.

does anybody have any suggestions on what might be the issue here?

Let me know if there is more info that would be helpful.

-Bob

---

### Post by prem1er on 2009-09-22
Outside your network are you trying to visit

```
http://youripaddress:9091/transmission/web/
```

and getting this error?

---

### Post by geirha on 2009-09-22
I'm guessing either that the port-forwarding is not working, or that the machines you're trying to connect from are not in the web ui's whitelist.

---

### Post by lovinglinux on 2009-09-22
I would recommend Deluge, it has a nice webui but you don't even need it, since also support remote gtk, which means you can install Deluge on both machines and connect remotely using the default interface.

---

### Post by jerrycrabb on 2009-09-22
> **prem1er said:**
> Outside your network are you trying to visit
```
http://youripaddress:9091/transmission/web/
```
and getting this error?

Yes

> **geirha said:**
> I'm guessing either that the port-forwarding is not working, or that the machines you're trying to connect from are not in the web ui's whitelist.

How can I check the whitelist?

---

### Post by geirha on 2009-09-22
> **jerrycrabb said:**
> 
How can I check the whitelist?

Edit -> Properties -> [Web]

Or, in a terminal:
```
grep rpc-whitelist ~/.config/transmission/settings.json
```

---

### Post by schnogg on 2009-09-26
I also had this problem with the whitelist not working. Rather, The problem is that I did not specify a whitelist at all, and can't connect from any ip address that isn't on my private LAN. Perhaps you need to add the ip address you are coming from on the internet or * for all ip addresses anywhere. 

I haven't tried that yet.

---

