---
title: "streaming video for Firefox ?"
date: 2005-03-18
forum: Desktop Environments
---

### Post by pieter hollenberg on 2005-03-18
HI

just installed Hoary (it is fast !) everything worked, internet, email, office, printing, sound, mp3, usb camera, etc 

but I found it quite disappoiting that I couln't see streaming files on the internet.

some packages suggest they do (in synaptic) but I cant get streaming movie to work in firefox.

how do you guys do this ? 

Ok, in XP I downloaden en installed realplayer.

but in linux this isn't so easy for me.

why isn't there a package for this available in the "universe" ?

For a newbie I think this should be a part of the install disk ! 

thanks....

---

### Post by bored2k on 2005-03-18
> **pieter hollenberg]HI

just installed Hoary (it is fast !) everything worked, internet, email, office, printing, sound, mp3, usb camera, etc 

but I found it quite disappoiting that I couln't see streaming files on the internet.

some packages suggest they do (in synaptic) but I cant get streaming movie to work in firefox.

how do you guys do this ? 

Ok, in XP I downloaden en installed realplayer.

but in linux this isn't so easy for me.

why isn't there a package for this available in the "universe" ?

For a newbie I think this should be a part of the install disk ! 

thanks....[/QUOTE]
 Add this line to your repository list:
> deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then install mozilla-mplayer . That gets you covered on most videos even apple's trailers on quicktime format  said:**
>  wget [https://helixcommunity.org/download.php/967/hxplay-1.0.3.749-linux-2.2-libc6-gcc32-i586.bin;](https://helixcommunity.org/download.php/967/hxplay-1.0.3.749-linux-2.2-libc6-gcc32-i586.bin;) chmod 755 hxplay-1.0.3.749-linux-2.2-libc6-gcc32-i586.bin; sh hxplay-1.0.3.749-linux-2.2-libc6-gcc32-i586.bin and follow the terminal installer [saying yes to anything] .

Easy huh ?

---

### Post by joekm on 2005-03-18
And then make sure the appropriate plugin files are linked or copied into your Firefox plugins directory.  You might also want to make sure you have the full set of codecs for all the file types you want to be able to play (just use Helix for RealMedia stuff though).

Xine also has a mozilla plugin in development I believe.

---

### Post by bored2k on 2005-03-18
[QUOTE=joekm]And then make sure the appropriate plugin files are linked or copied into your Firefox plugins directory.  You might also want to make sure you have the full set of codecs for all the file types you want to be able to play (just use Helix for RealMedia stuff though).

Xine also has a mozilla plugin in development I believe.[/QUOTE]
 Yes but mplayer is usually faster than Xine but thanks for pointing that out .

Yes i forgot, install w32codecs .

Thanks joekm for the reminder.

---

### Post by lifewithryan on 2005-03-18
I just use mplayer-plugin...if you google for it, you should find it.
if you were able to install mplayer easily enough, that you shouldn't have any problem installing the plugin...
and the install readme is really easy to understand.

---

### Post by pieter hollenberg on 2005-03-19
ok, thanks, I will try to install this by hand ( I enjoy to do so, but lot's of my friends and family don't )

my real point is:

will this "streaming audio/video" functionality built in in the final hoary ? 

I think this should be the case !

because the huge majority of this world are "simply users" who just want for a distro which is fast, easy, simple, complete, and for most of the time use the pc for 4 things:

1. internet (including streaming functionality)
2. email 
3. office 
4. multimedia devices etc

that's why I like ubuntu !.

but my point is that I miss a few things which I consider to be "urgent" for the majority of global pc users.

maybe I had to post this point in another forum ?

is there a forum where discussions are about the ubuntu basic "functionality", requierements, etc ?

---

### Post by pieter hollenberg on 2005-03-20
thanx

but to download realplayer 10 was for me the easiest way.

so it works now.

now i can can see streaming internet movies, like tv etc. great !

but the question remains why isn't this "streaming funktionality" part of the basic hoary ? 

I think it should !

because the majority of the people aren't capable of doing this kind of technical things.

I thougth the policy of ubuntu was "ease of use " and "for the common user" ?

---

