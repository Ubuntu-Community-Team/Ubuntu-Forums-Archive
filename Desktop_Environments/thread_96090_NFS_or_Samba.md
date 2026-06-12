---
title: "NFS or Samba?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by bogoliubov on 2005-11-28
Hello. I run Ubuntu on my PC at home. I also have an iBook G4 running OS X 10.4. At the moment these can share files using Samba. But I get the feeling that Samba isn't very fast.

What about NFS? What are the differences and which one is better for me? I have no need for stuff that are compatible with windows-stuff, since both computer are running some sort of *nix...

Both computers are connected to a Netgear router. The iBook use wireless connection, but the PC is connected with (TP) cable.

---

### Post by frodon on 2005-11-28
You could also try FTP protocol for sharing your files.

---

### Post by bogoliubov on 2005-11-28
[QUOTE=frodon]You could also try FTP protocol for sharing your files.[/QUOTE]

Ok, will that be faster? Or simpler? I'd like botg if possible. I didn't think there was any point in using ftp within the same LAN, but I've never used ftp all that much...

---

### Post by frodon on 2005-11-28
It's not as easy to configure than samba i think but FTP is one of the best solution in term of speed.
There's no problem to use ftp inside your lan if you have well set the IPs of all your computers.
Each computer will need to run a FTP server to share its file with others. One of the advantage of using ftp is that it will eat less cpu power when transferring a file.

---

### Post by bogoliubov on 2005-11-28
[QUOTE=frodon] One of the advantage of using ftp is that it will eat less cpu power when transferring a file.[/QUOTE]

That's sounds good. 
 However, if I use ftp I won't get a mounted volume in the file system, will I? That is quite practical when you use the terminal for moving files and stuff...

Also, can I set up my Ubuntu machine to start the ftp connection on start-up/login?

---

### Post by frodon on 2005-11-28
I never tried to mount a ftp directory on startup but it might be possible : [http://retronetworks.com/howto/mount/howToMountRemoteFS.html](http://retronetworks.com/howto/mount/howToMountRemoteFS.html)
In my case i use a FTP client to use my ftp directories, like gFTP for exemple.

Also what is your need ? Do you want a secure access with username and password or are you behind a router/firewall and then think that a secure access inside the LAN is not needed ?

---

### Post by Kray on 2005-11-28
U can use Nautilus to access FTP server. Although it isn't 100% reliable solution - at least in Hoary I've got problems with certain servers.

---

### Post by bogoliubov on 2005-11-28
[QUOTE=frodon]
Also what is your need ? Do you want a secure access with username and password or are you behind a router/firewall and then think that a secure access inside the LAN is not needed ?[/QUOTE]

I'm behind a firewall, so I don't need anything particulary secure...

Thank's for all the tips by the way!

---

### Post by frodon on 2005-11-28
So a basic configuration should work quickly : [http://ubuntuguide.org/#installftpserver](http://ubuntuguide.org/#installftpserver)
Feel free to ask more questions about setting a FTP server, i have some knowledge with proftpd FTP server.

---

### Post by bogoliubov on 2005-12-01
Thank's alot for the tips!

---

### Post by skeezer65134 on 2005-12-01
Can FTP be adapted to allow streaming of media?

I prefer Samba myself because I have all my MP3s and various other files on my main computer which is running Kubuntu at the moment (but always runs some form of Linux, and only Linux). My laptop is also usually booted in Linux (Ubuntu at the moment), but on some rare occasions I need to boot to Win2k. I rarely stream stuff back and forth here, so SSH and SFTP meet my needs back and forth to my laptop.

My media PC (the one hooked up to my TV and stereo), however, runs WinXP. I would switch that over to linux too, but BeyondTV is way too cool to leave behind, and I feel video game emulation in Linux is lacking (a major concern for me since I have a ton of roms and emulation engines). It's also one of the only Windows-based systems I have that runs stable, so I have no need to change it.

The point is, since all my music is on my desktop, I need to be able to stream it to my media PC if I want to listen to it through my stereo and not in my room. With samba, I just mount it in WinXP as a remote drive, cue up the files in Winamp (or any other player for that matter) and I'm all set. I can also password protect individual folders and leave others open to anyone in my house. This means anyone can stream my music or upload files to my desktop and I can still get to my more sensative files if the need arises. Since I can mount Windows shares in Linux, I have no problem streaming shows or movies I record back to my desktop either. By mounting the shares from the media PC at boot with fstab in Linux, it's a seemless stream both ways.

This is the one advantage I see with using Samba over FTP or anything else really. I'm open to other solutions though.... just wanted to throw in my 2 cents while I browse for a quick Samba guide for Kubuntu/Ubuntu.

---

### Post by crispingatiesa on 2005-12-01
[QUOTE=skeezer65134]Can FTP be adapted to allow streaming of media?

Kubuntu/Ubuntu.[/QUOTE]

Try gnump3 it is an streamin g server and U can get it using Synaptic. It works excellent, I have it running in my box and it runs without problems so far.

If any doubts how to set it up just let me know and I'll give you a hand.

---

### Post by thewanderer on 2005-12-01
I think for your needs samba shares that you can mount on boot is the most convenient solution.

You can then play mp3's or even video files straight off the file share. No fuss or messy solution required.

Interesting thing i found recently - i had a setup that involved an Ubuntu Hoary samba server as my file share (epia via mainboard 1Ghz) and was streaming video off this with no problem, even over a 11mb wireless link to my Ubuntu laptop.

I made a change to my environment which involved having the file share on another machine temporarily - Windows XP with filesharing (2.2ghz AMD CPU).

Streaming over the 11mb wireless link no longer works, it is jerky and problematic. This leads me to conclude that using Samba -> Samba is more efficient than Samba -> Windows Share. 

Perhaps there were other factors but that was certainly the major change. It would be interesting to see some real stats comparing the two since samba was derived from Windows file sharing protocols. :)

---

### Post by skeezer65134 on 2005-12-02
[QUOTE=crispingatiesa]Try gnump3 it is an streamin g server and U can get it using Synaptic. It works excellent, I have it running in my box and it runs without problems so far.

If any doubts how to set it up just let me know and I'll give you a hand.[/QUOTE]
Thanks for the suggestion, I'm always looking for something to tinker with. It's part of the reason I made the post.

As for Samba->Samba being faster, I recall reading somewhere that Samba was benchmarked as being faster than WFS, so I'm not too surprised. If I were less lazy, I'd Google it for ya, but I am lazy, so..... If I recall right, it may have actually been on /. a while back but I can't say for sure.

---

