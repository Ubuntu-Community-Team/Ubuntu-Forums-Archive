---
title: "Logins, Desktops and Remote Access"
date: 2023-02-05
forum: Desktop Environments
---

### Post by sahulkko on 2023-02-05
Hi,
I do not know if this is the right forum to ask this kind of things but would'nt it be a good thing that one could:
- Define a RDP/VNC connection to be a desktop also on Desktops (the now local desktops) list?
  - On would have remote desktop on and easily accessible trough 'Desktops' upon login
  - One could have multiple remote desktops open to multiple systems upon login
  - One could open and close remote desktops that are pre-configured in settings
[IMG]https://privateer925-my.sharepoint.com/:i:/r/personal/samihulkko_quantum-black-hole_com/Documents/Pictures/vnc.png?download=1[/IMG]

---

### Post by TheFu on 2023-02-05
Unix people don't use remote desktops. We use either ssh or remote X11 to run commands on other systems.  A full desktop being needed seems like a failure. Who needs all that overhead and doesn't want the programs integrated into their local desktop, regardless of where it is actually running?

The display location and the place where a program is running ARE NOT THE SAME.  There's a client/server architecture built into X11.  Use it.  When used with ssh X11Forwarding, all the traffic from the remote X/Client would be shipped to your local X/Server through that ssh tunnel.  It is very easy and has worked nearly 30 yrs.  

Stop thinking about remote desktops. That's a failure.

---

### Post by DuckHook on 2023-02-05
RDP has its uses. I use it, by way of Remmina, to access my Windows VMs, all of which are running locally within LXD containers. By using RDP, I don't have to install the virt-viewer/manager overhead. More importantly, I can map Windows' audio through RDP which, due to driver limitations, I cannot get through virt-viewer. Performance is better and I have more options as to video overhead.

I do agree that most people misconfigure RDP so badly that it becomes a security nightmare. For this reason alone, a visceral rejection of RDP is safer than an unreflective implementation of it. RDP is a notorious security cesspool for good reason but, if used properly, carefully and in a controlled way, it has its benefits.

---

### Post by TheFu on 2023-02-06
So ... the OP was in the DE subforum wanting to connect to other Linux systems.  That's why I was saying a remote desktop is usually a failure and unneeded.  Remote desktops break the fully integrated windowing capabilities of X11 that have worked for many decades.

There definitely are times when a full remote desktop makes sense to use.  When traveling and you don't want to bring any sensitive data with you, using a full remote desktop back into your main desktop computer makes perfect sense.  It is also nice to have a $200 laptop for this, so if it is lost or stolen during the trip, much less money was lost.
I'm loosing more and more touch with MS-Windows, since it is used less and less.  Because of things MS-Windows lacks, we are forced to use a full remote desktop into it for almost every purpose if any GUI program is needed.  For me, that's accounting and tax programs only. Those work fine, though I connect to the VM using virt-viewer with SPICE and the QXL driver for the Windows virtual machine.  If it runs directly on hardware, then SPICE cannot be used. Sigh.  Yet another reason for Windows to always be put into a virtual machine.  SPICE+QXL makes the GUI snappy, unlike other options.  I think there might be newer methods that are faster, but my VM-host with the Windows VM is on 18.04 still, which doesn't support virtGL (or whatever they call it this week).  Plans have been made to move to 20.04 on that system, soonish. ;)

Regardless, I'll avoid using full remote desktops, unless it is required to actually work.  I run many Linux programs on remote systems ... this browser is running on a different system. Same for thunderbird and a few other "high-risk" programs.  Performance is just like they are local, though I don't really watch videos in a browser.  I tend to snag the URL and use 'mpv' for that on the local workstation.

Over the decades, I've found that MS-Windows-centric people never learned that a full desktop isn't needed to run programs on other systems.  That's my main intent with these posts.  To open their eyes for a more efficient method, but only they can decide to try it and see it working.  How I run thunderbird on a different system, inside a firejail with limited access to RAM:
```
#!/bin/bash
TB_OPTS="-no-remote "
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=4700000000 "
ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ &

```
I do something similar for firefox and most other programs that I want to run on other systems, daily.

---

### Post by ActionParsnip on 2023-02-07
Are you wanting to connect to a Linux system from Windows or from Linux to Windows? Linux to Windows? Which way around please?

---

### Post by sahulkko on 2023-02-09
So, 1 click i have desktop to remote X11 is failure? With good positioning and ease of use on UI?

---

### Post by sahulkko on 2023-02-09
I have a xRDP and VNC servers working ok (with full remote X11 desktop). This is more of a question of usability of UI with Desktops that is now local would have possibility to have a VNC or RDP open when login. It would show on Desktops view on user interface.

---

### Post by adamjason on 2023-02-09
If you're encountering issues with logins, desktops, and remote access on Ubuntu, here are some steps you can try to resolve the issue:


[LIST=1]
[*]Check your login credentials: Make sure that you're using the correct username and password for your Ubuntu system. If you've forgotten your password, you can reset it using the recovery mode or by contacting the system administrator.
[*]Restart the display manager: If you're having trouble logging into your desktop, you can try restarting the display manager. To do this, log into a virtual terminal (e.g. Ctrl + Alt + F1) and run the following command:
[/LIST]
 
**          sudo service lightdm restart**
 

[LIST=1]
[*]Disable remote access: If you're encountering issues with remote access, you may need to disable it temporarily to see if it[']("https://dolgeneraldgme.com")s causing the issue. To disable remote access in Ubuntu, go to System Settings -> Remote Desktop[,]("https://mynstromy.com") and turn off the "Allow other users to view your desktop" and "Allow other users to control your desktop" options.
[/LIST]
 

[LIST=1]
[*]Check the firewall: If you're encountering issues with remote access, it's possible that your firewall is blocking incoming connections. To check the firewall in Ubuntu, run the following command.
[/LIST]
 
**         sudo ufw status**
 
If the firewall is active, you may need to allow incoming connections for the relevant services (e.g. SSH, VNC, RDP, etc.)


[LIST=1]
[*]Update the system: If you're encountering issues with logins or desktops, it may be due to outdated software or drivers. To update your Ubuntu system, run the following commands:
[/LIST]

**       sudo apt-get update**
**       sudo apt-get upgrade**
 
These steps should help you resolve the issue of logins, desktops, and remote access on Ubuntu. However, if the issue persists, you may need to seek technical support from the Ubuntu community or consult the Ubuntu forums.

---

### Post by TheFu on 2023-02-09
> **sahulkko said:**
> So, 1 click i have desktop to remote X11 is failure? With good positioning and ease of use on UI?

Not at all.  Remote X11 is what I'm suggesting you use, not a remote desktop.  In this way, each application window integrates into your normal desktop and each window can be placed into any workspace or on any monitor you like, regardless of other X11 client window locations.

I use 1 click for this - actually, I have 1 key-chords setup to launch applications on other systems, but display them locally.

Mainly, this avoids the entire DE problem, since the DE on a remote system doesn't matter. It isn't used.

---

### Post by sahulkko on 2023-02-14
> **TheFu said:**
> Not at all.  Remote X11 is what I'm suggesting you use, not a remote desktop.  In this way, each application window integrates into your normal desktop and each window can be placed into any workspace or on any monitor you like, regardless of other X11 client window locations.

I use 1 click for this - actually, I have 1 key-chords setup to launch applications on other systems, but display them locally.

Mainly, this avoids the entire DE problem, since the DE on a remote system doesn't matter. It isn't used.

Yes well: 1-click open remote desktop X11 (RealVNC), move to desktop 2 few clicks (right click...), define full screen for VNC client for few clicks.

or: In settings app define desktop number and VNC connection address (ssh tunnel possibly?) and does it open upon login automatically. Quick link if not open in app list desktop view to open 1-click. <-- is one-click above NOT.
SH

---

