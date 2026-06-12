---
title: "pyscrabble server fails to start"
date: 2008-12-08
forum: Gaming &amp; Leisure
---

### Post by Electraglider on 2008-12-08
Ubuntu Rocks!!:biggrin:

Now for my problem...

I have this extra computer sitting around I wanted to use as a local home network game server that I can access with all the other computers in the house for some gaming. So I decided to start with Pyscrabble. This is my first attempt at this sort of thing by the way.

To make a long story short, I installed the Pyscrabble server on the spare computer and the client on one of the other computers. During the course of trying to get the clients to connect to the server I discovered that the Pyscrabble server wasn't even starting. I tried it on two other computers with the same results.

Here is my terminal output when starting the server.

[PHP]@Gateway-mobile:~$ sudo /etc/init.d/pyscrabble-server force-reload
 * Restarting PyScrabble server pyscrabble-server                        [ OK ] 
@Gateway-mobile:~$ sudo /etc/init.d/pyscrabble-server status
 * Status of PyScrabble server: not running
@Gateway-mobile:~$ [/PHP]

Any ideas?

I am a long time lurker by the way and this is actually the first time I have been unable to find a solution to my problem that someone else hasn't already solved.

---

### Post by Xianath on 2009-04-15
A bit late but hopefully not too late. I stumbled upon your post while trying to find a solution for your problem but I saw no answers so I had to come up with it on my own and thought I'd share.

It looks like there are two versions of python installed with Intrepid -- 2.4 and 2.5 -- and 2.5 is the default, but some of the support libraries for pyscrabble-server (namely ZODB) comes with 2.4 only. So what I did was to edit /usr/games/pyscrabble-server.py and change its shebang to this:

```
#!/usr/bin/python2.4
```

pyscrabble libraries themselves install in the 2.5 tree so I had to link them:

```
sudo ln -s /usr/lib/python2.5/site-packages/pyscrabble /usr/lib/python2.4/site-packages/
```

That's all I had to do to get it to work. Give it a try and let me know if it works for you too.

Cheers,
Peter

---

### Post by Electraglider on 2009-04-16
> **Xianath said:**
> A bit late but hopefully not too late. I stumbled upon your post while trying to find a solution for your problem but I saw no answers so I had to come up with it on my own and thought I'd share.

It looks like there are two versions of python installed with Intrepid -- 2.4 and 2.5 -- and 2.5 is the default, but some of the support libraries for pyscrabble-server (namely ZODB) comes with 2.4 only. So what I did was to edit /usr/games/pyscrabble-server.py and change its shebang to this:

```
#!/usr/bin/python2.4
```

pyscrabble libraries themselves install in the 2.5 tree so I had to link them:

```
sudo ln -s /usr/lib/python2.5/site-packages/pyscrabble /usr/lib/python2.4/site-packages/
```

That's all I had to do to get it to work. Give it a try and let me know if it works for you too.

Cheers,
Peter

Thanks Peter,
I had nearly forgotten about that. I was trying to set it up so my wife and I could play on two seperate laptops. I eventually got Atlantis working which enabled us to play Monopoly over the network. That was pretty cool. The next chance I get I'll try out your solution to the Py-scrabble issue.
Lyle

---

### Post by cuz on 2009-07-28
Gentlemen,

I have a different and more elemental problem. The server starts up fine in Jaunty, but in my ignorance I can't locate the server_console.cfg file to set the game and web ports. Can either of you provide some guidance here?

Thanks,
cuz

---

### Post by vevel on 2009-11-23
Whew.  Well, /etc/pyscrabble contains the server_console.cfg file. 
Ports are 8888 and 9999 by default.

# game_port: port the Game Server will listen on
# web_port: port the Web Configuration console will listen on

[pyscrabble]
web_port: 8888
game_port: 9999

After reading the thread, I realized I could start pyscrabble-server via /etc/init.d/ and that worked fine.

---

### Post by SoFl W on 2011-01-16
I know it is an old thread but I will try...

Does anyone know where the user file is stored?  I didn't see a place to enter new users and I hit refresh, after that it keeps asking me for authorization.  Looking through the docs it said I needed to enter the first player as the admin, but never saw a place to do that.  Where is the user file kept?

---

### Post by Zero0hm on 2011-04-18
Yea I am at the same spot. Mine also has doesn't properly "add host." If you figure it out. Old thread or not please reply back here! Thx.

---

### Post by kostikvento on 2011-07-15
Well, I've found that the user data (and all the rest) are stored in db.fs-files in /var/lib/pyscrabble.

To add the first user you should just launch the client, then select your newly created server (if it is not in the list of public servers, then obviously you should "add host") and register as a new user. The first registered user automatically becomes admin.

That's what they say somewhere in deep docs (well, it's [http://svn.kibibyte.se/pyscrabble/trunk/debian/pyscrabble-server.README.Debian](http://svn.kibibyte.se/pyscrabble/trunk/debian/pyscrabble-server.README.Debian)).
But anyway, I didn't manage to do so. First, having added new host, I don't see it's name in the list, although it gets selectable (empty line, right! one should guess it is). Second, even having selected the host and filled the new user's form, I press 'create', but nothing happens. (Yes, I've checked if the server runs, it does).

PS. And when I try to connect to one of public servers available, the client just gets closed, with no messages at all. The server seems to be running, because when I misspell user's name, it says I'm wrong.

---

