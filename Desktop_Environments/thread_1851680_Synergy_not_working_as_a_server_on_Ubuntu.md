---
title: "Synergy not working as a server on Ubuntu"
date: 2011-09-28
forum: Desktop Environments
---

### Post by hewlett on 2011-09-28
Hi,

I'm new to Ubuntu and Linux, I installed (with great difficulty) Ubuntu 11.04 on an old dell machine, and I have also installed QuickSynergy on this machine.

I have a windows 7 PC also, and I want to control the mouse & keyboard (using synergy 1.3 on Windows Pc) on the dell. I can get the Ubuntu machine to control the mouse and keyboard of the WPC but cannot get it to work the other way around, any suggestions please?

I have searched the forums and the googles and can't find an answer, not sure if you need any more information to help me.

Both machines are connected using wifi to my router. Any all ports in Windows firewall are open and on my router. I have a funny feeling this is a windows networking problem, but I could be missing something, any help is greatly appreciated

Thanks!

---

### Post by bigmac01 on 2011-09-30
I'm a little confused. Are you using the Win7 as the main controller (server) for the mouse & Keyboard with the Ubuntu acting as a client or the Ubuntu as your main PC (server) and the Win7 PC as the client?
 
My primary PC is my Win7 PC so I use that as my (synergy) server and my Ubuntu 11.04 as my client. Not sure this had anything to do with it but I also configured Samba so that I could share folders across machines.
 
I also wasn't happy with the Natty GUI so I switch back to GNOME.
 
The one big thing I had to resolve was that I wanted to have synergy running on Ubuntu before login (auto logon doesn't work coming back from sleep or hibernate) so I had to add synergy as part of >start-application (for after login) and edit some files in /etc/gdm directory so I could switch back over to Ubunto to re-login.
 
bigmac

---

### Post by ivancp on 2011-09-30
I'm using synergys with a configuration file, like this: 

file: config.sgc

[FONT=Courier New]section: screens
    ivancp-ubuntu:
        switchCorners = none
        switchCornerSize = 0
    winxp-desktop:
        switchCorners = none
        switchCornerSize = 0
end
section: links
    ivancp-ubuntu:
        right = [/FONT][FONT=Courier New]winxp-desktop[/FONT]
[FONT=Courier New]winxp-desktop[/FONT][FONT=Courier New]:
        left = [/FONT][FONT=Courier New]ivancp-ubuntu[/FONT]
[FONT=Courier New]end
section: options
end
[/FONT]

To start synergy server:

synergys -c config.sgc

Thanks all.

---

### Post by bigmac01 on 2011-09-30
I'll assume from your reply that Ubuntu is your server (where your mouse & keyboard are primarily connected) and that your Win7 is your client.
 
I have the opposite configuration but I just switched mine to comform to what your config is like and mine (still) works.
 
First verify that you can ping the other PC from your (Ubuntu) server and (Win7) client. 
**(For whatever reason, on my Win7 I can ping Ubuntu using either HostName or IP address but the other way, Ubuntu to Win7, IP address works but HostName can't be resolved, might be the way I have Samba configure but that's for anaother day)
 
Next verify that (on your Win7) your network neighborhood shows the Ubuntu server.
 
Then on your server run QuickSynergy from Applications>Accessories>QuickSynergy. This will pop-up a GUI with 3 tabs Share, Use, Settings. On the Share tab fill in the HostName (not IP Address) of the client PC. In my case the (Ubuntu) server is on my left and the (Win7) client is on my right, so I fill in the HostName of the Win7 in the right window then hit execute.
 
On the (Win7) client I run the Synergy+ application which brings up its window. On the first line is "Use another computer's shared keyboard and mouse (client)". Click that and fill in the HostName of your (Ubuntu) server. Do NOT use an IP address. Then in Options click the Advanced button. In that screen put the HostName of your client and make sure the port is 24800. Plus make sure your firewall has the Synergy+ and port in its exception list.
 
Then hit Start and it should work.
 
bigmac01

---

### Post by michaelltaylor on 2011-12-11
I'm having the same trouble. My Ubuntu machine is the server and my 
Windows machine is the client. They are set up with the same port, they can ping each other using both IP and hostname, and can even share files. But Synergy never connects. If I switch it so the Windows machine is the server and the Ubuntu machine is the client, it works fine. But I don't want to use the keyboard and mouse of the Windows machine. Is there some kind of security setting in Ubuntu that's keeping the port closed?

---

### Post by bigmac01 on 2011-12-11
LIke I said in my previous post, I have Windows as the server and Ubuntu 11.04 as the client but I did test withe Windows as the client and it worked.
 
I'll reconfigure my setup for Windows as the client again, jot down the steps I did and post that to see if that is what you did. Can't do it right now though. I'll do it late tonight or Monday morning.

---

### Post by bigmac01 on 2011-12-12
Okay michaelltaylor, here goes...
 
My client is a Win7 64bit Pro running Synergy+ 1.3.4. My client's name (for the sake of reference) is WIN-DESK-01 and its workgroup is MYHOUSE. For testing purposes, launch the Synergy+ launcher.exe and check "Use another computer's shared keyboard and mouse(client)" and in the field (I put) LINUX-01, the name of the other PC with that will have the mouse and Keyboard. Firewall settings: None needed. My network is set as Private.
 
On LINUX-01 I installed Samba, QuickSynergy and windbind.
 
I made sure Samba was configured correctly(same workgroup and users configured) and both PC's could access each other's folders. With winbind I was able to see each PC from the other and especially see the LINUX-01 in Window's Network Neighborhood and ping each other using both IP address and host name.
 
Launch QuickSynergy from Applications>Accesories. My Settings tab has /usr/bin in the field. The Share tab has WIN-DESK-01 in the right-hand box. Hit Execute and it should work.
 
There is some extra work you'll need to do if you want synergy to execute at logon and even more work if you want it to launch before logon (which I've done to my machine).

---

### Post by bigmac01 on 2011-12-12
Quick Correction!
 
After running through the instructions, my Windows Firewall did flag synergy as blocked and asked permission to Allow (which I did). Now it works....

---

