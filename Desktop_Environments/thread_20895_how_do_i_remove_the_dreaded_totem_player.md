---
title: "how do i remove the dreaded totem player?"
date: 2005-03-19
forum: Desktop Environments
---

### Post by Datchew on 2005-03-19
as we all know by now, dvd play in warty sucks!  most of the time it just doesn't happen.  xine, totem, gxine, mplayer, etc... they all are goats!

gxine works well with eveyrthing BUT dvd play, so i'm keeping it around but everytime i simply double click on something, that damn TOTEM comes up and goes "HEY LOOK HEY LOOK... GIMME A CHANCE... I CAN DO IT...!" and then it bombs everytime. 

in short, i want to remove it.
i was just gonna find everything with "totem" in it in synaptic and uninstall, but on my last ubuntu installation (i'm on my 12th or so) that fried everything so i thought i'd ask for advice from the pro's this time. 

Thanks much.

---

### Post by Martin Witte on 2005-03-19
Well it is easy to remove with Synaptic. I struggled a while with palying video on DVD as well, but had success with totem-xine.

---

### Post by dcstar on 2005-03-19
[QUOTE=Datchew]as we all know by now, dvd play in warty sucks!  most of the time it just doesn't happen.  xine, totem, gxine, mplayer, etc... they all are goats!

gxine works well with eveyrthing BUT dvd play, so i'm keeping it around but everytime i simply double click on something, that damn TOTEM comes up and goes "HEY LOOK HEY LOOK... GIMME A CHANCE... I CAN DO IT...!" and then it bombs everytime.
.......[/QUOTE]
Computer-Desktop Preferences-Removable Storage

Change the "DVD Videos" command from Totem to the application you want them to play on, mine says: "xine dvd://" so when I insert a DVD, xine kicks in.

---

### Post by Datchew on 2005-03-19
thanks guys. 

I know how to uninstall it in synaptic... I just want to make sure i remove everything. 

Is that all that runs that whole program?  just one little file called totem?

what about all those little things called "dependencies" that it adds in when you install something?

does it automatically remove all that junk and just not say anything about it?

I just want to make sure i'm getting a clean uninstall and that nothing will be hanging behind to mess things up.  

Also, i just want to get some of the tons of stuff i'll never use off my OS so it will run faster.

---

### Post by munki on 2005-03-22
> 
inux user since 12-24-04.
have installed ubuntu from scratch about 12 times now and starting to hate linux!!! p.s. just give up playing dvd's on ubuntu. trust me on this.


Problems in playing dvd's on ubuntu? never heard of it, why do you give ubuntu the fault ? it's running on the same kernel as all other dists. 

All computers i've installed ubuntu on, plays dvd easy! It must be you that can't figure out how to play'em.

---

### Post by lordofkhemenu on 2005-03-23
[QUOTE=Datchew]thanks guys. 

I know how to uninstall it in synaptic... I just want to make sure i remove everything. 

Is that all that runs that whole program?  just one little file called totem?

what about all those little things called "dependencies" that it adds in when you install something?

does it automatically remove all that junk and just not say anything about it?

I just want to make sure i'm getting a clean uninstall and that nothing will be hanging behind to mess things up.  

Also, i just want to get some of the tons of stuff i'll never use off my OS so it will run faster.[/QUOTE]
Some dependencies do get left behind. However, search within synaptic for 'deborphan' and you'll find an answer to that little issue :wink:

---

### Post by Datchew on 2005-04-08
[QUOTE=munki]Problems in playing dvd's on ubuntu? never heard of it, why do you give ubuntu the fault ? it's running on the same kernel as all other dists. 

All computers i've installed ubuntu on, plays dvd easy! It must be you that can't figure out how to play'em.[/QUOTE]

uh huh... just plays em no problems right outta the box huh?
Believe me, i've done the how-to's, the ubuntuguide.org steps, tried alllll the different kinds.  I've gotten them to work, but then i do something terrible like REBOOT or try to install java for the browser and all the dvd's die. 
Do a search on setting up dvd's and you'll see just how much trouble multimedia can be in Linux.

---

### Post by carlc on 2005-04-08
Does Totem play anything? I have never had any luck with it. Other programs such as xine work great!

---

### Post by bored2k on 2005-04-08
[QUOTE=carlc]Does Totem play anything? I have never had any luck with it. Other programs such as xine work great![/QUOTE]
 If you
sudo apt-get install totem-xine it will run great.

---

### Post by Datchew on 2005-04-09
bored-2k... ya, i've had that working too for a few days. :-)  then it died as well. 


gonna move to hoary this weekend and hopefully, i'll have better luck. 

lately i've been so frustrated with the bugs in playing dvd's that i'm just giving up on using linux for multimedia for awhile.   you know... i'll have to work up the patience to get on it again later.

---

