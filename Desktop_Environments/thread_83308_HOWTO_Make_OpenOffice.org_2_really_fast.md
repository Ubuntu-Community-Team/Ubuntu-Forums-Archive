---
title: "HOWTO: Make OpenOffice.org 2 really fast"
date: 2005-10-28
forum: Desktop Environments
---

### Post by magnusbb on 2005-10-28
To make a perfect OpenOffice.org on your Breezy system, I've got a few tips.

First, upgrade your current beta version to the 2.0 final release by adding this repository to your /etc/apt/sources.list:

deb [http://people.ubuntu.com/~doko/OOo2 ./](http://people.ubuntu.com/~doko/OOo2 ./)

Then sudo a apt-get update and upgrade, and watch it download...

Then follow these speed tips published today at The Inquirer:

Goto Tools -> Options > Memory.
Increase graphics cache to 64 MB and memory per object to 8 MB.

Exit and restart OpenOffice a couple of times (it takes a few openings before it helps).

It's also important to have the correct version of Java installed. OpenOffice uses Java for a few things in version 2, and the GNU version of Java bundled with Breezy will slow it down. Download the original Java from Sun, and enable it in the Java tab under Tools -> Options.

---

### Post by mangoshake on 2005-10-28
[QUOTE=magnusbb]
Again, goto Tools -> Options and then click on the Java tab. Make sure that it's turned off. It really slows down OpenOffice.[/QUOTE]

Just curious, what role does Java play in OpenOffice? Following that, what effects does it have to turn Java off?

---

### Post by anderss on 2005-10-28
Aptitude is complaining about that repository not being valid or something (it returns an error at the line of where I added the repository you wrote)

---

### Post by magnusbb on 2005-10-28
Sorry for the wrong link, there was a minor mistake at the end of the line, it's now corrected.

---

### Post by coldrick on 2005-10-28
Don't know what Java you were using that made you say that Java really slowed oOo down, but I notice no performance problem with the standard Sun JRE (1.5.0_05). If you go to Tools\Options, note that the default appears to be to use gcj, which I'd avoid as much as possible: it certainly seems to have some compatability problems.

If you need help in installing Java, take a look at [http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part).
That installs the jdk (and the jre) - installing just the jre is pretty straightforward.

And you're quite right about the speed increase if you set memory parameters correctly: very impressive! Thanks for the tip.

Regards,
David

---

### Post by magnusbb on 2005-10-29
Thanks for your reply. I believe you're right! I changed from the standard GNU Java to the one from Sun, and now OpenOffice works great even with Java. 

I have changed parts of the tip.

---

### Post by DavidTangye on 2005-10-29
Putting "deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./" in /etc/apt/sources.list gives the following error in Synaptic -

"Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)"

What is the correct line? Shouldn't it end with 'universe' or something?

---

### Post by magnusbb on 2005-10-29
Well, that's very strange. Try to click on the link in your browser, and you'll surely see the packages there.

---

### Post by DavidTangye on 2005-10-29
[QUOTE=magnusbb]Well, that's very strange. Try to click on the link in your browser, and you'll surely see the packages there.[/QUOTE]

Yes, I see them... but what is the correct syntax for /etc/apt/sources.list?

---

### Post by cjazz on 2005-10-29
The above line in sources.list worked fine for me.

P.S. I should add that I didn't use synaptic. I followed with "sudo apt-get update" and "sudo apt-get upgrade" from a terminal.

---

### Post by davidsrsb on 2005-10-30
I noticed a significant speed up on Windows OpenOffice going from beta to rc versions, there must be some debug code in the betas.

OO is definitely a program that needs 512MB RAM, with only 256 MB increasing the graphics cache setting is just going to push into swap.

---

### Post by slux on 2005-10-30
[QUOTE=coldrick]Don't know what Java you were using that made you say that Java really slowed oOo down, but I notice no performance problem with the standard Sun JRE (1.5.0_05). If you go to Tools\Options, note that the default appears to be to use gcj, which I'd avoid as much as possible: it certainly seems to have some compatibility problems.
[/QUOTE]

It's too bad to hear that gjc is slow with Ooo2, but it's very likely not about compatibility as Ubuntu/Debian/Redhat have worked hard to get it's Java parts running on gcj so they could include the database component without Sun's proprietary Java. I for one hope to see gcj continue to improve and eventually replace the non-free jre (and would not install it just for slightly less startup time .. You don't need it if you don't use the parts written in Java anyway.

---

### Post by lothar_m on 2005-10-30
Was anyone able to use this repo to upgrade open office?

---

### Post by manicka on 2005-10-30
[QUOTE=lothar_m]Was anyone able to use this repo to upgrade open office?[/QUOTE]
Yes, I'm using Breezy

---

### Post by manicka on 2005-10-30
[QUOTE=DavidTangye]Putting "deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./" in /etc/apt/sources.list gives the following error in Synaptic -

"Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)"

What is the correct line? Shouldn't it end with 'universe' or something?[/QUOTE]
What messages do you get when you run

sudo apt-get update

before

sudo apt-get upgrade

---

### Post by keyes on 2005-10-30
You can also get Java from the PLF:

add this to your souces.list:
```
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
```

and ```
sudo apt-get update && sudo apt-get install sun-j2re1.5
```

---

### Post by manicka on 2005-10-30
Keep in mind that the PLF have advised that this repo will change soon.

check for changes here

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by anderss on 2005-10-30
[QUOTE=coldrick]Don't know what Java you were using that made you say that Java really slowed oOo down, but I notice no performance problem with the standard Sun JRE (1.5.0_05). If you go to Tools\Options, note that the default appears to be to use gcj, which I'd avoid as much as possible: it certainly seems to have some compatability problems.

If you need help in installing Java, take a look at [http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part).
That installs the jdk (and the jre) - installing just the jre is pretty straightforward.

And you're quite right about the speed increase if you set memory parameters correctly: very impressive! Thanks for the tip.

Regards,
David[/QUOTE]


In that how-to it says you have to install "java-package", but that package is not anywere in the repositories apparently - how do I follow that how-to then?

---

### Post by manicka on 2005-10-30
[QUOTE=anderss]In that how-to it says you have to install "java-package", but that package is not anywere in the repositories apparently - how do I follow that how-to then?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=manicka+w32codecs+easy](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=manicka+w32codecs+easy)

---

### Post by angrykeyboarder on 2005-10-30
[quote=magnusbb]To make a perfect OpenOffice.org on your Breezy system, I've got a few tips.

First, upgrade your current beta version to the 2.0 final release by adding this repository to your /etc/apt/sources.list:

deb [http://people.ubuntu.com/~doko/OOo2 ./]("http://people.ubuntu.com/%7Edoko/OOo2%20./") ....
[/quote]

How do did you ***ever*** come across that link anyway?

And thank you! :-)

---

### Post by angrykeyboarder on 2005-10-30
[quote=lothar_m]Was anyone able to use this repo to upgrade open office?[/quote]

Yupperz.

---

### Post by angrykeyboarder on 2005-10-30
[quote=magnusbb]Then follow these speed tips published today at The Inquirer:

Goto Tools -> Options > Memory.
Increase graphics cache to 64 MB and memory per object to 8 MB.

Exit and restart OpenOffice a couple of times (it takes a few openings before it helps).

It's also important to have the correct version of Java installed. OpenOffice uses Java for a few things in version 2, and the GNU version of Java bundled with Breezy will slow it down. Download the original Java from Sun, and enable it in the Java tab under Tools -> Options.[/quote] 

I followed these directions you gave and haven't noticed any performance improvement, which I find odd.

On the other hand, I wasn't noticing a problem beforehand either. I guess I'll need to do some "serious" work in OOo for this to be apparent.

Thanks again.

---

### Post by magnusbb on 2005-10-30
Well, yeah, that's pretty strange. But of course, it may vary between different setups.

But I noticed a change in both startup time, and responsiveness in general. OpenOffice is still too slow an application though, and it consumes way too much memory.

---

### Post by kakashi on 2005-10-31
actually openoffice is blazing fast. 
if you open it in ice-wm. 
gnome sucks. i love it for its interface but it makes good software look crappy cuz its slow as hell. same for kde btw.

---

### Post by No_Code on 2005-12-19
I was installing the Sun JRE for something completely different and it wasn't until I tried to use OpenOffice 2 with it that I realized that this was the way that OO2 should be used. I finally installed the Sun JRE on the system that I've been doing most of my OO2 experimentation on and I noticed that it has somewhat greater stability as well.

---

### Post by unf on 2005-12-19
double

---

### Post by unf on 2005-12-19
It's fives times faster than before thanks! ;)

---

### Post by mondi0924 on 2005-12-19
Thanks for this tip initial loading time went from 30 seconds to less than 5 woohoo!

---

### Post by tipi on 2005-12-19
could anybody post a direct link to the correct java download ?
can't quite figure out wich one I need
greetz:KS


okay found it, 10 posts back , to lazy

---

### Post by william_nbg on 2006-01-29
Thank you, thank you, thank you.

Now, my wife will stay with Ubuntu that her Office programs are opening and working as fast as MS crap was.

---

### Post by prox2far on 2006-02-20
WOW thanks it worked my openoffice now starts 150% faster :D 

Just thought I would noob secure this guide and sum up what everybody has written.

First open the terminal and open your source list.
```
 sudo nano /etc/apt/sources.list
```
Add the following sources to the end of your sources list.
```
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```
the first is for openoffice 2 ( thanks to magnusbb who started this post )
the 2 others are from PLF and is used 4 the JAVA part ( thanks to PLF and manicka )

update apt-get and update to openoffice 2 followed by installing JAVA
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-j2re1.5
```
close the terminal and open Openoffice

Goto Tools -> Options > Memory.
Increase graphics cache to 64 MB and memory per object to 8 MB.
Goto Tools -> Options > Java
press the add button and enter the following path
```
/usr/lib/j2sdk1.5-sun/
```
openoffice should now have an extra java protocol names "sun microsystems inc." select it and restart openoffice

all done :KS  it worked 4 me and I hope it will work 4 you :KS

---

### Post by rohan! on 2006-02-20
has anyone tried to use ooqstart-gnome?

OOo starts up slow, but once it's open you can open any Ooo prog very quickly. Apparently this thing just starts up open office on login so that when you open anything it just pops onto screen.

---

### Post by Devo66 on 2006-03-01
There is a problem with this build of OpenOffice.  Templates don't work.  You can't save new templates or select your default template in any of the applications.  I discovered this problem when I was trying to change my default font in Calc.  It just wasn't working.  I downgraded back to the "Official" Breezy OpenOffice and now it works fine.  I miss the speed of this build though.  Is there any chance this problem could be fixed?  I'm sorry I'm not able to provide any more information, but I had to get this working, so I'm sticking with 1.9 for now.

---

### Post by manicka on 2006-03-01
[QUOTE=Devo66]There is a problem with this build of OpenOffice.  Templates don't work.  You can't save new templates or select your default template in any of the applications.  I discovered this problem when I was trying to change my default font in Calc.  It just wasn't working.  I downgraded back to the "Official" Breezy OpenOffice and now it works fine.  I miss the speed of this build though.  Is there any chance this problem could be fixed?  I'm sorry I'm not able to provide any more information, but I had to get this working, so I'm sticking with 1.9 for now.[/QUOTE]

I don't have these problems with this build. How did you install it?

---

### Post by Devo66 on 2006-03-01
Added the line to my sources.list and did an apt-get update / upgrade.  Perhaps I should try it again.

---

### Post by Devo66 on 2006-03-01
Weird.  I did the upgrade again, same way, and this time it's working fine.  Oh well.  Second time's the charm, I guess.

---

### Post by cwmccabe on 2006-04-18
Has anyone had success creating a report with the wizard in Base?  When I try, it just opens Writer instead of the report wizard...  ](*,)

---

### Post by dajashby on 2006-04-20
[QUOTE=magnusbb]To make a perfect OpenOffice.org on your Breezy system, I've got a few tips.

First, upgrade your current beta version to the 2.0 final release by adding this repository to your /etc/apt/sources.list:

deb [http://people.ubuntu.com/~doko/OOo2 ./](http://people.ubuntu.com/~doko/OOo2 ./)

Then sudo a apt-get update and upgrade, and watch it download...

[/QUOTE]

This doesn't work with 64 bit Ubuntu.  Most of the OOo 2 files don't get flagged for upgrade and that leads to dependancy problems.  I ended up having to uninstall OOo and start again.  I found your directory for the AMD64 install via another post, but it's empty.

The reason I am interested in the upgrade is that I have a weird problem - Open Office refuses to open any files on an NFS share as read-write. I have the files stored on a fileserver running Kubuntu 5.10, and they are owned by a user with the same UID on both machines. I am logged in as that user on the client machine (but not on the server). I can open and save files on the same NFS share with other applications - Kate, The Gimp, etc. In fact I can open OOo files on the share in KOffice.  Well, that's one of the reasons. The other is that I'm a bit fed up with the beta version locking up the machine when it crashes...

I think the other people responding to this thread with problems didn't notice the space in front of the "./" at the end of your URL...

---

### Post by bionnaki on 2006-11-03
I tried this in edgy and it works great. I disabled java and set "remove from memory" for 24 hours (I have enough ram to do this without problem), but everything else from the original post works wonders. OO.o opens up **instantly** - it doesnt even show the splash screen.

---

