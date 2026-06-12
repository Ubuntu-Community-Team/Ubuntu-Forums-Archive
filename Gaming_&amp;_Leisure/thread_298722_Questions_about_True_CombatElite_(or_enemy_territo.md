---
title: "Questions about True Combat:Elite (or enemy territory)"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by javierfh on 2006-11-13
Hello,

i have installed during past week the enemy territory, True Combat Elite and i would like to ask two questions.

First one.

So im using linux, but i thought it would be nice to play also with my brothers, who are using windows. To try, i installed it to one of them and then we tried, i couldnt see the same servers he saw. So my question is: Can linux users play with other users that are windows users? I assumed that yes, but well i was surprised to see that we couldnt see each other.
I didnt tried to create a server and giving him my ip address, but that would be next thing i could try.

Second question:

When im playing the game, first of all sometimes i have trouble to log in, it normally says waiting for challenge or somethig like that and keep counting. I have read somewhere that lots of people have similar thing, but well i still can play in other servers, so no problem. 
But then the game starts and everything it is just fine and very smooth ...until the moment when the "bad guys" come to shoot me :) then my system slows down...seems to freeze or go extremely slow and that results, in dead for me. Because for when the computer speeds up again,im dead :) So does anyone having similar problem?? or any idea why that happens?


If it helps my system it is Pentium IV dual core, with 2GB of ram and Nvidia Geforce 7600GT. So i guess i should be more than fine with the Hardware, but still that annoying thing.


Any help would be more than welcomed.

Javi

---

### Post by javierfh on 2006-11-14
Anyone knows about this issue??
has anyone found similar behaviour?

I really would appreciate all kind of help, even if it is only some links to information.

Javi

---

### Post by javierfh on 2006-11-14
Since not much activity was happening here i went to TrueCombatelite.net and there, in their forums, seems that more people are having similar problem.
Their solution was to go to options or settings and disable there the "marks on walls" or setting it to off.

I havent tried yet since im at work but maybe that will do the trick. Hope that this will help someone else.

Javi

P.S. I still need to figure out if linux users can play together with windows users.

---

### Post by aidanr on 2006-11-14
yes windows users and linux users can play together, if you can't see your friends windows boxes then theres more than likely something up with your network

see if you can ping each other from the terminal/command prompt
```
ping 192.168.X.X
```
and make sure your firewalls are set up correctly, including the builtin firewalls (windows firewall/iptables)

turning off wallmarks fixes an 0.49 linux bug which caused very bad stutter when someone fires a weapon

as for the "awaiting challenge" thing, first of all get punkbuster updated, use the pbsetup.run program from [here]("http://www.evenbalance.com/index.php?page=pbsetup.php"), also use the xqf server browser instead of the ingame browser, you can get it through synaptic

---

### Post by javierfh on 2006-11-14
Hello aidanr,

thanks for your help.

I have tried the wall marks and did the trick.
And so far..i manage to log into some servers, but i have to check the Punkbuster, i have read that many people had that problem...so i will give it a try.
And about that browser..well i will try that one as well.

Another thing i would like to know is about the Teamspeak thing...i suppose that it is these programs that you can use micro to talk to others. Do you know anything about that or some other program that works?

And by the way..are there any other scenarios? i have seem some pics of some other ... any idea how to get into these?

Javi

---

### Post by aidanr on 2006-11-14
teamspeak works well for me, although i've heard that certain soundcards/onboard sound may have problems getting the games sound and teamspeak working at the same time. i've a soundblaster live though and it works just fine

not sure i understood the last question:-?

---

### Post by javierfh on 2006-11-15
Hi,
thanks for your replies.

About the teamspeak, I hope it works in my case, since i have sound card integrated into the Motherboard,an asus P5WD2. So i need to check that one.

With the last question, i was meaning that, are there some other scenarios where to play? do servers have the possibility to offer more scenarios where to play?
Are these called mods?


Javi

---

### Post by frodon on 2006-11-15
If you can't see both the same server, then just note the IP of the server then choose connect to IP rather than searching the server on the server list.
I often do that to connect to my favorite server.

@aidanr, I can't get teamspeak working because of my onboard sound cards which don't include hardware mixer, however i have an old soundblaster live card so i'll try it if you say that you don't have problem with this card.
Do you have also an onboard soundcard, i mean do you have 2 soundcards on your computer ?

---

### Post by aidanr on 2006-11-15
yeah, i have onbaord aswell but i disabled it in the bios, ubuntu detected the soundblaster and configured it perfectly

---

### Post by frodon on 2006-11-15
Thanks, i will do that this week end i think.

---

### Post by sanone on 2006-11-15
I saw your post already yesterday but I had to look the link up which fixed your second problem. I had the same problem but this fix worked on dapper so it should work on edgy as well. 

I found it again on this topic on the truecombat forums. You should make a launcher with these parameters:
```
et +set fs_game tcetest +set seta com_zoneMegs "128" +set com_soundMegs "64" +set com_hunkMegs "256" +set s_khz 22 
```

Check [this]("http://www.truecombat.us/forums/viewtopic.php?t=1019") forumthread for more info...

As for your first problem try an external game browser like XQF or ASE (for windows) or just connect and MSN/ICQ/AOL/IRC the ip of the server to your mates!

Cheers,
San

/me goes shooting some more specops with his fresh install of TCE ;)

---

### Post by javierfh on 2006-11-16
> **aidanr said:**
> yes windows users and linux users can play together, if you can't see your friends windows boxes then theres more than likely something up with your network

see if you can ping each other from the terminal/command prompt
```
ping 192.168.X.X
```
and make sure your firewalls are set up correctly, including the builtin firewalls (windows firewall/iptables)

turning off wallmarks fixes an 0.49 linux bug which caused very bad stutter when someone fires a weapon

as for the "awaiting challenge" thing, first of all get punkbuster updated, use the pbsetup.run program from [here]("http://www.evenbalance.com/index.php?page=pbsetup.php"), also use the xqf server browser instead of the ingame browser, you can get it through synaptic

Hello,

i downloaded XQF and well for some reason dont get any servers there, nor i know how to configure it.

And then about pbsetup.run...how do you run that? i cant make it work.

Any help will be more than welcomed.

Javi

---

### Post by aidanr on 2006-11-16
[http://www.linuxgames.com/xqf/docs.shtml](http://www.linuxgames.com/xqf/docs.shtml)
[http://www.edsgenericforum.com/node/24#xqffilter](http://www.edsgenericforum.com/node/24#xqffilter)

tce is a mod of enemy territory, so in xqf you want to add enemy territory as a game, and "tcetest" as a server filter

the pbsteup.run, make sure you right click -> properties ->permissions ->executable

---

### Post by javierfh on 2006-11-16
> **aidanr said:**
> [http://www.linuxgames.com/xqf/docs.shtml](http://www.linuxgames.com/xqf/docs.shtml)
[http://www.edsgenericforum.com/node/24#xqffilter](http://www.edsgenericforum.com/node/24#xqffilter)

tce is a mod of enemy territory, so in xqf you want to add enemy territory as a game, and "tcetest" as a server filter

the pbsteup.run, make sure you right click -> properties ->permissions ->executable

Thanks now it worked...im very happy :)

thanks for been always ready to help.

Javi

---

### Post by javierfh on 2006-11-18
Hello,

i have tried to install TeamSpeak but i dont know what to do now or at least dont understand what to do next.
Im following that tutorial [http://www.ubuntuforums.org/showthread.php?t=16361&highlight=teamspeak](http://www.ubuntuforums.org/showthread.php?t=16361&highlight=teamspeak)

But then the line where it says sudo sh setup.sh returns and error 
> 
setup.sh: 14: Syntax error: Bad substitution 


So then by accident i double clicked the icon, from nautilus and then it opened the installation wizard. It worked but it asks me where to install and by default shows "/home/javi/TeamSpeak2RC2" but the tutorial says to install it to "/opt/TeamSpeak2RC2 (Should be the default)" but if i try to install it there..i dont have privileges to install it, and since its not command line i dont know how to do it.

So where to install it? 


Thanks in advance again,

Javi

---

### Post by frodon on 2006-11-18
Type "sudo ./setup.sh" rather than "sudo sh setup.sh"

---

