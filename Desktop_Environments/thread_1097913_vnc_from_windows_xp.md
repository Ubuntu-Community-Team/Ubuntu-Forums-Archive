---
title: "vnc from windows xp"
date: 2009-03-16
forum: Desktop Environments
---

### Post by fabianus on 2009-03-16
Hello all, 

I would like to access to my ubuntu desktop (graphical interface) from another machine. I can see that on ubuntu 8.10 there is a Remote desktop Viewer installed by default. Now, what programm do I have to install in windows XP in order to do this from my windows machine?

Thanks a lot for any feedback !

Regards, 
Fabianus

---

### Post by alfplayer on 2009-03-16
UltraVNC should work.

---

### Post by fabianus on 2009-03-16
Hi alfaplayer !

thanks for your suggestion. I compared ultraVNC with tightVNC. UltraVNC is much faster (rendering faster the screen). But yet, it's not instant (dispite that fact that I am on a 100 bit Lan connection. I wonder if there is any solution to make this better. 

Also I would like to connect in secured mode. But if I turn on "Require encryption" it doesn't accept, saying with UltraVNC : "No Security type suitable for RFB 3.3 supported". 

Thanks for your help!

Regards, 
Fabianus

---

### Post by TinSoldier on 2009-03-16
Iv used Ubuntu before on this laptop but had to give up on it as my laptop is an HP and there was no solution to my video driver issue in Ubuntu..

That said, iv recently resurrected one of my other systems, its a desktop which used to have win XP Pro but i want to get rid of that.

Sooo, im going to install Ubuntu under windows to start with just to see how everything works hardware wise...

Iv also used to use TightVNC on this laptop and this other resurrected desktop machine, using both win98 and XP, both with no problems.

So as long as TightVNC and Ubuntu get along i don't see any issues.

My use was simply for remote desktop control of the resurrected machine, i found it much better to use my LAN and sharing to access the hard drives and CD / DVD drives, its much faster than transferring files through VNC.

So I will be setting this Ubuntu > **VNC > XP process up again and will report back here with any findings very soon.

---

### Post by alfplayer on 2009-03-16
TightVNC on windows should also work, I think it's mostly about finding out which one plays nicer with your VNC server (speed, supported features, bugs, etc.).
There is also FreeNX, it is supposed to be faster than VNC, it has a windows client but I haven't tried it.
I set up encryption with UltraVNC using a plugin about a year ago, both the server and the client were running UltraVNC (on windows). I don't know if VNC servers on linux support encryption but I wouldn't find it very useful because I would use a proven system like a SSH tunnel or a VPN that can encrypt any type of traffic.

---

### Post by andrea000 on 2009-03-16
you could remote desk top into it.I use tight vnc but i only run windows on 
virtual box for using autocad.But tight vnc is my pick

---

### Post by Thomasbx on 2009-03-17
Very informative.

I just loaded ubuntuon one of my workstations in a dual boot with XP Pro.

I am trying to connect to remote it over my lan using tightVNC which I just downloaded and installed on my laptop after reading this forum.

What do I need to do on ubuntu, service to start, etc...

I can not see my ubuntu box on my network, though I can see and manipulate files on my other networked boxes from ubuntu.

Thanks - Tom

---

### Post by andrea000 on 2009-03-18
> **Thomasbx said:**
> Very informative.

I just loaded ubuntuon one of my workstations in a dual boot with XP Pro.

I am trying to connect to remote it over my lan using tightVNC which I just downloaded and installed on my laptop after reading this forum.

What do I need to do on ubuntu, service to start, etc...

I can not see my ubuntu box on my network, though I can see and manipulate files on my other networked boxes from ubuntu.

Thanks - Tom

windows can't see a linux drive but linux can see a windows it depends
on what you are trying to do if it's just remoteing in from windows then
a vnc server and ssh tunneling and maybe terminal service's(not sure on 
that one)are you looking to run apps off the Ubuntu machine if so then 
terminal service's wouldn't be a bad idea.There may be more or less i run
a terminal server and from what i remember there are more.If your printing from 
the Ubuntu machine cups needs to be installed and samba for reading and writing
to a linux drive from windows.Without knowing exactly were your going
i can't say for sure.Maybe someone else on here can give you more expert 
advice.

Good luck

---

### Post by Anis0123 on 2009-03-18
Hi All!
Do any of you have any experience with these VNCs or others? I would like to learn and become proficient with the best VNC out there? I want to remote admin some 98 machines. And can they be done simultaneously like updating something like zone-alarm? Anyone have any experiences with this stuff?

---

### Post by andrea000 on 2009-03-18
> **Anis0123 said:**
> Hi All!
Do any of you have any experience with these VNCs or others? I would like to learn and become proficient with the best VNC out there? I want to remote admin some 98 machines. And can they be done simultaneously like updating something like zone-alarm? Anyone have any experiences with this stuff?

Just asking but does zone-alarm have a management console for linux?
I like using tight vnc but i am all Ubuntu now i only run autocad 
and itunes from Virtual Box as Linux has a open source app for about 
everything else.The vnc is just a viewer and the vnc server is just 
a way of tunneling ssh once setup unless you have a big problem that's 
about all there is to do.

Andrea

---

### Post by doghousedean on 2009-03-18
Morning all,

I have installed Ubuntu desktop on a machine in a remote location, enabled remote desktop and opened port 5800 and 5900.

The problem im getting is when i connect with realvnc or any other vnc app it refuses to show the desktop, it will accept my password and everything and even shows as authenticated on some apps i have tried (mainly on my phone, Nokia N95 with 2 different VNC clients)

Its almost like i need to open another port or something on the firewall or its blocking a specific protocol, does vnc use TCP or UDP as standard or is it using RDP?

Thanks for your help

EDIT: Also is ssh/telnet disabled by default on installation of ubuntu, it refuses to connect, active refusal looks like ubuntu is blocking the port too.

---

### Post by fabianus on 2009-03-18
Hi Alfaplayer, 

thanks for the suggestion about tunneling, I found a nice howto about it : 

[http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/](http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/)

Regards, 
Fabianus

---

### Post by kwacka on 2009-03-18
An alternative (which may be a bit faster) is 'No Machine" see [http://www.nomachine.com/](http://www.nomachine.com/)

How-to at: [http://ubuntuforums.org/showthread.php?t=941530](http://ubuntuforums.org/showthread.php?t=941530)

---

### Post by doghousedean on 2009-03-18
> **kwacka said:**
> An alternative (which may be a bit faster) is 'No Machine" see [http://www.nomachine.com/](http://www.nomachine.com/)

How-to at: [http://ubuntuforums.org/showthread.php?t=941530](http://ubuntuforums.org/showthread.php?t=941530)

Thanks but the problem is that it doesnt even show the vnc screen.  Its a remote server and difficult to gain physical access to to install more software.

I will have to go to site, thanks anyway

---

### Post by alfplayer on 2009-03-18
**Anis0123**:
You have to find out if there is a VNC server that works on win98 (it's old), you may need an old version (with old clients).
Updating ZoneAlarm over VNC? I don't think this is possible because you would need the network up after rebooting.

**andrea000**:
> Just asking but does zone-alarm have a management console for linux?
I don't think so.
> the vnc server is just a way of tunneling ssh once setup
A VNC server is a program that shares a desktop with other computers over the Internet. A VNC client or viewer is the program that displays and controls that desktop.
Tunneling is not necessary with VNC but can be used to secure the traffic between the server and the client.

**doghousedean**:
You can try connecting from a pc, the default VNC server in Ubuntu is vino. In my system it is only listening in TCP 5900 (not UDP). Authentication is also worked out in that port so apparently the port is open in your Ubuntu, that means that your port is open in the firewall. Maybe you have a configuration problem in your network or you haven't found a VNC client that can connect to Ubuntu.

---

### Post by andrea000 on 2009-03-18
I wasn't trying to get to deep into the tech stuff.
i am sure there are smarter people on here.I was just
trying to give a basic understanding of how it works.

sorry

voce ir caras

Boa tarde

---

### Post by TinSoldier on 2009-03-18
Wouldn't you know it, i had to re-install XP AGAIN cause i messed it up somehow, or did it mess-up cause it's windows ? .

So anyway, just another annoying delay in the process.....


I don't really, but i have played with 3 systems locally in the past, but that was using TightVNC, just so i didn't have to switch from keyboard to keyboard.

Prior to that in past years, i had a four system setup running a multi-line dial-in BBS.  The multi system was the cheaper way to go for 4 dial in modems and all so allowed the BBS to support 4 user multi-player games ( can anyone say 4 player DOOM way back when).
Back back then i was using a Lantastic network with a BNC cable system.

You left out some info here, are you using or planning on using Ubuntu or is this a windows system?

Second, with 98 machines i would go with a store bought back-up - restore solution ( Norton ghost maybe).  Something that would allow you to make a backup restore DVD or CD set and or supported networking restore process.  

The VNC would be useful for monitoring / desktop control of the machines, the one issue here is that (tightVNC) uses the IP as the identifier for each machine, you dont have a machine name to use, you would need a map of the machines and the assinged IP for each.

Another thing is not all programs will display properly across VNC's connection, you could have very degraded display or even no display from the remote program, it would be trial and error... for all app's being used.

> **Anis0123 said:**
> Hi All!
Do any of you have any experience with these VNCs or others? I would like to learn and become proficient with the best VNC out there? I want to remote admin some 98 machines. And can they be done simultaneously like updating something like zone-alarm? Anyone have any experiences with this stuff?

---

