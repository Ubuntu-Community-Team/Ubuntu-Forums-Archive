---
title: "Using KDE 3.3.2 over KDE 3.4"
date: 2005-10-09
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-09
Hello. I am new to Ubuntu, just moved here from Mepis. I am using Kubuntu 5.04. I was wondering how I could change my KDE from version 3.4 to KDE 3.3.2? I have never tried to apt-get install a program to "downgrade" it to a lower version, only upgrade. Help would be greatly appreciated.

---

### Post by GeneralZod on 2005-10-09
I hate to say this, but KDE is so big and complex that this might be more trouble than it's worth! :)

Just out of interest, what don't you like about 3.4? Fixing these issues will probably save you more headaches than attempting to downgrade.

---

### Post by tseliot on 2005-10-09
I guess you can't unless you decide to compile it from scratch (you can follow the instructions on the KDE website).

BTW why do you want to do that? I think you should upgrade to 3.4.2 instead (in which many bugs which affected 3.4.0 have been fixed)

If you want to upgrade to 3.4.2 you can follow these steps:

1) Open Konsole and type:
sudo kate /etc/apt/sources.list (you can also use "nano" instead of "kate")

2) add the following line to the end (or wherever you wish) of the document:

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

Save the document and exit.

3) Open Kynaptic and press the "Mark all upgrades" button (select Smart upgrade if it asks you) and the the "Apply" button.

And enjoy your KDE 3.4.2

---

### Post by SadaraX on 2005-10-09
Well stability really is the issue. I suppose upgrading to a newer version (such as 3.4.2) is probably the only real course I can take. I generally preferred a few things in version 3.3.2 over the 3.4 series, in which some of my favorite features were effectively removed. :(

Eitherway, if you claim its more stable, then I shall go with it. Actually, using the unstable KDE version and the lack of default root passwords are thus far the only complaints I have against kubuntu, which is saying quite a lot.

---

### Post by Freddy on 2005-10-09
Kubuntu has never used the unstable version of KDE by default, version 3.4.0 was consider a stable version. There are of course repos for installing the unstable version of 3.5 but that's only for testing purposes.

About downgrading, no that's not a good idea, it's hard and probally impossible to get and remove all the lib packages and dependecies of the 3.4, and you would have to do that for a downgrade. I tried to downgrade from 3.5 beta back to 3.4.2 which just left me in a real mess.   /// Freddan

---

### Post by tseliot on 2005-10-09
[QUOTE=SadaraX]Well stability really is the issue. I suppose upgrading to a newer version (such as 3.4.2) is probably the only real course I can take. I generally preferred a few things in version 3.3.2 over the 3.4 series, in which some of my favorite features were effectively removed. :(

Eitherway, if you claim its more stable, then I shall go with it. Actually, using the unstable KDE version and the lack of default root passwords are thus far the only complaints I have against kubuntu, which is saying quite a lot.[/QUOTE]
I've tried 3.3.2 in Linspire and it didn't seem too stable: I had several messages of KDE crashes. Same thing with 3.4.0. The number of warnings has decreased dramatically in 3.4.2 (at least for me).

---

### Post by SadaraX on 2005-10-09
[QUOTE=Freddy]Kubuntu has never used the unstable version of KDE by default, version 3.4.0 was consider a stable version. There are of course repos for installing the unstable version of 3.5 but that's only for testing purposes.[/QUOTE]

Hmm, seems like it would be true. 

[QUOTE=tseliot]I've tried 3.3.2 in Linspire and it didn't seem too stable: I had several messages of KDE crashes. Same thing with 3.4.0. The number of warnings has decreased dramatically in 3.4.2 (at least for me).[/QUOTE]

I can say this, I have used 3.3.2 for a many months now and had it (konquorer) crash about 6 or 7 times. Since I installed KDE 3.4.0 yesterday, I have had konquorer crash more than 15 times in the last 24 hours.

---

