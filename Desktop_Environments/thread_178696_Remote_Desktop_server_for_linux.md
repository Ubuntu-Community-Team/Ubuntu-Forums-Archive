---
title: "Remote Desktop server for linux"
date: 2006-05-18
forum: Desktop Environments
---

### Post by blackest_knight on 2006-05-18
I generally use a wireless laptop to remote into my windows systems to harness thier more powerful resources sometimes i may have 3 or 4 remote sessions to different PC's sometimes I will remote in twice as two different users  sometimes i just want to listen to some music or i get an audible alert a friend has logged on and i swop sessions to chat a while.

about the only time i physically touch one of my desktop machines is to load a cd or dvd or load more paper into a printer.

Thing is i achieve this by running xp pro with a multiuser patch. 

I want to do this with a Linux distro running on my pc's and kick windows into touch save for the occassional vmware session.

I know about vnc but i want audio as well. Shouldn't I be able to remote in to a desktop and use amorok or something to play my music files cut and paste between desktops. 

My new laptop will run osx86 and will still be capable of running as a terminal to my xp sessions. 

what I am looking for is similar functionality in linux. Is there any development  going on to provide a remote desktop solution similar to that offered in XP?

preferably something as straightfoward as xp's remote desktop

regards j

---

### Post by tribaal on 2006-05-18
Let's start by the obvious: did you check out Application -> Internet -> "Terminal server client"?

This is the rough equivalent to remote desktop client in Windows. I use it on a daily basis at work, and it works great.
If you wish to access a linux desktop from windows, I guess you should then install VNC or a similar server on your linux box. This is a handy graphical tool, but that is *NOT SECURE*. 

The best way to access a linux machine from a distance is ssh, though it is much less graphical it is much much safer... It's a matter of choosing between quality or graphicality :)

Hope this answers you questions...

- trib'

---

### Post by bluenova on 2006-05-18
vnc forwards sound doesn't it? The best setup is VNC via SSH. There are lots of posts on the forum here about VNC via SSH

---

### Post by blackest_knight on 2006-05-19
[QUOTE=tribaal]Let's start by the obvious: did you check out Application -> Internet -> "Terminal server client"?

This is the rough equivalent to remote desktop client in Windows. I use it on a daily basis at work, and it works great.
If you wish to access a linux desktop from windows, I guess you should then install VNC or a similar server on your linux box. This is a handy graphical tool, but that is *NOT SECURE*. 

The best way to access a linux machine from a distance is ssh, though it is much less graphical it is much much safer... It's a matter of choosing between quality or graphicality :)

Hope this answers you questions...

- trib'[/QUOTE]
The problem is not with a terminal server client least not with windows as server and linux as client (i am pretty sure that is already working fine) 

The problem is with linux as server and windows / osx as client and VNC is quite a good method of exporting the desktop "graphically" but this is not good enough. File shares work samba is great. 

but its not quite remote desktop is it. I work remotely on a lan pretty close to the same as working locally on an xp pro pc. 

To be equivilent to M$ remotedesktop solution requires a mechanism to redirect audio resources over the network. 

To Exceed M$ requires the redirection of as many resources as possible. 
Take for example a WebCam connected to a laptop surely its possible to redirect the feed from the webcam over the lan as a data source for a messaging client running on another PC. surely a scanner could be shared piping the data to an image processing/grabbing program. 

[http://www.remote-scan.com/](http://www.remote-scan.com/) 

Shows this can be done, in windows anyway. 

Do you understand where I am going with this? fairly independant light weight systems using the power of bigger more powerful systems within the lan.

chuck all your data in one big powerful basket but share it with numerous lightweight terminals (aka laptops)

---

### Post by jones_jj on 2006-05-20
Supposedly you should be able to forward X using ssh.  First do an install of Openssh through apt-get or synaptec, this will install both the client and server for your Ubuntu machine.  Then supposedly from any machine that has an ssh client installed you should be able to run this command:  ** ssh -X <user>@<server> **and it should forward X to the remote machine.  The only problem that I'm having at the moment is something with running X in passive mode on the server.

I am just curious, but you said you're running a Macbook Pro laptop, how is that a lightweight terminal?  What kind of workstations/desktops are you running that makes a Macbook Pro lightweight and not as beefy?

---

### Post by blackest_knight on 2006-05-20
I didn't say I was running a MacBook Pro, I said It was my intention to run OSX86 on a laptop. This is quite possible on cetain laptops if you look for Nx6110 and OSX86 on google you should find a laptop which runs OSX86 without problems and currently its possible to buy this laptop for around £430 The version I am loooking at has a 1.4 ghz celeron processor.  likelyhood is I will probably finish up with a triple boot. system with the choice of osx86 XP or Ubunto.  Probably its going to need a memory boost and a HD upgrade imediately 
I Will let you know how I get on after I get it set up (it arrives Monday). 

As for lightweight I have an aging toshiba tecra with 48 meg of ram and a p160 processor running 98 and this runs XP Pro remotely superbly as all the laptop does is display the screen and relay the sound it manages this well with no need to hit the swop file. (what price for that laptop £50?)

Actually I probably should try ubunto on that laptop (time is always a problem)

on the xbox with xebian i use ssh to login set up a vnc session and then use vnc to connect. I like the unusual :) I set up a small webserver on a Toshiba E740 Pda (cheap silent and enough for the traffic likely to go there). currently  its on other dutys running satnav 

I wish I had more time to actually develop solutions. I don't think currently there is a free solution to get a full remote desktop solution on Linux but developers read this forum and maybe someone will think thats a cool idea and work on code to redirect audio streams from a linux server to a remote session. Maybe it is quite possible already after all you can stream mp3's linked on a webpage. in fact i think I read darwin has a streaming server for video. 

maybe it wouldnt be so hard to write a small java ap to listen on a port for incoming audio streams and a server which can be directed to load files and playem perhaps a shoutcast kind of thing. 

lots of idea's here just too little time.

---

### Post by jones_jj on 2006-05-21
An application you may want to check out is a program called Exceed, by Hummingbird.  It may actually do what you're wanting to do.  It is an X server for Windows, and I believe it should transmit audio from a remote Linux machine.  [Exceed]("http://http://www.hummingbird.com/products/nc/exceed/index.html?cks=y")
Now if you can get your hands on it to play with it, it may be what you're looking for.

Also, not to pry to much, but wouldn't it better to instead of triple booting to use some sort of VM and install all the OSes you want?  I know in the version of Ubuntu coming out this fall they are adding Xen, I guess it's suppose to be similar to VMWare.  May be another option to check out.

Just some suggestions

---

### Post by blackest_knight on 2006-05-21
exceed is a $545 dollar sledgehammer to crack a relatively straight forward nut. 

freeNX might be better.

an integrated part of linux would be best. 
A virtual soundcard which allows linux audio to be streamed over a lan and fed to a daemon program on the client to play any audio. 

maybe something like shoutcast... 

the virtual sound card concept seems a workable solution for audio at least
configure the target as 127.0.0.1 it feeds locally 192.x.x.x it sends it to a remote client on the lan  x.x.x.x anywhere on the internet...

just a thought

---

### Post by jones_jj on 2006-05-22
Yea I know Exceed is rather expensive, very nice product actually.  I know some Universities use the product and if you're still in school, or have friends in school, you might be able to get a copy of it for free.  That's how I got an older version of it. 

As always an integrated application would be best.  That just seems odd that there's nothing out there that will do what you want.  You know Remote Desktop from XP or Terminal Services Client if you're on Win2k has an option for bringing sound down from the remote computer.  And this seems to be what you want correct?

Now if this is correct, and you have a CD in your "remote" Linux box, and you're on your XP laptop in another room, and you connect into the Linux box using Remote Desktop through a Terminal Server, you should be able to hear the CD on the laptop.  (Sorry just thinking out loud)

---

