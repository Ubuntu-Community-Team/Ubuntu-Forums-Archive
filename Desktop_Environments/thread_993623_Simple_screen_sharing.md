---
title: "Simple screen sharing?"
date: 2008-11-25
forum: Desktop Environments
---

### Post by tjko on 2008-11-25
Hello Ubuntu community!

This is my first post, but I have been trolling for a few days. I don't consider myself a complete newbie in the world of computers as I've owned a few PCs, then used MAC OS for a little while. I consider myself maybe above average relative to the general public, however I want to learn much more. Therefore, I will be looking through here much more in order to learn everything I possibly can about Linux and computers in general (I'm a first year Computer Science major in College right now if that tells you anything more about me.).

In any case, I just installed Ubuntu about 4 days ago and have been getting to know CLI and just started working with vim (which I want to become an expert of some day). But anyway, I was just wondering for now if there was any way of simlpy screen sharing with someone (e.g. my parents) back at home to show them what I do, etc...

Please let me know if you know of anything that could help.

Much thanks,
TJ

Edit: I am not sure this is the right forum to post in, let me know of that too if it's wrong, please.

---

### Post by tjko on 2008-11-26
Does something like this not exist? It seems like if it did, you all would have pretty quick responses to it...

Please pm me or respond here if you know of anything that could work, thanks.

---

### Post by msageg8 on 2008-11-26
undesirable comment on your blog entrylet's go to the forum Good Services[img]http://pic.piclib.net/sunvv/images/pic/new20_711.gif[/img]About all go to= Good Services ok!sites where they can express&#65281;[cheapest wow gold](http://www.wowpowerleveling-wow.com/)-wow gold on Sale with Fast site[massage](http://www.massageinshanghai.org/)-massage help you to relax[beijing massage](http://www.massageinchina.com/)-the best massage in beijing[massage shanghai](http://www.full-body-massage.cn/)-massage is a 24-hours out call massage

---

### Post by mitchroberts on 2008-11-26
in fact something like this does exist it might work a little different basic screen sharing or vnc viewer and server or running terminal services on a different pc there are a lot of software like this out there...If this is what you are looking for.software has to be streamed over the internet or 
LAN to work.

my pic and also what i use
tightvnc is a vnc software /server

also

Nomachines do a free Client and Server for Linux.They even ship debian packages. The Windows client is free too and it works very well.

Download the packages from 

[http://www.nomachine.com/select-pack...?os=linux&id=1](http://www.nomachine.com/select-pack...?os=linux&id=1)

install them on your linux box

Download the Windows Client

[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

install it and off you go.

Good luck

---

### Post by tjko on 2008-11-26
Thank you very much for the response, I'll look into both of those and let you know how it works out.

If I'm running Ubuntu, can I just download the Linux one? 

(I'll do some searching myself, just let me know if the answer's simple, please)

---

### Post by concorde106 on 2008-11-26
I would like to do this too, however to access a Mac OS X machine. The NoMachine link is *broken!!!* What can I do? Do you know of any that will work so I can VNC or SSH into my Xubuntu machine from Mac OS X? The opposite as well? Mostly need the first one though.

---

### Post by tjko on 2008-11-26
Interesting concorde...

I actually am more concerned with showing my screen than actually having any exchange of control.

Essentially, I would like to emulate the screen sharing properties of applications like iChat on MAC OS, if anybody knows what I mean by that.

---

### Post by mitchroberts on 2008-11-30
> **concorde106 said:**
> I would like to do this too, however to access a Mac OS X machine. The NoMachine link is *broken!!!* What can I do? Do you know of any that will work so I can VNC or SSH into my Xubuntu machine from Mac OS X? The opposite as well? Mostly need the first one though.

I do not know alot about mac i did fine a viewer to work on
mac os x and on the linux end you should be able to use any
vnc server just make sure you do x forwarding.I thank your
saying you would like to do this both ways?Then i would say
you need a vnc viewer/server on both?

mac os x viewer
[http://desktopecho.com/tsclientx/](http://desktopecho.com/tsclientx/)

---

### Post by Cyhawk on 2008-11-30
NX is ok.. but any number of VNC clients works just as well, if not better.

A built-in VNC server is included with 8.04 and 8.10, you can enable it from System -> Remote Desktop.

Then Check "Allow other users to view your desktop" make sure to uncheck "Allow other users to control your desktop" if you dont want to fight for the mouse (with this unchecked, it will be in View only mode, which is good for what I believe you want to do.) and check both Ask for your confirmation and put in a password. (Since its your parents, Id recommend something simple, and then disable it when your done just to be safe, the confirmation part makes it pretty safe(tm) for the most part)

If they/you are on a slow connection, I would disable the wallpaper in the advanced tab. Speeds things up quite a bit.

As for viewing from Windows, or any platform, TightVNC is a good solution. Free, and has both a client and a server. 

[http://www.tightvnc.com/](http://www.tightvnc.com/)

Also the client and server are available in the repository, but since its built in, Id use that server for simplicity sake.

-------------------

Now, if you want to go backwards, You connect to their Windows machine, you can go with the VNC route as well, or you can use Microsoft's RDP. There are many googlable guides on how to enable RDP on windows to act as a server, and rdesktop works great for nix to connect to them. 
However, this option does not allow for remote sharing, as when you connect, they log off (well, Im assuming they DONT have Windows Server 2003/2008 =)

The TightVNC website has plenty of documentation for anything that doesnt make sense =)

---

### Post by mitchroberts on 2008-11-30
> **tjko said:**
> Interesting concorde...

I actually am more concerned with showing my screen than actually having any exchange of control.

Essentially, I would like to emulate the screen sharing properties of applications like iChat on MAC OS, if anybody knows what I mean by that.

if all your concerned with showing your screen just set
the permission on there account to read only so they can 
not do anything i am sure someone made software it do this
but it would be just as easy to do it this way it just cost
less.

---

