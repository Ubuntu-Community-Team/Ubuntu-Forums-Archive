---
title: "MP3 encoding with Grip"
date: 2005-03-12
forum: Desktop Environments
---

### Post by niels on 2005-03-12
I have just installed Grip (think Sound Juicer wasn't good enogh). The problem is, that I can't encode my ripped files as mp3's. I have installed lame, but Gripper tells me, that there is some problems.
Wat van i do?

Niels

---

### Post by lorap on 2005-03-12
hi!
i'd also troubles until installed "xmms" cool looking and goog working player.
install it from synaptic and let mo know.
to find it out fast press on the search button write "xmms" choose the option "names and descriptions" and press ok.
pavel

---

### Post by keyshawn on 2005-03-12
Hello lorap and niels, 

As lorap suggested, i'd recommend getting xmms installed as well. I believe it might require some libraries that would get grip to work. 
If you're still having problems, describe the error message in greater detail to us. 
You could try to take a screenshot of the error message as well.

good luck,
keyshawn

---

### Post by niels on 2005-03-14
[QUOTE=keyshawn]Hello lorap and niels, 

As lorap suggested, i'd recommend getting xmms installed as well. I believe it might require some libraries that would get grip to work. 
If you're still having problems, describe the error message in greater detail to us. 
You could try to take a screenshot of the error message as well.

good luck,
keyshawn[/QUOTE]

I installed XMMS before Grip - so it's there...

I have attached screenshots of the error message I get and the encoding config.

Niels

---

### Post by keyshawn on 2005-03-14
go to the command line and type in:  ```
which lame
``` 
If it returns to you no results, then you don't have lame installed at all. 
Then, go to the synaptic manager and search for lame. It's most likely not even installed at all. Then, just install it and you should be good to go. 

If you had something that returned when you typed in the command,
then change the 'encoder executable' to match the result that you got.
Hope that helps.


regards,
keyshawn

---

### Post by carlc on 2005-03-14
I believe you have to install both liblame0 and gstreamer0.8-lame

---

### Post by jangjing on 2005-03-14
Hi Niels,

You have to write /usr/local/bin/lame  at encoder executable. 

regards Jan G

---

