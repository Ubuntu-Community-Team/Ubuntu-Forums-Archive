---
title: "[SOLVED] SSH to remote computer and use bit torrent"
date: 2009-01-02
forum: General Help
---

### Post by skajoeska on 2009-01-02
I have used Ubuntu for a bit and can get along with the command line but still mostly a beginner. I have done various things from various articles regarding the topic, but just need some clarification to bring it all together because I can be dense. 

Problem: My school blocks any kind of bit torrent traffic in or out. I am able to download .torrent files through [www.txtor.dwerg.org](www.txtor.dwerg.org) but cannot get them to start while in my school network. So I would like to be able to download the torrent through a laptop I have at home(Xubuntu 8.10) and copy the contents over to my computer at school(Ubuntu 8.10). 

Through various articles I have gathered that the best way to do this is with a SSH connection with X11 forwarding enabled. Is this correct? From there I can run Transmission on my home internet connection. I enabled X11 because I would get "no display detected" error if I tried to run a program over ssh.

So far I have setup openSSH server on the home laptop and can successfully SSH to the home computer while in the local network. In order to do this from my school computer I need to enable port forwarding on my wireless router(linksys WRT300N) of port 22. Is this correct? I had some trouble doing this so I used DMZ to allow any incoming IP to go to my laptop's MAC address. Then I allowed SSH on port 22 in firestarter firewall for everyone. So as far as I can tell anyone can SSH to computer with my user password. I don't know if this is that safe or not and I would rather just forward port 22 and only allow my computer in.

I have also set up an account at dyndns.com to update the ip of the home laptop to the address skajoeska.homelinux.com. So whenever i'm in the terminal I enter > ssh [email]joe@skajoeska.homelinux.com[/email] and enter the password and from there can start transmission. When I log in it tells me I logged in from the ip 192.168.1.1 which is the ip of the router. Is this what should be happening?

I also use ubuntu's "Connect to Server" option in nautilus so I can just drag and drop the contents of the torrents to my school computer when they finish. 

Is there a way to test if it is all working correctly from inside the local network? meaning can I test if my SSH connection will work if i'm on a remote computer but actually in the local network?

Sorry for the long article and all of the basic questions. Also sorry if General Questions is the wrong section. I just have done so much that I don't know if it is set up right. And once I go back to school I can't access the home laptop so I want to get it right the first time. Tell me if there is anything I missed that I should be doing.


Thanks,
joe

---

### Post by skajoeska on 2009-01-02
Also could I use the screen command so I could turn off my school computer but keep transmission running at home? And I read an article where I could set Transmission to run through a proxy to get around all of this. If so, is it easier and faster?

---

### Post by plr4ever on 2009-01-02
Yes, you are correct in forwarding port 22, and it would be wisest to only forward that port. be advised, however, that many school districts block SSH and FTP ports, and you might not even be able to access it from school.

assuming you can however, the command you should use is 
```
 ssh -Y user@address 
```

Are the computers at school running a version of linux? Your client must have X11 for X-forwarding to work. As far as i know, only Unix-like OS's (linux, Mac OS X, OpenSolaris, BSD, etc)  can run X11, but there may be a windows mod to run it. 

If you cannot forward X due to OS restrictions, you could just use the text based method (via putty or another windows ssh program) and then use FTP to transfer the files you have downloaded.

---

### Post by skajoeska on 2009-01-03
That's what I thought about port 22. Thanks.

Sorry I wasn't clear. I'm at a university living in the dorms so I use my personal laptop(Ubuntu 8.10/Vista) to access the internet. They don't official support linux(even though their servers on it) but I can use it on the school network without trouble. Hopefully they allow X11 forwarding and SSH.

What would I do if they don't allow SSH on port 22? do I just change the port number in my wireless router settings(under applications and gaming for my linksys)?

thanks

---

### Post by ubrox on 2009-01-03
Hi,

You got off to a great start. I do the same thing all the time .. login in to a server somewhere else and do stuff including torrent download. 

Here is what I do:
1. Configure my router/firewall so I can remotely login to the system using SSH, which you are able to do right now.
2. install screen
3. install bittorrent - this is a CLI version of the bit torrent download client
4. install wget
5. Login to your system from your college
6. start screen
7. download the torrent file using wget
8. use /usr/bin/btdownloadcurses.bittorrent <.torrent file> It will start downloading
9. disconnect screen Ctrl+a followed by d
10. logout from your system, exit SSH.
11. connect back later, restore screen "screen -r"
12. check progress

---

### Post by skajoeska on 2009-01-03
thanks Kalyanakrishna! I read up on screen and this sounds perfect for my needs. It seems to be installed by default. Once again Ubuntu proves how much it rocks.

---

### Post by jimmy the saint on 2009-01-03
I would also point out that you can use deluge as your torrent app.  It is set up to serve your needs very well without all the extra steps.  You would simply install it on both machines and run the deluged daemon on the remote machine.  The beauty is that you don't need to worry about forwarding an x session, which can be slow, because you simply open deluge client on your computer, set it up to connect to your remote machine and it is just like it is installed on your machine except that all the downloading is done on the remote one.  It sounds a lot more complex that it is.  Just check out the faq on their site.  I use it to offload the torrenting to my home server and free up my main box for other things.

Oh yeah, in order to get that functionality you need to install a newer version than is available in the repos though.

---

### Post by skajoeska on 2009-01-03
I marked this as solved because my questions were answered. I'll report back in a week or so if this actually worked for me when I get back to school.

And I'll look into deluge. Thanks.

---

### Post by davidmigl on 2009-05-08
> **skajoeska said:**
> I marked this as solved because my questions were answered. I'll report back in a week or so if this actually worked for me when I get back to school.

And I'll look into deluge. Thanks.

Any word on how this worked out for you?

I realize I am resurrecting this thread. I am interested in the subject matter and the follow-up hinted at  by the user.

---

### Post by skajoeska on 2009-05-08
wow I forgot about this thread. To answer your question yes, it did work. I was able to connect using ssh and then copy the files to my computer at school.

I used openSSH, transmission, dynDNS.org, and screen to accomplish everything.

I ended up making a launcher on my panel with a command simular to
```
screen ssh skajoeska.homelinux.com transmission&
```

everything was smooth. the only problems was there was some lag and copy files took a very long time.

---

