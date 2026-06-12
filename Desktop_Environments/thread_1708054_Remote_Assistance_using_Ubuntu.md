---
title: "Remote Assistance using Ubuntu"
date: 2011-03-16
forum: Desktop Environments
---

### Post by fballem on 2011-03-16
I have been helping a friend with his computer issues for a number of years. In the process, I have converted both of us from Windows to Ubuntu. We are both running ubuntu 10.10 desktop AMD64.

When we were running Windows, he was able to allow me access to view (and at his option, share control of) his computer so that I could see exactly what is on his screen.

Is there a way to set this up in ubuntu?

We are both connected to a public network that uses dynamic addresses. He suffered a stroke some years ago, so whatever is setup needs to be very simple for him to use.

Any suggestions would be appreciated, and detailed instructions on how to setup the two computers would be even more appreciated!

Thanks very much,

---

### Post by ChipOManiac on 2011-03-16
I'm not aware of any others but KRDC seems to be a good try... and in ubuntu there seems to be a Remote Desktop connection service under the System tab 

<<http://www.codeunit.co.za/2010/07/13/ubuntu-lucid-lynx-remote-desktop-and-vnc-viewer/>> <-- Tad bit old but good enough :D

Hope this helps

---

### Post by Kirboosy on 2011-03-16
Hi! 

There is a free program called [TeamViewer]("http://www.teamviewer.com") It takes zero configuration and the program is multi-platform compatible that way you can help your Windows friends as well ;)

You don't even need to make an account with TeamViewer if you don't want to. Creating an account just allows you to friend people and allow fast access to the computers.


~Caboose

---

### Post by fballem on 2011-03-17
> **ChipOManiac said:**
> I'm not aware of any others but KRDC seems to be a good try... and in ubuntu there seems to be a Remote Desktop connection service under the System tab 

<<http://www.codeunit.co.za/2010/07/13/ubuntu-lucid-lynx-remote-desktop-and-vnc-viewer/>> <-- Tad bit old but good enough :D

Hope this helps

I looked at the Remote Desktop, but it appears that both machines have to be on the same local area network. Since my friend and I are not, I'm hoping that there is a way to configure access on his machine so that I can connect to it through the internet.

Any suggestions?

Thanks,

---

### Post by fballem on 2011-03-17
> **Caboose885 said:**
> Hi! 

There is a free program called [TeamViewer]("http://www.teamviewer.com") It takes zero configuration and the program is multi-platform compatible that way you can help your Windows friends as well ;)

You don't even need to make an account with TeamViewer if you don't want to. Creating an account just allows you to friend people and allow fast access to the computers.


~Caboose

I think Team Viewer is a Windows program that uses WINE in Linux (at least there is a WINE folder in the installation). I don't think that's where I want to go.

I am hoping that there is a way to configure the Remote Desktop and VNC to work through the internet, since this sounds simpler and better.

Thanks,

---

### Post by PRC09 on 2011-03-17
So did you try the link from Caboose885 above??? I use Teamviewer with my parents and friends some on Vista and some on XP and it works fine.I am running 10.10 64bit....

---

### Post by PRC09 on 2011-03-17
If you download the .deb you need and double click let it install itself and it is ready to go.It will install whatever it needs as far as wine goes and has been flawless so far for me.....


[http://www.teamviewer.com/en/download/index.aspx?os=linux](http://www.teamviewer.com/en/download/index.aspx?os=linux)

---

### Post by Krytarik on 2011-03-17
TeamViewer for Linux is indeed a windows port and makes use of Wine. I just yet checked it. I only installed it to have a more stable access to my mom's Windows7, at least more stable than RealVNC, on both ends in this case.

She also has Ubuntu 10.04, which is her main OS. To access those, we run "x11vnc" on her side, and RealVNC on mine. And this fairly fast and stable, but I still run it without encryption.

On the other hand, you can definitely set up Ubuntu's default remote access tools to run over internet. But I haven't tried exactly that way so far. I only tried recently to access her x11vnc server with "Remote Desktop Viewer" on my side. All you have to do there to access via VNC over internet is to choose "VNC" as "Protocol" and enter the IP-adress of the remote machine into the "Host" field. Therefore, of course, your friend has to get his own IP-adress, e.g. via [http://www.whatismyip.com/](http://www.whatismyip.com/) , but that should not be a problem, since even my mom is able to do so. To set up the remote server, the configuration via "System -> Preferences -> Remote Desktop" should be enough.

Also see those guide, it includes infos about a wide range of server/viewer, including the ones I mentioned:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by Kirboosy on 2011-03-17
I know it makes use of Wine but its painless and it has always been stable for me (10.10 64bit) I just like how you can tell a non-computer-savvy person go install teamviewer on their computer and in about 2 minutes (depending on how fast they are) you can connect and see their desktop.

VNC on the other hand can get messy. Port forwarding and setting up access parameters...

Its all a matter of preference and rest asured whichever method you choose we can help :)


~Caboose

---

### Post by Krytarik on 2011-03-17
> **Caboose885 said:**
> I know it makes use of Wine but its painless and it has always been stable for me (10.10 64bit) I just like how you can tell a non-computer-savvy person go install teamviewer on their computer and in about 2 minutes (depending on how fast they are) you can connect and see their desktop.

VNC on the other hand can get messy. Port forwarding and setting up access parameters...

Actually, I totally concur! But the fact is, TeamViewer just crashed in the very first trial, I believe it was an Ubuntu<->Ubuntu session, but I'm not sure. You may just try it, get yourself a picture.

---

### Post by cybergalvez on 2011-03-17
I do this with my Mom all the time, however I did set it up for her the last time I was at her house. I just use the normal vnc server that comes with ubuntu, however I do pipe it over ssh. What I did was
1) set up a dyndns account to take care of the dynamic IP issues
2) installed and set up ddclient to keep dydns updated
3) install sshd and changed the default port from 22 to something else
4) turned on the vnc server on her account
5) tunnell vnc through ssh

---

