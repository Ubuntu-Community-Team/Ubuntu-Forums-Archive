---
title: "Very very frustrated help asap"
date: 2009-03-06
forum: General Help
---

### Post by uns3r on 2009-03-06
first of all when i went to install Ubuntu 8.10 it removed vista
now i find out i am going to have to get a special disc to get vista back
i accidently removed ubuntu when i went into the partion manager and made a partion to try and put vista back
now Ubuntu wont even install onto my computer 
like what is going on 
can someone help me right away please
 edited part 
the installer to install Ubuntu is stopping at 82% and i have used this disc before and am having troubles making new ones

---

### Post by kanikilu on 2009-03-06
So where are you at this point? Neither Vista nor Ubuntu work on your computer? Are you looking to just reinstall both of them from scratch? If so, check out the very extensive Windows Dual Boot guide:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Also, if you are expecting help, please try to be a little more specific and help us help you. For instance, you say that Ubuntu won't install on your computer. I'm sorry to say, that tells us absolutely nothing. What did you try? Did you get any errors?

---

### Post by uns3r on 2009-03-06
ok sorry i wasnt clear enough 
i used to have windows vista
then i installed Ubuntu and it removed vista 
so i reinstalled Ubuntu and gave it more space 
then something happened when i was giving Ubuntu even more space with gparted and now i dont have Ubuntu working on my computer or Vista
I have to pay for special discs cause Toshibia changed the vista program a little bit and Ubuntu is now stopping to install at 82%

---

### Post by uns3r on 2009-03-06
oh wow it took 20 minutes to get to 82% and now its going again after a hour at being at 82%

---

### Post by Vince4Amy on 2009-03-06
Sounds like it's hanging on checking for updates. Try unplugging the ethernet cable if you reinstall again, does it work right now?

---

### Post by Slim Odds on 2009-03-06
> **Vince4Amy said:**
> Sounds like it's hanging on checking for updates. Try unplugging the ethernet cable if you reinstall again, does it work right now?

The Live CD install does not check for updates as part of the install. You can do that **after** you install.

---

### Post by Jubward on 2009-03-06
When it stops at 82% what does it say its doing? If I remember correctly it tells you everything it does while installing...

---

### Post by uns3r on 2009-03-06
i got it now
it just stayed at 82% for about a hour saying it was copying files 
but now it wont let me update or download anything it brings up something saying

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

wont let me update, download wine, emesene messenger it just brings that up 
what can i do so i can download the stuff?

---

### Post by Jubward on 2009-03-06
So, in terminal
```
sudo apt-get update
```
won't work?

---

### Post by uns3r on 2009-03-06
okay i got it now
just the painful part of getting games to work on here now that i lost vista

---

### Post by Vince4Amy on 2009-03-06
> The Live CD install does not check for updates as part of the install. You can do that after you install.

Yes you're right, I didn't mean it quite like that but I know for a fact that if it detects a connection at 80% or something it configures apt and adds the repos.

---

### Post by Jekshadow on 2009-03-06
> **uns3r said:**
> first of all when i went to install Ubuntu 8.10 it removed vista

That was caused by auto partitioning im guessing (reduce the vista partion and use the freed space to create a ext3 partion (linux partion) instead of doing it automatically)
> **uns3r said:**
> now i find out i am going to have to get a special disc to get vista back

Why not just use the disk that came with your computer?
> **uns3r said:**
> i accidently removed ubuntu when i went into the partion manager and made a partion to try and put vista back
now Ubuntu wont even install onto my computer 
See answers #1 and #4
> **uns3r said:**
> the installer to install Ubuntu is stopping at 82% and i have used this disc before and am having troubles making new ones
Try ordering a disk from [Ubuntu Shipit]("https://shipit.ubuntu.com"). Its free and a good disk will be sent to you.

---

### Post by uns3r on 2009-03-06
ya i think i did hit auto partion cause it wasnt working right
my computer didnt come with a disc its a year old and warranty doesnt cover it anymore
and toshibia is retarded not to send a disc with it
and i guess i was supposed to back up the data as soon as i got it
and i have got it going like a said either in this thread

---

### Post by lindsay7 on 2009-03-06
Look at the info that came with you Toshiba laptop. They should have provided a restore cd or dvd with the documentation. If you have that you need to put in the the cd tray and start the computer from being completely off. It should start up and restore the computer to the way it was when you got it. If this is successful you will have windows back plus everything else that was on this computer when it was new.  You can go on from there. If you do not have that cd maybe toshiba will provide you one if you give then the information on you computer, serial number etc.

---

### Post by lindsay7 on 2009-03-06
I looked at this post again, I wonder if the special discs Toshiba is talking about was just a service pack change. If so putting the original vista back on your computer with the restore disc, would still be fine since MS would automatically update the sp and all other updates by itself after your system was restored.

---

### Post by uns3r on 2009-03-06
the special discs have special software that you need for toshibia and software on the computer thats meant for toshibia only 
i figured this out cause i called microsoft then i talked to toshibia and figured out its $50 for a recovery disc

---

### Post by Jubward on 2009-03-06
> **uns3r said:**
> the special discs have special software that you need for toshibia and software on the computer thats meant for toshibia only 
i figured this out cause i called microsoft then i talked to toshibia and figured out its $50 for a recovery disc
scam

---

### Post by namegame on 2009-03-06
> **Jubward said:**
> scam

No, not really. I have a Toshiba Laptop. The recovery discs include some Toshiba-exclusive recovery tools among other things. Toshiba also includes some useful utilities in their "customized" Vista installs.

---

### Post by uns3r on 2009-03-06
lucky, mine didnt come with a recovery disc
i looked in the box and all over
the guy said that when i started my computer it should have gave me the option to make one

---

