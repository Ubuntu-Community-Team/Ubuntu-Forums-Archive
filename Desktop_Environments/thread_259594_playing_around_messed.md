---
title: "playing around messed"
date: 2006-09-17
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-17
playing edgy upgrade(trying to) I messed up package manager, actually repositorys says edgy now but there are no packages in there. Have I really gone to far??

---

### Post by nalmeth on 2006-09-17
bust out the terminal, and enter:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by DougieFresh4U on 2006-09-17
Password:
E: Malformed line 19 in source list /etc/apt/sources.list (dist parse)
dougie@ubuntu:~$ sudo apt-get dist-upgrade
E: Malformed line 19 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
I think I'm totaly lost.

---

### Post by nalmeth on 2006-09-17
Don't worry, it's not a show stopper.

Simply a malformed line in your sources.list. A mis-spelling or something.
Get that terminal open again, and enter:
```
sudo gedit /etc/apt/sources.list
``` Go to line 19, and if something is obviously mis-spelled, correct it. If you can't tell, just put ## at the start of the line.

Like:
## deb [http://archive.ubuntu.com/](http://archive.ubuntu.com/) ubuntu yada yada

```
sudo apt-get update
sudo apt-get dist-upgrade
``` OR 

you can post your sources.list if you don't know what to do with it:
```
cat /etc/apt/sources.list
```

---

### Post by DougieFresh4U on 2006-09-17
sorry, I don' really know what I am looking for so here's what came out of your last codeougie@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main rest ricted


deb-src [http://us.archive.ubuntu.com/ubuntuedgy](http://us.archive.ubuntu.com/ubuntuedgy) main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntuedgy-updates](http://us.archive.ubuntu.com/ubuntuedgy-updates) main restricted
deb-src [http://us.archive.ubuntu.com/ubuntuedgy-updates](http://us.archive.ubuntu.com/ubuntuedgy-updates) main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/edgy](http://archive.ubuntu.com/ubuntu/edgy) universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntuedgy](http://us.archive.ubuntu.com/ubuntuedgy) universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntuedgy-backports](http://us.archive.ubuntu.com/ubuntuedgy-backports) main restricted universe m ultiverse
deb-src [http://us.archive.ubuntu.com/ubuntuedgy-backports](http://us.archive.ubuntu.com/ubuntuedgy-backports) main restricted univer se multiverse

deb [http://security.ubuntu.com/ubuntuedgy-security](http://security.ubuntu.com/ubuntuedgy-security) main restricted
deb-src [http://security.ubuntu.com/ubuntuedgy-security](http://security.ubuntu.com/ubuntuedgy-security) main restricted

deb [http://security.ubuntu.com/ubuntuedgy-security](http://security.ubuntu.com/ubuntuedgy-security) universe
deb-src [http://security.ubuntu.com/ubuntuedgy-security](http://security.ubuntu.com/ubuntuedgy-security) universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restrict ed
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restrict ed
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restrict ed
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restrict ed
dougie@ubuntu:~$

---

### Post by DougieFresh4U on 2006-09-18
I have been messing alot w/computer today trying to get live cd (Edgy) just to see what it's like First I can not get the cd to boot, I burned 3 times w/differant speeds still nada now the good part, playing in repositorys & terminal I managed to gewt Edgy in my repos  list, but the system is still Dapper  and I have NO packs. in synaptic. I want to try and recover my system back to dapper origanal set-up as it was before today. Also, out of curiosity any one familiar with puppy linux??

---

### Post by nikhilk on 2006-09-18
You have just messed up the spaces in your sources.list file.
The line in your file
```
deb http://us.archive.ubuntu.com/ubuntuedgy-updates main restricted
```
should actually be
```
deb http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted
```
Note the space after "deb http://us.archive.ubuntu.com/ubuntu"
You must change every line which does not have the above mentioned space.

Also restricted, universe, multiverse are a single word (does not look like that in your post) so confirm that and change if required.

I hope you realize now the importance of making a backup of important files before you expirement with them :)

---

### Post by DougieFresh4U on 2006-09-18
Thank you, please can you see if I corrected and what do I do next,Please?deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/edgy](http://archive.ubuntu.com/ubuntu/edgy) universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universemultiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universemultiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universemultiverse

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universemultiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted     deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/edgy](http://archive.ubuntu.com/ubuntu/edgy) universe main restrictedmultiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricteduniversemultiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricteduniversemultiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricteduniversemultiverse

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricteduniversemultiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted

---

### Post by Najand on 2006-09-18
> # Ubuntu packages from CD-ROM
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted

# Ubuntu supported packages
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu supported packages
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Ubuntu community supported packages
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
It must work for you... Better not to add Dapper and Breezy sources in it.... Wow, you are doing great job... Linux for a family.... That sounds great to me.

---

### Post by nikhilk on 2006-09-18
> **nikhilk said:**
> Also restricted, universe, multiverse are a single word (does not look like that in your post) so confirm that and change if required.

Ok that was a VERY ambiguous sentence. What I meant was restricted, universe, multiverse are EACH one single word. I say this because they appeared like this in your post
```
deb http://us.archive.ubuntu.com/ubuntuedgy-backports main restricted universe m ultiverse
deb-src http://us.archive.ubuntu.com/ubuntuedgy-backports main restricted univer se multiverse
```

Sorry about the confusion caused. Thank you Najand for showing the right way to do it :)

Also I have never dealt with the CD-ROM thingy so maybe some else can help you with that. In the meanwhile you can just comment out the cdrom lines (by putting a ## at the begining of the respective lines) and see if the rest of the stuff works correctly.

---

### Post by DougieFresh4U on 2006-09-18
First I want to thank the two of you for your help (Nijand nikhilk) as one user on here had tried to discourage me away yesterday and I was kind of upset. please I do not even know where line 36 is or what I'm looking for and what does comment out mean in very simple laguage? also please have a look  and see line 36?? Thanks so much and we are learning here at home    ## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/edgy](http://archive.ubuntu.com/ubuntu/edgy) universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.-B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricte

---

### Post by nikhilk on 2006-09-18
Change the following lines and let us know if Synaptic (or aptitude, apt-get) work properly now.
```
deb http://archive.ubuntu.com/ubuntu/edgy universe main restricted multiverse
```
should be
```
deb http://archive.ubuntu.com/ubuntu edgy universe main restricted multiverse
```

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```
should be
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```
Note the absence of backslash after "deb http://archive.ubuntu.com/ubuntu"

Do the same for all the other lines describing the dapper packages viz.
"dapper-updates", "dapper-backports" and "dapper-security"

---

### Post by nikhilk on 2006-09-18
> **DougieFresh4U said:**
> please I do not even know where line 36 is or what I'm looking for and what does comment out mean in very simple laguage?
Sorry missed that first time around. The phrase "comment out" comes from the programming/scripting world.
In a very general sense commenting out a line means telling whoever reads the file to ignore that line.

So if you "comment out" a line in sources.list apt-get won't fetch anything from that corresponding repository.

---

### Post by DougieFresh4U on 2006-09-18
Thanks for clarrifiing that. I'm working on that list now going between 2 differant machines and Iwiil have it in a minute for you's

---

### Post by DougieFresh4U on 2006-09-18
ok, here is what I get now but I tried update and it says line 36 where ever that is   m:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubunt](http://archive.ubuntu.com/ubunt) edgy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.-B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted

---

### Post by nikhilk on 2006-09-18
You forgot to remove the backslash from the last three uncommented lines.

Change
```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
to
```
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
```

Change
```
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
to
```
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

Change
```
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted
```
to
```
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
```

Another point-
```
deb http://wine.budgetdedicated.com/aptedgy main
```
Are you sure this line is correct, if not comment out this line too and see if update works.

---

### Post by DougieFresh4U on 2006-09-18
some thing is still not right-- dougie@ubuntu:~$ sudo apt-get update
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
dougie@ubuntu:~$ sudo gedit /etc/apt/sources.list   # deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release  (i38620051012)]/edgy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubunt](http://archive.ubuntu.com/ubunt) edgy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.-B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://wine.budgetdedicated.com/aptedgy](http://wine.budgetdedicated.com/aptedgy) main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060915.1)]/ edgy main restricte

---

### Post by nikhilk on 2006-09-18
Just comment out the line
```
deb http://wine.budgetdedicated.com/aptedgy main
```
and see if it works now.

---

### Post by DougieFresh4U on 2006-09-18
this may sound stupid, but EXACTLY how or what do I do to comment out , remove the whole line or put ## in front of it or what, sorry

---

### Post by nikhilk on 2006-09-18
Just put ## in front of that line.

---

### Post by DougieFresh4U on 2006-09-18
You are the greatest in my linux world!! Where to next and does it look ok?  dougie@ubuntu:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [19.6kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [189B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release [34.7kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [19.6kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release [19.6kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [23.3kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [14B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [14B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [14B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [14B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [14B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [14B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources [276kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [49.1kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [71.4kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4269B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources [1426B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources [1056kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 195.248.90.23 80]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [6574B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [10.5kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 195.248.90.23 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 195.248.90.23 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
  404 Not Found [IP: 195.248.90.23 80]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages [14B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources [14B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages [14B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages [14B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages [14B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages [14B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources [14B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources [14B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources [14B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources [14B]
Fetched 1655kB in 1m14s (22.3kB/s)
Failed to fetch [http://archive.ubuntu.com/ubunt/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubunt/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 195.248.90.23 80]
Failed to fetch [http://archive.ubuntu.com/ubunt/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubunt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 195.248.90.23 80]
Failed to fetch [http://archive.ubuntu.com/ubunt/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubunt/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 195.248.90.23 80]
Failed to fetch [http://archive.ubuntu.com/ubunt/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubunt/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 195.248.90.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
dougie@ubuntu:~$

---

### Post by nikhilk on 2006-09-18
I guess it is pretty much alright. I can see there are errors regarding the edgy repository. Since I haven't enabled edgy repos I do not know about that, maybe someone who has can help you.

---

### Post by DougieFresh4U on 2006-09-18
Thank you so much for taking the time and effort, as it was appreciated!! "Peace" to You

---

### Post by nikhilk on 2006-09-18
I am glad I could be of help :)

---

