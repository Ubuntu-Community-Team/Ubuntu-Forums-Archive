---
title: "AWN woes"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by Nythain on 2007-09-14
ok, so i've got a problem here... awn-manager wont load, wont do anything.
i followed the incredibly oh so popular guide on how to get functional eye candy with awn yadda yadda yadda... but whenever i run awn-manager, i get nothing, nadda zip zilch... teh little dock thingy runs, though its sort of annoying at the moment, just a little box with a bouncy firefox emblem that happens to stay above EVERYTHING... im assuming i can make this app cool if i can ever figure out how the hell to configure it... any suggestions???

---

### Post by Rupertronco on 2007-09-14
Right click on the AWN bar and hit preferences. If you're unable to do so Alt+F2 and run gconf-editor (or select it from your gnome menu) and go to apps>avant-window-navigator. 

i'm unaware of an awn-manager package, I surely don't have one. I would expect the awn-manager command to fizzle. 

You can easily have maximized windows overlap awn, it's in the settings options i've mentioned above.

---

### Post by Nythain on 2007-09-14
so basically im screwed... what a great app

---

### Post by Rupertronco on 2007-09-14
> **Nythain said:**
> so basically im screwed... what a great app
Utter nonsense. 



Did you read anything I wrote? Did you try any of the above steps? If so what went wrong? awn-manager does not exist as far as I know, that's not the way to configure the program. the other two ways i mentioned are the steps to configure awn. 

Also to run the program itself, the command is avant-window-navigator.

---

### Post by ssteinbr on 2007-09-14
> **Nythain said:**
> so basically im screwed... what a great app

Ummm, not really.  I had this problem last night.  My fix was to delete the old AWN folders (from previous installations).  The one that seemed to do the trick was /usr/local/share/avant-window-navigator/

Try running awn-manager in the terminal and see what errors are coming up.  You can also ask the people over at the AWN forums [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum") 

Hope this helps.

---

### Post by Nythain on 2007-09-14
ok, first off awn-manager does exist
```

rune@swinebox:~$ whereis awn-manager
awn-manager: /usr/bin/awn-manager /usr/X11R6/bin/awn-manager /usr/bin/X11/awn-manager
rune@swinebox:~$

```

next problem, as i've said, running awn-manager gives no errors, it does, well nothing really
```

rune@swinebox:~$ awn-manager
rune@swinebox:~$

```

if awn-manager is not teh way to configure awn, then the link in my kmenu (placed there during teh installation of awn) is effen retarded, cause it just points to... awn-manager

finally, right clicking on the awn bar and clicking "preferences" (wich im assuming also just runs awn-manager) does, well, absolutely nothing..

and lastly, as for gconf editor, it didnt exist... i guess thats because im running kde instead of gnome... i can install gconf-editor, i already have gconf 2 installed so what can it hurt, but that would make this apps reliance on gnome probably one of the worst i've ever encountered, and it should be brough to peoples attention in the many guides and forum threads from teh get go that this is a GNOME only app, as in "you gonna need like hard core gnomage" to run this. Thats not directed to either one of you for you didnt write any of the guides, but its relatively irritating that i have to keep junkin up my kde system with 90% of gnome for this one, im hoping, cool app.

Edit: instaling gconf-editor has given me a very minimal amount of configuration for awn, yay, but its still not as optional as awn-manager
[http://lifehacker.com/photogallery/awn/2452031](http://lifehacker.com/photogallery/awn/2452031)
pretty spiffy for a program that doesnt exist

and another note, to the advice to delete the old folder or whatever, this is my first installation, it would be weird that i have to delete a folder after installing???

---

### Post by Rupertronco on 2007-09-14
> i'm unaware of an awn-manager package

is what i said, i believe. my apologies for spending my free time trying to help you. 



furthermore, what version of awn did you install and did you update it via svn?

---

### Post by Nythain on 2007-09-14
sorry, just got a little upset at someone basically telling me what my problem was is something that doesnt exist, wich does, and is my problem...

back to the point at hand (and thank you for taking your time to help, it is appreciated, though im about to give up on it)

the version i installed is
avant-window-navigator-bzr Version: 0.1.2-bzr78-1
awn-core-applets-bzr Version: 0.1.0-bzr43-1
both pulled from
# Avant Window Navigator packages
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
following the instruction at
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

as i mentioned, i am running kde, wich could be my problem, i may never know... all i know is awn-manager just doesnt run, at all, with no error or anything, its weird and irritating...

once again, thanks for your help, im sorry again for gettin an attitude

---

### Post by Shadowline on 2007-09-14
I don't think AWN will run under KDE, I've never been able to get it to. So I would think its a gnome only app. There are docks for KDE, kxdocker I believe is one.

---

### Post by ssteinbr on 2007-09-15
Just took a peak over at the AWN forums and KDE integration is on the devs "TODO" list.  So I'm guessing that's why awn-mamanger isn't working for you.

Re: suggesting you delete folders:  I had to do this because I had compiled AWN from source and the old settings were mucking around with the new installation.  Guessing that's not yer problem either.

---

### Post by Rupertronco on 2007-09-15
I'm working getting it to run on my KDE session, it's not an easy task, to be honest, I'm sure it will involve editing a bunch of files and will probably result in a greater effort than it's really worth. I'm at an airport, so I don't have my usual tools at hand, good tlhing my flight was cancelled so I won't be seeing home anytime soon. 

Anyway, in the meantime, I'd suggest Kooldock or Kiba. Kiba has some really cool features but it's lacking compared to awn. 

I don't see how you can get around installing a bunch of gnome libraries though...

---

### Post by JBAlaska on 2007-09-15
Rupertronco, I feel for ya buddy. I've spent alot of time in airports waiting for a plane, they have to have the most uncomfortable chairs known to man. It's nice that you have your puter with ya though.

@Nythain, you might try installing gnome desktop along with kde. I was happy with kde before I saw compiz fusion running on gnome. Now I have both desktops but seem to spend most of my time in xgl/gnome playing with the desktop effects lol.

Before you give up, here's a screenshot of my desktop with awn tweaked a bit:
[[IMG]http://img451.imageshack.us/img451/1569/compizawngnomedesktopti3.th.png[/IMG]](http://img451.imageshack.us/my.php?image=compizawngnomedesktopti3.png)

If you try it,  Make sure you do a good backup first cause compiz fusion (you have to have desktop effects to run awn) can bugger your system..It's a bit of a pain but I think it's worth it.
Good Luck!

---

### Post by Nythain on 2007-09-15
ok, well awn itself runs, my only problem is with the manager, so ill just abandon hope on there... and i pretty much really dont like gnome... but thanks for the help and the info, im just gonna chalk this one up to not gonna work, and look into kxdocker, though i doubt its as cool as awn... its not so much the docker end of it i was interested in, it was a lot of the applets and the other functionality of it

thanks again guys

---

### Post by Rupertronco on 2007-09-15
> **JBAlaska said:**
> Rupertronco, I feel for ya buddy. I've spent alot of time in airports waiting for a plane, they have to have the most uncomfortable chairs known to man. It's nice that you have your puter with ya though.


Not only that, but I'm in the most loathsome airport, in possibly the worst city on the planet. Welcome to Los Angeles and LAX. Thank god they at least have a Wolfgang Puck. 

Anyway I've got awn running on this comp with a KDE setup, the only problem is, I also have gnome installed so it's impossible for me, using this equipment, to isolate running awn in KDE. I'm sure there's a ton of people that would like to get this working so I'll try my best to help you out.

---

