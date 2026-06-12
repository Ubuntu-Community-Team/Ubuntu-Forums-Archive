---
title: "Mplayer and Realplayer /Firefox Plug in help"
date: 2006-01-18
forum: Desktop Environments
---

### Post by Omnios on 2006-01-18
Hi I have just installed firefox 1.5 and its slick. I had this same problem with the old version of firefox as I found the mplayer plug ins to be very agressive to the point where it tryes to open realplayer preference set media. Mostly yahoo news vidio. I did a test by moving the mplayer plugins into a temp backupfile and shure anouph realplayer worked flawless. I also found the same thing occurs with media cionnect. 

 Is there a specific mplayer plug in for realmedia content that I can remove or keep in a backup file so that Realplayer launches? Also did the gnome preference thing and could not find a mplayer listing in it.

---

### Post by Fixxxer on 2006-01-18
I think you need to edit your /etc/mplayerplug-in.types file and comment out the line with realmedia. I don't use mplayerplug-in (anymore) so I can't give you the exact line... Hope that helps.

---

### Post by ossi on 2006-01-18
Concerning Firefox Video-plug ins I decided for a partly external but very good solution, where you can decide yourself with what to open a Video. Probably you like to look at it:

[https://addons.mozilla.org/extensions/moreinfo.php?id=446]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")

---

### Post by krypto_wizard on 2006-01-18
I have the same issue with embedded firefox plugin

[www.raaga.com/hindi](www.raaga.com/hindi) 

this site needs realplayer. When i click on any song it wont play just hangs..



any solutions please

---

### Post by art on 2006-01-18
To enable RealPlayer to play the files it's associated with, you need to do

sudo gedit /etc/mplayerplug-in.conf

and look for line saying 
#enable-rm=0(maybe 1)
 and change it to (uncomment)
enable-rm=0

Now RealPlayer will do it's job. You should also have linked all the plugins from RealPlayer directory to /opt/firefox/plugins. 
HTH

---

### Post by krypto_wizard on 2006-01-18
I didnt get the line 

#enable-rm=0(maybe 1)

What should I do now ? How to link realplayer plugins to firefox ?

I want to get this site [www.raaga.com/hindi](www.raaga.com/hindi) work at any cost.

My friends and me had a bet and they were saying that if Ubuntu can play this thing we will quit windows. I just want to get this thing working.

Please help me do that



[QUOTE=art]To enable RealPlayer to play the files it's associated with, you need to do

sudo gedit /etc/mplayerplug-in.conf

and look for line saying 
#enable-rm=0(maybe 1)
 and change it to (uncomment)
enable-rm=0

Now RealPlayer will do it's job. You should also have linked all the plugins from RealPlayer directory to /opt/firefox/plugins. 
HTH[/QUOTE]

---

### Post by art on 2006-01-18
Well, as for linking realplayer, just symbolic links all the plugins from RealPlayer/plugins directory to firefox/plugins (I am not sure about the paths. not at home right now, but something in those lines). I don't know if it will work though with that website...

---

### Post by Omnios on 2006-01-18
K I figuered it out, reallayer is based on Helix so I changed

 ```
#enable-helix=1
```

 to 

 ```
enable-helix=0
```

 It also counts how the web site you are visiting is set up as some have multi streams such as yahoo based news when you can configure media player or realplayer.

---

