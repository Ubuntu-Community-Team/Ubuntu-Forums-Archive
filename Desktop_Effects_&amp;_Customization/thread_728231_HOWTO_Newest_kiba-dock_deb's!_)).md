---
title: "HOWTO: Newest kiba-dock deb's! :):)"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by terrax on 2008-03-18
Hello everybody :):)

I just wanted to share my newly builded debs of the fancy kiba-dock. Just download the attached 5 files, and do the following in the directory where you downloaded the deb's.

```

sudo dpkg -i *.deb ; sudo apt-get install -f

```

This will install kiba-docks with every available plugins. PLZ reply if the debs won't work. Have only testet them on my own machine. So I might have forgot a dependency :-)

Install at own risk. Enjoy!

[COLOR="Red"]**EDIT: The newest kiba doesn't work with physics (Described in #2). If you want the physics you should install some older debs, look at #3.**[/COLOR]

Terrax.

---

### Post by terrax on 2008-03-18
BTW. Please note the physics engine has been disabled temporary, because of a bad implementation. When it arrives in svn, I will make new deb's for you.

---

### Post by terrax on 2008-03-18
LOOK HERE IF YOU CAN'T WAIT.

If you like me can't wait for the physics engine to be reimplementet, I have made some deb's of the last know svn version with physics enabled. Just install them like in the howto, and just use the newest akamaru libs from the howto. Enjoy :guitar:

---

### Post by Dr.Dixie on 2008-03-18
Umm... Where are my physics?
I installed everything flawlessly, but now...how do the physics come in?


!Dr.Dixie!

---

### Post by terrax on 2008-03-18
Did you install the debs from svn20080201? Thats the only one which contains physics. Remember akamaru libs also.

---

### Post by Eclipse. on 2008-03-18
> This will install kiba-docks with every available plugins. PLZ reply if the debs won't work. Have only testet them on my own machine. So I might have forgot a dependency 

libglade0 dependancy problem on hardy using physics version, will check on gutsy in two mins.

EDIT: Basicly no chance of it working on hardy without breaking everything else.lol

Any chance of a hardy deb <3

---

### Post by terrax on 2008-03-19
> **Eclipse. said:**
> libglade0 dependancy problem on hardy using physics version, will check on gutsy in two mins.

EDIT: Basicly no chance of it working on hardy without breaking everything else.lol

Any chance of a hardy deb <3

It was meant for gutsy. But Ill look into some hardy debs sometime.

---

### Post by Eclipse. on 2008-03-19
> **terrax said:**
> It was meant for gutsy. But Ill look into some hardy debs sometime.

Cheers.;)

Physics version works on gutsy well.

Thanks

---

### Post by stiansoftcore on 2008-03-21
nice try, mr terrax!!!

```
 $ sudo dpkg -i *.deb ; sudo apt-get install -f
(Reading database ... 103903 files and directories currently installed.)
Preparing to replace songbird 0.2.5.1 (using songbird_0.2.5.1_i386.deb) ...
Unpacking replacement songbird ...
Setting up songbird (0.2.5.1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libawn0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```

Nah, it probably work fine, just me that messed something up. Does somebody know what's the problem?

---

### Post by thechilipepper0 on 2008-03-28
i installed it via this thread, but its turned out to be a memory hog and i want to try the newer version. how do i uninstall the older version?

---

### Post by talsemgeest on 2008-03-28
Just overwrite the svn with the new version and install.

---

### Post by xoreaxeax on 2008-03-31
great work on the debs, installed fine here on xubuntu 7.10 and kiba-dock is up and running. one weird thing though, everytime I click on a icon and launch a program kiba shows some animated gears below the icon and although the program launches quickly the program cursor stays in sleep/loading mode synced to that animation on the kiba dock for a few seconds. anyone know what am I doing wrong?

---

### Post by piratesmack on 2008-04-01
Thanks for the debs.

I encountered  a small problem, though. 

In Linux Mint Daryna (Basically Ubuntu Gutsy on steroids), it mentions a dependency error for kiba-dbus-plugins, but goes ahead and installs it anyway. Kiba-dock seems to be working fine, though so I guess it's not very important. 

Does anyone know where I can find the source for the latest version of kiba with physics?
I'd like to compile it myself

Thanks again

---

### Post by talsemgeest on 2008-04-01
The last release that still had physics in it it 602. From 603 onwards there are no physics.

---

### Post by piratesmack on 2008-04-02
> **talsemgeest said:**
> The last release that still had physics in it it 602. From 603 onwards there are no physics.

Thanks man, I'll compile 602 then.

---

### Post by terrax on 2008-04-02
> **piratesmack said:**
> Thanks man, I'll compile 602 then.

Look at #3, there you got the debs with physics... :-) Guess you missed it.

---

### Post by piratesmack on 2008-04-02
> **terrax said:**
> Look at #3, there you got the debs with physics... :-) Guess you missed it.
Thanks
yeah I saw those, I'd just prefer to compile it myself

I got nothing else to do :lolflag:

---

### Post by piratesmack on 2008-04-02
um I'm having trouble downloading the trunk directory for kiba-dock rev 602, lol. Can anyone help me out?

What's the command?

I'm new to this svn stuff

---

### Post by talsemgeest on 2008-04-02
Take a look here: [http://ubuntuforums.org/showpost.php?p=4475291&postcount=329](http://ubuntuforums.org/showpost.php?p=4475291&postcount=329)

---

### Post by talsemgeest on 2008-04-02
Oh, and just in case you haven't found it, here is the tutorial for installing from the SVN: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by piratesmack on 2008-04-02
> **talsemgeest said:**
> Take a look here: [http://ubuntuforums.org/showpost.php?p=4475291&postcount=329](http://ubuntuforums.org/showpost.php?p=4475291&postcount=329)

Awesome! Thanks man

So this would do it?
```

svn co -r 602 https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk kiba

```

---

### Post by piratesmack on 2008-04-02
Thanks again, talsemgeest

I now have kiba-dock 602 compiled and all the problems I was having before are fixed.

Does anyone know when they plan to reimplement the physics?

---

### Post by talsemgeest on 2008-04-02
The guy doing it sounds like he is going to be a while, and it it isn't at the top of his priorities list

---

### Post by piratesmack on 2008-04-03
> **talsemgeest said:**
> The guy doing it sounds like he is going to be a while, and it it isn't at the top of his priorities list

Thanks, I guess I'll just stick with 602 for a while then

---

### Post by theji on 2008-04-15
wait~~~

---

### Post by SAKO2008 on 2008-04-20
Hi! It's my first post in this forum!:lolflag:

Thanks for your deb!
I install kiba dock with your files but when I try to run kiba I get a message error:

fabio@fabio-laptop:~$ kiba-dock
** Message: cant load file '/home/fabio/.kiba-dock/config': Errore nel leggere il file "/home/fabio/.kiba-dock/config": È una directory
Can you help me?please.

---

### Post by El Lance-O on 2008-05-09
PLEASE! PLEASE! PLEASE!

Make Hardy .deb's! I've wanted kiba-dock for years now, and it's just never compiled right for me.

With the ones in this thread, I also get the libglade0 problem, and it's just too glitchy to run properly (white boxes for icons, tons of errors in the terminal, etc)

PLEASE!!!

My desktop would be complete in eyecandy.



No really, it would be COMPLETE.

---

### Post by vapotrini on 2008-05-22
lance try post #265...

[http://ubuntuforums.org/showthread.php?t=554127&page=27](http://ubuntuforums.org/showthread.php?t=554127&page=27)

---

### Post by rated_emman on 2008-06-10
if i have the latest kiba dock and i wanted the old physics, how do i downgrade? 

thanks guys

---

### Post by talsemgeest on 2008-06-11
To download you need to download the svn, downgrade that to the version you want, then build it.

The instructions are on this post: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by rated_emman on 2008-06-11
> **talsemgeest said:**
> To download you need to download the svn, downgrade that to the version you want, then build it.

The instructions are on this post: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

im sorry.. ur probably annoyed but i appreciate all your help :D.. im super new to ubuntu.. it's like my first week and im still getting familiar of the stuff...

so here goes the issue, i have the latest kiba dock installed... i followed the step by step by mattgaunt... and so i have the latest kiba dock... so how do i download the svn? how do i downgrade to the version i want? do i need to uninstall the one i have right now? or it will automatically replace it? thanks for you help again... i really appreciate everybody that helps in here...


you guys rocks! :D

---

### Post by talsemgeest on 2008-06-11
Ok, I have posted on the other thread...

---

