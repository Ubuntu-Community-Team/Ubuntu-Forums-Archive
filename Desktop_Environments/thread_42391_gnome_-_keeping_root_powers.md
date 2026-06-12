---
title: "gnome - keeping root powers?"
date: 2005-06-17
forum: Desktop Environments
---

### Post by ELD on 2005-06-17
Hi is there a way on my normal user accoun to keep root powers so i dont have to keep entering root password all the time?

---

### Post by hw-tph on 2005-06-17
[QUOTE=ELD]Hi is there a way on my normal user accoun to keep root powers so i dont have to keep entering root password all the time?[/QUOTE]
 The whole idea by using sudo or su to gain root privileges when needed is essential to the security of the system. If you make a single mistake as root you can easily hose your entire system, and if malicious code is run as root there is limit to what damage it can do. I suggest you think about it for a while. System administration tasks that need to be run as the root user is not very common in daily use once you have your system setup and configured according to your wishes, so it's not only dangerous - it is pretty pointless too, IMHO.

If you still want to do specific system administration tasks without entering the password I suggest you either read up on sudo or set up groups with the privileges you want and add yourself to those groups.


Håkan

---

### Post by SGC on 2005-06-17
[QUOTE=ELD]Hi is there a way on my normal user accoun to keep root powers so i dont have to keep entering root password all the time?[/QUOTE]
 Read this: [http://ubuntuforums.org/showpost.php?p=214170&postcount=6](http://ubuntuforums.org/showpost.php?p=214170&postcount=6)

---

### Post by ELD on 2005-06-19
[QUOTE=SGC]Read this: [http://ubuntuforums.org/showpost.php?p=214170&postcount=6](http://ubuntuforums.org/showpost.php?p=214170&postcount=6)[/QUOTE]
 Well then i guess linux isnt what im looking for back to windows, i dont want to have to enter a friggin password 24/7 to install/update or wotever.

---

### Post by cohort on 2005-06-21
[QUOTE=ELD]Well then i guess linux isnt what im looking for back to windows, i dont want to have to enter a friggin password 24/7 to install/update or wotever.[/QUOTE]
Geez, and you wonder why viruses/spyware/trojans are so damn prevalent in windoze...

---

### Post by angkor on 2005-06-21
[QUOTE=cohort]Geez, and you wonder why viruses/spyware/trojans are so damn prevalent in windoze...[/QUOTE]

Yeah, and he's even too lazy to use the search button on the forum or browse some of the settings in gdm to get what he wants.
     :roll:

---

### Post by Dave_is_sexy on 2005-06-21
I dunno. I haven't had a virus or intrusion on my windows installation since last August because i actually took a week out to make it hyper-secure. 

I asked for the same thing last week (logging in and out was a right pain) but then found some scripts to let me run nautilus as root from my account (+password) and then one for "right-click > open as root"

Yeah it's not a good idea to be root 24/7 but easy access to "acknowledge my power" is such a help to a new system. Why? Because it's a new system, we're gonna be setting things up for a long time

---

### Post by Dave_is_sexy on 2005-06-21
Scripts are here btw fellow newbie people:

[http://www.ubuntuguide.org/#clipboard-daemon](http://www.ubuntuguide.org/#clipboard-daemon)

---

### Post by angkor on 2005-06-21
[QUOTE=Dave_is_sexy]I dunno. I haven't had a virus or intrusion on my windows installation since last August because i actually took a week out to make it hyper-secure. 

I asked for the same thing last week (logging in and out was a right pain) but then found some scripts to let me run nautilus as root from my account (+password) and then one for "right-click > open as root"

Yeah it's not a good idea to be root 24/7 but easy access to "acknowledge my power" is such a help to a new system. Why? Because it's a new system, we're gonna be setting things up for a long time[/QUOTE]

Maybe you're right, if you plan on setting things up for a long time. I've enabled a root account and can use 'su' if I want a root shell. Setting up Ubuntu the way I like it took me about 2 days and I hardly ever use 'su' anymore...I just keep it around cause I'm used to it from Debian.

I've seen numerous threads on enabling gnome root login and once explained to  someone how it could be done. Eld is just to lazy to learn or use the search function. :-) He's better off with Win.

---

