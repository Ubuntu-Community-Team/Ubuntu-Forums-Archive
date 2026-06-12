---
title: "Remote connection to current desktop?"
date: 2014-02-02
forum: Desktop Environments
---

### Post by AlliumPorrum on 2014-02-02
I have Ubuntu 13.10 + xubuntu desktop. I would like to use remote desktop connection to connect my current desktop with all running applications, but what ever I do, it always starts a new desktop without any applications running. I already tried this, without any help: [http://askubuntu.com/questions/235905/use-xrdp-to-connect-to-desktop-session](http://askubuntu.com/questions/235905/use-xrdp-to-connect-to-desktop-session)

What should I do to connect my current desktop?

---

### Post by tomearp on 2014-02-02
I find [x11vnc]("https://help.ubuntu.com/community/VNC/Servers#x11vnc") to be fairly easy for that purpose.

---

### Post by AlliumPorrum on 2014-02-02
Ok, thanks for the hint, tomearp! I checked that x11vnc link and it says that "It's designed to be run from the command-line, which makes it flexible but difficult to learn". Does this mean that it is meant only for non-graphical terminal connections..? What I would like to do is to connect with Windows' Remore Desktop Connection- client to my Xubuntu's graphical desktop.

---

### Post by tomearp on 2014-02-02
It runs from the command line but provides a graphical connection to the desktop.
```
x11vnc -display :0
```
is the most basic usage example that provides a connection to display 0, the default desktop session, listening on port 5900.
The default behaviour is that it will accept one connection, then exit when you disconnect. This can be changed with command line options of which there are quite a few (which is presumably why it's described as 'difficult to learn' although if you're used to working in the terminal it's really not that hard).
```
man x11vnc
```
is a good place to start.

I'm not sure if it's compatible with the Windows RDC client, I have only ever used it with [UltraVNC]("http://www.uvnc.com/downloads/ultravnc.html").

---

### Post by AlliumPorrum on 2014-02-02
> **tomearp said:**
> It runs from the command line but provides a graphical connection to the desktop.
...
(which is presumably why it's described as 'difficult to learn' although if you're used to working in the terminal it's really not that hard).


I really aren't used to working with terminal. If something can't be done with a mouse, I'm lost ;=)

You said that "it runs from a command line"; how can I run it from a command line from my Windows PC where I would like to connect from?? :-o 

I mean; I'm used to connecting Windows servers just by clicking Remote Desktop Client- from laptop and giving server's address on it? It's suprising if this is not possible with Ubuntu???

---

### Post by AlliumPorrum on 2014-02-03
Could some please help me with this issue...? I already tried to install TeamViewer for the remote desktop, but it won't install either since there seems to be some dependency problems :-(

---

### Post by tomearp on 2014-02-03
x11vnc needs to be run from the command line of the Ubuntu machine before you can connect. There are a couple of ways you can do that.

Option 1
Use a startup script to run x11vnc when the machine boots. The -forever command line option will create a persistent vnc server.

Option 2
Use SSH to provide remote access to a command line where you can run x11vnc on an ad-hoc basis. You can optionally use SSH tunnelling to connect to the vnc server over the SSH connection.

Both methods require ports to be forwarded. If the VNC server is going to be directly facing the internet it will need to be secured with a strong password.
If you choose to use SSH it is a good idea to consider methods of enhancing the security of the SSH server such as changing the port that the server listens to something other than 22, disabling password authentication and using public key authentication.
In any event you should probably look into setting up a firewall on the Ubuntu machine. If you look in the Security section of the forum there are some sticky posts about setting up a firewall and improving security in general.

The other option is to try and get something like Teamviewer working as you won't need to map ports, and it will allow more of the click to connect user experience that you're looking for.

---

### Post by AlliumPorrum on 2014-02-04
Thank you very much tomearp! I googled this discussion, and installed x11vnc exactly as adviced: [http://ubuntuforums.org/showthread.php?t=2039022&p=12157164#post12157164](http://ubuntuforums.org/showthread.php?t=2039022&p=12157164#post12157164). The installation seemed to go OK. 

But, I still cannot get connection from Windos laptop with UltraVnc to port 5900 on that machine, it just says that "failed to connect to server". How can I check if x11vnc actually is running after the restart? How exactly should I open the connection, should it work just with address 192.168.x.xxx:5900 (from local network, naturally)?

---

### Post by tomearp on 2014-02-04
If you want to specify the port you need to use two colons in the UltraVNC Viewer address box; e.g. 192.168.0.1::5900.

The other format is to specify the display number; e.g. 192.168.0.1:0 which will default to port 5900 anyway.

---

### Post by AlliumPorrum on 2014-02-05
Hmmm... I tried with two colons, but still the same result. How can I ensure that x11vnc is up & running in the correct port?

I was also suprised that there isn't any username & password field in the UltraVNC, but maybe it asks them with popup..?

---

### Post by tomearp on 2014-02-05
On the Ubuntu machine type the following into the terminal
```
ps aux | grep x11vnc
```
If it is running you should see a result.

---

### Post by steeldriver on 2014-02-05
you can use netstat or lsof to verify that it's actually listening on the port

```

sudo netstat -nlpt | grep ':59..'

sudo lsof -i :5900

```

---

### Post by AlliumPorrum on 2014-02-05
Thanks guys! :=) All those commands are showing that x11vnc is running on port 5900, but still I always just get that error message with UltraVNC . What what what??

---

### Post by AlliumPorrum on 2014-02-05
I don't know if this helps but here's what I got:

~$ ps aux | grep x11vnc
root      1312  0.1  0.3 100784 14096 ?        Ss   helmi04   1:36 x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -localhost
user      9189  0.0  0.0  14872   980 pts/5    S+   19:51   0:00 grep --color=auto x11vnc

@Ubuntu1:~$ sudo netstat -nlpt | grep ':59..'
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      1312/x11vnc     
tcp6       0      0 :::5900                 :::*                    LISTEN      1312/x11vnc     

@Ubuntu1:~$ sudo lsof -i :5900
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
x11vnc  1312 root    5u  IPv4  10127      0t0  TCP localhost:5900 (LISTEN)
x11vnc  1312 root    6u  IPv6  10128      0t0  TCP *:5900 (LISTEN)

---

### Post by AlliumPorrum on 2014-02-05
I also tried to connect 127.0.0.1 with Ubuntu's own Remmina client, without success. This is what was written to x11vnc.log:

05/02/2014 20:00:55 Got connection from client 127.0.0.1
05/02/2014 20:00:55   other clients:
05/02/2014 20:00:56 Normal socket connection
05/02/2014 20:00:56 check_access: checking against full string "127.0.0.1"
05/02/2014 20:00:56 check_access: client 127.0.0.1 fullmatch matches host 127.0.0.1
05/02/2014 20:00:56 Disabled X server key autorepeat.
05/02/2014 20:00:56   to force back on run: 'xset r on' (3 times)
05/02/2014 20:00:56 incr accepted_client=3 for 127.0.0.1:56575  sock=7
05/02/2014 20:00:56 Client Protocol Version 3.8
05/02/2014 20:00:56 Protocol version sent 3.8, using 3.8
05/02/2014 20:00:56 rfbProcessClientSecurityType: executing handler for type 2
05/02/2014 20:00:56 Pixel format for client 127.0.0.1:
05/02/2014 20:00:56   8 bpp, depth 8
05/02/2014 20:00:56   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
05/02/2014 20:00:57 rfbProcessClientNormalMessage: ignoring unsupported encoding type ultraZip
05/02/2014 20:00:57 Using compression level 9 for client 127.0.0.1
05/02/2014 20:00:57 Using image quality level 0 for client 127.0.0.1
05/02/2014 20:00:57 Using JPEG subsampling 1, Q15 for client 127.0.0.1
05/02/2014 20:00:57 Enabling X-style cursor updates for client 127.0.0.1
05/02/2014 20:00:57 Enabling full-color cursor updates for client 127.0.0.1
05/02/2014 20:00:57 Enabling cursor position updates for client 127.0.0.1
05/02/2014 20:00:57 Enabling KeyboardLedState protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Enabling NewFBSize protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Enabling LastRect protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Enabling SupportedMessages protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Enabling SupportedEncodings protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Enabling ServerIdentity protocol extension for client 127.0.0.1
05/02/2014 20:00:57 Using tight encoding for client 127.0.0.1
05/02/2014 20:00:57 rfbSendUpdateBuf: write: Connection reset by peer
05/02/2014 20:00:57 client_count: 0
05/02/2014 20:00:57 Restored X server key autorepeat to: 1
05/02/2014 20:00:57 Client 127.0.0.1 gone
05/02/2014 20:00:57 Statistics             events    Transmit/ RawEquiv ( saved)
05/02/2014 20:00:57  FramebufferUpdate   :      1 |         0/        0 (  0.0%)
05/02/2014 20:00:57  tight               :     10 |     11641/   122681 ( 90.5%)
05/02/2014 20:00:57  ServerIdentify      :      1 |        41/       41 (  0.0%)
05/02/2014 20:00:57  SupportedEncoding   :      1 |        92/       92 (  0.0%)
05/02/2014 20:00:57  SupportedMessage    :      1 |        76/       76 (  0.0%)
05/02/2014 20:00:57  RichCursor          :      1 |       402/      402 (  0.0%)
05/02/2014 20:00:57  TOTALS              :     15 |     12252/   123292 ( 90.1%)
05/02/2014 20:00:57 Statistics             events    Received/ RawEquiv ( saved)
05/02/2014 20:00:57  PointerEvent        :      1 |         6/        6 (  0.0%)
05/02/2014 20:00:57  FramebufferUpdate   :      1 |        10/       10 (  0.0%)
05/02/2014 20:00:57  SetEncodings        :      1 |        88/       88 (  0.0%)
05/02/2014 20:00:57  SetPixelFormat      :      1 |        20/       20 (  0.0%)
05/02/2014 20:00:57  TOTALS              :      4 |       124/      124 (  0.0%)

---

### Post by steeldriver on 2014-02-05
Since you added the -localhost flag, you will need to tunnel the connection (over SSH) in order to connect from a remote client - as confirmed by the netstat / lsof port lists (the service is only listening on the localhost interface) 

As to why it failed when you tried to connect from 127.0.0.1 I'm not sure - but probably just as well, because you would have got in an infinite loop (opening a VNC client to view a desktop on which you were opening a VNC client to view a desktop on which... you get the idea) ;)

---

### Post by AlliumPorrum on 2014-02-05
Hey thank you very much, removing  -localhost solved the problem and now it works! You're the greatest :=)

---

### Post by steeldriver on 2014-02-05
imho it would be better to keep the -localhost option and configure the client to use ssh tunneling - if there's any chance of the machine being exposed to the public internet I'd go as far as to say it's ESSENTIAL

---

### Post by tomearp on 2014-02-05
Glad you got it working!

I agree with steeldriver that it is better to leave the -localhost in place and tunnel over SSH than to forward a port directly to your VNC server. Exposing any service to the Internet brings risks with it, but a new security problem with openssh is likely to get fixed a whole lot quicker than a new security problem with x11vnc, in my opinion.

Installing SSH in Ubuntu is easy; securing it requires a bit of effort.

The first thing to do is disable password authentication and enable public key authentication. You'll find some useful info [here]("https://help.ubuntu.com/12.04/serverguide/openssh-server.html"), and there are loads of articles explaining how to do it on Google. If you're going to connect from a Ubuntu machine you can generate keys quite easily from the command line, in Windows you'll need some software (see below about PuTTY).

You will also want to change the port that the server listens on (same config file as the above items) to something random in the range 10000 - 65535. The default is 22, a common choice is 2222; using either of those will attract a lot of attention from port scanners and automated attack tools. If you have disabled password authentication you will have rendered most automated tools useless as they tend to focus on brute-forcing weak passwords but they will still consume resources by making repeated connection attempts.

There are more things you can do (e.g. setting up an iptables firewall to limit access) but this is a good start for securing SSH itself.

To connect from Windows machines you'll need a client; [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") works well. Download the installer so you get everything. As well as the client there is a tool called PuTTYgen that can generate keys for public key authentication and export them in a format suitable for use in the authorized_keys file on the Ubuntu machine.
PuTTY can then be configured to connect using a key automatically. There are lots of HOWTOs/FAQs on Google.

Tunnelling is reasonably easy to set up in PuTTY as well, again Google is a good source. You'll want to set up a tunnel with source port 5900 and destination 127.0.0.1:5900. Set the radio buttons to local and IPv4.
The first time you connect after adding the tunnel Windows Firewall might come asking for permissions, say yes.
When connected to the SSH server you can connect to 127.0.0.1:0 in UltraVNC and it will go through the tunnel to the x11vnc server.

Going back to firewalls for a moment. You may choose not to implement a firewall on the Ubuntu machine (it is effectively turned off on a fresh install) but it is something to think about. Limiting access by IP range is a good idea, as is rate limiting to temporarily ban IP addresses that make lots of connections.
There are bits of software that can assist with rate limiting, such as [denyhosts]("http://denyhosts.sourceforge.net/") and [fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page"). Personally I don't use them as I prefer to implement everything in iptables directly, it depends how deeply you want to get into it.

Where security is concerned I like to practice the philosophy of belt, braces, and self-supporting trousers and I would encourage everyone to do the same. Yes it is a bit of a ball ache to set all this up, but it will deter most casual attackers, and the professionals are probably already hired out to infiltrate far more interesting targets than you or I anyway :)

---

### Post by AlliumPorrum on 2014-02-06
> **steeldriver said:**
> imho it would be better to keep the -localhost option and configure the client to use ssh tunneling - if there's any chance of the machine being exposed to the public internet I'd go as far as to say it's ESSENTIAL

Thanks again for your concern guys, but this PC should never be exposed to the public internet. I'm using DLink router with a firewall, and the VNC port is forwarded to totally different public port. Do you think that this with x11vnc password protection is still a bad idea...?

---

### Post by tomearp on 2014-02-06
Given that people have previously found authentication bypass exploits for libvnc, I would strongly advise against it.

[http://www.securityfocus.com/bid/18977/info](http://www.securityfocus.com/bid/18977/info)

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2450](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2450)

I'm not saying openSSH is invulnerable; [it's not]("http://search.debian.org/cgi-bin/omega?DB=en&P=openssh"). But there are a lot more people looking at openSSH, so vulnerabilities are likely to be found early and fixed before exploits become widely available.

---

### Post by tomearp on 2014-02-06
> **AlliumPorrum said:**
> I don't know if this helps but here's what I got:

~$ ps aux | grep x11vnc
root      1312  0.1  0.3 100784 14096 ?        Ss   helmi04   1:36 x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -localhost
user      9189  0.0  0.0  14872   980 pts/5    S+   19:51   0:00 grep --color=auto x11vnc

@Ubuntu1:~$ sudo netstat -nlpt | grep ':59..'
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      1312/x11vnc     
tcp6       0      0 :::5900                 :::*                    LISTEN      1312/x11vnc     

@Ubuntu1:~$ sudo lsof -i :5900
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
x11vnc  1312 root    5u  IPv4  10127      0t0  TCP localhost:5900 (LISTEN)
x11vnc  1312 root    6u  IPv6  10128      0t0  TCP *:5900 (LISTEN)

I also just noticed something else; you are running x11vnc as root. That is probably not a good idea.

I generally find x11vnc will run and work quite happily with user-level permissions. You could try adding
```
sudo -u yourusername
```
to the front of the command issued in your startup script to make it run with less privileges.

---

### Post by AlliumPorrum on 2014-02-06
Good advice, thanks again tomearp! :)

---

