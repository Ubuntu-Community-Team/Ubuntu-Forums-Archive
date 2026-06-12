---
title: "Login to Gnome via SSH"
date: 2012-09-22
forum: Desktop Environments
---

### Post by SeMeidl on 2012-09-22
Hey

I'm new to Linux and to this forum so I hope I got the category right. I know that I have to learn a lot in order to aministrate a linux server, but for doing that, I first need a secure and stabel way of accessing my system. My problem is the following:
I managed to set up an SSH tunnel for a VNC connection from my windows machine to my ubuntu 12.04 server using the following guides:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

The problem is that I can only connect if I'm already logged in to gnome, similar to here:
[http://ubuntuforums.org/showthread.php?t=1544847](http://ubuntuforums.org/showthread.php?t=1544847)

But the given solutions don't work for me. I was wondering if this is due to the fact that I got my home directory encrypted? 
I'm using x11vnc as well and when I enter ```
x11vnc -safer -localhost -nopw -once -display :0
``` as stated in the above guide, I get

```

22/09/2012 14:51:14 -safer mode:
22/09/2012 14:51:14    vnc_connect=0
22/09/2012 14:51:14    accept_remote_cmds=0
22/09/2012 14:51:14    safe_remote_only=1
22/09/2012 14:51:14    launch_gui=0
22/09/2012 14:51:14 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2802
No protocol specified
No protocol specified
22/09/2012 14:51:14 XOpenDisplay(":0") failed.
22/09/2012 14:51:14 Trying again with XAUTHLOCALHOSTNAME=localhost ...
No protocol specified
No protocol specified

22/09/2012 14:51:14 ***************************************
22/09/2012 14:51:14 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.


```I appreaciate any form of help!

Thanks

---

### Post by steeldriver on 2012-09-22
Try pointing it at the root Xauthority file - for lightdm that would be something like

```
sudo x11vnc [COLOR=Red]-auth /var/lib/lightdm/.Xauthority[/COLOR] -localhost -safer -nopw -once -display :0
```

This seems to work for me (although the server end is Xubuntu so things may be set up a little differently)

---

### Post by SeMeidl on 2012-09-22
Thx for your Tip! what this does is that it makes x11vnc vorking, so I can vnc connect to the login screen, bu when I enter my pw and press enter I lose connection and x11vnc terminates in my ssh session. Once again I don't really have a clue why this happens, probably because after logging in, the system tries to open a new window which is not being forwarded to my remote client?

regards

---

### Post by d.atanasov on 2012-09-22
Hi, 

I don`t understand what you are trying to do infact. Do you open a ssh tunnel to the server from your Windows machine and then try to do something with x11vnc or something else. What I found is the manual of the x11vnc 
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html](http://www.karlrunge.com/x11vnc/x11vnc_opts.html) 
Inside you can find some examples and if you still don`t find the answer to your problem you can contact the person made this command. (I think when you type man x11vnc there should be some author written and some contacts)  

cheers
EDIT: [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)  probably already you know that, but anyway inside you can ask for help too :)

---

### Post by SeMeidl on 2012-09-22
what I do:

I connect to my machine via SSH, establishing a tunnel for VNC. After connecting, I have terminal access to my machine. Now its time to start x11vnc but here is where i run into problems: I can use x11vnc to forward my Gnome session to my windows computer JUST when I'm already logged into gnome on the server, which is not the case when I remotely boot the system and thus is not going to work out for me. I don't know how to express myself very well as I just started Linux but have a look at the related topic I mentioned above: 
[http://ubuntuforums.org/showthread.php?t=1544847](http://ubuntuforums.org/showthread.php?t=1544847)
I belive that there's a pretty straight forward solution to my problem, just that I don't know about it as a beginner.

---

### Post by d.atanasov on 2012-09-22
Just to be clear you have Putty installed on your Windows ? 

EDIT: Can you give me all the commands you use to access the server ?

---

### Post by SeMeidl on 2012-09-22
yes. I followed this guid here: 
[https://help.ubuntu.com/community/VNC#accessing-your-pc](https://help.ubuntu.com/community/VNC#accessing-your-pc)

but when it comes to 

4. ) In the PuTTY window, he types x11vnc -safer -localhost -nopw -once -display :0 and presses *Return*

in the section "Logging in from a Windows PC" I get the error that I posted above. On the other hand, If I use the keyboard to login to Gnome on my machine before I issue the command x11vnc -safer -localhost -nopw -once -display :0,
I'm able to get x11vnc running and connect using the TightVNC viewer for Windows. 

Regards

---

### Post by d.atanasov on 2012-09-22
> **SeMeidl said:**
> yes. I followed this guid here: 
[https://help.ubuntu.com/community/VNC#accessing-your-pc](https://help.ubuntu.com/community/VNC#accessing-your-pc)

but when it comes to 

4. ) In the PuTTY window, he types x11vnc -safer -localhost -nopw -once -display :0 and presses *Return*

in the section "Logging in from a Windows PC" I get the error that I posted above. On the other hand, If I use the keyboard to login to Gnome on my machine before I issue the command x11vnc -safer -localhost -nopw -once -display :0,
I'm able to get x11vnc running and connect using the TightVNC viewer for Windows. 

Regards

Did you tried with sudo in front like this 
```
sudo x11vnc -safer -localhost -nopw -once -display :0
```

---

### Post by SeMeidl on 2012-09-22
Yes I did. I also used steeldrivers advice to issue

sudo x11vnc [COLOR=Red]-auth /var/lib/lightdm/.Xauthority[/COLOR] -localhost -safer -nopw -once -display :0 which actually works and makes x11vnc running so that I'm able to see the Gnome login screen on my windows machine. But when I type my pw and hit enter, the vnc session terminates. So what I need is a command line way to get logged in to gnome, then these commands work just fine. Or some other sort of work around

Regards

---

### Post by d.atanasov on 2012-09-22
Sorry That I was asking stupid questions. I think that now I understand the problem. Here is what I found in the Fedora forum: 

> OK I ended up finding a solution after some more reading and testing,  based on the solution posted here:  [http://www.karlrunge.com/x11vnc/faq.html#faq-inetd](http://www.karlrunge.com/x11vnc/faq.html#faq-inetd) .  Basically, it  involves these steps:

1. Create the file /usr/local/bin/x11vnc_sh, and chmod 775.  Make the contents of this file:

#!/bin/sh

authfile=`ps wwaux | grep '/X.*-auth' | grep -v grep | sed -e 's/^.*-auth *//' -e 's/ .*$//' | head -n 1`

if [ -r "$authfile" ]; then
        exec /usr/bin/x11vnc -inetd -o /var/log/x11vnc.log -display :0  -auth "$authfile" -many -bg -xkb -ultrafilexfer -users username -rfbauth  /home/username/.vncpasswd -noxrecord

fi
exit 1

2. Create the file /etc/xinetd.d/x11vnc with the following contents:

service x11vnc
    {
            flags           = REUSE NAMEINARGS
            port            = 5900
            type            = UNLISTED
            socket_type     = stream
            protocol        = tcp
            wait            = no
            user            = root
            server          = /usr/sbin/tcpd
            server_args     = /usr/local/bin/x11vnc_sh
            disable         = no
    }


With this setup, I no longer get dropped x11vnc sessions, and I can log  out, lock the screen, reboot, and it continues to work!  Hope this helps  others that want a similar setup.

Here is the link to it 
[http://forums.fedoraforum.org/archive/index.php/t-259665.html](http://forums.fedoraforum.org/archive/index.php/t-259665.html)
I hope that It will help but before doing anything of the mentioned please make a backup of all files you need to edit.  

cheers

---

### Post by SeMeidl on 2012-09-22
Oce again, thanx for your reply. I tried this solution without really understanding what it does. From what I get this solution uses xinedt to start x11vnc so that switching from the login screent to a gnome session should be possible wqithout losing connection, right?
I installed xinedt and configured the mentioned files. Judging from the fact that now i can VNC to my machine without having to type any x11vnc commands before and that now it asked me for the vnc password, I guess this worked.  But after I try to login, the connectio is still lost.
Once again, I don't understand the world of unix yet, how to pass parameters, use scripts etc.. I'll try to learn that all, but for now I need a solution that just works and enables me to connect. 
What I want to do is actually pretty basic. Just requires a couple of mouseclicks on MacOSX or Windows, so it can't be that complicated on Ubuntu? Isn't it quite normal that one wants to have a VNC connection to a machine where he's not currently logged in to?

Regards

---

### Post by steeldriver on 2012-09-22
Here is another way of doing it (provided you are using lightdm as the session manager)

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

BOTH methods works for me - if they aren't working for you then there must be other reasons to do with your exact setup - what error message(s) are you getting now?

I am using the Windows TightVNC client but I have used UltraVNC in the past and that worked as well

---

### Post by d.atanasov on 2012-09-22
> **SeMeidl said:**
> Oce again, thanx for your reply. I tried this solution without really understanding what it does. From what I get this solution uses xinedt to start x11vnc so that switching from the login screent to a gnome session should be possible wqithout losing connection, right?
I installed xinedt and configured the mentioned files. Judging from the fact that now i can VNC to my machine without having to type any x11vnc commands before and that now it asked me for the vnc password, I guess this worked.  But after I try to login, the connectio is still lost.
Once again, I don't understand the world of unix yet, how to pass parameters, use scripts etc.. I'll try to learn that all, but for now I need a solution that just works and enables me to connect. 
What I want to do is actually pretty basic. Just requires a couple of mouseclicks on MacOSX or Windows, so it can't be that complicated on Ubuntu? Isn't it quite normal that one wants to have a VNC connection to a machine where he's not currently logged in to?

Regards
Well from my point of view I have never used VCN connection, because I switched completely to linux several years ago. What I (I use linux at the moment Ubuntu and Mint) do and what Mac Os can do (according to my knowledge) is just use a "ssh" protocol to connect to any UNIX-like systems like this: 
```
ssh -X user@IP 
``` 
where -X stands for forwarding all X windows to your display from the machine you are accessing. I assume you don`t want this which is dependant on the network and is slow. The Putty in Windows do almost the same job. It open just a Terminal where you can type any Unix-like commands and where you can forward the X through ssh.  I can try to explain how the commands and passing a parameters to a commands work but I think you don`t need this at the moment. So after all I said I just wanted to help but I just want to stress here that I am not an expert in VNC connections so please don`t hate me much :) for asking stupid questions. So if I can help with something else ... 

regards

---

### Post by SeMeidl on 2012-09-22
@ d.atanasov: Probably you got me wrong, I don't hate anyone, I'm just about to get desperate on this (seemingly) basic issue. :(

@ steeldriver: I now used this method which is actually for ubuntu 11.10:

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

which someone posts in the comment section of the blog you provided the link to. 

As I already said, I don't know what I'm doing wrong. I just downloaded ubuntu 12.04 server, installed GNOME

```
sudo aptitude  install --without-recommends ubuntu-desktop
```

installed and successfully configured SSH and installed X11VNC. So everything is default settings. I followed the instructions here (english translation on the bottom):
[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)
but after entering my password to the ubuntu login screen and hitting enter the session drops (Tight VNC diplays: failed to receive data from socket)
and in the terminal ssh session I get 
```
/usr/bin/xauth:  timeout in locking authority file /home/michael/.Xauthority

```

---

### Post by steeldriver on 2012-09-22
OK so let's see the output from

```
ls -l /home/michael/.Xauthority
```

Are you sure your issue is specific to the remote login? Can you log in OK at the physical machine?

---

### Post by SeMeidl on 2012-09-22
just tried on the physical machine: you were right: It now also happens on the physical machine :confused: After logging in, I just get the login screen again. This wasn't the case when I started working on the issue, but I tried so many solutions now that something might have changed that 

Entering this command, I get:
```
michael@server:~$ ls -l /home/michael/.Xauthority
-rw------- 1 root root 100 Sep 20 00:08 /home/michael/.Xauthority
```thanks for your patience and advice

---

### Post by steeldriver on 2012-09-22
Ok well you won't be able to start ANY X session (local or remote) with a root-owned .Xauthority file - let's try

```
rm /home/michael/.Xauthority
```

(a new file will get generated on your next successful session start)

---

### Post by d.atanasov on 2012-09-22
On the physical machine, when you are at the login screen. Hold Alt+F1 and you will see (probably) some prompt. You can enter your user name and press enter and then it will ask you for a password. Type it and then see if it logs in. If yes then there is something in the graphical display manager.

---

### Post by SeMeidl on 2012-09-24
Hey, its me again. I reinstalled the complete system, but still I had the issue that I couldn't login from the login screen. The problem was similar to here:
[http://askubuntu.com/questions/140652/12-04-desktop-login-loop](http://askubuntu.com/questions/140652/12-04-desktop-login-loop)

And the given solution was to issue

```
sudo chown -R user:user /home/user
```
which worked perfectly fine for me. What remains unclear is why this issue appeared and if the solution I found is a good one or if it probably has some undesired side effects I'm going to discover soon?

cheers

---

### Post by d.atanasov on 2012-09-24
Hi again, 
Sorry for asking but how did you create your home folder, because from what I understand you somehow manage to change the ownership of your entire home folder giving it to root. This will end up in a way that you cannot access the files in the home because the linux thinks that you are not the owner. So I think that you will not have any problems from now on after you changed the ownership. :) 

cheers

---

