---
title: "HELP me before I quit"
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by VEGAMO on 2007-07-05
Ok so I am the kind of guy that doesn't have much patience.

Yesterday I've been seeing how people just love to bash windows just for the hell of it, I tried to defend it but NOOOO.

So anyway I decided to try Linux Ubuntu (which they have been worshipping), I installed it on my computer and it's running fine :)

HOWEVER, I need to run Windows programmes, which is how I learned about this *Wine* software 

I go download Wine from the main site version 9.40? I think? and double click on the package to install.

The thing started installing then stopped and said *ERROR: Conflicts with installed package 'Wine-doc'*

Ok so as I remember from using windows since child hood, I am supposed to find Wine-doc and remove it, HOWEVER I CAN"T FIND IT!!!!! 

Going OUT OF MY MIND!

I would be greatfull if someone helps me here or else I guess ubuntu is a waste of my time.

---

### Post by doh224 on 2007-07-05
what version of ubuntu do you have?

---

### Post by hikaricore on 2007-07-05
Exactly what ***dows software are you trying to run.

You may want to see if it works under wine first:  [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by doh224 on 2007-07-05
to get wine try typing this in the terminal:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

and then:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

and then:

sudo apt-get update

and then:

sudo apt-get install wine

then you should have wine....

---

### Post by jimbob on 2007-07-05
I do not see anything named wine-doc on my system.  Try entering *[COLOR="Blue"]sudo apt-get remove --purge wine-doc[/COLOR]* in a terminal window and see what it comes up with.

How did you try to install wine - from Synaptic?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by VEGAMO on 2007-07-05
> **doh224 said:**
> what version of ubuntu do you have?

I downloaded *Ubuntu 7.04 - Supported to 2008*

and im trying run AIM and Diablo 2 (and some diablo 2 maphack software)

---

### Post by bigken on 2007-07-05
> **jimbob said:**
> I do not see anything named wine-doc on my system.  Try entering *[COLOR=Blue]sido apt-get remove --purge wine-doc[/COLOR]* in a terminal window and see what it comes up with.

How did you try to install wine - from Synaptic?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR=Red][SIZE=1]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

its **sudo**

---

### Post by doh224 on 2007-07-05
> **VEGAMO said:**
> I downloaded *Ubuntu 7.04 - Supported to 2008*

and im trying run AIM and Diablo 2 (and some diablo 2 maphack software)

then this is the perfect guide for you then:

[http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo](http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo)

-doh

---

### Post by bigken on 2007-07-05
if you list the windows applications you want to run the people here will tell the linux equivalents if there are any

---

### Post by Drate on 2007-07-05
If you strictly want to remove a given file from your system... from a terminal session type: sudo locate *filename*

(it will ask for a password)

then type: sudo rm */complete/path/filename*

---

### Post by hikaricore on 2007-07-05
Is there a specific function of AIM that you need or do you just need a messenger that connects to the AIM network?

There are several alternatives such as Pidgin (formerly GAIM).

GAIM should be in the repos, you can find pidgin here if it hasn't been added yet to the ubuntu repos:  [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

---

### Post by VEGAMO on 2007-07-05
> **hikaricore said:**
> Is there a specific function of AIM that you need or do you just need a messenger that connects to the AIM network?

There are several alternatives such as Pidgin (formerly GAIM).

GAIM should be in the repos, you can find pidgin here if it hasn't been added yet to the ubuntu repos:  [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

oh yeah? alright thanks.

well I can't really find the damn Wine-doc, but at least we got the AIM out of the way.

---

### Post by hikaricore on 2007-07-05
Someone already linked you a guide to installing Diablo II:

> **doh224 said:**
> then this is the perfect guide for you then:

[http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo](http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo)

-doh

If you need more info on WINE read the man pages:

```
man wine
```

Or goto the official WINE website: [http://www.winehq.org](http://www.winehq.org)

---

### Post by VEGAMO on 2007-07-05
ok I am connected to AIM by GAIM, thanks.

Now about WINE lol :) IDK man confusing crap to me hhaa, sorry about that. 

I mean I see links and everything it's just like chinese to me.

By the way:

There is a command letter I didn't understand, it looks like this * l *   im sure it's not an L tho or an i.

---

### Post by mytwobears on 2007-07-05
Why don't you just open up the synaptic package manager, then click on the search button, then type in "wine" without the quotes, then click ok.  It will search and locate all the files with wine in the name or description.  

Scroll through the list and find the file you need to remove.  Click on the small box in front of the file, then mark it for complete removal and then click the apply button and synaptic will remove it from your system.

You can then go ahead and install the wine package you are trying to install.

---

### Post by VEGAMO on 2007-07-05
OK So I got everything working.

now it's asking me to figure out what is the name of the CD drive that I have the CD in.

How do I know that?

---

### Post by hikaricore on 2007-07-05
I'm going to go out on a limb here and guess that very little planning when into you installing Ubuntu.

We can't do everything for you, and you're expected to know atleast a little about your computer vegamo.

---

### Post by VEGAMO on 2007-07-05
> **hikaricore said:**
> I'm going to go out on a limb here and guess that very little planning when into you installing Ubuntu.

We can't do everything for you, and you're expected to know atleast a little about your computer vegamo.

errr ok.

---

### Post by VEGAMO on 2007-07-05
Wait I think you didn't understand me.

Right now I am just trying to install Diablo 2, I got wine working from the terminal, I just don't know what is the method to find the *NUMBER* of the Drive the Diablo 2 CD is in.

I have a CD-RW and a DVD-Read only.

---

### Post by hikaricore on 2007-07-05
Well it depends on your system to be honest.

In linux drives are known as /dev/???? or as UUIDs

If you had only one hard drive with only one partition it would likely be:

/dev/hda1

or

/dev/sda1


Making your cdrom drives:

/dev/hdb
/dev/hdc

or

/dev/sdb
/dev/sdc

There are many topics around this forum that could explain the names of your drives better than I can on the spot like this, perhaps you should search around for something a little more thorough.

---

### Post by Nehvrook on 2007-07-05
When you put the CD in does it not mount and put an icon on the desktop? If not try looking in /media/Diablo 2

---

### Post by mytwobears on 2007-07-07
Type:

sudo lshw

into the terminal.  This will give you a listing of all your hardware with their names and addresses.  Just scroll through the list until you find your CD player.

---

### Post by Contrast on 2007-07-07
I'm not sure exactly what step you're at in getting Diablo II installed. Are you following the tutorial found [here]("http://appdb.winehq.org/appview.php?iVersionId=49")? From my experience, any program you're trying to install under WINE that has a rating of gold or platinum shouldn't give you any problems, assuming you very closely follow the directions.

Not to lecture or anything, but as someone else here stated, you would do well to try researching your problem a little bit before asking others for help. It's hard for us to know where to start when you haven't already started yourself. ;-)

---

