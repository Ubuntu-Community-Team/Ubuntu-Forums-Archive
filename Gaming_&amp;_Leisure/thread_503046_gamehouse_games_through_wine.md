---
title: "gamehouse games through wine"
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by vortex_noob on 2007-07-17
Hi, i'm a new ubuntu convert. Tried linux since 2 years ago but got stuck in installation till i found ubuntu. (First Dapper, now in Feisty)
I'm trying to convert my friends and family to ubuntu from MiSs WaXp :)
with my aunt, all she wants to do with a computer is playing games (small and simple ones like the ones from gamehouse). I installed feisty on her system, installed wine 9.41 and installed tumblebugs.

when i click on the icon launcher on the desktop, nothing happend, so i ran it from the console and got this message in the console:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:EnumDisplayDevicesW ((null),0,0x33f604,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33f604,0x00000000), stub!
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (12000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:dbghelp:SymGetModuleInfo Wrong size
err:seh:setup_exception stack overflow 96 bytes in thread 0009 eip 7bc656a2 esp 00230fa0 stack 0x231000-0x340000

the game just won't work
since my encounter with wine is just through utorrent (which work flawlessly.. thank god)
can someone point me in the right direction??

Thanks in advance...

---

### Post by hikaricore on 2007-07-17
If it won't run, chances are there is nothing you can do to make it work.
I couldn't find any info on the game in the [wine application database]("http://appdb.winehq.org").  Looks like you're just outta luck at the moment.

However there are hundreds upon hundreds of games that are either native to linux or have been ported.  Here's a few sites to check out:

[http://gaming.gwos.org/](http://gaming.gwos.org/)
[http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)
[http://freegamer.blogspot.com/](http://freegamer.blogspot.com/)
[http://www.happypenguin.org/](http://www.happypenguin.org/)
[http://www.linux-gamers.net/](http://www.linux-gamers.net/)
[http://www.linuxgames.com/](http://www.linuxgames.com/)
[http://linuxgamingworld.com/](http://linuxgamingworld.com/)
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.ubuntugames.org%2F&langpair=pt%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fwww.ubuntugames.org%2F&langpair=pt%7Cen&hl=en&ie=UTF8)
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.holarse-linuxgaming.de%2Fh2006%2Fspace%2Fstart&langpair=de%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fwww.holarse-linuxgaming.de%2Fh2006%2Fspace%2Fstart&langpair=de%7Cen&hl=en&ie=UTF8)
[http://linuxemu.retrofaction.com/](http://linuxemu.retrofaction.com/)

You may want to enable the universe/multiverse repos for more software titles and games: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

And for simple quick game downloads, checkout GetDeb's gaming section: [http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by hobieone on 2007-07-17
the thing about about gamehouse games and games from similar place is they all like to send data back to them or install somesort of spy ware on the systems which why i tell people don't even bother with those places  you r just asking for trouble. 
 but the issue  you had  with wine looking at the erroor was in fact a common one  when a programis attempting to establish a net work link thru ms .net network wich wine doesn't  support yet.  the error  with is  primarily whats blocking quite few games  from working with wine  such as everquest 2 that uses the net protocol.

---

### Post by vortex_noob on 2007-07-17
well, i guess i'm outta luck, huh? 

Anyone know any game in linux that resembles tumblebugs or zuma??
At least i can show people that linux has a lot to offer rather than staying with MS software for these measly spyware-infested games.

---

### Post by Beren Camlost on 2007-07-17
Tried with Virtual Machine? Since these games don't need a lot of machine resources one would think it would be possible to run them like that. I do not unfortunately have any experience with it and can't test myself until Thursday earliest.

---

### Post by hikaricore on 2007-07-17
> **vortex_noob said:**
> well, i guess i'm outta luck, huh? 

Anyone know any game in linux that resembles tumblebugs or zuma??
At least i can show people that linux has a lot to offer rather than staying with MS software for these measly spyware-infested games.

Did you look through the game lists on any of the sites I linked you?
HappyPenguin is a good place to start as they have one of the largest lists around.

> **Beren Camlost said:**
> Tried with Virtual Machine? Since these games don't need a lot of machine resources one would think it would be possible to run them like that. I do not unfortunately have any experience with it and can't test myself until Thursday earliest.

I guess atleast under a VM it would be safe_r_ to install spyware lol.

---

### Post by vortex_noob on 2007-07-18
Thanks all for the replies. 

I did check to getdeb.net and happy penguin, but i haven't seen any games that resembles zuma nor tumblebugs (my aunt insist on it.. heh heh).

Well there are more links that i have to check out (thx again hikaricore!)

Again, if anyone knows about any game that i'm looking for, i appreciate it.

Btw, i'm currently installing virtualbox in my system. We'll see if it runs on it.....

---

