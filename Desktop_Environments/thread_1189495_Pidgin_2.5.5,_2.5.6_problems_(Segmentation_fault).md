---
title: "Pidgin 2.5.5, 2.5.6 problems (Segmentation fault)"
date: 2009-06-16
forum: Desktop Environments
---

### Post by Wanas on 2009-06-16
First my problem with pidgin 2.5.5:
I was using it from a while and it was working well, but I have a problem when trying to change my display pic sometimes it crashes but I dont care much about that, then I updated to 2.5.6 through the launchpad ppa of pidgin developers then I got problems with the last release so I changed back to 2.5.5 here is the problem with 2.5.5:
 all of my msn and yahoo emails works fine except one msn email when I try to login with this email pidgin crashes, I tried amsn to login with this email this email works fine with amsn.

my problem with pidgin 2.5.6:
 When I try to add or remove any contact it disconnects, this is discussed here [http://developer.pidgin.im/ticket/8977](http://developer.pidgin.im/ticket/8977) but I didnt understand the solution :(.    

here what I got when I type pidgin -d in the terminal (pidgin 2.5.5)
> (02:43:02) msn: Sending ADL with payload: <ml l='1'><d n='hotmail.com'><c n='polo-89' l='3' t='1'/></d></ml>

(02:43:02) msn: C: NS 000: CHG 79 HDN 1073741856 %3cmsnobj%20Creator%3d%22wanasathry%40hotmail%2ecom%22%20Size%3d%226201%22%20Type%3d%223%22%20Location%3d%22TFR2C2%2etmp%22%20Friendly%3d%22AAA%3d%22%20SHA1D%3d%2295seES2mITTEpLpsPlqpDkr2BzY%3d%22%20SHA1C%3d%22dYyvh51%2fuiGgP%2bM3hzg4VmP1A5c%3d%22%2f%3e
(02:43:02) msn: Sending UUX command with payload: <Data><PSM/><CurrentMedia/><MachineGuid/></Data>
(02:43:02) msn: C: NS 000: UUX 80 48
(02:43:02) msn: unqueueing command.
Segmentation fault


---

### Post by Wanas on 2009-06-18
any suggestions please.....

---

### Post by Clorow on 2009-06-18
Segfaults, in technical terms, happen when the program tries to write memory to a space it doesn't have the permissions to write to. Usually, this is fixed by:


[LIST=1]
[*]Open Synaptic
[*]Type in "Pidgin"
[*]Mark pidgin and pidgin-data for Complete Removal (please note, this does not delete your personal settings. It just deletes the global settings which you shouldn't have to worry about)
[*]DON'T PRESS "APPLY CHANGES". Instead, erase your search box, go to Custom Filters, and click on Marked Changes. Write down everything that is being uninstalled, so you can reinstall it.
[*]Press "Apply Changes".
[*]Once it's done, reinstall everything you wrote down.
[/LIST]

---

### Post by Wanas on 2009-06-18
I have tried to reinstall pidgin alot of times but I think its not the problem 

> Segfaults, in technical terms, happen when the program tries to write memory to a space it doesn't have the permissions to write to.
I have tried to open pidgin in root mode but the same error accures :(

and thanks for replaying

---

### Post by Clorow on 2009-06-18
Reinstalling by complete removal or just removal? Also, being root won't matter, since that's really not how it works. It's not files, it's RAM and swap space. So just try completely removing Pidgin and installing it again.

---

### Post by Wanas on 2009-06-18
thanks for your fast replay ;)
yeah I always do the complete removal of my applications

but I have the same .purple folder in /home folder, I dont change it from like a 5 months does this matter ?

---

### Post by Wanas on 2009-06-19
any other suggestions plz

---

### Post by Wanas on 2009-06-20
I am now using pidgin 2.5.2 and every thing works fine 
thanks for helping :p

---

### Post by dumblebee100 on 2009-08-20
This ******* pidgin never work for me ...when I try to connect to google talk ...It always segfaults ..

last resort I have to use wine and windows pidgin ..but I dont want to do like that ...

is there any other way to connect to google talk

---

### Post by Wanas on 2009-08-20
> **dumblebee100 said:**
> This ******* pidgin never work for me ...when I try to connect to google talk ...It always segfaults ..

last resort I have to use wine and windows pidgin ..but I dont want to do like that ...

is there any other way to connect to google talk

Try to use pidgin 2.6.1, I tried it and google talk works, and they said that the new pidgin 2.6.1 support voice/video for google talk chat but it didnt work for me :(
Download it from [http://www.getdeb.net/](http://www.getdeb.net/) (the site wont open at this minute)
So try this [http://linux.softpedia.com/progDownload/Pidgin-Download-6.html](http://linux.softpedia.com/progDownload/Pidgin-Download-6.html)

---

### Post by dumblebee100 on 2009-08-20
> **Wanas said:**
> Try to use pidgin 2.6.1, I tried it and google talk works, and they said that the new pidgin 2.6.1 support voice/video for google talk chat but it didnt work for me :(
Download it from [http://www.getdeb.net/](http://www.getdeb.net/) (the site wont open at this minute)
So try this [http://linux.softpedia.com/progDownload/Pidgin-Download-6.html](http://linux.softpedia.com/progDownload/Pidgin-Download-6.html)

I even tried the2.6.1 from the getdeb but the history repeats itself ..

the same error ..

by the way what are your settings for google talk ..could you tell me like 
label: value

---

### Post by Wanas on 2009-08-23
> **dumblebee100 said:**
> I even tried the2.6.1 from the getdeb but the history repeats itself ..

the same error ..

by the way what are your settings for google talk ..could you tell me like 
label: value

here a screenshot ;)

---

