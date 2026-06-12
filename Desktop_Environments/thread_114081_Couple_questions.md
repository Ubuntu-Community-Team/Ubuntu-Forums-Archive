---
title: "Couple questions"
date: 2006-01-07
forum: Desktop Environments
---

### Post by Deathvalley on 2006-01-07
so ok, i'm using wine for emulation program ( yeah i know it isn't emulator but i use that word), so i have this problem: [http://s27.yousendit.com/d.aspx?id=1JR2R49A818N90SOXG1TJKHR7J]("http://s27.yousendit.com/d.aspx?id=1JR2R49A818N90SOXG1TJKHR7J")
so there is on where should be text, there is squares on there, how i sould fix that?

and other prob. i use video watching program called vlc, it is good program thought
but why i can't hear voice of some of my wrestling and music videos?that just sucks watching wrestling without voice, thanks for help.

---

### Post by zoiks on 2006-01-08
[QUOTE=Deathvalley]so ok, i'm using wine for emulation program ( yeah i know it isn't emulator but i use that word), so i have this problem: [http://s27.yousendit.com/d.aspx?id=1JR2R49A818N90SOXG1TJKHR7J]("http://s27.yousendit.com/d.aspx?id=1JR2R49A818N90SOXG1TJKHR7J")
so there is on where should be text, there is squares on there, how i sould fix that?

and other prob. i use video watching program called vlc, it is good program thought
but why i can't hear voice of some of my wrestling and music videos?that just sucks watching wrestling without voice, thanks for help.[/QUOTE]

For wine, you are missing some font files.  They are files like arial.ttf and maybe a few other ttf files.  You can copy these from a windows installation.

---

### Post by Thirsteh on 2006-01-08
You can search for 'Arial font' on Google, and I'm sure you'll find it, and others.

Also, use MPlayer :)
sudo apt-get install mplayer
File->Right Click->Open with->MPlayer

---

### Post by Deathvalley on 2006-01-08
ok i tried to dl mplayer but it says like this: 

Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu... Valmis
Paketti mplayer on näennäispaketti, jonka kattaa:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
Yksi pitää valita asennettavaksi.
E: Paketilla mplayer ei ole asennettavaa valintaa

ok it is on finnish but last words are "packet of mplayer there isn't installion choice"
damn i know my english sucks and it is word to word to finnish english you know :P but when i find that font. where i should but that?

---

### Post by handy on 2006-01-08
If you install **WineTools**, from synaptic or from here:

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

It makes a really easy config' of Wine, installs M$ system files & fonts, plus options for a whole lot of other files.

I wouldn't install Internet Explorer, it has some problems, causes the screen to get messed up when you run DVDShrink !??

handy

---

### Post by Deathvalley on 2006-01-08
[QUOTE=handy]If you install **WineTools**, from synaptic or from here:

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

It makes a really easy config' of Wine, installs M$ system files & fonts, plus options for a whole lot of other files.

I wouldn't install Internet Explorer, it has some problems, causes the screen to get messed up when you run DVDShrink !??

handy[/QUOTE]

kind of stupid quoestion though, but i dl that package from that link and where i put those files now?

---

### Post by Thirsteh on 2006-01-08
[QUOTE=Deathvalley]ok i tried to dl mplayer but it says like this: 

Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu... Valmis
Paketti mplayer on näennäispaketti, jonka kattaa:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
Yksi pitää valita asennettavaksi.
E: Paketilla mplayer ei ole asennettavaa valintaa

ok it is on finnish but last words are "packet of mplayer there isn't installion choice"
damn i know my english sucks and it is word to word to finnish english you know :P but when i find that font. where i should but that?[/QUOTE]

Sorry, type 'sudo apt-get install mplayer-586'.

---

### Post by handy on 2006-01-08
[QUOTE=Deathvalley]kind of stupid quoestion though, but i dl that package from that link and where i put those files now?[/QUOTE]

Hi, before we get into tarballs, have you gone to the **_Menu:_  System/Administration/Synaptic Package Manager**  Select **Search** from the toolbar, & type into the search field in the little search box when it appears **winetools**  Synaptic will search & if it finds it you will see it in the right hand window, right click on **winetools** & select **Mark for Installation**  Then go to the **Synaptic Toolbar** & select **Apply**  It will then download (again, I know, it's not that big) WineTools & install it for you.  Synaptic is the easiest way to install packages.

So have a look if you haven't allready, if you have, or after having done the above, post here & we'll carry on. :p 

handy

---

### Post by Deathvalley on 2006-01-08
[QUOTE=Thirsteh]Sorry, type 'sudo apt-get install mplayer-586'.[/QUOTE]

i still don't know why i can't hear voice of the videos, i got the mplayer now, reminds me about bsplayer, but still no voice, only video.

---

### Post by Thirsteh on 2006-01-08
[QUOTE=Deathvalley]i still don't know why i can't hear voice of the videos, i got the mplayer now, reminds me about bsplayer, but still no voice, only video.[/QUOTE]

Hmm, do you have any audio at all (Ubuntu startup, etc.)? Maybe your sound drivers aren't even working. Try opening a console and type 'alsamixer'.

---

### Post by Deathvalley on 2006-01-08
[QUOTE=Thirsteh]Hmm, do you have any audio at all (Ubuntu startup, etc.)? Maybe your sound drivers aren't even working. Try opening a console and type 'alsamixer'.[/QUOTE]
i can listen music by XMMS player, it works really fine, and someof the videos have worked with voice on vlc but not all.


[QUOTE=handy]Hi, before we get into tarballs, have you gone to the Menu: System/Administration/Synaptic Package Manager Select Search from the toolbar, & type into the search field in the little search box when it appears winetools Synaptic will search & if it finds it you will see it in the right hand window, right click on winetools & select Mark for Installation Then go to the Synaptic Toolbar & select Apply It will then download (again, I know, it's not that big) WineTools & install it for you. Synaptic is the easiest way to install packages.

So have a look if you haven't allready, if you have, or after having done the above, post here & we'll carry on.

handy[/QUOTE]

yeah i have look for that synaptic package manager for it but didn't find it :I.

---

### Post by handy on 2006-01-08
Are you running the Gnome desktop?

handy

---

### Post by Deathvalley on 2006-01-08
[QUOTE=handy]Are you running the Gnome desktop?

handy[/QUOTE]
as you can see i'm noob with linux so i don't know what Gnome means :) can you tell me?

---

### Post by handy on 2006-01-08
OK, if you look up at the title bar of the screen, does it have written from left to right:

**Applications  Places  System**

Followed by some small icons?

handy

---

### Post by Deathvalley on 2006-01-08
[QUOTE=handy]OK, if you look up at the title bar of the screen, does it have written from left to right:

**Applications  Places  System**

Followed by some small icons?

handy[/QUOTE]

yeah it have

---

### Post by handy on 2006-01-08
[QUOTE=handy]Hi, before we get into tarballs, have you gone to the **_Menu:_  System/Administration/Synaptic Package Manager**  Select **Search** from the toolbar, & type into the search field in the little search box when it appears **winetools**  Synaptic will search & if it finds it you will see it in the right hand window, right click on **winetools** & select **Mark for Installation**  Then go to the **Synaptic Toolbar** & select **Apply**  It will then download (again, I know, it's not that big) WineTools & install it for you.  Synaptic is the easiest way to install packages.[/QUOTE]

So, use the above to look for synaptic, we are using those the System menu, out of those 3 that you just found in the title bar:

**Applications  Places  _System_**

**[Edit:]** By the way you are using the Gnome desktop manager = Ubuntu,  KDE desktop = Kubuntu.

See how you go...

handy

---

### Post by handy on 2006-01-08
Also, something that you really do need to be aware of is the **Help** available from the **System** **_Menu_**. 

It takes a while to adapt to Ubuntu (or any linux distribution) there is sooo much to learn, so give yourself a month of adapting, it will be much easier as a bit of time goes by & the learning gets easier. ;)

So many new users of Ubuntu seem to want to do too much too quickly, this causes a lot of stress, it can even make people feel bad about themselves.  There is no need for this, it is normal to take time to learn things. :KS 

handy

---

### Post by Deathvalley on 2006-01-08
[QUOTE=handy]Also, something that you really do need to be aware of is the **Help** available from the **System** **_Menu_**. 

It takes a while to adapt to Ubuntu (or any linux distribution) there is sooo much to learn, so give yourself a month of adapting, it will be much easier as a bit of time goes by & the learning gets easier. ;)

So many new users of Ubuntu seem to want to do too much too quickly, this causes a lot of stress, it can even make people feel bad about themselves.  There is no need for this, it is normal to take time to learn things. :KS 

handy[/QUOTE]


ok, thanks, well what i can say, i'm windows noob =D i have use it all my life and when i install ubuntu i was first totally out, but i try to make everything work, thanks.

---

### Post by handy on 2006-01-08
I've been at Ubuntu for about 5 weeks, & 2 of Debian before that.  I know how hard it is at first.  :rolleyes: 

It gets easier, the start is the hardest.

Here is another link, I really like the layout of this site, it makes it easy to find things, & easy to see all the topics.  I only found it tonight!  I'll go there first before I post questions in the future.  You have helped me find the following site, thanks. :smile: 

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Don't give up, it's worth it.

handy

---

### Post by Deathvalley on 2006-01-08
Still have a one quostion about mplayer, how i can but that video on bigger? if i took those "half size, full screen etc the picture stands a same you know, but the square on it just gets bigger, i don't know if you get what i was thinking on that but =D

---

### Post by Thirsteh on 2006-01-08
[QUOTE=Deathvalley]Still have a one quostion about mplayer, how i can but that video on bigger? if i took those "half size, full screen etc the picture stands a same you know, but the square on it just gets bigger, i don't know if you get what i was thinking on that but =D[/QUOTE]

Sorry, I knew it would come up and I should have said so earlier.

Smack up a console and do
sudo gedit /etc/mplayer/mplayer.conf

In this file, where it says
vo=x11,

Change that to
vo=xv,

Save and close.

Now try playing something and going fullscreen :)

Update: Actually I'm not sure if this works for the GUI version of mplayer, if it doesn't, try going into Options and see if there's anywhere where you can change the video output to "xv" X video or something similar. If nothing works, you can always use the CLI version of mplayer which is the one I prefer. Just "Open With.." a file, click the Custom Command button thingie and type in "mplayer" all in small letters, then use your arrows, space, and F to forward/rewind, pause and full-screen.

---

### Post by Deathvalley on 2006-01-08
[QUOTE=Thirsteh]Sorry, I knew it would come up and I should have said so earlier.

Smack up a console and do
sudo gedit /etc/mplayer/mplayer.conf

In this file, where it says
vo=x11,

Change that to
vo=xv,

Save and close.

Now try playing something and going fullscreen :)

Update: Actually I'm not sure if this works for the GUI version of mplayer, if it doesn't, try going into Options and see if there's anywhere where you can change the video output to "xv" X video or something similar. If nothing works, you can always use the CLI version of mplayer which is the one I prefer. Just "Open With.." a file, click the Custom Command button thingie and type in "mplayer" all in small letters, then use your arrows, space, and F to forward/rewind, pause and full-screen.[/QUOTE]


hmm i don't know, but still it is same o_O i did all the things you said :C. and btw the voice of videos works sometimes and sometimes not, pretty weird thought

edit: now it works :) thanks man for help o/

---

