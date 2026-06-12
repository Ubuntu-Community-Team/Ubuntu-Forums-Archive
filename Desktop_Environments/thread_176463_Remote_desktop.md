---
title: "Remote desktop"
date: 2006-05-14
forum: Desktop Environments
---

### Post by christooss on 2006-05-14
Hello

Which application should I use if I want graphical remote desktop?

I would need a server aplication on ubuntu machine and viewers on both linux and windows machine


I was looking around and I found RealVNC but it doesn't bring many of the feautures in basic installation. File transfer would be a must

Thanks for the anwsers

---

### Post by aysiu on 2006-05-15
I don't think file transfer and remote desktop go together. 

Remote desktop means you can view and/or control the PC from another PC.

Maybe you're thinking of SSH?

If you want VNC, though, I would highly recommend TightVNC, which is available for both WIndows and Ubuntu.

---

### Post by christooss on 2006-05-15
[QUOTE=aysiu]I don't think file transfer and remote desktop go together. 

Remote desktop means you can view and/or control the PC from another PC.

Maybe you're thinking of SSH?

If you want VNC, though, I would highly recommend TightVNC, which is available for both WIndows and Ubuntu.[/QUOTE]

:)

But i would like to have GUI interface for everything together.

I will try thightvnc. Thanks

---

### Post by fallencan on 2006-05-16
gnome-rdp wokred for me. using dapper flight7 in laptop and win xp pro in desktop. connecting from laptop to desktop take my 30 second almost.

---

### Post by xenmax on 2006-05-16
Krdc, a KDE app is excellent. I highly recommended it.(it was recommended to me by GeneralZod if i remember correctly). I use it even though my DE is Gnome.
In XP, i use TightVnc viewer. However, like aysiu, i have not come across (or am not aware if feature exists) any app with remote desktop and file transfer bundled together.

---

### Post by christooss on 2006-05-16
For file transfer I can transfer it through email. But I really see that I have to learn about ssh

---

### Post by elamericano on 2006-05-16
[QUOTE=christooss]For file transfer I can transfer it through email. But I really see that I have to learn about ssh[/QUOTE]

You mean scp, not ssh.

If you're going to access from a windows OS, maybe vnc and ftp is the combination you want. There are plenty of clients for that. (Filezilla on Windows)

Also, you can mix and match vnc clients. I like UltraVNC on windows for its auto-scaling, although you don't get some of the features (like file transfer) unless both sides are UltraVNC.

---

### Post by wthanna on 2006-05-16
WinSCP is free and can be used to transfer files securely between the windows machine and the ubuntu machine.   [http://www.winscp.com/](http://www.winscp.com/)     I highly recommend freenx for your remote desktop connections. Clients for freenx are available for free for both windows and ubuntu, and it is much faster than VNC. I use these two programs together, and they do everything I need them to do.

---

### Post by changlinn on 2006-05-16
I tend to use rdesktop as it can be scripted very easily, krdc is good cause it supports resizing, so a 1024x768 fits into 800x600, good for me vncing into a high resolution pc on this low res laptop. Krdc also scripts nicely.
File transfer I assume would be tricky to do like MS do in rdp, since it would have to map a folder to the server, or the whole thing. I just use, sftp, ftp, even samba.

---

### Post by jones_jj on 2006-05-17
Now this is going to sound pretty stupid, but I was reading a help file on how to view a Ubuntu desktop remotely via Windows and it said something about going to System->Preferences->Remote Desktop and doing some configuration with Remote Desktop.  Well When I go to System->Preferences there is no Remote Desktop application.  Is this a default application that is off the CD or do you have to do an apt-get to get it?  I do have rdesktop which seems to be a different application.  rdesktop pretty much only allows from Ubuntu to Windows, I want to go the other way.

Thanks for the help.

---

### Post by stealth_gsx1300r on 2006-05-17
You can also do file transfer through samba for win2lin or nfs for lin2lin...

---

### Post by changlinn on 2006-05-17
jones_jj - I think the help file is telling you how to connect from Ubuntu to a windows pc. For Windows to ubuntu, you will probably want to look at vnc and its variants, probably either tightvnc or realvnc.You apt-get install it, or use synaptic/aptitude. Then configure it with password etc.
Then on windows go to tightvnc or realvnc's website and download the viewer only or the whole install. Then open the viewer point it at the ip of the ubuntu server and you are done, if you are on the same lan that is, different kettle of fish if you aren't

---

### Post by AndyCooll on 2006-05-18
Remote desktop is already installed in Ubuntu, you just need to amend the settings. Part of the process involves allowing permissions to login to your desktop. This is done under System-->Preferences-->Remote Desktop (not being at my box as I'm at work at the moment I'm not sure if this is correct). 

To use the client process go to Menu-->System Tools-->Terminal Server Client. There are a number of versions you can use, RDP, VNC.

Other alternatives maybe to look at Freenx (there is a Win$ version of this too).

For _Linux to Linux_ you can also use ssh to open indivdual remote graphical applications that exist on another machine and then have them display on the machine you are sat at. 
Additionally you could use GUI's Ctrl+Alt+F9 to F12 and have the whole desktop of your remote pc on your local machine. This is what I use. I have 3 other boxes around the house and login to them from my main machine. My main machine is on F7, my server F9 etc etc. I just flick between them as needed.

:cool:

---

### Post by melchior on 2006-05-19
Does anyone have a solution for connecting to a remote session? The same way as the built in vnc server does in picking up the existing session, only faster? (since vino is uselessly slow even over LAN)

thanks!

---

### Post by vinfred on 2006-05-19
Have a look at [http://www.ubuntuforums.org/showthread.php?t=179109](http://www.ubuntuforums.org/showthread.php?t=179109)

The Xserver section provides you what hou need if you're in front of a MS Windows workstation

I'm pretty certain it would not be to hard to do also from an Ubuntu workstation
I would search for how to create xdmcp session

---

### Post by jones_jj on 2006-05-19
> Remote desktop is already installed in Ubuntu, you just need to amend the settings. Part of the process involves allowing permissions to login to your desktop. This is done under System-->Preferences-->Remote Desktop (not being at my box as I'm at work at the moment I'm not sure if this is correct).


Now I've done an install of Ubuntu, and it never sees the light of day, e.g. it does not have an internet connection.  I am on dialup, poor me.  So this means I have a base install of Breezy from the CD that I have.  I have looked up System->Preferences and there is no Remote Desktop anywhere at all.

To get rdesktop, I had to install it using synaptic and it's there, but that's pretty much only a command line application to get the process started.  Where would one find Remote Desktop if not connected to internet?  Is it on the base install off the CD or no?

Thanks.

---

### Post by xenmax on 2006-05-19
On my Breezy install, i find it at Applications - > Internet -> Terminal Server Client. This must be from base install since i don;t remember installing remote desktop seperately.

---

### Post by jones_jj on 2006-05-19
[QUOTE=xenmax]On my Breezy install, i find it at Applications - > Internet -> Terminal Server Client. This must be from base install since i don;t remember installing remote desktop seperately.[/QUOTE]

Now this is just a client, does it also have server settings also?  I read somewhere under the infamous remote desktop preference you should be able to allow X forwarding.  Maybe it's time for me to get my eyes checked again because I just don't see remote desktop anywhere.  I will have to check out Terminal Server Client to see what it has.

---

### Post by jimcooncat on 2006-05-19
On Windows, I use UltraVNC for both a server and a viewer. It comes with file transfer and chat for Windows to Windows.

For SSH and file transfer between Windows and Linux, get WinSCP. It comes with the PuTTY tools, which serve as the SSH client. 

There's a bit of learning to do to make it all work securely, and much more can be learned to add a lot of functionality. It's all good learning though -- you'll use the knowledge for years to come. For example, use SSH tunnelling to VNC across the internet.

Other technologies that comes in handy:
[LIST]
[*]Samba, especially for printing
[*]xming, view your Ubuntu programs directly on your Windows desktop
[*]FreeNX, faster alternative to VNC across slow networks
[*]Pageant (Windows) and keychain (Linux) for managing keys
[*]IMAP, for central email storage you can access from any client
[/LIST]

---

### Post by xenmax on 2006-05-20
[quote=jones_jj]Now this is just a client, does it also have server settings also?  I read somewhere under the infamous remote desktop preference you should be able to allow X forwarding.  Maybe it's time for me to get my eyes checked again because I just don't see remote desktop anywhere.  I will have to check out Terminal Server Client to see what it has.[/quote]
Yes, thats just the client. I don;t know much about server settings, however, i can see "Remote Desktop" available under System->Preferences.

---

### Post by jones_jj on 2006-05-23
You know I must be the only person to have an install of Breezy that doesn't have Remote Desktop under System->Preferences.  I did an install with the CD with no outside connection to download anything.  I take it this is a default application that gets installed?

---

### Post by rvergara on 2006-05-23
just install vino using synaptic. It will probably ask for other packages (vnc common and vnc viewer, I believe) just confirm those as well and that will do it.

Regards

Ramiro

---

### Post by jones_jj on 2006-05-25
Easier said then done.  My Ubuntu server never sees an internet connection.  :-(

---

### Post by brentoboy on 2006-05-25
THIS SUGGESTION ONLY WORKS ACROSS A LAN, and IT IS NOT VERY SECURE!!!
But it works, I spent the last few months looking for options on doing exactly what you are asking about, and this is the best I can come up with:


get cygwin for your windows box, then you can connect to a graphical desktop on any linux PC on your lan that is running xdmcp (which can be enabled in the gdm preferences -- I think it is "login screen" in the admin menu)

share your local folders that you want to have access to, and then, once you are in your server, map a samba share to your client PC, then you have access to your files.

from linux, if you want a relativly "thin" client, install the server install, add x-window-system-core, xserver-xorg, and gdm that's it.  when gdm boots, the actions menu lets you run a session using xdmpc--effectivly making you a thin client.  you might also want the msttcorefonts package to make websites look a little cleaner.

if you want a thick client, then do the same thing, except install the entire ubuntu system, and when you want to start a client-server session, use the newlogin option in the Applications>System Tools menu  There is also a newlogin option to run your new login in a window (rather than full screen) so then you dont even have to suspend your existing session to start a remote thin session.

as long as you have a good lan in place, you will not notice any lag at all (at least I dont) it is like I am sitting at the primary computer when I work from the other workstations.  my old pentuim 233 w 48 MB ram humms like the p4 its connected to.

---

### Post by spelingchampeon on 2006-05-25
Currently I am using the default VNC program that comes with Breezy. My main problem is, upon boot (I have VNC running at startup) most of system resources are being used by VNC. It takes a couple of seconds for me to move around the remote machine (Ubuntu) files. I was under the impression that VNC was not a resource hog, but I'll be damn! If I was to shut down VNC and hook up a monitor, my system screams FREEDOM and runs like a monster machine..no lag or slowdowns whatsoever. 

The other programs mentioned (FreeNX or TightVNC).. do they tie up a lot of resources? Also, is setting these programs to run at boot easy or daunting?

BTW, I have a P3 950 with 256meg ram on my Ubuntu box...

---

### Post by jones_jj on 2006-05-25
Just a quick question.  What is xdmpc and what does it do?

---

### Post by christooss on 2006-05-26
Speling champeon how to kill vnc?

---

### Post by spelingchampeon on 2006-05-26
[QUOTE=christooss]Speling champeon how to kill vnc?[/QUOTE]I'm not looking to kill VNC, I'm looking for something that isnt a resource hog. If I killed it, I would lose my ability to remote into it again, without rebooting. 

Since I am fairly new to Linux.. I have many questions, and this one is beyond me. If I go to TERMINAL and put in TOP, it shows vino-server (remote desktop) as using on average 56-60% cpu usage. This is KILLING my ability to move about remotely. Thats why I was looking for something that does not use so many resources... any ideas?

---

### Post by brentoboy on 2006-05-26
[QUOTE=jones_jj]Just a quick question.  What is xdmpc and what does it do?[/QUOTE]

xdmcp can be enabled in the login manager (gdm) settings by allowing remote login (the second tab).

in a nutshell, it listens on a port on your network for incoming remote requests to run an x session from across the lan.

"clients" boot to the gui login, and then, instead of loging in, they choose to login to a remote host.  (ussually in the actions menu, I see it for both kdm and gdm on dapper, and dont have any breezy's left in the house)

anyway, the prelogin screen then offers you a list of all the pc's who resonded when they broadcast out on the network: "hey do any of you support xdmcp?"

then, you pick one, and it loads the remote gdm login to the local pc.  then, you have a client (potentially slow shell of a pc) and a server (whiz bang get-er-done pc) and for the entire session, all the user interaction happens on the client PC, and all the programs are acutally run from the server.  The client benefits from low low disk acess, and relativly unchanging memory usage.

its great if you are like me and have one expensive pc (yours) and then a few cheapies from a thrift store, and you want other people in the house to stop copmlainting about how bad thier PCs suck.

it is as easy to comprimise your system when xdmcp as it would be if someone was right there at the pc itself, the login just asks for your name and password, and I think it sends them across your lan without any encrypion.

make sure, if your router doesnt block all incoming ports already, that it specifically blocks that one you define in the advanced area of xdmcp setup.  (you really should leave it at the default anyway, so as to not create problems on the clients)

---

### Post by jones_jj on 2006-05-27
Well thanks Brentoboy for the nutshell description of what xdmcp and what it does.

Another quick question, what is XUbuntu and what is the difference between it and Ubuntu?  Probably a wrong place for this question, but I have seen it show up in the desktop forums about XUbuntu not working this way or that way... Thansk

---

### Post by brentoboy on 2006-05-27
> what is XUbuntu and what is the difference between it and Ubuntu?

Ubuntu uses the Gnome desktop
Kubuntu uses the KDE desktop
Xubuntu uses the xfce desktop

xfce is generally a bit more light weight.
it works for folks who have somewhat older PCs, or who just like to run a little bit meaner.

each desktop includes "standard" things like office software (gnome: abiword, and gnumeric), (kde: has koffice) (xfce - I donno)   Web browser (Konquerer, Epiphany, I donno) Text editor (gedit, kate, mousepad)  as well as configuration / control panel type stuff.  for what it's worth, I prefer mousepad to either of the others, it is exatly what I need from a text editor, and it opens way faster than gedit does on my pc.

kde tends to have more options, gnome tends too look better by default, but doesnt allow much configuration beyond that, and xfce tries to do things in a more minimalistic way.

but-- (and here is where you will get a dosen people pipe in and defend xfce) -- if you really want to be minimalistic, I recommend fluxbox or openbox, but take a couple of days to get used to, but they are really really small.  and they arent full blown "desktops" meaning they dont have the basic stuff like web browsers, office apps, and texteditors that are built specifically for them with a common theme and goal.

from any (x/k/ubuntu) you can run any app from any of the others, so it really is just a matter of what looks good on your PC, and what runs smoothest.

I use ubuntu (I have been test driving kubuntu for the last few days, just to see if I like it more in dapper than I did in breezy)

---

### Post by jones_jj on 2006-05-28
Now will XUbuntu be a part of the same image as Ubuntu, or is it a seperate image?   I get my CDs from ShipIT (I think is what it's called) are they going to offer XUbuntu that way, or do you have to download the ISO for it?

---

### Post by brentoboy on 2006-05-29
some day, xubuntu will be its own cd, but for now, you just get any of the other cds, and install the "server" option, which includes no gui stuff, and 
apt-get install xubuntu-desktop

that grabs all the stuff that willsome day be the xubuntu cd.

search the wiki for more xubuntu details, I havnt used it enough to really know answers for xub' stuff

---

### Post by aysiu on 2006-05-29
[QUOTE=brentoboy]some day, xubuntu will be its own cd[/QUOTE] You mean this Thursday, right?

---

### Post by jones_jj on 2006-05-30
Thanks a lot brentboy for the nutshell description of what Xubuntu is, I really appreciate it.

---

### Post by starkruzr on 2006-06-13
So I installed vncserver (which is apparently realvnc) on my Dapper server, and UltraVNC on my Windows desktop.  When I connect to the Dapper machine, the window appears to be 640x480 and scales weirdly, and the color depth is atrocious (it might be 256 or even 16 colors).  I tried editing /etc/vnc.conf to force a 1024x768 resolution and 32K color depth, but when I did that I got a blank screen rather than my metacity desktop when I connected.  No amount of clicking produced a menu of any kind.  I changed it back and have the same problem.

Help?

---

### Post by christooss on 2006-06-13
I use tightVNC client for connecting from windows machine. I choose best compresion. and picture is normal ubuntu resolution.

As server I use that one which comes with ubuntu by default

---

### Post by encompass on 2006-06-20
[QUOTE=jones_jj]Now this is going to sound pretty stupid, but I was reading a help file on how to view a Ubuntu desktop remotely via Windows and it said something about going to System->Preferences->Remote Desktop and doing some configuration with Remote Desktop.  Well When I go to System->Preferences there is no Remote Desktop application.  Is this a default application that is off the CD or do you have to do an apt-get to get it?  I do have rdesktop which seems to be a different application.  rdesktop pretty much only allows from Ubuntu to Windows, I want to go the other way.

Thanks for the help.[/QUOTE]
First I would start a new post here as it doesn't totally aply to this thread.
If you are in ubuntu you can enable a remote destop session very easily but ggoint to System preferences Remote Desktop.  If you don't see it there, you much have done a very custome installation, which I highly doubt.  From there you can specify settings and any details.  From there you should also get your systems host name and or IP address.
From somewhere on your local network, like the windows machine, install the program xvnc, do a google and it will help you there.  That vviewer program will do it's magic al you have to do is enter the information that the remote desktop program to you to enter.  for instance... 192.168.0.100:1 If you need more help than that start another post.  an pm me if no one helps you from there.
:-)

---

