---
title: "Trying to build a headless box.  Struggling with X security over VNC"
date: 2021-03-16
forum: Desktop Environments
---

### Post by pi-thrower on 2021-03-16
Good Evening,

I'm on a fresh install of 20.04.  I have TightVNC running with XFCE.  All the built in applications work just fine but when i attempt to open anything else i get errors like this one.
> Client is not authorized to connect to Server[6117:6117:0317/024325.644018:ERROR:browser_main_loop.cc(1390)] Unable to open X display.
AUDIT: Wed Mar 17 02:55:10 2021: 5616 Xtightvnc: client 14 rejected from local host


If i start the VNC server with '-ac' to disable X security it works fine.  I've checked several tutorials on setting up VNC on 20.04.  None of them mention this error or how to fix it.  Searching using the error text has gotten me nowhere.

Thanks in advance,

*EDIT*  The problem is that apparently SNAP packages have a different XAuthority file.  The solution is here:   [https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381/2](https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381/2)

Symlink the Xauthority in the snap package with the one in the home directly.  I suspect that an update may break this.
```
[COLOR=#434343][FONT=Consolas]ln -s ~/.Xauthority ~/snap/brave/current/.Xauthority[/FONT][/COLOR]
```

---

### Post by TheFu on 2021-03-17
How tied to VNC are you? There are better solutions with 1000x better network security and 2-3x better performance.

What are the client machines running?

---

### Post by ActionParsnip on 2021-03-17
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Use this. It's excellent

---

### Post by pi-thrower on 2021-03-17
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Use this. It's excellent

I've essentially followed that.  There are others that give the effectively the same guidance with only minor changes in the 'xstartup' script.
[LIST]
[*][https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)
[*][https://linuxconfig.org/vnc-server-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/vnc-server-on-ubuntu-20-04-focal-fossa-linux)
[/LIST]

*edit*  This one uses a different VNC server.  I haven't tried it but i get the sense that this is an X problem not a VNC problem: [https://tecadmin.net/install-vnc-server-on-ubuntu-20-04/](https://tecadmin.net/install-vnc-server-on-ubuntu-20-04/)

---

### Post by pi-thrower on 2021-03-17
> **TheFu said:**
> How tied to VNC are you? There are better solutions with 1000x better network security and 2-3x better performance.

What are the client machines running?

Client machines are mainly windows but I'd prefer not to break Linux/OSX compatibility.  My current plan was to use SSH port forwarding with PuTTY.  People aren't kidding about the bad performance though.

---

### Post by TheFu on 2021-03-17
> **pi-thrower said:**
> Client machines are mainly windows but I'd prefer not to break Linux/OSX compatibility.  My current plan was to use SSH port forwarding with PuTTY.  People aren't kidding about the bad performance though.

x2go is the answer you seek.  [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04) I guess those instructions are fine. Didn't look to closely. The clients for linux and Windows are solid.  All traffic goes over ssh, automatically, but setup ssh w/keys first.

---

### Post by pi-thrower on 2021-03-17
> **TheFu said:**
> x2go is the answer you seek.  [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04) I guess those instructions are fine. Didn't look to closely. The clients for linux and Windows are solid.  All traffic goes over ssh, automatically, but setup ssh w/keys first.

I don't seem to be able to win here.  I'm on a windows box that has key auth working.  I'm using the *same* private key in X2Go as i am in Putty.  It endlessly asks me for the decryption passphrase and never goes through.  Auth log shows only shows that the user disconnected during preauth after several attempts.

---

### Post by TheFu on 2021-03-17
> **pi-thrower said:**
> I don't seem to be able to win here.  I'm on a windows box that has key auth working.  I'm using the *same* private key in X2Go as i am in Putty.  It endlessly asks me for the decryption passphrase and never goes through.  Auth log shows only shows that the user disconnected during preauth after several attempts.

I don't think the same ssh-key format that putty uses works anywhere else. [S]Maybe if you setup the ssh-key using the pseudo-native Win10 ssh-keygen and append that over to the remote system?[/S]

Honestly, I haven't used x2go from Windows in over a year. We didn't move to Win10 here. We kept a few systems on Win7 for emergencies and all the others moved to Linux desktops.  Not everyone can do that.

Let me look for x2go issues with ssh-keys from Windows10.

Got it working.  Use the ssh-keygen program included with x2go, not the putty one.

A quick search found this guide from the x2go team: [https://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh](https://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh)
[LIST=1]
[*]Ok, so I booted a Win7 box, installed the "current" x2go client.  
[*]Created an **ssh-keygen -t ed25519** (using the ssh-keygen in the X2Go-Client directory) and forced it into the directory I wanted/expected.  For me, that was d:/Users/thefu/.ssh/  2 files are created ... id_ed25519 and id_ed25519.pub.  
[*]The .pub file has to be transferred to the remote system.  I used the x2go pscp.exe program to do that. On Unix, I'd use **ssh-copy-id** and it would do the right thing correctly, always.  
[*]From Windows, we are in the 1990s and have to manually get the .pub file over to the remote system, 
[/LIST]
Now move to the Linux server
[LIST=1]
[*]Next append it to the ~/.ssh/authorized_keys file correctly.  If you don't already have any ~/.ssh/authorized_keys file, just copy the .pub file into that file/location. Each key must be on 1 line. Some editors insert line breaks rather than wrapping. Don't allow that.
[*]The permissions need to be 600 on that file and 700 on the ~/.ssh/ directory.  Get those wrong and ssh won't work.  Security matters.
[/LIST]

Back on the client/Windows system, 
[LIST=1]
[*]run the x2go-client program.  
[*]In the session settings, there's a place to browse to the d:/Users/thefu/.ssh/id_ed25519  file and 
[*]1 checkbox that says to use that automatically.  
[/LIST]
The first time you use it, ssh-agent will ask if you want to remember the key-unlock credentials.  Your choice.  Then for the next few hours, you won't be asked to unlock that ssh key on any system where you've pushed that .pub keyfile.  

Personal Notes/Techniques: I use a different key for each customer and for different security levels for systems.  For normal servers inside a customer's LAN, I use 1 key.  But for any internet facing systems, I use a different key.  This sounds like a hassle, but it isn't.  On Unix systems, we can specify which keys are used for each remote system in the ~/.ssh/config file - it supports all sorts of other configuration options to make life easier.  But that's a different question.

If you don't use ed25519 keys ... well, please go read this: [https://nbeguier.medium.com/a-real-world-comparison-of-the-ssh-key-algorithms-b26b0b31bfd9](https://nbeguier.medium.com/a-real-world-comparison-of-the-ssh-key-algorithms-b26b0b31bfd9)  RSA and DSA really shouldn't be used.

I use x2go mainly when traveling, not when I'm at home working.  99.9% of the time, I use straight ssh connections from home. On the LAN, I'll use **ssh -X** for X/Windows tunneling.  It is much more convenient for me than wasting a full Linux desktop, but we are all different.  Right now, I have 22 windows open on my workstation across a few different virtual desktops. Of those, 10 are ssh sessions into other systems inside a terminal each. Each terminal gets started with something like this command:
```
xterm -geometry 80x25+1030+50 $XTERM_OPTS -e ssh -X istar &
```
They have different placement and different remote system names for a nice layout.  Some people use **tmux** or **screen** tools to accomplish the same thing. In the olden days, connectivity was not so great and a disconnect would kill remote programs. I've been lucky - never had that issue. Part of me wishes I'd have learned to use tmux.

You can tune x2go connection parameters as needed.  I usually set the connection speed to be 1 less than whatever the truth is. Also, I tweak the image compression to use 4k-png.  This is the difference between a nice, fast, experience and something sluggish ... like VNC or RDP.

Anyway, hope this is helpful and I'll see the night vs day difference that x2go provides.  xfce is a good choice, btw.  Really just avoiding Gnome3 seems to be the only DE requirement for x2go to work well.  I've used it from different continents and been happy.  I've connected to my Mom's Lubuntu desktop over the slowest DSL possible - basically ISDN speeds. That wasn't snappy, but it was serviceable.

---

### Post by ActionParsnip on 2021-03-18
What are you wanting to do on the remote system once you get connected via VNC? What is the purpose of the connection? There may be a sleeker solution to what you are trying to achieve

---

### Post by pi-thrower on 2021-03-18
> **TheFu said:**
> I don't think the same ssh-key format that putty uses works anywhere else. [S]Maybe if you setup the ssh-key using the pseudo-native Win10 ssh-keygen and append that over to the remote system?[/S]

Honestly, I haven't used x2go from Windows in over a year. We didn't move to Win10 here. We kept a few systems on Win7 for emergencies and all the others moved to Linux desktops.  Not everyone can do that.

Let me look for x2go issues with ssh-keys from Windows10.

Got it working.  Use the ssh-keygen program included with x2go, not the putty one.

A quick search found this guide from the x2go team: [https://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh](https://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh)
[LIST=1]
[*]Ok, so I booted a Win7 box, installed the "current" x2go client.
[*]Created an **ssh-keygen -t ed25519** (using the ssh-keygen in the X2Go-Client directory) and forced it into the directory I wanted/expected.  For me, that was d:/Users/thefu/.ssh/  2 files are created ... id_ed25519 and id_ed25519.pub.
[*]The .pub file has to be transferred to the remote system.  I used the x2go pscp.exe program to do that. On Unix, I'd use **ssh-copy-id** and it would do the right thing correctly, always.
[*]From Windows, we are in the 1990s and have to manually get the .pub file over to the remote system,
[/LIST]
Now move to the Linux server
[LIST=1]
[*]Next append it to the ~/.ssh/authorized_keys file correctly.  If you don't already have any ~/.ssh/authorized_keys file, just copy the .pub file into that file/location. Each key must be on 1 line. Some editors insert line breaks rather than wrapping. Don't allow that.
[*]The permissions need to be 600 on that file and 700 on the ~/.ssh/ directory.  Get those wrong and ssh won't work.  Security matters.
[/LIST]

Back on the client/Windows system, 
[LIST=1]
[*]run the x2go-client program.
[*]In the session settings, there's a place to browse to the d:/Users/thefu/.ssh/id_ed25519  file and
[*]1 checkbox that says to use that automatically.
[/LIST]
The first time you use it, ssh-agent will ask if you want to remember the key-unlock credentials.  Your choice.  Then for the next few hours, you won't be asked to unlock that ssh key on any system where you've pushed that .pub keyfile.  

Personal Notes/Techniques: I use a different key for each customer and for different security levels for systems.  For normal servers inside a customer's LAN, I use 1 key.  But for any internet facing systems, I use a different key.  This sounds like a hassle, but it isn't.  On Unix systems, we can specify which keys are used for each remote system in the ~/.ssh/config file - it supports all sorts of other configuration options to make life easier.  But that's a different question.

If you don't use ed25519 keys ... well, please go read this: [https://nbeguier.medium.com/a-real-world-comparison-of-the-ssh-key-algorithms-b26b0b31bfd9](https://nbeguier.medium.com/a-real-world-comparison-of-the-ssh-key-algorithms-b26b0b31bfd9)  RSA and DSA really shouldn't be used.

I use x2go mainly when traveling, not when I'm at home working.  99.9% of the time, I use straight ssh connections from home. On the LAN, I'll use **ssh -X** for X/Windows tunneling.  It is much more convenient for me than wasting a full Linux desktop, but we are all different.  Right now, I have 22 windows open on my workstation across a few different virtual desktops. Of those, 10 are ssh sessions into other systems inside a terminal each. Each terminal gets started with something like this command:
```
xterm -geometry 80x25+1030+50 $XTERM_OPTS -e ssh -X istar &
```
They have different placement and different remote system names for a nice layout.  Some people use **tmux** or **screen** tools to accomplish the same thing. In the olden days, connectivity was not so great and a disconnect would kill remote programs. I've been lucky - never had that issue. Part of me wishes I'd have learned to use tmux.

You can tune x2go connection parameters as needed.  I usually set the connection speed to be 1 less than whatever the truth is. Also, I tweak the image compression to use 4k-png.  This is the difference between a nice, fast, experience and something sluggish ... like VNC or RDP.

Anyway, hope this is helpful and I'll see the night vs day difference that x2go provides.  xfce is a good choice, btw.  Really just avoiding Gnome3 seems to be the only DE requirement for x2go to work well.  I've used it from different continents and been happy.  I've connected to my Mom's Lubuntu desktop over the slowest DSL possible - basically ISDN speeds. That wasn't snappy, but it was serviceable.

Thanks for the help.  I got this working on Windows with the recommended keygen.  It fired up on my ubuntu laptop with a couple attempts to figure out settings.

I noticed that after a certain amount of time (inactivity?), somewhere around 15 min, the session locks up.  The behavior is the same on both clients.  The cursor still moves and changes if hovered over the edge of a window but the session stops responding or any other inputs.  I even went so far as to open a terminal, wait for it to freeze then use 'wall' on a different terminal to see if the text would pop up.  It didn't.  Could it be that there is some sort of screen saver or power saving mode that X is trying to go into that i cannot wake it from?

---

### Post by pi-thrower on 2021-03-18
> **ActionParsnip said:**
> What are you wanting to do on the remote system once you get connected via VNC? What is the purpose of the connection? There may be a sleeker solution to what you are trying to achieve

A desktop that persists between connections on a computer at my home/office that i can access from the internet with minimal client side software.

---

### Post by TheFu on 2021-03-18
> **pi-thrower said:**
>  Could it be that there is some sort of screen saver or power saving mode that X is trying to go into that i cannot wake it from?

I suppose. I don't see that, but I don't use DEs.  I use fvwm or openbox, but mostly fvwm.
I used to work 8+ hrs a day from a Windows desktop into my Linux desktop using x2go. Did this for years.

Laptops likely have power saving or wifi disconnects or non-static IPs or screen savers.  Check all those.
I have my laptop setup to never sleep, never hibernate, unless I specifically request it.  Nightly, 5 minutes after the backups for that system complete, I have it pm-suspend.  That laptop happens to be on now:
```
$ uptime
 19:58:06 up 24 days,  9:14,  4 users,  load average: 0.03, 0.08, 0.08

```
It has a pm-suspend nightly, just after midnight, to make some daily backup reports clean.  Last night, 
```
=== Time for Backups to posc === 
StartTime 1616040424.00 (Thu Mar 18 00:07:04 2021)
EndTime 1616040602.84 (Thu Mar 18 00:10:02 2021)
ElapsedTime 178.84 (2 minutes 58.84 seconds)
TotalDestinationSizeChange 35680938 (34.0 MB)
```
It has a wired ethernet connection and via DHCP-reservations, a static IP when on my home LAN.
3 minutes to backup a running system - I can live with that.

It doesn't run x2go-server. It is just a client.  My main desktop runs inside a virtual machine (KVM) and I can access it via ssh, x2go or most often these days, using SPICE high-speed interconnects through an SSH tunnel.  SPICE is nearly fast enough to game.  But SPICE only works for KVM virtual machines, not for any other hypervisors or bare metal. Sorry.   I've posted some different performance tests in these forums between x2go, SPICE, and some other remote desktop methods. You might find that interesting.  SPICE blows away all the others.

---

### Post by TheFu on 2021-03-18
> **pi-thrower said:**
> A desktop that persists between connections on a computer at my home/office that i can access from the internet with minimal client side software.

I really hope your employer blocks all ssh outbound traffic.  Employers should mandate the use of proxy servers for all traffic egress and block all default routes from internal desktops to the internet.  DNS queries for internet servers shouldn't work from a desktop. No routing to the internet from desktops either.  Some things are just too scary to consider.

But it is their network, not mine.

---

### Post by pi-thrower on 2021-03-18
> **TheFu said:**
> I suppose. I don't see that, but I don't use DEs.  I use fvwm or openbox, but mostly fvwm.

Truth be told, i'd prefer fvwm as well.  At this point i'm getting back into the Linux game after a long time away.  I gotta pick and choose my learning curves.  Hitting the ez-button and installing the Xubuntu core let me skip over most things involved in getting X running.

Uninstalling xfce4-screensaver and disabling display power management then rebooting yielded a system that hasn't frozen yet.  I'll leave the session up overnight.

---

### Post by TheFu on 2021-03-18
That should do it. Because my "desktop" is inside a VM, it is headless and there isn't any power management nor screen savers. Those don't make sense.

Nothing wrong with ez-buttons, provided they work.  fvwm still needs that config file you recall, but getting it working via x2go is just selecting "Custom" and putting in /usr/bin/fvwm for the command to run.  Assuming you have fvwm installed from the repos.

---

### Post by ActionParsnip on 2021-03-19
> **pi-thrower said:**
> A desktop that persists between connections on a computer at my home/office that i can access from the internet with minimal client side software.

Yes, but what will you do on the persistent desktop, that's the question.

---

### Post by pi-thrower on 2021-03-24
Found the fix!

[https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381/2](https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381/2)

---

### Post by TheFu on 2021-03-24
snap packages break all sorts of new things. I knew about this issue had snaps been mentioned earlier might have clicked sooner. Probably not, but sorry just the same.

Notes are for chromium. I prefer to use a browser on a locked down VM.
```
# ##############################################
#   ####  Not working over remote X11 due to ~/.Xauthority problems
#   ## log into the remote system and setup the .Xauthority for each snap
cd ~/snap/chromium/current
ln -s ~/.Xauthority
```

---

### Post by scorp123 on 2021-03-30
> **pi-thrower said:**
> Could it be that there is some sort of screen saver or power saving mode that X is trying to go into that i cannot wake it from?

Yes, I had the same issue here where I work. I installed XFCE and it would randomly freeze on my X2go users. Solution for me was to remove the **"xfce4-screensaver"** package. Depending on what desktop UI you use you might need to identify the screensaver package there and remove it too? Since you're using the desktop UI via X2go there really is no need for a screensaver, in my opinion.

---

