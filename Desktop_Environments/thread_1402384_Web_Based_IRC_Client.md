---
title: "Web Based IRC Client"
date: 2010-02-09
forum: Desktop Environments
---

### Post by HDave on 2010-02-09
I am a happy user of Pidgin and use it to connect to about 25 different IRC channels from time to time.

However, I have many different desktop machines and am tired of having to manually maintain the list of channels on each desktop machine as well as having my chat logs spread out all over the place.  I am also frequently on the road and it seems some hotels are blocking all outgoing ports except 80 and 443.

I guess I am looking for some kind of web based IRC client that I can run on my own server that will let me login securely from anywhere on any desktop and connect to multiple freenode and ubuntu channels, etc.

Researching this idea, I've come across a few solutions, but they all seem to be for letting the web chat be to my own IRC server.  I don't want to run an IRC server (if I can help it) -- I just want a Pidgin that runs in a browser....for just me a perhaps a few friends...

Any ideas?

---

### Post by mushwars on 2010-02-09
mibbit, it is very good.

[http://mibbit.com/chat/](http://mibbit.com/chat/)

port 80

---

### Post by HDave on 2010-02-09
Thanks.  I saw mibbit -- and the GUI looks good.  Two things though:

1) I'd like to run my own server and Mibbit looks like it is a proprietary system.

2) Mibbit has been banned from freenet for abuse -- but perhaps it's just the mibbit site, not the software that is block.  Not 100% sure.

Thoughts?

---

### Post by mushwars on 2010-02-09
I have been experimenting with flash irc client, However it has some kind of shady thing i have to do to apache to get it to work, and I dont trust it.

I run my own irc server, I was running unrealircd for a while until I discovered ircd-seven


Setting up your own irc is easy, I would give it a shot its a good learning experience.

---

### Post by HDave on 2010-02-10
I checked out the Flash IRC client...and its not open source which always leaves me wondering....

It did find this one:  [https://blueimp.net/ajax/]("https://blueimp.net/ajax/")

But I don't understand enough to know if I can use it to connect to Freenode channels or do I have to run my own IRC server??

---

### Post by Satoru-san on 2010-02-10
HDave, I was doing some thinking since my last post (I am mushwars) and I totally forgot about something that I use!!!

Its called a bnc. I have one called znc and it is in the repository!!!

Very easy to set up and you can make it listen on port 80 if you would so please. Then on your irc client you type /server <YOUR BNC IP> 80 username:Password and you are connected into your old session on irc, you dont ever leave, even when you type /quit you rejoin and see what happened while you were offline, the only problem is you have to have a server set up somewhere.

There are several free ones just search around for a free BNC

But if you can set up a server, do so and install ZNC.:KS

---

### Post by HDave on 2010-02-15
Thanks for the tip!  I had no idea that IRC bouncers even existed!

It looks like I get to keep my favorite client IRC program, keep the logs on my own ZNC server, and attach over port 80...it's perfect.

A couple of quick questions:

1) will ZNC let me set up limits on the history it keeps...don't think I want months worth of #eclipse history....maybe a day or two...and definitely the parts where I was active....

2) will ZNC let me set up all 25+ channels I regularly use?

3) Is version 0.074 in the repos recent enough?  or should I be looking at doing a manual install?

Thanks again!

---

### Post by Satoru-san on 2010-02-16
Yes! You can limit what you want as far as lines. The best way (after you make the initial config) is to go to [http://your.ip/](http://your.ip/) since you are on port 80 for your znc you dont even need to touch that and it will bring up a login for your webadmin. :) as long as you enabled it.


Read the znc man pages, It has everything you need. I LOVE my znc, I have it running in America. :)


EDIT: 

```
mkdir ~/opt
mkdir ~/opt/znc
cd ~/opt/znc
svn co https://znc.svn.sourceforge.net/svnroot/znc/trunk 
./configure --enable-extra --with-openssl
make
sudo make install

```

I also use the latest. It is also then easy to compile your own plugins or addons from the site like infobot, otherwise they dont work.

Cheers ;)

Also ubuntu has a weird problem with some of the modules, do build it from source.

---

### Post by HDave on 2010-02-16
Terrific -- thanks for the help!

---

### Post by lukjad on 2010-02-16
irssi and screen?

Just a though.

---

### Post by fogNL on 2010-07-27
I know this is an old thread, but, does anyone know of a web-based irc client that I could use to connect to a running BNC?

I want to create a system where some friends of ours, who aren't on irc or have an irc client, can connect in from the web to a running BNC.

---

