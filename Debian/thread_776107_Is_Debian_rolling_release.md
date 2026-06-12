---
title: "Is Debian rolling release"
date: 2008-04-30
forum: Debian
---

### Post by MONODA on 2008-04-30
I have been thinking about trying out debian with kde but would first like to know somethings about it's releases. Is Debian rolling release like arch? if so, what is the command for upgrading the packages. also if I install the kde version with 3.5, once kde 4 is added to the repos, will it upgrade to that if I run the upgrade command? thanks

---

### Post by dptxp on 2008-04-30
If you want cutting-edge rolling release, go for SIDUX.It is Debian sid, made stable.
KDE4.0 has problems.

---

### Post by MONODA on 2008-04-30
so is debian rolling release? I realize that kde4 has problems, I was just trying to use an example.

---

### Post by Vorian Grey on 2008-04-30
Debian is broken up a little differently than most distros. If you use stable, then you can do most of your uograding when the newest release comes out. For example, Etch is the latest and Lenny is suppose to be released this fall. There are backports, of course, but not everything makes it in there.

Testing is the next level down. It is definitely rolling release if you leave your sources at testing. Lenny is in testing right now and it's in a soft freeze. After Lenny is released, a new version will begin testing. It has the latest but it has been subjected to certain tests before it makes it into this level. 

Under that is Sid, or unstable. it'as not as bad as all that and you do get the leatest of everything. It is rolling release. You can't install Sid, you can only upgrade to it. Personally, if I wanted to use Sid I would give sidux a try. it's very cool. 

The command to upgrade is aptitude full-upgrade of apt-get dist-upgrade, depending on what you use. Debian now recommends aptitude.

I think KDE 4 is in experimental, the level down from Sid. The minute it gets into Sid you can upgrade. If you are brave you probably could pull it out of experimental now, as you can mix your sources, but I wouldn't recommend it.

---

### Post by MONODA on 2008-04-30
thanks ill try out sidux.

---

### Post by MONODA on 2008-04-30
alright i am downloading sidux, I am downloading the lite version, what is the difference between that and the full?
EDIT: also is the only difference between sid and sidux that you can install sidux?

---

### Post by markharding557 on 2008-04-30
the full version has more apps preinstalled.
in answer to your earlier query sid and therefore sidux and testing are rolling releases stable is not.
sidux is debian sid with some extra scripts and other goodies which make it easier to install and maintain.
also sidux is a live cd,debian sid itself can only be installed as an upgrade from testing and there are no live cd editions of debian

---

### Post by dptxp on 2008-05-01
The Lite sidux does not have open office or Gimp. You can add them. Go through sidux manual. Install using apt-get only.
sidux installs real fast, boots fast and runs fast.

---

### Post by MONODA on 2008-05-01
> The Lite sidux does not have open office or Gimp. You can add them. Go through sidux manual. Install using apt-get only.
 sidux installs real fast, boots fast and runs fast.
sweet, thanks this is exactly what I need, im burning the iso now. (man I love linux XD)

---

### Post by MONODA on 2008-05-01
wait one last question before I install sidux, is it stable? (I realize that it is sid unstable but is it usable or should I expect it to crash every now and then?) thank you

---

### Post by jdhore on 2008-05-01
> **MONODA said:**
> wait one last question before I install sidux, is it stable? (I realize that it is sid unstable but is it usable or should I expect it to crash every now and then?) thank you

It probably won't crash very often, but figure that something will horribly break at least once every 6 month-1 year...This is why i run Testing...Stuff in testing almost never breaks

---

### Post by MONODA on 2008-05-01
oh, that sucks... Then I guess I wont be using sidux or any other debain release, thanks anyway, I will look for another OS.

---

### Post by jdhore on 2008-05-01
> **MONODA said:**
> oh, that sucks... Then I guess I wont be using sidux or any other debain release, thanks anyway, I will look for another OS.

No, go with Debian Testing, It's extremely stable (moreso than Ubuntu), it is rolling-release, it's pretty damn up-to-date and i've been running it for at least 3-4 years and could not be happier.

---

### Post by MONODA on 2008-05-01
is lenny rollinf release as well? does it have OOo 2.4 yet?

---

### Post by jdhore on 2008-05-01
> **MONODA said:**
> is lenny rollinf release as well? does it have OOo 2.4 yet?

It is rolling release (as i just said), it's running on OpenOffice 2.4, kernel 2.6.24, parts of GNOME 2.22 and 2.20 (though most is 2.22), KDE 3.5.9, Xorg 7.2...That's all i can think of off the top of my head (i know version numbers of almost every package that's important, but those are the only important ones i could think of)

---

### Post by MONODA on 2008-05-01
ok thanks for your help, one last question, can I upgrade from debian stable to testing? thanks.
EDI: Never mind, I was asking thins because I already have the stable cds with gnome but I want kde instead.

---

### Post by MONODA on 2008-05-01
what is the difference between:
beta1 installer
weekly build
daily build 
for lenny? I dont know which one to download

---

### Post by SunnyRabbiera on 2008-05-01
Also if you like debian sid there is Mepis too

---

### Post by dptxp on 2008-05-01
Try sidux. make "fromiso" installation first on any partition (ext3), not full. No need to burn CD, you just need iso file. You just need to create a directory in the partition. Boot "fromiso".
Check sidux manual. You will be impressed with sidux.It is my regular OS.

---

### Post by Vorian Grey on 2008-05-01
> **jdhore said:**
> No, go with Debian Testing, It's extremely stable (moreso than Ubuntu)
That hasn't been my experience. Things will break in testing as well. Maybe not frequently, but it does happen.

---

### Post by MONODA on 2008-05-01
> Try sidux. make "fromiso" installation first on any partition (ext3), not full. No need to burn CD, you just need iso file. You just need to create a directory in the partition. Boot "fromiso".
Check sidux manual. You will be impressed with sidux.It is my regular OS.
i am reconsidering sidux, but first is it stable? how often do things break?

---

### Post by Vorian Grey on 2008-05-01
sidux almost never breaks. Sid sometimes breaks and you'll see warnings on the sidux site telling it's users not to upgrade at this time or to hold certain packages. If you run the smxi script to upgrade, there is a good chance you'll never see any breakage. 

But there is always the potential of something breaking. You have to be alert and not just blindly update. Sometimes an update might want to remove most of KDE, for example. That is because certain packages are in transition. If you wait a day or two and then update everything will be fine.

Just be aware that it is stable but something could happen.

---

### Post by dptxp on 2008-05-01
You can download updates and put on hold for a couple of days (2/3). If you see no warnings in sidux forums, execute the update.

Upadates can create problems with any distro.
I have installed sidux to HDD, but retained "fromiso" install. Can help at times.

If you try different distros, keep a Puppy Linux Cd with you. Comes handy if you can not boot or X fails - you can edit/restore files.

---

### Post by MONODA on 2008-05-01
thanks for the advice, but i always use system rescue cd for rescuing :D.

---

### Post by markharding557 on 2008-05-01
> **MONODA said:**
> ok thanks for your help, one last question, can I upgrade from debian stable to testing? thanks.
EDI: Never mind, I was asking thins because I already have the stable cds with gnome but I want kde instead.

yes you can upgrade from debian stable to testing(lenny)and from there if you wish to sid,also if you add sidux repositorys you can covert it to sidux from sid

---

### Post by MONODA on 2008-05-03
alright well i installed lenny with kde and already my bluetooth is broken :'( I am having lots of trouble with the package managment, I keep getting errors that I never got in ubuntu...

---

### Post by jdhore on 2008-05-03
> **MONODA said:**
> alright well i installed lenny with kde and already my bluetooth is broken :'( I am having lots of trouble with the package managment, I keep getting errors that I never got in ubuntu...

Right now, i'm using Bluetooth with Lenny just fine (my KB/Mouse and my headset is bluetooth) and i haven't had or heard about any "package management issues"...What package management issues do you speak of?

---

### Post by MONODA on 2008-05-03
I kept in getting errors like:
broken packages
broken dependencies
no installation candidate
etc

---

### Post by markharding557 on 2008-05-03
try apt-get dist-upgrade

---

### Post by RedSquirrel on 2008-05-08
> **Vorian Grey said:**
> You can't install Sid, you can only upgrade to it.

I use the "business card" image to install Debian. You can install sid if you boot the installer in _expert_ mode. ;)

---

