---
title: "Neverwinter Night(mare)"
date: 2005-05-07
forum: Gaming &amp; Leisure
---

### Post by N'Jal on 2005-05-07
I have a small problem with neverwinter night's multiplayer mode. When i connect to the servers i see the servers but not the server types, nor the people online or the chat window. Everything except my ./nwn file passes the md5 check and its because of an sdl problem the file needed editing and thus the md5 checksum will be different.

What might cause this?

I have tryed the NWN forums and it seems they don't know what the problem might be. They suggested the md5 check and allowing some ports through my firewall but i don't know how to configure my running firewall, in fact i don't even know what firewall i am running.

---

### Post by bored2k on 2005-05-07
[QUOTE=N'Jal]I have a small problem with neverwinter night's multiplayer mode. When i connect to the servers i see the servers but not the server types, nor the people online or the chat window. Everything except my ./nwn file passes the md5 check and its because of an sdl problem the file needed editing and thus the md5 checksum will be different.

What might cause this?

I have tryed the NWN forums and it seems they don't know what the problem might be. They suggested the md5 check and allowing some ports through my firewall but i don't know how to configure my running firewall, in fact i don't even know what firewall i am running.[/QUOTE]
 Do you have a router ? You need to open up ports for it manually. Do you use a linux firewall? wich  one?

---

### Post by N'Jal on 2005-05-07
No router i use the Alcatel Speed Touch USB hack, revision 0

I don't know what firewall i use, i have Firestarter but i have a feeling ubuntu activates one at start up that's the one i don't know about, nor how to find out about.

---

### Post by graigsmith on 2005-05-07
i was having problems with neverwinter nights, but it turned out to be a BIOS setting. i turned off spread spectrum. and i stopped having 3d problems.  

are you able to join and play servers? or are you just not seeing the chat thing?  what version of nwn are you using?

---

### Post by N'Jal on 2005-05-08
I have 1.65 patch applied

As for connection i didn't get that far as i was joining my GF on a server but with no chat list nor user lists i couldn't see her so gave up. I can't seem to take a screenshot, if someone can tell me how to do this (Yes i tryed print screen and gnome screen thing, they didn't work) i will provide a screenshot to show you the problem

I CAN see the: -

Scroll bars
Server list
Buttons
Check boxes

Everything else is just white.

---

### Post by graigsmith on 2005-05-08
you know what, i bet it has to do with permissions.  mabey some of the files dont have read write permissions.

either that or try reinstalling.

---

### Post by N'Jal on 2005-05-09
That maybe the case however the command they told me to run didn't work so i did this: -

cd /usr/local/games/nwn
sudo chown neil /*

That gave me permission's to everything but it was the only command i could think of to use.

Has that done something bad? Or incompletely?

---

### Post by rpgcyco on 2005-05-09
Hey,

Try this. :)

```
cd /usr/local/games/nwn
sudo chown -R user:group .
sudo chmod -R ugo=rX,ug+w .
```

So for you, that'll probably be...

```
cd /usr/local/games/nwn
sudo chown -R neil:neil .
sudo chmod -R ugo=rX,ug+w .
```

That was taken from [this](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72) thread on the NWN Linux forums.

> sudo chown neil /*

That gave me permission's to everything but it was the only command i could think of to use.

Has that done something bad? Or incompletely?

Errr... I think you just set yourself as owner of the entire file system, which is bad.

- Rpg Cyco

---

### Post by N'Jal on 2005-05-10
> Errr... I think you just set yourself as owner of the entire file system, which is bad. 

No i havn't i made myself the owner of everything in that directory, i know this because I have tryed accessing other part's of the file system and don't have access it's still safe, thank goodness

The reason i used my command is because i get this

```
neil@ubuntu:/usr/local/games/nwn $ sudo chown -R neil:neil
Password:
chown: too few arguments
Try `chown --help' for more information.

```

---

### Post by rpgcyco on 2005-05-10
You must have the period (.) after those commands I listed. :) The period signifies the contents of the current directory.

Good news about the rest of your file system. :)

- Rpg Cyco

---

### Post by N'Jal on 2005-05-10
The commands now work but havn't fixed the problem.

> Good news about the rest of your file system. 

Thank's I'm still learning been using for a year 2 maybe not really that long. So will make a lot of mistakes. I know the dangers of giving myself fs permissions but it wouldn't supprise me if i did it accidentally.

Thank's for your help so far.

---

### Post by DarkKnight on 2005-05-28
[QUOTE=N'Jal]Everything except my ./nwn file passes the md5 check and its because of an sdl problem the file needed editing and thus the md5 checksum will be different.[/QUOTE]

Could you tell me how you fixed that? 

My nwn install keeps spitting this at me: 
```
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory

```

I know I'm s'pose to run ./nwn, but I just get "Error".  :|

---

### Post by nautilus on 2005-06-02
[QUOTE=DarkKnight]Could you tell me how you fixed that? 

My nwn install keeps spitting this at me: 
```
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory

```

I know I'm s'pose to run ./nwn, but I just get "Error".  :|[/QUOTE]

The reason you get the libmss error is because you aren't setting the preload path.

The reason you aren't setting the preload path, is because you aren't running "./nwn".  Why you're doing that, you have yet to explain, and the best fix is to paste the script in here.

As for the primary issue of missing content on your display (except scrollbars, it seems) the most likely cause is the usage of system SDL libraries, instead of the provided NWN libraries.

Or, alternatively, a general OpenGL problem; Mesa, DRI, DRM, X... One of them...

---

### Post by DarkKnight on 2005-06-03
[QUOTE=nautilus]The reason you get the libmss error is because you aren't setting the preload path.

The reason you aren't setting the preload path, is because you aren't running "./nwn".  Why you're doing that, you have yet to explain, and the best fix is to paste the script in here.

As for the primary issue of missing content on your display (except scrollbars, it seems) the most likely cause is the usage of system SDL libraries, instead of the provided NWN libraries.

Or, alternatively, a general OpenGL problem; Mesa, DRI, DRM, X... One of them...[/QUOTE]
 Yeah, I figured that out after I looked at the script >_>

The problem was the fglrx drivers that told me where setup; wernt. 
Once I fixed them, the problem went away, and was replaced with massive amounts of errors in the in-game log thingy >_<
(Even though the graphics and sound look fine, the errors are so vast it makes it feel like I'm running on mostly swap...)

---

