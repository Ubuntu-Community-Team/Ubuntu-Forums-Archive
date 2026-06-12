---
title: "Pass argument to a running program via SSH?"
date: 2009-05-09
forum: General Help
---

### Post by NorQue on 2009-05-09
Hello,

is there a way to pass a command line argument to a running program via SSH? I'm connected to my PC via Putty on my Nokia Communicator and I want to remote control Amarok with it, rudimentary functions like play, pause or skip track would be great – having a garden party soon and it'd be quite convenient not having to go inside each time. I know that can be done with Amarok locally from terminal, but from SSH I always get a missing X-Server complaint (of course, there's no X-Server...).

Any input?

---

### Post by Kareeser on 2009-05-09
I know Rhythmbox includes this functionality in a separate program called "rhythmbox-client"

Perhaps there's an "amarok-client" installed along with amarok?

---

### Post by NorQue on 2009-05-09
Thanks, but unfortunately there's nothing like that in the repositories. :/

---

### Post by gamblor01 on 2009-05-09
Wow nifty idea!

So when you're using putty from your phone, I assume you have a terminal to type commands into (otherwise you wouldn't know about the no X server complaint).  As long as you have a terminal then fear not!

[https://team-emphasis.org/category/misc/quick-tips/amarok-command-line/](https://team-emphasis.org/category/misc/quick-tips/amarok-command-line/)


I tried it and it worked perfectly!  I didn't put the alias command in my .bashrc, I just ran it manually after logging in over ssh.  You can put it into a script that is in your PATH instead of using the alias like this:

```

#!/bin/bash

/usr/bin/dcop --user <username> amarok player $1

```The $1 there is the first argument to the script (such as next, prev, and so on).  Just for reference, here is the information from the above link in case the page becomes unavailable at some point:


> 
I wanted to control amarok out of my command line. I searched the internet for an appropriate tool, and found [narc]("http://www.necoro.net/?projekte/narc"), a tool to control amarok over ssh. But it is difficult to handle and requires a ssh connection even to localhost. So I had a look at the source &#8212; and now I solved the problem like this:
 
[LIST]
[*]add the following line to your bashrc: (at least on Gentoo: ~/.bashrc)
alias amarokctl='/usr/kde/3.5/bin/dcop --user nils amarok player'
(*Maybe* your username is not **nils**. If so, please change it ;-)
[*]now you can control amarok with this usage:
[LIST]
[*]amarokctl next: next song
[*]amarokctl prev: previous song
[*]amarokctl title: get title of currently played song
[*]amarokctl artist: get artist of currently played song
[*]amarokctl playPause: toggle play / pause
[*]amarokctl enableRandomMode: enable random mode
[*]amarokctl setVolume VOLUME: set Volume to VOLUME (I think VOLUME shoud be an integer between 0 an 100)
[*]amarokctl volumeDown: decrease volume
[*]amarokctl volumeUp: increase volume
[*]amarokctl stop: stop playing.
[/LIST]
 
[/LIST]



Just note that his path to dcop is different than the one you should expect.  He was obviously running gentoo and you're most likely not, considering the forum that you're posting on.  ;)

---

### Post by NorQue on 2009-05-09
Woah, that's great, it works! Exactly what I wanted. Thanks a lot! :D

EDIT:
Looks like you can do a lot more interesting stuff with that: [http://cpan.uwinnipeg.ca/htdocs/DCOP-Amarok-Player/DCOP/Amarok/Player.pm.html](http://cpan.uwinnipeg.ca/htdocs/DCOP-Amarok-Player/DCOP/Amarok/Player.pm.html)

---

### Post by gamblor01 on 2009-05-09
Sweet Perl module -- I don't have a phone capable of connecting to my system via ssh (at least, I don't think it can), but you can bet that once I get one I will be setting this stuff up to try it out!

---

