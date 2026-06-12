---
title: "Help with Wine"
date: 2006-07-09
forum: Desktop Environments
---

### Post by tonyp1969 on 2006-07-09
Hi I have installed the WINE Windows emulator, it is terrific I am sure. I have installed a game, however when trying to run the game from the shortcut or the CD-Rom I keep getting a message that the CD-ROM cannot be found, this was installed ok from there and I can browse the CD-ROm. 
Any help or recommendations very welcome.
Love the product. Top stuff.

Tony

---

### Post by Rackerz on 2006-07-09
Just wondering, what game is it?

---

### Post by tonyp1969 on 2006-07-09
Rollercoaster Tycoon 3

---

### Post by FredB on 2006-07-09
> **Rackerz said:**
> Just wondering, what game is it?

:lol:

To be sure your game is supported, look here :

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Thund3rstruck on 2006-07-09
I know this doesn't help you with your question but actually Wine stands for Wine is *not* an emulator.

---

### Post by ShiningHolden on 2006-07-09
Did you make virtual links to your CD-ROM Drive? Here's how.

```

ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
ln -s /media/cdrom0 ~/.wine/dosdevices/d\:

```

I can't ensure that /dev/hdc and /media/cdrom0 are the correct devices, so please do the following:
```

Insert the CD into your CD ROM drive.
Go to Places > Computer
Right Click the correct CD ROM drive.
Select mount the select volume.
Open a terminal
Type in 'df' without the ''.
Paste the results for me.

```

Then again, it may be.

Good luck with your game, This happened to me with War III. Once you do this, the link is always there and will never need to be done again. :)

---

### Post by FredB on 2006-07-09
> **tonyp1969 said:**
> Rollercoaster Tycoon 3

Kinda middle result :

[http://appdb.winehq.org/appview.php?iVersionId=3781&iTestingId=1228](http://appdb.winehq.org/appview.php?iVersionId=3781&iTestingId=1228)

All comments on it :

[http://appdb.winehq.org/appview.php?iVersionId=3781](http://appdb.winehq.org/appview.php?iVersionId=3781)

Stinks like crappy CD protection will give you a lot of problems.

> **Thund3rstruck said:**
> I know this doesn't help you with your question but actually Wine stands for Wine is *not* an emulator.

So, why did you answer that ? To make you rating higher ? ;)

Wine translate win32 code into linux code. A translator, in some way.

---

### Post by ShiningHolden on 2006-07-09
> **FredB said:**
> Kinda middle result :

[http://appdb.winehq.org/appview.php?iVersionId=3781&iTestingId=1228](http://appdb.winehq.org/appview.php?iVersionId=3781&iTestingId=1228)

All comments on it :

[http://appdb.winehq.org/appview.php?iVersionId=3781](http://appdb.winehq.org/appview.php?iVersionId=3781)

Stinks like crappy CD protection will give you a lot of problems.



So, why did you answer that ? To make you rating higher ? ;)

Wine translate win32 code into linux code. A translator, in some way.

ThunderStruck was just telling tonyp what WINE meant because tonyp called WINE an emulator and Thunderstruck was simply correcting him, saving him from humilation.

There shouldnt be any problems CD protection if the actual CD is in the actual CD ROM...?

---

### Post by Thund3rstruck on 2006-07-09
> 
So, why did you answer that ? To make you rating higher ?


No. In my experience, calling wine a windows emulator on most linux boards would be a mortal sin, I know this because I did the same thing on linuxforums.org years ago... this board is the most friendly and helpful I have ever been to.. I just wanted to point out that wine fact for the readers

---

### Post by FredB on 2006-07-09
I was just kidding. Indeed, Wine Is Not an Emulator ;)

But the result is nearly the same. And forget *assholes* who said it is a mortal sin to say Wine is an Emulator.

These kind of people are really the less interesting you will ever find in your whole life.

---

### Post by tonyp1969 on 2006-07-09
Thanks guys for trying to help, here is my df result

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             16737908   2731308  13156360  18% /
varrun                  778044       108    777936   1% /var/run
varlock                 778044         4    778040   1% /var/lock
udev                    778044       144    777900   1% /dev
devshm                  778044         0    778044   0% /dev/shm
lrm                     778044     18856    759188   3% /lib/modules/2.6.15-25-386/volatile
/dev/hdc                638468    638468         0 100% /media/cdrom
/dev/hdd               7808156   7808156         0 100% /media/dvdrecorder
tony@tony-desktop:~$


Hey, I didn't mean to offend anyone by saying that wine is an emulator, maybe I just logically thought that way as WINE = WIN + E (emulator)
There you go

---

### Post by tonyp1969 on 2006-07-09
Sorry I forgot to mention that it still doesn't work.

---

