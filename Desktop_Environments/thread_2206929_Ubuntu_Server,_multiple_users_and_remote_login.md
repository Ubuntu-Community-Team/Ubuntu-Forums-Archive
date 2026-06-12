---
title: "Ubuntu Server, multiple users and remote login"
date: 2014-02-21
forum: Desktop Environments
---

### Post by antony3 on 2014-02-21
Hello,

I'm setting a new Ubuntu Server (12.04) to which up to 5 (possibly more) people will have access at the same time. Some of the users will need a GUI while they are logged in.
Last time I had to face the same issue, I resolved this by installing the ubuntu-desktop package and vnc4server. 
The problems in the current situation are the following:
• Logging in via ssh to enable each users VNC is tedious at best
• VNC security is close to non existing
• Having 5 instances of VNC running at all times is power consuming 

What options would you suggest?

For the reference I have very little experience on having multiple users working on one Server with different rights (btw any recommendation on what I could look into to get more of a hang on it is also appreciated), so excuse me if my worries and question is a bit/totally off...

---

### Post by TheFu on 2014-02-21
FreeNX as the server. ssh is built-into the protocol.
Any NX-client on the client side.

The server setup has manual steps and the newly created ssh keys need to be placed on each client, plus either personal ssh-keys or a password for each user is needed. [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) follow the instructions carefully.

Plus, NX is much more efficient than VNC or RDP protocols.
I prefer the NoMachine v3.5 client over their newer release. Remmia or qtnx work too.

Or setup openVPN on every client and forget about the ssh part with VNC.

---

### Post by SeijiSensei on 2014-02-21
If the users do not need a whole desktop, but just need to execute a couple of programs on the Ubuntu box, you might consider the simple solution of tunnelling X over SSH.  If you run "ssh -X servername" you can run graphical programs on the remote but display them on the client.  If they only need to use a specific program or two, this is a pretty easy solution to implement.

For instance, try running "firefox &" at the prompt on the server after logging in over SSH.  You'll see Firefox appear on the client machine.  The "&" tells the operating system to run Firefox in the background and returns you the command prompt.

---

### Post by antony3 on 2014-02-22
ssh -X seems to have me covered, but when I try connecting with ssh -X I get the following error:
X11 forwarding request failed on channel 0

I tried connecting from my Mac to itself as well, because I have there already X11 tested and running, but even that returns the same error.
Can I have some more insight on this method?

EDIT: I fixed that problem I had not disabled on my Mac X11Forwarding in sshd_config, but I'm still getting an error.
Now when I connect and try to run something, I get the following:
root:~# firefox &
[1] 5073
root:~# Error: no display specified

---

### Post by TheFu on 2014-02-22
X11 forwarding through ssh works great over a LAN, but not-so-great over the internet.
The ssh-server settings must be configured to allow X11Forwarding - that is on the remote ssh machine, not the local one.

---

### Post by SeijiSensei on 2014-02-22
On my 14.04 machine, X forwarding is enabled in sshd_config.  However I'm not sure that's the case in earlier versions.  Check /etc/ssh/sshd_config on the server.

Also the server itself needs to have a full implementation of X even if it is not running with a GUI desktop.  Run "sudo apt-get install xorg" on the server if it only has support for text-mode displays.

---

### Post by TheFu on 2014-02-22
First, we need to be extremely clear on what is the "client" and what is the "server."

X/Windows is a client/server architecture with the "client" being the remote system and the "server" being the machine you sit behind, where windows, buttons are displayed. The sever also controls keyboard and mouse input to the remote "client" running X11. This is opposite what we normally think of as C/S architecture, but completely makes sense.  I was an X/Windows programmer. The wikipedia article on X/Windows explains more.

The remote machine - i.e. the X-client - DOES NOT NEED a full X11 server install.  I am 100% positive on that. No need to add bloat to a remote server just for X.  Any GUI application will have dependencies to load any needed X11 client libraries.

X11forwarding has been the linux default for many years - perhaps 10?

---

### Post by antony3 on 2014-02-22
Ok, I fixed it. Apparently in sshd_config X11UseLocalhost should be off on the Server.
That made it run, but apparently TheFu is right. It is too slow to be useable.

I will set up NX and try it out

---

### Post by antony3 on 2014-02-22
EDIT2: i changed the /etc/nxserver/node.conf and uncommented the COMMAND_START_GNOME='gnome-session --session gnome-fallback' and it is running although some graphical issues exist.
For example the top menu bar is black and nothing shows unless clicked. Another issue is that all items in the file browser are blank, make files and folders indistinguishable.

I also have another question. If I setup more users, will they each need a key, or will they be able to log with the same key and simply use different usernames and passwords?

BTW thank you both for your guidance and patience :P


[HR][/HR]EDIT: Forget about everything beyond the line, I made a new connection and it connected, now my problem is I get an error when truing to connect on a new GNOME session:
Failed to load session "gnome-fallback"
It appears in a linux error window within the NX-Client, so something is missing on the Server.

If I click ok, I just get a black screen until the connection times out and an error is returned


[HR][/HR]Ok, I need some help with FreeNX.
I installed it and it seems to be running on the remote server, but I cannot connect to it.
 I have installed the latest client from nomachine and have downloaded the generated key from the server, but it doesn't seem to connect.
If I use the System Login settings, it returns a "The NoMachine service is not available" when using password as an authentication and if I use the NoMachine login, after giving the password, it loads for hours, both when specifying the key and not.

---

### Post by TheFu on 2014-02-22
Forget gnome for now. Can you run an xterm, then start a pure WM from that terminal?  Use the full path to the xterm program location in the settings for this testing. Later, once you see that working, you can screw around with DEs as much as you can stand.  I don't use any DE for remote connections unless I'm on the same LAN.  I also use 2 different profiles - one for on the LAN (GigE) and one for around the world (dialup sometimes).  Don't forget that ~/.ssh/config settings are honored. That can make life easier too.

I'm using the v3.5.x client - NOT THE LATEST. Honestly, I didn't try to make the latest NoMachine client work very hard - the settings were all screwy and didn't make sense to me.

If you didn't manually generate a new NX server key, then the system is using the default that everyone in the world knows. Not good.  If you didn't grab that script in the instructions - get it now and run it.

NX servers work over ssh. Only the ssh port needs to be opened from the outside world.  I let my router do port translation, so internally everything runs on port22, but from remote locations, it runs on some high port. Don't forget to lock down the ssh connections with DenyHosts or Fail2ban too. If you leave the default port on the server, the defaults are fine for fail2ban.  Some networks will block outbound ssh connections and any connection on strange ports. I've seen this in hotels around the world. To get around it, I've given up one of my static IPs port 443 just for ssh connections. Nobody filters that port if you connect by IP.  I have seen some countries filter my domainname for web traffic (don't know why), but they didn't block the IP, just the domain. Clearly I haven't been to **every** country on Earth ... but I'm working on it. ;)

---

### Post by antony3 on 2014-02-22
I have it running perfectly for the root account!
(apart from the graphic glitches)
Also it took me some time, but I got the v4 working (I couldn't find the non-linux version of 3.5 to download)

I don't get what you mean with `start a pure WM from that terminal`, but I'm logging in just fine.

Also, I changed the key from the default one, my question is if this will be the key for all users and they will log in just with their ssh login criteria or if I should create a new key for each user.

---

### Post by TheFu on 2014-02-22
Great!

A Window Manager, WM, is what we used before all the DE - Desktop Environment - stuff started.  DEs sit on top of WMs even today. There must be 50 different WMs to select from.  I'm using the same basic settings from my DEC workstation in 1995 to run fvwm today.  I suppose all the different layers of GUI libraries can be confusing for people without the training I've had. I wouldn't worry about it if you are happy.

As to the ssh-key - think of it as "network-level" authentication, so every client machine will need that key in the NX-client config. But they will also need personal authentication credentials - that can be their password or their own ssh-keys.

BTW, I've never tried to login as root - our default settings (and security policies) do not allow remote root logins to anyone - PERIOD.

So - you have NX with a GUI working and the performance is acceptable?  Pretty slick, right?  If only we could convert all those poor folks running VNC. They don't know what they're missing.  I hope you disabled Unity and as many "cheese" graphics programs as possible. Don't install Flash or any media players either.

Of course, if you had more than a few users, then FreeNX with a single ssh-key would be a terrible thing. A RADIUS server would make more sense so that 1 problem person could be locked out of the system without impacting the security of others.

When 14.04 is GA, it might be worth looking at the SPICE implementation to see if that is better performing.  I tested it on a few systems here and hit a keyboard mapping issue that was a complete show-stopper. The audio performance wasn't bad at all and the video performance was better than any other remote desktop I've seen - not great, but ... too bad the keyboard map was screwed here. My fingers are crossed.   Oh ... and it has SSL as part of the spec - never used that, figured I'd setup openvpn instead.  I don't think SPICE is intended for WAN desktops, so NX will probably continue.

---

### Post by antony3 on 2014-02-26
Sorry for delaying on replying,
but WOW!
I have been "playing" around with NX and I must say I'm more impressed than I thought was possible with remote access!

This seriously beats all competition with ease, I'm only waiting for an NX client program for my phone and tablet and it's bye bye time to TeamViewer and Parallels Access!

The client was a bit of a confusion to set up, but I get it now and will start looking on ways to mod the WM to fix the bare minimums GNOME.

Thanks a lot and may you travel to all countries to check security settings and filters  :P :P :P

---

### Post by TheFu on 2014-02-26
Yep.  People don't really understand how much better than all the other solutions NX is. 
**Easy** beats **security and performance**. Too bad.
[http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) for how I use it to access Windows while remote.

Only a few folks on these forums espouse the greatness that is NX, so the word isn't getting out.
I travel with a netbook ($200) rather than a tablet purely due to NX support.  The new Acer C720 netbook is completely AWESOME and it can work with Ubuntu. The CPU is about the same speed as a Core2 Duo E6600 (inside a NETBOOK??!!!!!!!!).  The only things holding me back from getting one is the lack of wired ethernet and soldered-in RAM.  My Asus Eee is about 15x slower, has only a 600p screen, and the battery doesn't hold charges like it used to.  

NoMachine has been working on an Android client, but I think it might be designed to only work with NoMachine commercial NX servers. ;( Bummer. We can cross our fingers.  I can't imagine using any remote desktop from a phone, but definitely on a tablet.  I did get Ubuntu running in a chroot on the tablet, but again the poor keyboard mapping made it worthless.  'm' caused an email program to be launched.  Plus, NoMachine doesn't have an ARM-based Debian package. ;(

---

### Post by antony3 on 2014-02-28
Sadly I still have an issue with Nx and haven't found a way to fix this.

It is mostly an inconvenience though and doesn't affect the performance, but it is annoying.

I think there is some issue with my gnome-classic setup. The left part of the top bar is black, the Application and Files tab are black, but show up when I click on it, all bars are a simple grey and generally there seems to be a graphical glitch of some sorts...

Here is an image of what I get: 
[http://imgur.com/cUbhzQp](http://imgur.com/cUbhzQp)
[IMG]http://imgur.com/cUbhzQp[/IMG]


The only thing I have tried to play with is the /etc/nxserver/node.conf where I have this line
COMMAND_START_GNOME="/usr/bin/gnome-session --session=gnome-classic"
(gnome-fallback does the same and so does removing the /usr/bin/ bit)


Any ideas?


PS: unity-2d doesn't work either, it returns an error saying unity-2d session not found.

---

### Post by TheFu on 2014-02-28
**kill -HUP** the "panel" process, so it re-reads the conf files.  I don't use gnome, but when I'm on the same LAN, I might use LDXE - the lxde panel is ...
```
psg lxp
thefu      6498  6480  0 Feb22 pts/2    00:04:46 lxpanel --profile LXDE

```
So, **kill -HUP 6498** is the command.  Easy to script. 

Specifying the full-path when there isn't any environment is necessary.  I kick off an xterm, then run a script depending on whether I want LXDE or fvwm.  Plus, it isn't like I do this more than once every month or 2. Most of the time the connection is live - worst case is that I'll reconnect to it from a different location. My desktop is like the server itself - only rebooted when a kernel update makes it necessary.

---

### Post by antony3 on 2014-02-28
For the first time after quite some time, I have no idea what someone is talking about when talking about computers :P

OK, if I get it correct, you say I should kill the panel process, because it somehow, somewhere read the conf files wrong. 
This seems not to be very likely, since I have rebooted the machine more than a few times (not to mention the times I have restarted just the nxserver to check if my altered configurations worked) and it has reopened the nxserver, so it should have re-read the conf file.

Apart from that, I have no idea what the psg command does (and neither does ubuntu :P ), so I tried locating the process id with the good ol' ps -A and no process with "panel" in its name has been found. I found a few nxserver and nxnode instances and the following three (only after connecting with the client): 
```
16139 ?        00:00:00 gnome-session
16153 ?        00:00:00 gnome-settings-
16156 ?        00:00:00 gnome-keyring-d
```

I don't think any of those should do.

Since it is running but bugged, I was thinking it was a missing component issue...

EDIT: I tried connecting to a KDE Environment, but I got a black screen and after a few seconds, I got a timed-out connection error. I just uncommented the ```
COMMAND_START_KDE='startkde'
``` line in node.conf file, so I might be missing something here as well.

---

### Post by TheFu on 2014-02-28
psg - is an alias for a "ps with a grep" - it searches the process table. Sorry.
```
alias psg='ps -eaf | grep $*'
```

Can't help on the process name, unless you run LXDE or fvwm.

Re-reading config settings AFTER an environment is setup can be different than reading configs earlier. Different login methods will get different environments too.

I have never touched the node.conf file - ever, but **always, always, always, specify the full path to the command.** Do not trust your PATH to be available at that stage or inside any scripts. This is a best practice for scripting and not connected to NX at all. Obviously, I can't tell you the location of commands not on my system - like anything KDE related. I go out of my way to keep the bloat minimized here, so there aren't **any** k* commands here.

Which are you running? Gnome OR KDE? Pick one - actually - suggest you NOT use either heavy DE like either of those for remote sessions, but do what you think is best.

Sorry that I'm not more help.

---

### Post by antony3 on 2014-02-28
You've been a great help already and the things that are now wrong can be any of a thousand different ones. I'm gonna ask in a new topic to keep this cleaner.

Thanks a lot

---

