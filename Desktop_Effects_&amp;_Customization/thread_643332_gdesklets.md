---
title: "gdesklets"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by LT72884 on 2007-12-17
So i did a sudo apt-get install gdesklets and it installed. the only problem is how do i get it to start automatically. after every reboot i have to do a alt+F2 and then type in gdesklets and then it starts it. But once i close it i cant reopen it unless i reboot the pc and re run it.

---

### Post by jimbob on 2007-12-17
System->preferences->sessions->startup programs then click add and create an entry called gdesklets.  (Assume you are using GDM here).

---

### Post by LT72884 on 2007-12-18
So it seems that i cant have gdesklets turned on along with beryl. even though beryl craps out on me right now, i still cant have gdesklets and beryl at the same time can i.

o BTW thanks for the help

---

### Post by jimbob on 2007-12-18
No, right now they seem to be mutually exclusive.

---

### Post by LT72884 on 2007-12-18
> **jimbob said:**
> No, right now they seem to be mutually exclusive.

dang. so is there a plug in for beryl that will have the menu bar like mac osx does. because thats what i have now on my desktop. its pretty cool

---

### Post by Armadillo Kilr on 2007-12-18
really? i'll have to check that out...

---

### Post by LT72884 on 2007-12-18
> **Armadillo Kilr said:**
> really? i'll have to check that out...

yeah ill post a pic of it.

[[IMG]http://aycu16.webshots.com/image/35975/2004565912570511551_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004565912570511551)

i used gdesklets to make it and then i made all the icons and starters for it. it took about 4-6 hours of playing with.

---

### Post by jviscosi on 2007-12-18
I haven't run gDesklets in quite a while but there used to be a checkbox in the gDesklets configuration that was supposed to make it aware of a compositor; would that help at all?  (I never tried to use gDesklets with Beryl so I have no idea what the problem is, I'm just tossing this out as an idea.)

ADesklets might have something similar to the gDesklets StarterBar by now.  Does ADesklets work with Beryl?

---

### Post by LT72884 on 2007-12-18
> **jviscosi said:**
> I haven't run gDesklets in quite a while but there used to be a checkbox in the gDesklets configuration that was supposed to make it aware of a compositor; would that help at all?  (I never tried to use gDesklets with Beryl so I have no idea what the problem is, I'm just tossing this out as an idea.)

ADesklets might have something similar to the gDesklets StarterBar by now.  Does ADesklets work with Beryl?

i have never heard of Adesklets. i just barley started using gdesklets yesterday. Right now im currently trying to get them to work on my fedora laptop but it wont start. i double click the icon and it says starting gdesklets but it never opens anything.

---

### Post by jviscosi on 2007-12-18
> **LT72884 said:**
> i have never heard of Adesklets. i just barley started using gdesklets yesterday. Right now im currently trying to get them to work on my fedora laptop but it wont start. i double click the icon and it says starting gdesklets but it never opens anything.

The little gdesklets icon isn't appearing in your system tray, then?  Hmm, you might want to open a terminal and run **gdesklets** from there to see if it spits out any error messages.  I remember it used to periodically hang on me or fail to start for whatever reason, usually python-related.  Sometimes a bad desklet could hose it up pretty good too.

You can also do **gdesklets shutdown** and **gdesklets restart** to manipulate the gdesklets daemon.  I think there are some other commands too but I don't remember them off the top of my head.  **gdesklets --help** will probably show them.

ADesklets does the same sort of thing as gDesklets, little desktop widgets and stuff.  I haven't used that in a long time either but when I did there weren't as many desklets for it yet as there are for gDesklets.  I don't know if it would also suffer from compatibility issues with Beryl.

---

### Post by LT72884 on 2007-12-18
> **jviscosi said:**
> The little gdesklets icon isn't appearing in your system tray, then?  Hmm, you might want to open a terminal and run **gdesklets** from there to see if it spits out any error messages.  I remember it used to periodically hang on me or fail to start for whatever reason, usually python-related.  Sometimes a bad desklet could hose it up pretty good too.

You can also do **gdesklets shutdown** and **gdesklets restart** to manipulate the gdesklets daemon.  I think there are some other commands too but I don't remember them off the top of my head.  **gdesklets --help** will probably show them.

ADesklets does the same sort of thing as gDesklets, little desktop widgets and stuff.  I haven't used that in a long time either but when I did there weren't as many desklets for it yet as there are for gDesklets.  I don't know if it would also suffer from compatibility issues with Beryl.

i did a 
root#gdesklets
can NOT run gdesklets as superuser
root#

so i logged out and logged in as a normal user and the shell starts but guess what............. its empty. nothing in there. found out that it is a different version than the ubuntu. ubuntu is 0.53.3 and fedora uses 0.53.4. so now i have to figure out how to install them. also im looking for a background display that will display a new picture every minute or so.

---

### Post by jviscosi on 2007-12-18
> **LT72884 said:**
> i did a 
root#gdesklets
can NOT run gdesklets as superuser
root#

so i logged out and logged in as a normal user and the shell starts but guess what............. its empty. nothing in there. found out that it is a different version than the ubuntu. ubuntu is 0.53.3 and fedora uses 0.53.4. so now i have to figure out how to install them. also im looking for a background display that will display a new picture every minute or so.

Hmm, most likely the shell is empty because you installed the desklets as a different user, so they don't exist in the hidden **.gdesklets** directory of the home directory of the other user.  The revisions are close enough that I should think the same desklets would work in both of them otherwise.  (I very rarely had an upgrade break a desklet, but it's possible.)  You could try copying the .gdesklets folder from the one user's home directory to the other, or you could just try installing a desklet or two and see if they work.

Do you mean you want a new wallpaper every few minutes?  Your desktop might already support that, depending on what you use.  (I know XFCE does, for instance.)  Your screenshot looks like Gnome, so here's a [thread]("http://ubuntuforums.org/showthread.php?t=49336&page=9") about this very topic for Gnome.

I'll skip the lecture about not running as root because I'm sure you've heard it before.  ;-)

---

### Post by LT72884 on 2007-12-18
> **jviscosi said:**
> Hmm, most likely the shell is empty because you installed the desklets as a different user, so they don't exist in the hidden **.gdesklets** directory of the home directory of the other user.  The revisions are close enough that I should think the same desklets would work in both of them otherwise.  (I very rarely had an upgrade break a desklet, but it's possible.)  You could try copying the .gdesklets folder from the one user's home directory to the other, or you could just try installing a desklet or two and see if they work.

Do you mean you want a new wallpaper every few minutes?  Your desktop might already support that, depending on what you use.  (I know XFCE does, for instance.)  Your screenshot looks like Gnome, so here's a [thread]("http://ubuntuforums.org/showthread.php?t=49336&page=9") about this very topic for Gnome.

I'll skip the lecture about not running as root because I'm sure you've heard it before.  ;-)

LOL not running as root is a good idea but i am so dam lazy and LOVE to be root. i hate trying to copy files from one place to another but cant becasue i dont have permissions. i COULD set my main user to act pretty much like root but that takes time but then again a great learning expeirence. im studying to be a RHCE in a year or so.maybe even more. yes i am using gnome. KDE has the feature i am talking about but i hate KDE's orginaztional features. gnome is so much better at that part. in gnome i can go to computer then network and browse my other window machines. i have not figured that out yet in KDE. i cant get beryl to work for either gnome or KDE ATM so any way ill try out your idea because i was thinking the exact same thing. but i wonder why the app cant be run as root anyway... hmmm

---

### Post by jviscosi on 2007-12-18
> **LT72884 said:**
>  but i wonder why the app cant be run as root anyway... hmmm

I think the devs just coded it that way because they don't want it running with superuser permissions.  Maybe there are security flaws that they're aware of but haven't gotten around to fixing yet so this is their way to protect us.  (Idle speculation ... gDesklets devs, please don't flame me!)

You can put some pretty neat stuff on your desktop with gDesklets so I hope you can get it working.  :-)

---

### Post by LT72884 on 2007-12-19
> **jviscosi said:**
> I think the devs just coded it that way because they don't want it running with superuser permissions.  Maybe there are security flaws that they're aware of but haven't gotten around to fixing yet so this is their way to protect us.  (Idle speculation ... gDesklets devs, please don't flame me!)

You can put some pretty neat stuff on your desktop with gDesklets so I hope you can get it working.  
:-)

DUDE, LOL i wouldnt flame..  I was thinkning the same thing. Maybe they are trying to get us away from using root as much as possible. BTW wouldnt mind hearing your lecture on that. Ok i have them working some what. i found a website 

[www.gdesklets.ca/zencomputer.org](www.gdesklets.ca/zencomputer.org) or something close to that. that has alot of desklets but alot of them are busted. now im just trying to get it to work and also trying to get beryl or fusion to work but it doesnt want to play nice

---

### Post by jviscosi on 2007-12-19
You may have already been here too but the new (well, not that new anymore I guess) gDesklets home page is at [http://www.gdesklets.de/](http://www.gdesklets.de/).  I think they also have an archive of older desklets there which may or may not work, due to a major rearchitecturing that they did to gDesklets a while back (which is probably why the ones you found at that other site are broken).

---

