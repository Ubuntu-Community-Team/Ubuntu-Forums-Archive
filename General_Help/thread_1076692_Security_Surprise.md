---
title: "Security Surprise"
date: 2009-02-21
forum: General Help
---

### Post by artnis on 2009-02-21
It appears that despite having FireStarter working on my machine that a service called ISPNETBILLING.com is running a service in the background on my computer. Firestarter shows the activity and so does the System Monitor.
I am using Ubuntu 8.10. Everything is up to date.

The activity occurs about every 20-30 seconds from the same IP and on the same port each time. Typically data is sent and downloaded at the same interval about 2 seconds.

I thought that Ubuntu was secure - this make me think otherwise. Anyone ever run into this before? What is the solution?

---

### Post by wowbagger53 on 2009-02-21
Hmmm. Do you by any chance have a usenet news account? This domain name is an alias for news.sisna.com (and possibly others).

---

### Post by artnis on 2009-02-21
No - nothing like that.

---

### Post by wowbagger53 on 2009-02-21
So what ip is it, and which port is it connecting on?

---

### Post by artnis on 2009-02-21
Hope This is right: IP 216-198-50-106  Port 443 (usually)

---

### Post by heindsight on 2009-02-21
Ubuntu is secure, but as soon as you open ports to the outside world you make yourself vulnerable. 

Is it a process on your machine that is making connections to ispnetbilling.com, or is ispnetbilling.com attempting to connect to you?

Post the output of
```
sudo netstat -tuaevpn
``` That will show all processes listening for network connections as well as all active network connections.

---

### Post by artnis on 2009-02-21
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          15188       4755/cupsd      
tcp        1      0 216.198.50.106:54015    8.12.204.126:80         CLOSE_WAIT  1000       63375       5710/gweather-apple
udp        0      0 0.0.0.0:38921           0.0.0.0:*                           110        15106       4717/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          58513       14077/dhclient  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           110        15105       4717/avahi-daemon:


The data shows as both send and receive at the same time in the System Monitor so it appears that my computer is communicating with the other simultaneously. Also, Firestarter shows this as a normal hit vs. serious - I would not have knowingly opened a port. The firewall has been in the default mode since instalation.

---

### Post by wowbagger53 on 2009-02-21
Since the IP in question was talking with the gweather applet, I'd suggest that it may be a data source that gweather is using.

---

### Post by artnis on 2009-02-21
I don't think that is the case. The weather applet is an Ubuntu Gnome panel applet that comes with the Distro and is added without any external downloads etc. When removed from the panel (disabled) the activity from ISPNETBILLING doest not stop either.  

Her is what Firestarter tells me about the active connection:

SOURCE:216-198-50-106 
HOST NAME: Ispnetbilling.com
DESTINATION:74-125-19-83
NAME:cf-im-f103.google.com
PORT:443
SERVICE:HTTPS
PROGRAM: Python

---

### Post by wowbagger53 on 2009-02-21
Hold on a sec...

What's **your **IP address?

---

### Post by artnis on 2009-02-21
216-198-50-106

---

### Post by damis648 on 2009-02-21
> SOURCE:216-198-50-106
HOST NAME: Ispnetbilling.com
DESTINATION:74-125-19-83
NAME:cf-im-f103.google.com
PORT:443
SERVICE:HTTPS
PROGRAM: Python

If your IP is 74.125.19.83, then all that is happening is this website is trying to connect to you.

---

### Post by heindsight on 2009-02-21
216.198.50.106 is your IP address. It seems at the time you ran netstat there wasn't any active connection to ispnetbilling.com

perhaps try to run netstat again, while a connection is active.

By the way, according to whois your IP address lies in a range belonging to Ikano Communications (your ISP perhaps?), running ```
whois ispnetbilling.com
``` seems to indicate that that domain name is also registered with them.

I'm wondering, what exactly do the firewall logs say? Is ispnetbilling.com actually succeeding in establishing a connection to you or is it merely trying, or is some app on your side connecting to them?

---

### Post by wowbagger53 on 2009-02-21
```
penguin:~$ nslookup 216.198.50.106
Server:         208.67.222.222
Address:        208.67.222.222#53

Non-authoritative answer:
106.50.198.216.in-addr.arpa     name = 216-198-50-106.ispnetbilling.com.
```


QED.

---

### Post by heindsight on 2009-02-21
Wait a minute. As I understand that firestarter output, you are ispnetbilling.com
It's saying: Host with address 216.198.50.106 and name Ispnetbilling.com is connecting to host with address 74.125.19.83 and name cf-im-f103.google.com (dig confirms that 74.125.19.83 is cf-im-f103.google.com)

This means that the connections you are talking about are from your computer connecting to a google server.

---

### Post by artnis on 2009-02-21
FireStarter shows that just today I have received 21.6 MB and sent 5 MB  of data. Every time there is activity from ISPNETBILLING the totals change (increase). If I disconnect networking everything stops. If I lock the firewall, the activity seems to die down (less data) but does not cease.

This all started when I inquired about by DSL download speed to my ISP DSLExtreme.com. they checked the issue and could see a background service running from my computer that was intense enough to cause me to have slow download speeds - 300Kb/s.

If I knew how I would set the firewall to block ISPNETBILLING but I don't want to mess up everything else I do on the internet.

---

### Post by Perryg on 2009-02-21
Do you have an instant messenger running?  Some of them use port 443  as well as google.  I agree that from what I have seen so far it looks more like a request from your machine to something outside your local net.  Do you have or can you install wireshark and watch your traffic?

---

### Post by artnis on 2009-02-21
I don't use an instant messenger service nor do I have Wireshark installed.

The System Monitor shows the pattern of the activity is both regular in time, and similar in the amount of data each time the activity occurs.

It also does not seem to affect any other applications or activity - it is completely hidden.

---

### Post by wowbagger53 on 2009-02-21
> **artnis said:**
> If I knew how I would set the firewall to block ISPNETBILLING but I don't want to mess up everything else I do on the internet.

I think perhaps you misunderstand. **Your** machine is ISPNETBILLING. Do an nslookup on your IP address and it comes back as something.ispnetbilling.com.

---

### Post by artnis on 2009-02-21
How did my machine become ISPNETBILLING?  If it is it's a surprise to me. I've been retired for 10 years and have nothing to do with billing anyone if that's what ISPNETBILLING is about.

Sounds like Ive been taken over by something mysterious- even with Linux which I happen to love.

---

### Post by Perryg on 2009-02-21
Does any of this look familiar to you?  Is this your provider?

Anyway you may be following a false positive.  Not to say you do not have a problem.  Wire shark would show you where all of the data is going.  Might be worth installing to find out.

Domain name: ispnetbilling.com

Registrant:
   DNS Administrator (L9PZP) [email]dnsadmin@sisna.com[/email]
   SISNA, Inc.
   265 East 100 south
   Salt Lake City,    UT    84111
   United States
   Phone: (801)924-0900

Administrative Contact:
   DNS Administrator (YXUEW) [email]dnsadmin@ikano.com[/email]
   Ikano Communications
   265 East 100 south
   Salt Lake City,    UT    84111
   United States
   Phone: 8019240900

Technical Contact:
   DNS Administrator (YXUEW) [email]dnsadmin@ikano.com[/email]
   Ikano Communications
   265   Salt Lake City,    UT    84111
   United States
   Phone: 8019240900

Billing Contact:
   DNS Administrator (YXUEW) [email]dnsadmin@ikano.com[/email]
   Ikano Communications
   265 East 100 south
   Salt Lake City,    UT    84111
   United States
   Phone: 8019240900

Record last updated on 2008-11-13 00:00:00
Record created on 1999-11-17 00:00:00
Record expires on 2009-11-17 00:00:00

Domain servers in listed order:
   ns1.sisna.com   209.210.176.8
   ns2.sisna.com   209.210.176.9

Registration Service Provider: Ikano Communications Inc.
   [email]domains@ikano.com[/email]
   +1 (801)9240900

Registrar: NAMES4EVER, [http://www.names4ever.com](http://www.names4ever.com)

---

### Post by wowbagger53 on 2009-02-21
You've not been taken over by anything. You are assigned an IP address by your ISP. That IP address has an external name. In your case it is 216-198-50-106.ispnetbilling.com. The domain name ispnetbilling.com belongs to your ISP. That's all there is to it.

---

### Post by artnis on 2009-02-22
Well I'll be a monkey's uncle!   
I went into my system this morning and opened up System Monitor and Firestarter to see what if anything was taking place. It turns out that nothing happened until I activated Gmail Notifyer which checks to see if there is mail in your account.This was the culprit. This little applet must check every 20 seconds for mail. The end result is it down grades your system performance (if you have a computer with low hardware resources such as mine).

I could notice a much more responsive performance than before especially while on the internet with Firefox. I don't know if it will make that much difference when I use update manager or synaptic to download apps - we'll see. 

Tech support at my service provider noticed this network activity and told me that it was sufficient to slow down my downloads.

Thanks to everyone for their support and helping me to be more aware of what was happening.

---

### Post by Perryg on 2009-02-22
> **artnis said:**
> Well I'll be a monkey's uncle!   
I went into my system this morning and opened up System Monitor and Firestarter to see what if anything was taking place. It turns out that nothing happened until I activated Gmail Notifyer which checks to see if there is mail in your account.This was the culprit. This little applet must check every 20 seconds for mail. The end result is it down grades your system performance (if you have a computer with low hardware resources such as mine).

I could notice a much more responsive performance than before especially while on the internet with Firefox. I don't know if it will make that much difference when I use update manager or synaptic to download apps - we'll see. 

Tech support at my service provider noticed this network activity and told me that it was sufficient to slow down my downloads.

Thanks to everyone for their support and helping me to be more aware of what was happening.

Yup!  That's what I thought.  The reason I mentioned google and even instant messenger.  The address you gave goes right back to them.  Anyway glad to see you have it under control.  Happy Ubuntu-ing.

---

