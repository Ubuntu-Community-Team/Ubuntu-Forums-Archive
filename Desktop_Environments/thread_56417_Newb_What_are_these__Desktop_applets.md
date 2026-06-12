---
title: "Newb: What are these?  Desktop applets?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by DrQuincy on 2005-08-12
Hi

I'm configuring my first install of Kubuntu (and indeed any Linux distribution!) and I love what I've got so far.  I've seen lots of cool KDE screenshots like this: [http://hoth.amu.edu.pl/~higgs/progs/zrzutekranu10a.jpg](http://hoth.amu.edu.pl/~higgs/progs/zrzutekranu10a.jpg) that have some really nice features on the desktop / tool bar such as the weather, a cool clock and so on.  What are these applications called?  Can you tell me of some nice one like the one on that link that I can download?  Is there / are there any good repositories anywhere?

Many thanks.

---

### Post by PeP on 2005-08-12
install superkaramba it runs those desktop applications
get almost anything you can dream of from [http://kdelook.org/](http://kdelook.org/)

---

### Post by uperjer on 2005-08-12
just to give you a heads up with superkaramba -

i am also new to the whole linux scene, as well as kubuntu.  i downloaded the tar file and started the ./configure process, and it came up with an error message saying that i had some files missing.  the nice thing is that kde comes with a package finding program - knaptic i believe (please correct me if i'm wrong).  you can search for the files that are missing in the configure process and install them.  

i had to install X development tools, python dev. tools, jpeg libraries, etc.  i can't remember what else.

good luck!

---

### Post by PeP on 2005-08-12
[QUOTE=uperjer]just to give you a heads up with superkaramba -

i am also new to the whole linux scene, as well as kubuntu.  i downloaded the tar file and started the ./configure process, 

good luck![/QUOTE]
Dear uperjer,
It 's time to really switch to linux before you go back to windows saying linux sucks for you can' t install anything...

To really switch just try the tools linux provides you to install programs. It is the strongest point of debian like distributions.

This tool for debian is called apt, and comes in various interfaces called dselect (console), aptitude (console), synaptic (gnome gui) and kynaptic (kde gui)

kynaptic is not very powerfull yet, so even in kde you should try either synaptic or aptitude.

This will change the way you use a computer.

For example to get superkaramba, change the config of apt to allow the unsiverse repositories first as explained here.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then launch synaptic
say yes to update the list of packages 
search -> karamba
select superkaramba
install it

->so easy, it just works!

in the ubuntu world you don't google for an app, then for a crack, then follow a long installation assistant by clicking yes twenty times. You just search for a package, select it and the program  downloads it and its dependencies for you, then installs all the stuff and configures it.

The same program can also cleanly remove the package or update it.

And you can even update *everything* : two clicks and a few options to set only.

As a conclusion: forget .tar.gz unless you can't find a .deb

---

### Post by DrQuincy on 2005-08-13
Thanks I've got it running - I love it.

It seems to slow my machine down when I run a status monitor though - is this normal?

Im running p2 2.0 ghz with 1.5 gig sdr ram and geforce 4 128 meg.

Thanks

---

### Post by PeP on 2005-08-13
[QUOTE=DrQuincy]Thanks I've got it running - I love it.

It seems to slow my machine down when I run a status monitor though - is this normal?

Im running p2 2.0 ghz with 1.5 gig sdr ram and geforce 4 128 meg.

Thanks[/QUOTE]
a little applet should never slow down your computer, especially one like yours (1.5 gig ram !!!  you should be able to run a windows through vmware and qemu without slowdown! )

You can track the performances of your apps through 'top'(command line) or ksysguard.

If the applet uses moe than 5% cpu or more than 5% of your ram, just delete it and try another one.

---

### Post by uperjer on 2005-08-14
[QUOTE=PeP]Dear uperjer,
It 's time to really switch to linux before you go back to windows saying linux sucks for you can' t install anything...

To really switch just try the tools linux provides you to install programs. It is the strongest point of debian like distributions.

This tool for debian is called apt, and comes in various interfaces called dselect (console), aptitude (console), synaptic (gnome gui) and kynaptic (kde gui)

kynaptic is not very powerfull yet, so even in kde you should try either synaptic or aptitude.

This will change the way you use a computer.

For example to get superkaramba, change the config of apt to allow the unsiverse repositories first as explained here.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then launch synaptic
say yes to update the list of packages 
search -> karamba
select superkaramba
install it

->so easy, it just works!

in the ubuntu world you don't google for an app, then for a crack, then follow a long installation assistant by clicking yes twenty times. You just search for a package, select it and the program  downloads it and its dependencies for you, then installs all the stuff and configures it.

The same program can also cleanly remove the package or update it.

And you can even update *everything* : two clicks and a few options to set only.

As a conclusion: forget .tar.gz unless you can't find a .deb[/QUOTE]


dude - i never said linux sucked.  i was just trying to help him out. 

<sarcasm> thanks for not treating me like a noob </sarcasm>

the point i was trying to make is that it's a lot easier to install things in windows, that's all.  it took me a good 2 or so hours to install superkaramba because i had to jump through like a million hoops.  i am TRYING to make linux my primary operating system, but i just don't have a billion years to install all the dependencies and figure out how to type out the bazillion commands that linux requires.

---

### Post by PeP on 2005-08-14
[QUOTE=uperjer]dude - i never said linux sucked.  i was just trying to help him out. 

<sarcasm> thanks for not treating me like a noob </sarcasm>

the point i was trying to make is that it's a lot easier to install things in windows, that's all.  it took me a good 2 or so hours to install superkaramba because i had to jump through like a million hoops.  i am TRYING to make linux my primary operating system, but i just don't have a billion years to install all the dependencies and figure out how to type out the bazillion commands that linux requires.[/QUOTE]

What ?? I don't think it is easier to install something in windows at all.

**Synaptic** is a GUI (graphic user interface: no commands) that resolves dependancies for you.

Kynaptic is another, easier but less powerfull.

If it took you two hours to install superkaramba, you are missing ALL the power of ubuntu. 

Please avoid your sarcasms, did I say:
<sarcasm> What a n00b, it takes 15 secs</sarcasm>

I just tried to show you another (Far more powerfull) way to install stuffs, and your post proves that you don't used it this time.

---

### Post by f1dave on 2005-08-15
*steps into middle with arms stretched out*

Now now lads, obviously just a misunderstanding. I'm sure noone meant to hurt anyone's feelings here.

---

### Post by uperjer on 2005-08-15
the fact is, when i download something for windows, i get a nice little .exe file.  i click install, and lo and behold, it installs.  15 seconds.

when i download something for linux, i have to untar, ./configure, find out which dependencies i'm missing, find those dependencies, install those dependencies, then try to install again only to find that i'm missing MORE dependencies, etc.  2 hour chore.

now don't get me wrong.  i really do like linux, the open source community, and even boards like this (and i will try not to be sarcastic from now on).  i just wish the OS could be a little more user friendly as far as installing programs goes.  i've tried kynaptic and i can't find some of the programs i'd like to install (azureus, java, etc.)

---

### Post by uperjer on 2005-08-15
[QUOTE=PeP]
If it took you two hours to install superkaramba, you are missing ALL the power of ubuntu. 
[/QUOTE]


then i am obviously missing out.  what am i doing wrong?

---

### Post by PeP on 2005-08-15
read the post: you don't use the package manager.

synaptic is a very good frontend for the debian package manager, did you install superkaramba with it ?

---

### Post by PeP on 2005-08-15
[QUOTE=uperjer]
when i download something for linux, i have to untar, ./configure, find out which dependencies i'm missing, find those dependencies, install those dependencies, then try to install again only to find that i'm missing MORE dependencies, etc.  2 hour chore.[/QUOTE]
that is the ** wrong ** way to install, and that's why it took you 2 hours two install superkarmba.  

Again, please !, before you go back to win users saying how linux is difficult to handle, give a fucking try to ** synaptic ** <- moderator please make that blink :-)

I hope I didn't used a to rude language, but synaptic is what makes the strenght of debian like distribs, saying that it is uneasy to install a program is not fair if you didn't try to do it with synaptic or apt-get (kynaptic is just far less powerfull than synaptic).

If you tried kynaptic, it is maybe a configuration pb:

**synaptic provides azureus and superkaramba did you just enable extra repositories ??? check this: **
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)



java is quite special as the sun licence requires you to dowload it from them, 
install java-package and then 
fakeroot make-jpkg jre-1_5_0_02-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update02_i386.deb

---

### Post by GreyFox503 on 2005-08-16
[QUOTE=uperjer]i've tried kynaptic and i can't find some of the programs i'd like to install (azureus, java, etc.)[/QUOTE]

You can get Azureus and Java through apt-get, I have done it myself.

If you haven't already done so, go here:  [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

to add the extra repositories to your list.

To install those specific apps:

```
sudo apt-get install azureus
sudo apt-get install sun-j2re1.5
```

And I would definitely run Synaptic to search for future packages.

---

### Post by uperjer on 2005-08-17
installing the extra repositories made it a lot simpler to find this stuff.  thanks.

why wasn't the extra repositories included in the install disc?  would have made more sense.

and i have installed synaptic.  will try to use that more to find what i'm looking for.  does it keep an updated list of all the programs available for linux?  if so that's fantastic.

---

### Post by PeP on 2005-08-18
[QUOTE=uperjer]installing the extra repositories made it a lot simpler to find this stuff.  thanks.
[/QUOTE]

indeed ...

[QUOTE=uperjer]
why wasn't the extra repositories included in the install disc?  would have made more sense.
 [/QUOTE]
read this: 
[http://www.ubuntulinux.org/ubuntu/components/]("http://www.ubuntulinux.org/ubuntu/components/")

 
 [QUOTE=uperjer]
and i have installed synaptic. will try to use that more to find what i'm looking for. does it keep an updated list of all the programs available for linux? if so that's fantastic.[/QUOTE]
It is easy to refresh the list (refresh button in synaptic/ apt-get update in the command line interface), it doesn 't provide all programs available for linux, but most of them that are provided through ubuntu repositories. 

And yes it' s fantastic :-) You can see my point now :-).

---

### Post by rjwood on 2005-08-18
I have to say that there is probably no-one in any of these forums that is less of a computer skilled person than I am. Just amazes me how people get lost tho. While I know literally nothing about this stuff, It has been pretty plain to me that all u have to do is search for the answers. What I notice most about myself is that I was really doing nothing on my computer when I was using windows and now the reason I am lost is that now I know that there is so-o much to do with this thing that I dont know what to do. I am figuring out where to start. I havent been able to continue any of my business activities since installing ubuntu. But that is only because of my lack of knowledge. I dont really like any of the banking financial programs I have seen so I am back to paper and books. That is still better than windows. By the way I just installed kubuntu after using ubuntu for a couple of months and I do feel more comfortable with it than gnome. Anyway keep fighting for your freedom from microsoft and I am sure it will pay off.

---

