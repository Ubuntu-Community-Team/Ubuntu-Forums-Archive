---
title: "qtcreator problem"
date: 2009-02-21
forum: General Help
---

### Post by mrga on 2009-02-21
hello i have downloaded qtcreator and everything is working fine except when i try to build and run project the compiler says this

No valid Qt version set. Set one in Tools/Options 
Error while building project Adresar
When executing build step 'QMake'
Canceled build.

i don't know what to do in tools options, i went there and i saw system Qt but under the path this is written 
the qt versions is not installed , run make install

so what should i do., thanks

---

### Post by edajai on 2009-04-02
i've got the same problem.
Do update here if u get the solution ;)

---

### Post by t3ht0m on 2009-04-05
I ran into the same problem with the qt-creator package in Jaunty. Installing the packages libqt4-dev and build-essential fixed it.

---

### Post by gramound on 2009-05-21
This symptom happened to me after:
[LIST]
[*]Installed (and used) Qt SDK from Nokia's website
[*]Installed qt-creator package
[*]uninstalled Nokia's Qt SDK
[/LIST]
The menu Tools->Options->Qt4->"Qt versions" showed the "/usr" autodetected version plus 2 invalid entries from the (uninstalled) Qt SDK.

I removed the 2 invalid entries, verified that the autodetected version was valid, selected it as the default version, clicked "apply" a few times, but it still said "No valid Qt version set."

I already had libqt4-dev, but reinstalling it did the trick.

---

### Post by jojo cs on 2009-07-07
I have the same problem plz help us

:(

---

### Post by akakingess on 2009-07-07
Are any of the suggestions that t3ht0m or gramound provided helping anyone, or do we need to continue looking into this?

---

### Post by jojo cs on 2009-07-08
[CENTER]^
^
^

C o n t i n u e[/CENTER]

---

### Post by jojo cs on 2009-07-08
the problem is solved 


thanks 
):P

---

### Post by abhilashm86 on 2009-07-08
actually even i first did direct download of qt from syaptic, but i could'nt work qmake and designer and editor din't sync each other, 
finally i downloaded qt sdk package which has Qt creator and designer and tutorials with help, works great, just executing .bin works Qt 4.5......check this

[http://www.qtsoftware.com/downloads](http://www.qtsoftware.com/downloads)

---

### Post by abhilashm86 on 2009-07-08
> **jojo cs said:**
> the problem is solved 


thanks 
):P

how you solved the problem?? please tell

---

### Post by jojo cs on 2009-07-08
> **edajai said:**
> i've got the same problem.
Do update here if u get the solution ;)

go to

Tool -> options -> Qt4

then look at the path I think there is invalid path 

remove it by pressing - sign

---

### Post by jojo cs on 2009-07-08
> **abhilashm86 said:**
> how you solved the problem?? please tell

open Qt creator

Tools-> options ->Qt4

check the paths I think there
is invalid path

then 

remove it

it was my problem

good luck
:)

---

### Post by Krzysztow on 2009-11-09
Hi all,

I had the same problem. As stated before, but maybe clearer... for laymen like me:
1) in QT Creator go to tools/options
2)unfold QT4 option and then check QT Versions
3)in the field QT Versions press add and find folder with qt installed files
4) then go to subfolder qtsdk-2009.04/qt/bin and press open button
5) select default QT Version into one added by You
6) apply changes

Now it should work. Hope this spares someone wasting his or her time.

---

### Post by 601 on 2010-01-06
The Tools->Options solution didn't work for me. I think there are differences depending on how you got/installed Qt. In my case I got the full development bundle (SDK+IDE) from Nokia website. 
What worked for me is a solution suggested earlier in the thread: install libqt4-dev (Synaptic package manager or 'sudo apt-get install libqt4-dev').
On a side note I was surprised to see such basic failures in the bundle version.

---

### Post by Vi-Maker on 2010-04-23
> **gramound said:**
> this symptom happened to me after:
[list]
[*]installed (and used) qt sdk from nokia's website
[*]installed qt-creator package
[*]uninstalled nokia's qt sdk
[/list]
the menu tools->options->qt4->"qt versions" showed the "/usr" autodetected version plus 2 invalid entries from the (uninstalled) qt sdk.

I removed the 2 invalid entries, verified that the autodetected version was valid, selected it as the default version, clicked "apply" a few times, but it still said "no valid qt version set."

i already had libqt4-dev, but reinstalling it did the trick.


thanks!!

---

