---
title: "&quot;RemoteDesktop&quot; - looking 4 alternative to VNC?"
date: 2007-05-16
forum: Desktop Environments
---

### Post by Finch75 on 2007-05-16
Hello everybody,

I'm in the process of switching from Windows to dual boot ;-) I'm currently evaluating alternatives for the applications for which I cannot find Linux versions. One of them is "RemoteDesktop" which works really great "out of the box" in Windows XP. I was surprised and happy to find a RemoteDesktop _client_ in Ubuntu so the Linux -> Windows connection is covered. I still need Windows -> Linux and especially Linux->Linux or actually really only Feisty->Feisty.

I use it to access my home PC from the office, the office PC from home and even my (business) notebook from my PC (I only have one keyboard and one nice large monitor).

Even before I'd ever used Linux, I'd heard of X11 and the clear separation of the window manager from "other stuff". I'd always thought remote access should be really easy?!

So far, it doesn't look really easy. I've found some installation instructions for XDMPC (?) and they really scared me. Is there really no standard way of accessing one Linux/Ubuntu PC from another Linux/Ubuntu PC?

My question really only concerns the desktop connection, not the networking involved (I have ssh and OpenVPN running).

I have used VNC of course, but that's not really an option. It's ok for a few clicks but I'm looking for something that lets me use a PC remotely for hours!

Please help me! :-)

---

### Post by rdoolen on 2007-05-17
Try No Machine [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

---

### Post by bob.xiao on 2007-05-17
> **rdoolen said:**
> Try No Machine [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

UltraVNC is also a good server&client.

---

### Post by musther on 2007-05-17
If you aren't scared of the command line, just use SSH with x tunnelling and run the app you want.  What this basically involves is installing an SSH server on your linux machine, then connect to it (command line login), then, assuming you've used the correct options, you can just start what you want, eg type 'firefox' or 'ooffice'.

If you want in depth info on how to do this, I'll give you a hand.

I sometimes use VNC (why don't you like it?) but usually use SSH, it has two clear advantages:

 - Data is encrypted
 - You're only sending the graphical info for the app you want, not the whole desktop, and the window incorporates into your local desktop.

Let me know if you need more info on this.

---

### Post by mannheim on 2007-05-18
I second the recommendation for No Machine. It is an [Anything]->Linux solution. When I travel, I carry the Windows NX client with me on a usb stick. Then I can connect to my own familiar desktop from wherever I am.

---

### Post by Finch75 on 2007-05-20
Hello everybody,

thanks for the hints. I took a look at NoMachine. Looks good. They have a "demo server". When I first tried it, I got an error message. The next day, I tried again and always got "server busy". Now (an hour ago) it worked and looked good. I guess I'll use it.

HOWEVER, I'd still like some solution with "built-in" programs so I can connect from anywhere. Is that possible?

> **mannheim said:**
> I second the recommendation for No Machine. It is an [Anything]->Linux solution. When I travel, I carry the Windows NX client with me on a usb stick. Then I can connect to my own familiar desktop from wherever I am.

Sounds good. That's what I currently do with RemoteDesktop (Win XP) - and I don't even have to carry anything around :-). Can I use the NX client without an installation? I mean...  I cannot install it on some PC "when I travel"... Being able to use it without installtion would be a REAL plus!

> **musther said:**
> If you aren't scared of the command line,

No, I'm not scared. Actually, "moderate" use of the command line is one of the reasons I'm trying to use Linux. I even have cygwin and sshd installed on my Windows machine. :-)

> **musther said:**
>  just use SSH with x tunnelling and run the app you want.  What this basically involves is installing an SSH server on your linux machine, then connect to it (command line login), then, assuming you've used the correct options, you can just start what you want, eg type 'firefox' or 'ooffice'.

If you want in depth info on how to do this, I'll give you a hand.

Yes, that would be nice. I hope I can install sshd by myself (I'll try...), but it'll take me a couple of days because I really want to understand what I'm doing with the CA and the keys this time :-)
After that, what do I need to do? Which options?

> **musther said:**
>  I sometimes use VNC (why don't you like it?) 

Two or three reasons:
The most important one is: It does not open a remote login, it uses a local login. I.e. when I'm connected, that local desktop is also "open". While this is a good thing in "remote assistance" scenarios (like when I need to help my mother *bg*), it's a very bad thing in my case. For example: I often leave my notebook in the office and use it remotely from home. I'd really prefer the screen to be locked when I do that ;-)

Apart from that, I don't like two things about the "handling": I have not yet figured out a nice solution if the local and the remote screen have different resolutions. If the remote screen is smaller, that's still ok but not ideal. But what if the remote screen is larger? That's really hard to use...

Last thing: VNC really feels like it "stupidly" transmits the whole screen instead of changed windows / areas. It just doesn't feel "integrated". The 3.x versions where really bad (ok, I don't mean that - it's a good thing we had them, but there are just MUCH better alternatives now!), 4.x is ok for small taks but I really wouldn't want to use it for a long time...


> **musther said:**
> 
but usually use SSH, it has two clear advantages:

 - Data is encrypted

Well, that is an advantage of ssh, but not a disadvantage of VNC. I try to keep my PC safe/secure and don't open "plain text logins" anyway. (ok, sometimes I do for just one IP). If I use VNC, I usually use SSH tunneling for the port or I use OpenVPN...

> **musther said:**
> 
 - You're only sending the graphical info for the app you want, not the whole desktop, and the window incorporates into your local desktop.

That can be good or bad, depending on what you want to do - and if you know the names of all the programs you want to open :-)

> **musther said:**
> 
Let me know if you need more info on this.

Yes, I do ;-) For one thing, I want to give it a spin and see if I like it. The other reason is that X11 forwarding seem to be the "standard Linux/Unix option" for this kind of thing and I'd like to know how to use it... It might take a couple of days for me to post my results, but I will...

Thanks,

Finch

---

### Post by musther on 2007-05-20
Ok, I've found SSH with X tunnelling to be dead easy, hopefully you should experience the same! :)

Firstly, install the server on the machine you want to connect into, the package you need is openssh-server, so use whatever method you want to install it.

And that's it for the server, ssh just provides a remote TTY (though an encrypted tunnel), so any existing user accounts can be logged into, so if you need new ones, create new users in normal way (System - Administrations - Users and Groups).

For the client, it's really easy if it's a linux machine, make sure the ssh client is installed (it is by default on ubuntu), then type:

```
ssh -X -C the_machine_to_connect_to
```

So, the -X tells ssh to use X forwarding (what we need) and the -C tells it to compress the data - easy as that.

The machine can either be an ip address or a recognised host name.  I don't know if your machine will have a static IP, if not you could use something like dyndns.org to get an address to use (free), so mymachine.dyndns.org will continue to point to your current IP, if you're lucky your router will support updating it so you'll never need the little update client.

This seems like a good time to mention that by default ssh runs on port 22, so you'll have to create a 'virtual server' in your router setup to direct port 22 to your machine.

Now, to connect form windows you'll need two little bits of software, the first is PuTTY:
[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)
and the second is an X server for windows, Xming:
[http://downloads.sourceforge.net/xming/Xming-6-9-0-23-setup.exe?use_mirror=optusnet](http://downloads.sourceforge.net/xming/Xming-6-9-0-23-setup.exe?use_mirror=optusnet)
Now you may also want other parts of Xming, such as Xlaunch which makes full screen X sessions and the like possible easily, I assume it's part of the 'tools and clients' package:
[http://downloads.sourceforge.net/xming/Xming-tools-and-clients-6-9-0-28.zip?use_mirror=optusnet](http://downloads.sourceforge.net/xming/Xming-tools-and-clients-6-9-0-28.zip?use_mirror=optusnet)

So basically what you do is start Xming (sits in the system tray by default and runs an x server) then just open PuTTY and make sure that on the left, under SSH > X (or somewhere like that) X tunnelling is enabled, and you may have to specify the display (can be found by hovering your mouse over the Xming icon).  You can look at other settings like compression.

Then connect using PuTTY (tip, you can save the session info, where to connect, settings etc under a simple name, then when you start PuTTY in the future you can just double click the name you saved).

Once connected, you can just start your X app, a good test is 'xeyes'.

So, then you should be good.  

Also, remember that you can run ALL of your desktop, not just common apps, for example if you want to get to your gnome menu's, you can even load gnome-panel.  And finally it is possible to get a whole desktop, it's not something I've done, but it should be pretty easy, and here's a page with lots of info:
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

Have Fun!

-----EDIT-----
Forgot to mention that you can add hosts to /etc/hosts, that way you can type:
ssh -X -C homecomp
rather than:
ssh -X -C 124.241.211.141   - or someting :)

---

### Post by Finch75 on 2007-05-20
[COLOR="Blue"][SIZE="4"]About X11 forwarding[/SIZE][/COLOR]

> **musther said:**
> Ok, I've found SSH with X tunnelling to be dead easy, hopefully you should experience the same! :)

Yes, actually, I did. It's easy as soon as you know the "magic" commands. :-)
I'll try to find the most comfortable solution for "every day work", but this X forwarding is definitely the part I was looking for: a simple solution with "on board / out of the box programs" :-)

> **musther said:**
> 
ssh, sshd, ... The machine can either be an ip address or a recognised host name.  ... dyndns ... port 22 ... PuTTY ... 

*hehe* - thanks for the little "Networking 101" ;-)
I think I had mentioned that I "usually run VNC through an SSH tunnel or OpenVPN", have sshd on my Windows machine and have disabled "plain text logins" in favor of public/private key authentication... ? :-)

However, all of that is "standard networking" which also applies to Windows. X11 is rather *nix-specific, so that's where I'm lost...

> **musther said:**
> 
And finally it is possible to get a whole desktop, it's not something I've done, but it should be pretty easy, and here's a page with lots of info:
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

Yeah, I'll have to read that page again - very slowly ;-) I just "scanned" it and launched KDE and Gnome remotely. That's fun and completely confusing ;-) (having all the windows mixed and also two menus...)

Thanks for all the hints, I'm off for a good start but might have more questions a little later. The weekend's over now, so I'll have less time for experiments...

> **musther said:**
> 
Forgot to mention that you can add hosts to /etc/hosts

Yes, i know (did you know that "hosts" also exists on Windows?). However, that'll only work if I have a static IP (which I don't).

[COLOR="Blue"][SIZE="4"]About NoMachine[/SIZE][/COLOR]

Also looks good, but the installation sucks! Can anybody help me?

I tried to install the server and it failed and said that it required the client. So I went and installed the client and it failed because it required some library I didn't have. Synaptic could fix that for me and the client is now "happy".
Then I tried to install the server again and it failed because it cannot find package "nxnode". So where can I find that one?! I'm a Linux newbie and I have no idea how to deal with dependency hell... I want and need an easy installation. I'll probably have to reinstall my system sooner or later (as soon as I have a better idea of how things work and realize how many stupid things I've already done to my system *g*) and I don't want stuff that takes a long time to install...

Any help?

---

### Post by musther on 2007-05-20
No, I didn't know about hosts for windows, where's the list?

And if you don't have a static IP, you should definitely use dyndns.org, I'm lucky that my router supports it out of the box so it does the updating for me, no need for a client!.

---

### Post by Finch75 on 2007-05-20
> **musther said:**
> No, I didn't know about hosts for windows, where's the list?

Oh, quite easy (if you know where it is *g*):
C:\WINDOWS\system32\drivers\etc

Makes so much sense, right?

> **musther said:**
> And if you don't have a static IP, you should definitely use dyndns.org, I'm lucky that my router supports it out of the box so it does the updating for me, no need for a client!.

Yeah, so does mine :-) I'm not new to networking in general, just new to Linux and X(11)...
While we're exchanging tips & tricks... did you know that you can "alias" a domain name to a dyndns name? :-)
Let's say you own the domain musther.org (which is free, btw :-), you can have it point to your computer permanently by setting its CNAME ;-) It's really cool!

Oh well, that's a little off topic :-)

---

### Post by musther on 2007-05-20
Yes, I knew about that.  I haven't got a domain at the moment though.  Although I do consider it from time to time as a way to have an effectively permanent email address, and if I get one, I might do that.

---

### Post by mannheim on 2007-05-25
> **Finch75 said:**
> 

[COLOR="Blue"][SIZE="4"]About NoMachine[/SIZE][/COLOR]

Also looks good, but the installation sucks! Can anybody help me?

I tried to install the server and it failed and said that it required the client. So I went and installed the client and it failed because it required some library I didn't have. Synaptic could fix that for me and the client is now "happy".
Then I tried to install the server again and it failed because it cannot find package "nxnode". So where can I find that one?! I'm a Linux newbie and I have no idea how to deal with dependency hell... I want and need an easy installation. I'll probably have to reinstall my system sooner or later (as soon as I have a better idea of how things work and realize how many stupid things I've already done to my system *g*) and I don't want stuff that takes a long time to install...

Any help?

I agree that the instructions from nomachine are seriously lacking. You need to install (as you discovered), the client, then the nx-node package, then the nx-server package. All of these are linked to from [this page]("http://www.nomachine.com/download.php") on nomachine's site.  (Scroll down the page to find the link to the NX node package).

It's actually easier than it sounds (install three packages, all from nomachine's web site).

Sorry I didn't check on this thread for a while.

---

### Post by Finch75 on 2007-05-26
> **mannheim said:**
> Sorry I didn't check on this thread for a while.

Your reply came just in time for the weekend, thanks ;-)
For the installation: ok, I guess I could've found the nxnode package if I'd looked more thoroughly. However, they REALLY could've mentioned that on the server page. It takes three attempts to install this software because only the installation complains about missing pieces. 
Anyway, I got it working now and it looks ok.

However, I need one thing it doesn't seem to offer: Can I "join"/control an existing session remotely? The scenario is this: I have my office PC in the office and I just lock the screen when I leave. Then if I have to do something later at night or during the weekend, I just log in remotely and do the stuff. However, I need to access all my open windows - VNC does that.But I do NOT want people in the office to see what I'm doing or more importantly, have access to my computer during that time (that's why I lock the screen, duh...)

It's exactly how Windows' RemoteDesktop works. I know it might be annoying if people keep saying: "I want it to work exactly the same way it works in Windows". However, I really have good reasons for this wish ;-) It's just exactly what I need and the alternatives cause big problems...  (e.g. I cannot open a browser in a second session because the profile is in use; same thing for Eclipse... so I'd have to close most of my programs before locking the screen and somehow, that's not the point of keeping the computer on...)

Can I somehow use X-forwarding to join and forward the existing session?

Any more hints?

---

### Post by mannheim on 2007-05-27
> **Finch75 said:**
> Your reply came just in time for the weekend, thanks ;-)
It's exactly how Windows' RemoteDesktop works. I know it might be annoying if people keep saying: "I want it to work exactly the same way it works in Windows". However, I really have good reasons for this wish ;-) It's just exactly what I need and the alternatives cause big problems...
Any more hints?

I know what you mean. I used to use Windows XP and really miss this feature. Some people have suggested a workaround of using NX even when you are sitting in front of the "remote" machine -- i.e. an nx connection to localhost. You can suspend that session and pick it up again later from home. But I don't like doing this. I don't my local session to go through nx.

The workaround that I use for Firefox is to have separate profiles for remote use and local use.  This is rather complicated, and won't suit everyone. It works well for me. (Others have suggested switching to Epiphany for a browser, which apparently behaves better in this context.) 

For what it's worth, here are the horrible details of what I do with Firefox (and also Thunderbird.) I create two profiles, called "default" and "remote-profile". To make sure that the correct profile is used, I do the following. First I configure the NX session by going to the "General" tab, selecting "Custom" from the drop-down menu instead of GNOME or KDE. Next to that drop-down menu, click "Settings .." and then check the radio button for "Run  custom command". Enter "/home/Your-Username/bin/remote-gnome-session". Then make an executable script in ~/bin/remote-gnome-session with something like the following:
```
#! /bin/bash

# To be run to start an nx session

# Export some environment variables here. Eg, choose a Firefox profile, whatever:
export FF_PROFILE="remote-profile"

dbus-launch --exit-with-session gnome-session

```

The effect of all this is that you can set whatever environment variables you want, specifically in the environment of all your remote nx sessions. For example, you can then create your own "firefox" script in ~/bin/firefox and put something like this in it:

```
#!/bin/bash
if [ "${FF_PROFILE}" = "" ]
then
  FF_PROFILE=default
fi

/usr/bin/firefox -p "${FF_PROFILE}" "$@"
```

Once this is all set up, when you launch firefox in your nx session, you will be using the profile called "remote-profile". In your regular sessions, you will be using the profile "default".

---

