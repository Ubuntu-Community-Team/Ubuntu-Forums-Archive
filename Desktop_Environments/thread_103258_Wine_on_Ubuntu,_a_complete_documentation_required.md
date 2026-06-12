---
title: "Wine on Ubuntu, a complete documentation required"
date: 2005-12-13
forum: Desktop Environments
---

### Post by harisund on 2005-12-13
Hello

I was trying to get some websites to play music and simply couldn't get them to play in Firefox. Not surprising at all, since they don't play all the time even in Firefox running on Windows. 

I want to go the Wine way. Is there a good documentation out there which explains the basics to deal with wine? I know I did *apt-get install wine* and it installed it fine, and running *wine* created the configuration directories. 

Should I just go ahead, download the exe files of IE and RealPlayer and use Wine? Before that, I want to know (learn) how Wine handles the C:\\ etc kind of paths and My Documents and so on. 

I tried searching for Wine in the ever friendly Ubuntu wiki (where I read the awesome documentation on Apache / MySQL / PHP ) but couldn't find any. 

Do any of you know whether such a comprehensive documentation exists for Wine? If not, I would like to start writing one after I am done with the setup and get some apps working. 

Thanks !

Hari

---

### Post by Akya on 2005-12-13
wine just makes a new partion i think, or something to that extent, just go to your home folder and hit ctrl+h and it will show all the hidden folders just click on .wine and that should be self explanitory

---

### Post by dcstar on 2005-12-14
[QUOTE=harisund]
......
I want to go the Wine way. Is there a good documentation out there which explains the basics to deal with wine? I know I did *apt-get install wine* and it installed it fine, and running *wine* created the configuration directories. 
......[/QUOTE]
Go into Synaptic, put in "wine" as a search term and choose what you need.

---

### Post by harisund on 2005-12-14
Hmm..The problem is I don't have synaptic installed (I did an apt-get install xubuntu-desktop after a server install) and prefer installing my programs through the command line. 

But I guess I could still do a search of apt-cache search wine or dpkg -l wine*. Will try that out. 

Thanks.
Hari

---

### Post by harisund on 2005-12-14
[QUOTE=Akya]wine just makes a new partion i think, or something to that extent, just go to your home folder and hit ctrl+h and it will show all the hidden folders just click on .wine and that should be self explanitory[/QUOTE]
Thanks for that.. that was helpful.. didn't think of seeing the hidden folder at all.. and you are right, the hidden folder is more than self explanatory. 

Hari

---

### Post by kaamos on 2005-12-14
xubuntu-desktop installs synaptic.

Anyway if you want ie on linux theres a script for that. It does everything for you.. The homepage is [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

Worked great on my ubuntu.

---

### Post by harisund on 2005-12-14
xubuntu-desktop has synaptic? looks I have to do more searching then.. 

anyway, thanks for your script, but I am not really keen on having all the versions of IE. All I want is ie6 with real player and possibly windows media player support, so that I can stream online music from websites like [http:\\www.raaga.com](http:\\www.raaga.com), [http:\\www.musicindiaonline.com](http:\\www.musicindiaonline.com) and [http:\\music.yahoo.com](http:\\music.yahoo.com)

Which begs the question, do you know of any automated script that downloads and installs IE6, Media player support, RealPlayer  automatically? 

Thanks..
Hari

---

### Post by art on 2005-12-14
Here

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by Franko30 on 2005-12-14
Hi,

for me as a German User the new (redeveloped) Automatix script did the trick - no need to use IE via wine - everything works in Firefox (at least all the Real Player stupp and Flash etc. Didn't come across Windows Media stuff yet).

Automatix even has a GUI that lets you choose stuff before automatically installing it. :-)

If you understand German go to

[http://www.ubuntuusers.de/viewtopic.php?t=16639](http://www.ubuntuusers.de/viewtopic.php?t=16639)

Oh, I just found out that the English version can be found here:

[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)

Cheers

---

