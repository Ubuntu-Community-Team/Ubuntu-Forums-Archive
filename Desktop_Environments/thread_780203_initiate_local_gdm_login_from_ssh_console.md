---
title: "initiate local gdm login from ssh console?"
date: 2008-05-03
forum: Desktop Environments
---

### Post by jeffk on 2008-05-03
On a new rollout of Ubuntu 8.04 desktops, I need to be able to a) see what the logged-in user sees, and b) log in as a specified user to perform desktop config tasks without the user being present.

I enable VNC connections (password, no confirm via vino, I think it's called) and have ssh access to the machines, which I prefer for most admin tasks. 

I do have gdm autologon enabled for the primary user. Sometimes the user logs out at the end of the day, or I need to log in as a different user.

I would like to know how to issue command(s) at the ssh console that have the same effect as the local user typing in a username and password to gdm, starting a local GNOME session. I think what I'm trying to describe is a way to signal gdm to log in with parameters passed from the command line.

I don't want an X over SSH sesion, I want to use ssh to initiate/kill a local gdm login, after which I should have access to that local session via VNC.

Thanks if anyone has ideas,
Jeff

---

### Post by achianese on 2008-05-23
I'll bump this, as I would also like to know the answer.

---

### Post by prshah on 2008-05-26
> **jeffk said:**
> I don't want an X over SSH sesion, I want to use ssh to initiate/kill a local gdm login, after which I should have access to that local session via VNC.
Thanks if anyone has ideas,
Jeff

You can kill a local gdm session from an ssh terminal with the command```
sudo /etc/init.d/gdm stop
```, and similarly use start or restart to bring it back up. In theory (I'm guessing), it should come up as the user who's logged in via ssh.

---

### Post by urthen on 2008-05-31
Anyone have any ideas on this? I have my computer set up as a media server, attached to a TV with my laptop acting as the remote, so dispensing with the keyboard and mouse entirely is optimal. However, I also don't really like the idea of auto-login, because I don't want anyone getting on my computer without my permission. It would be nice to get gdm to log a user in on the local monitor (the TV) without physical keyboard access (as in from the laptop)

---

### Post by Jrdgames on 2008-05-31
As long as your media server is within 10 or 20 feet of your sitting location then I would just buy a wireless keyboard and mouse (you could also use a trackball so you don't need a flat surface).

But to do it how you want to I would try what prshah said:
Login to the server with ssh:
```
ssh user@server
```
and then stop GDM:
```
sudo /etc/init.d/gdm stop
```
next start GDM:
```
sudo /etc/init.d/gdm start
```

I haven't tried this so please let us know if it works or not.

---

### Post by jeffk on 2008-06-01
Thanks for the replies, everyone, but I think my objective is obscured by my original poor choice of words.

I am looking to send a signal to gdm that it should initiate a GNOME session,  exactly as if a physical user sitting at the keyboard entered a login and password.

The end result would ideally be a logged-in user session. Stop-starting the gdm service as a logged-in ssh user won't result in the login-password dialog being skipped and a session started, will it? That would be nice, but unexpected.

I'm uninformed about the Ubuntu mechanism since I never use gdm on my own Gentoo Linux laptop. I've always booted to the console and startx'd. And all the Ubuntu 8.04 desktops I manage are offsite, making me hesitate to mess with the gdm remotely.

Alternatively. I could do what I need to do if there were some mechanism to enable Vino VNC connections from the gdm login screen, instead of only at the logged-in session. I don't like to enter system passwords over VNC of course, but in the short term it would be a sufficient workaround.

Thanks,
Jeff

---

### Post by Jrdgames on 2008-06-01
I have not used gentoo before but does it's login screen show an "options" button? if it does try clicking on it and if it has "Remote Login via XDMCP" then you can connect to your Ubuntu desktop and then login, You may need to enable XDMCP on the Ubuntu desktop first: System->Administration->Login Window, Enter your Password if asked, "Remote" tab->Style: "Same as Local" (although this might just be for styling a remote view on your local computer if so then you may have to do something like this on your laptop)

That should enable XDMCP and remote logins you should be able to login from your laptop if it has the options above Like I said.

Although this won't be like using VNC and it won't make your session show up on the remote monitor (atleest I don't think it will), It will be closer to actually being in front of the Ubuntu desktop.

---

### Post by prshah on 2008-06-01
> **jeffk said:**
> Thanks for the replies, everyone, but I think my objective is obscured by my original poor choice of words.

Stop-starting the gdm service as a logged-in ssh user won't result in the login-password dialog being skipped and a session started, will it?

Nope, your objective is clear. I'm futzing around.

Anyway I tried my own suggestion and you're right, it didn't work. So at least this is one thing you can eliminate.

Good hunting.

---

### Post by ttconrad on 2010-07-28
i thought i would post a solution to this as i found this thread even though it was dead for several years


this essentially came from the ubuntu section explaining vnc
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Connecting via VNC over SSH (to unlock initial Gnome login screen)
1. ssh into box (the one you cannot vnc into).  then run vnc server manually (install if need be):
$ ssh user@10.10.10.10
$ sudo x11vnc -create -safer -localhost -nopw -once -display :0

2.  leaving the above ssh session active, ssh again making sure to allow X window through:
$ ssh -X -C user@10.10.10.10

3.  run vnc client via ssh pointed to localhost which will push back GUI via X
$ vncviewer localhost:0

this gave me the local login window, which you can use to login and then do everything you need on gnome

this seems to be more complicated than it needs to be and i am basically a linux newbie so there is probably something else i am missing ... but it worked for me

---

### Post by bdjantl on 2010-09-29
Thanks a lot for this outline. Looking for it for a long time. Until now with no succes. Thanks!

---

### Post by neovandeen on 2011-05-17
Thanks man! This is also working for me. Tested on Ubuntu Natty

---

### Post by masuch on 2011-09-06
> **ttconrad said:**
> i thought i would post a solution to this as i found this thread even though it was dead for several years


this essentially came from the ubuntu section explaining vnc
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Connecting via VNC over SSH (to unlock initial Gnome login screen)
1. ssh into box (the one you cannot vnc into).  then run vnc server manually (install if need be):
$ ssh user@10.10.10.10
$ sudo x11vnc -create -safer -localhost -nopw -once -display :0

2.  leaving the above ssh session active, ssh again making sure to allow X window through:
$ ssh -X -C user@10.10.10.10

3.  run vnc client via ssh pointed to localhost which will push back GUI via X
$ vncviewer localhost:0

this gave me the local login window, which you can use to login and then do everything you need on gnome

this seems to be more complicated than it needs to be and i am basically a linux newbie so there is probably something else i am missing ... but it worked for me


Hi,

Thanks for this manual - it works perfectly fine.
I have a question. When I connect to remote computer, anything what I am doing is visible on the second computer as well. So, person who is working on that machine is not possible to do anything. I would like to connect to remote computer but (probably start another X session) not to control existing gdm ?

thanks for any help.

---

### Post by nothingspecial on 2011-09-06
You could just use ssh with X forwarding and type the name of the app ou want to use, eg

system-config-printer would bring up the printing preferences dialogue

nautilus --no-desktop would bring up the file browser etc

---

### Post by masuch on 2011-09-06
> **nothingspecial said:**
> You could just use ssh with X forwarding and type the name of the app ou want to use, eg

system-config-printer would bring up the printing preferences dialogue

nautilus --no-desktop would bring up the file browser etc

Hi,

thanks for quick answer. Nautilus and printer works fine.

but if I want to run gdm like this:
$ ssh -X -C [email]user@hostname.local[/email] gdm

I have got error:

** (gdm-binary:20117): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.152" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:20117): WARNING **: Could not acquire name; bailing out



What should I change, probably in /etc/ssh/ssh_config to make gdm start?


--- OR
u1@UBU2TBEXT41 1:2008:9 $ ssh -X -C [email]u1@USBHD230G.local[/email] blackbox
Ubuntu 11.04
[email]u1@usbhd230g.local[/email]'s password: 
blackbox: another window manager is already running on display 'localhost:10.0'
blackbox: another window manager is already running on display 'localhost:10.0'
blackbox: no manageable screens found, exiting...
:-( 0.29 0.13 0.14 5/781 15380 pts/2 jobs=0 19:36:15 ~
--- OR
u1@UBU2TBEXT41 1:2009:10 $ ssh -X -C [email]u1@USBHD230G.local[/email] icewm
Ubuntu 11.04
[email]u1@usbhd230g.local[/email]'s password: 
IceWM: using /home/u1/.icewm for private configuration files
IceWM: A window manager is already running, use --replace to replace it

On remote machine is running gdm, not icewm ???

thanks for explanation

---

### Post by masuch on 2011-09-06
As well I did not find -C parameter in man ssh. What is it for ?

---

### Post by DrPotoroo on 2011-09-16
The -C option in ssh compresses the data going over tue network. It is only recommended for slow or expensive networks. On a fast network you are likely to lose more speed on the compression than you gain by saving bandwidth.

---

### Post by masuch on 2011-09-17
> **DrPotoroo said:**
> The -C option in ssh compresses the data going over tue network. It is only recommended for slow or expensive networks. On a fast network you are likely to lose more speed on the compression than you gain by saving bandwidth.

Thanks, so I removed it :-)

---

### Post by gpalarea on 2011-10-17
Great solution ttconrad!

I tweaked it a little, in which you only need one ssh session, and you might need to restart vino-server afterwards (if you had it on):

ssh -X user@host
sudo x11vnc -create -safer -localhost -nopw -once -display :0 &
vncviewer localhost:0

notice the & at the end of the x11vnc command, it leaves it running and you regain control of the prompt.

Now, when you disconnect you will no longer be able to vnc since the -once option was used.  If you had vino-server configured, it won't be working well, it needs to be restarted:

killall vino-server
export DISPLAY=:0.0
/usr/lib/vino/vino-server &  

again, the magic of the & will let vino-server running and give you prompt control, so vino-server will keep running even after the ssh session is closed.

If for some reason vino-server does not accept the password, run vino-preferences and check.

This has helped me a lot, I hope somebody else finds it useful.  I have needed this sometimes during vnc sessions that for some reason leave the keyboard with stuck shift or ctrl keys.  So right after the ssh login, the first thing to do is restart gdm with:
sudo service gdm restart

btw, I am on Ubuntu 10.04.

---

