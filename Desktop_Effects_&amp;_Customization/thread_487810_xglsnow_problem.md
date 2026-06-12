---
title: "xglsnow problem"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by tetsura on 2007-06-29
firstly, just wanna say that i absolutely LOVE compiz fusion. it makes me cry when i have to log back in winXP now :'(.

anyways back to the point, everythings workin great but the snow plugin isnt working for me, and in the settings for xglsnow the images just show up as little squares with 1's and 0's in? (screenshotted below)

[[IMG]http://img92.imageshack.us/img92/5529/snowky4.th.png[/IMG]](http://img92.imageshack.us/my.php?image=snowky4.png)


if anyone could help me out i'd really appreciate it ;)

---

### Post by hyperair on 2007-06-29
Firstly, please get it straight. It's not XGL Snow. It's just Snow. Or Compiz Fusion Snow or Beryl Snow if you wish. XGL doesn't give you any great graphic. You're still going to need Beryl/Compiz/Compiz Fusion whether or not you use XGL.

Secondly... The boxes with the numbers in them mean nothing. You can remove them. You can also add your own images in place of them to be used as snowflakes

---

### Post by pt123 on 2007-06-29
If you had beryl try and find the flakes from there & the settings. 

/usr/share/beryl

Default one is snowflake2.png


Attached are some I found win a beryl plugin tar file but have forgotten where I got it from.

---

### Post by hyperair on 2007-06-29
Beryl's snowflakes are in the directory /usr/share/beryl when beryl-plugins-data is installed.

---

### Post by tetsura on 2007-06-30
k sorry yeh, it's xsnow not xglsnow
i found the beryl snowflakes in that directory and added those but i still just get white squares :(

any ideas? thanks for the help so far

---

### Post by hyperair on 2007-06-30
Enable the png plugin in CompizConfig Settings Manager.

---

### Post by tetsura on 2007-06-30
yeh it already is
still not working though :(

---

### Post by hyperair on 2007-06-30
Ok... try restarting CompizConfig Settings Manager and Compiz and see if the settings stick. I know that for the gconf backend of the CompizConfig Settings Manager, it has some problems, whereby some settings won't stick.

---

### Post by TXBDan on 2007-06-30
i'm working on the same exact problem. its for my gf's computer i swear :P

png are enabled and i have the full path and filename to my snowflake2.png added as a texture. still just white squares.

also if i close and reopen the snow settings, the path/filename to the texture is replaced w/ the little square w/ the 1/0s.. is it not sticking?

---

### Post by tetsura on 2007-06-30
yeh iv tried logging in and out, or restarting pc, still no luck. is it supposed to have those box's with the 1's and 0's in?

---

### Post by samurailink3 on 2007-07-01
Same for me... where is the config file located? I'm just gonna change it by hand...

---

### Post by hyperair on 2007-07-02
It really depends. If your CompizConfig Settings Manager backend is the flat-file backend, then it's at ~/.compizconfig/YOURPROFILE.ini

If your backend is gconf then you must use the Configuration Editor and go to /apps/compiz instead.

Actually I'd recommend you to just abandon the gconf backend, set your backend to the flat-file backend, and then do whatever changes you need to your system. I found the gconf backend to be slightly unresponsive.

---

### Post by tetsura on 2007-07-03
how do u edit it if the backend is gconf?
i dont think i want to redo all the settings i had before if i change it to a flat file hehe

thanks

---

### Post by hyperair on 2007-07-03
it's in CCSM. On the left panel, look for something called Backend & Profile or something of that sort. Click on that, then change your backend from gconf to flat file.

---

### Post by skymera on 2007-07-03
ok i got tyhe exact same problem!!
white sqaures.

got beryls directory and box with 1 and 0.
hummmm

---

### Post by skymera on 2007-07-03
ok i changed to flat file, it stuck!!
but still square.

---

### Post by hyperair on 2007-07-03
Could you show me a screenshot of that? And you're not supposed to put the directory, you're supposed to put the path of each FILE. For example: /usr/share/beryl/snowflake.png or something of that sort. Not /usr/share/beryl.

---

### Post by skymera on 2007-07-03
flat file here it is 
snow settings

but still the problem of them being square

---

### Post by hyperair on 2007-07-03
Uh if you dragged the file into the dialog that popped up for adding the paths, you have to remove the last character, which I think is invisible. I don't see any 1's and 0's though.

---

### Post by tetsura on 2007-07-03
i wrote out the paths aswell, didn't drag and drop. and about the 1's and 0's, it goes like that when u go out of the snow config and then back in again, like my original screenshot.

---

### Post by FuturePilot on 2007-07-03
Check the box that says "Snow Over Windows"
That worked for me.

---

### Post by hyperair on 2007-07-03
So you're using the flat file backend and the settings won't stick? Make sure you have the Inotify plugin and Dbus plugin checked.

---

### Post by tetsura on 2007-07-04
thanks futurepilot but it didnt work for me :(

yeh i hav those enabled. i dont think theres anything else to try, i'd try reinstalling compiz but i don't wanna risk screwing it up seeing as it works perfectly at the moment hehe (apart from the snow anyway lol)
thanks for the help, i guess il just learn to live without it :P

---

### Post by saxin on 2007-07-04
I had the same issue, but got some help from joost_ and isthatall on #compiz-fusion on freenode and now it works great! 
First I went into the: compiz config settings manager - backend & profile - here I changed Backend from GConf Configuration Backend to Flate-file Configuration Backend. I then started compiz-fusion with
```
compiz --replace ccp --sm-disable
``` and started the snow and now everything is working :D
[IMG]http://img441.imageshack.us/img441/9374/snowjx2.png[/img]

---

### Post by tetsura on 2007-07-04
awesome! thanks saxin that totally worked! ^_^

---

### Post by TXBDan on 2007-07-05
hrm when i go to back end to change from gconf to flat, the setting doesnt stick.. ? can i edit a file somewhere?

Thanks

---

### Post by tetsura on 2007-07-06
not sure, i just redid all my settings :s

---

### Post by matt_evans on 2007-11-15
thanks saxin- that worked right away.:)

Would you mind posting your background?

---

