---
title: "Quake 3 Punkbuster"
date: 2006-04-07
forum: Gaming &amp; Leisure
---

### Post by R3linquish3r on 2006-04-07
Ok, well for some reason whe I try to enable punkbuster in Quake 3, it says "Enable Punkbuster YES/NO" as usal and when I click yes it goes back to the menu page and it still says disabled. I also tried setting it to "1" in the config and as soon as I start the game it resets to zero. I also tried re-installing the latest patch but that didn't help either. Has anyone else had this problem and been able to fix it? I really want to play some Insta but all the servers are PB...

---

### Post by dermotti on 2006-04-07
I had this happend to me in Battlefield vietnam. Go into the config file like you did and save. Then take away the write permissions on the config file. Voila!

---

### Post by Adrian_b on 2006-04-07
I thought PB doesn't support linux and you'll be kicked off the servers..
That's what happens all the time in CoD anyways...

---

### Post by R3linquish3r on 2006-04-07
Yeah takign away write protection doesn't help.... And PB wasnt supported in Cedega with BF2 for a while. It is supported O_O

---

### Post by crane on 2006-04-08
I think there are two things you can try. Changing the config and setting and making the config read only could work. This should be done with your q3config, not an autoexec.cfg in the .quake3 folder in your home directory. Are you using and autoexec.cfg file? You could enter the setting in that config file then delete your q3config file. When you start the game it will write a new one.

 Let us know if you get it working. Be sure to update it before going online to play. This will keep you from getting kicked to spec while you wait for it to update. check out [http://www.evenbalance.com/index.php?page=pbsetup.php]("http://www.evenbalance.com/index.php?page=pbsetup.php") for help on updating.

---

### Post by R3linquish3r on 2006-04-08
Everything you mentioned was tried a while ago crane ;) No luck though. Im using q3config no point in the auto one. DOn't want a new one made anyway I got some nice tweaks in it ;)

---

### Post by crane on 2006-04-09
[QUOTE=R3linquish3r]Everything you mentioned was tried a while ago crane ;) No luck though. Im using q3config no point in the auto one. DOn't want a new one made anyway I got some nice tweaks in it ;)[/QUOTE]


OK, lets see.... Which one are you changing? This is how mine is set now and all is working well. 
seta sv_punkbuster "0"
seta cl_punkbuster "1"

Make sure you have permissions to write to the q3config then. Maybe the config file is read only and the game can't change it. Be sure to check the log files. ( in the /q3a directory)
Also, what latest patch have you installed? I think it is now 1.32b for quake3

---

### Post by R3linquish3r on 2006-04-09
ITs got all writes or I couldnt add in stuff from the menu. yeah I'm running 1.32b. What I tried changing was sv_punkbuster "0" to "1" but that didnt work. I'll see if i can find the cl one.

---

### Post by R3linquish3r on 2006-04-09
I found cl_punkbuster and set it to "1" but as soon as I start the game it changes it back to '"0". Seems to me that my game just doesn't see that PB is installed.... If you have IRC you can stop by my clans channel at irc.atheme.org #asylum and maybe you could help a bit better directly :)

---

### Post by R3linquish3r on 2006-04-09
K well my uncle came over today and helped me figure it out. Turns out the files were being slip between /usr/local/games/quake3/pb and /home/ed/.q3a/pb. I also had to run the game as sudo. Thanks for your help.

---

### Post by crane on 2006-04-09
[QUOTE=R3linquish3r]K well my uncle came over today and helped me figure it out. Turns out the files were being slip between /usr/local/games/quake3/pb and /home/ed/.q3a/pb. I also had to run the game as sudo. Thanks for your help.[/QUOTE]
 
Sorry I couldn't make it to your IRC channel, Things are crazy here at home right now. So you got it enabled? What was the acual problem. Just in case I hear someone else with this problem.

---

### Post by R3linquish3r on 2006-04-09
Yeah the problem is I tried updating the files from evenbalance.com. DOnt use the single files. Get the pbsetup.run program and use taht.

---

