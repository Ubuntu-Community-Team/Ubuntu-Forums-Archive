---
title: "Ut under dapper"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by hebus on 2006-07-08
Ok noob question 2 ... :p

i'm adicted to the good old ut :)

when i want it on another pc (running windows)$
I just needed to coppy the compleet ut map to it and i coud play it. 
(so no install needed :) )

Now i have donne it with my linux install also.

and i can run it using cvscedeag ;

But ... i got no sound and tyhe grafics looks bad.

---

### Post by livingtarget on 2006-07-08
If you got the disc you can play UT natively. All versions beside Unreal can, then again you can play Unreal maps through oldskool.

It takes a bit of trying but it's smoother then running it through cedega.

See attached screenshot, it starts full screen of course but just to show it's running Linux.

You can try this how-to if you don't find it too difficult:
[http://ubuntuforums.org/showthread.php?t=153181](http://ubuntuforums.org/showthread.php?t=153181)

Once you got it all set up the *.unr are the same as on windows, so if you have old maps you like on your windows machine then all you need to do is copy it over.

---

### Post by eqisow on 2006-07-08
You shouldn't be runing UT with cvscedega. UT has a native Linux port.

Edit: livingtarget beat me to it, and was much more informative. :)

---

### Post by Azzco on 2006-07-31
I'm also having some problems with UT.
I can't get it to run with the native linux install. I install it, browse over to the ut directory in home. Then I try to launch ut. This is how it looks like.
```
azzco@Home:~/ut$ ./ut
Signal: SIGIOT [iot trap]
Aborting.
azzco@Home:~/ut$ 
```

I don't want to use wine to play UT. :-( I guess that I'll have to dual boot if everything else fails, if I do that I can map aswell.:p  However I'm a bit sceptic about anything network related and windows in the same sentence.:lol:

---

### Post by Harleen on 2006-08-01
I don't own UT, but I know there's a problem when installing certain editions, that the maps aren't decompressed on installation. So you have to do it "by hand" afterwards. This script does that for you:

(taken from [http://www.holarse-linuxgaming.de/h2006/space/Unreal+Tournament](http://www.holarse-linuxgaming.de/h2006/space/Unreal+Tournament) - sorry, only in German)

```
#!/bin/sh
# set the following path to your UT-installation directory
#
INSTALLDIR=/usr/local/games/ut
cd $INSTALLDIR/System
for i in `ls ../Maps/*.unr.uz`
do
../ucc decompress ../Maps/$i -nohomedir
done
rm ../Maps/*unr.uz
mv *.unr ../Maps
echo "..:: Done! ::.."
```

---

### Post by Azzco on 2006-08-03
tried it but it seems that I had another problem...

---

### Post by User_Program on 2006-08-03
> **Azzco said:**
> I'm also having some problems with UT.
I can't get it to run with the native linux install. I install it, browse over to the ut directory in home. Then I try to launch ut. This is how it looks like.
```
azzco@Home:~/ut$ ./ut
Signal: SIGIOT [iot trap]
Aborting.
azzco@Home:~/ut$ 
```

I don't want to use wine to play UT. :-( I guess that I'll have to dual boot if everything else fails, if I do that I can map aswell.:p  However I'm a bit sceptic about anything network related and windows in the same sentence.:lol:


Do you have the drivers for you video card installed?  Also what version of UT are you installing (game of the year editor has a dif installer) .  If you can play other 3d games you can try renaming you UnrealTournament.ini and ut will write a new one.   it should be in .loki/ut/System 

Another thing you shouldn't have to got the the loki dir to launch ut in the console just type ut

---

