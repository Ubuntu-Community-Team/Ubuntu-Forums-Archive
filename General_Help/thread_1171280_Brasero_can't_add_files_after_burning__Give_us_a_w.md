---
title: "Brasero can't add files after burning?  Give us a warning next time!"
date: 2009-05-27
forum: General Help
---

### Post by mag1 on 2009-05-27
I can't believe i've now basically wasted a disk or two with this stupid piece of software, why the heck can't i add files after burning like is standard in xp and probably most burning software!?

I expected this was standard so it came as quite a shock and annoyance when i find after writing 9mb to disk that i can't add anything else, how pathetic! :rolleyes:

Sorry to moan its just im quite angry that such a simple thing you'd expect to be in any half decent burning software and which is the main choice for the os just isn't there there and with no warning, i mean dragging and droping files the same way as in xp, honestly what were they thinking?

---

### Post by MJWitter on 2009-05-27
Im sorry but if you are using a disc that can only be written to once then that is not Brasero's fault.. Once you click burn, that is what it does. Add and remove as much as you want, but be certain of what you want before pushing burn.

---

### Post by tpmoney on 2009-05-27
The feature you're looking for is called "multi-session" disc burning.

From the Brasero help:

> Data Project

    * Brasero Manual V2.2
    * Creating a New Project

    To burn a data CD, proceed as follows:
    
   ...

* 3.2.1.&#8194;Data Project Options

      Before starting the burning process, it is possible to
      modify some of the burning options.
    
        Section Select a disc to write to:

        *               Click on Properties to open
                        the properties dialog for the burning device. See Section 3.6 &#8213; Burning Device Properties
                        for more information.
                      
        Section Disc options:

        *             Increase compatibility with
                      Windows systems
                     
                              Select this option if you intend the disc to be used on 
                              computers running Windows. Files on the disc will be 
                              checked to ensure that their filenames do not contain 
                              characters which are invalid on Windows.

                    
[B]        *          Leave the disc open to add
                      other files later

                              Select this option to create a
                              multisession disc, so
                              that it will be possible to add files to
                              the disc at a later date (without erasing
                              it, if it is rewritable).
                            [/B]

Incidentally, discs that aren't completely closed such as the ones XP produces by default and what you will get with a multisession in Brasero are not completely compatible with all systems. While the problem is minimized now, you will still come across a system from time to time that can't read multi-session discs until the whole disc has been closed.

---

### Post by mag1 on 2009-05-27
> **tpmoney said:**
> The feature you're looking for is called "multi-session" disc burning.

Incidentally, discs that aren't completely closed such as the ones XP produces by default and what you will get with a multisession in Brasero are not completely compatible with all systems. While the problem is minimized now, you will still come across a system from time to time that can't read multi-session discs until the whole disc has been closed.

Ah thats it, couldn't remember what it's called but it should really be standard if brasero can do it.

---

### Post by nikgare on 2009-05-27
Sorry to moan, but it's very annoying when people go off on a rant here without even bothering to read the manual.

---

### Post by mag1 on 2009-05-27
I still think my rant is valid, multisession burning should really be standard or at least made obvious in the menu before burning, especially when done from nautilus using drag and drop like in xp.

---

### Post by baseface on 2009-05-27
i hate to burst your bubble, but ubuntu is not windows. its not like windows in any way, shape, or form. you need to read the documentation before you do stuff. deal with it.

---

### Post by wsonar on 2009-05-27
Try k3b multisession is auto


I think it's a better burner

it's kde's default

---

### Post by baseface on 2009-05-27
theyre both the exact same thing. they both use cdrecord to write to discs.

---

### Post by mag1 on 2009-05-27
> **baseface said:**
> i hate to burst your bubble, but ubuntu is not windows. its not like windows in any way, shape, or form. you need to read the documentation before you do stuff. deal with it.

Lol don't be silly, i've been using ubuntu for years, while they're doing a good job and i have little problem with most stuff, simple things like this that should just work are annoying, it's something you expect by default, the average user doesn't want or should have to read every manual to get simple stuff working, if its intuitive and just works then they can get on with doing the stuff they want, better software design is always good, no one should ever have to touch a command line and everything should have a gui also.

> **wsonar said:**
> Try k3b multisession is auto


I think it's a better burner

it's kde's default

Thanks might check it out.

---

### Post by tpmoney on 2009-05-27
> i hate to burst your bubble, but ubuntu is not windows. its not like windows in any way, shape, or form. you need to read the documentation before you do stuff. deal with it.

It may not be windows, but it is wort investigating how to improve that process. If your users have to read documentation to get simple behaviors, then you should reconsider your design. For example, in the drag and drop interface, when the user commits the burn, a dialogue asking about which burn method you would like to use would be a simple solution to the problem. You could even set the dialogue to remember the setting so that it only appears on the first burn.

Ubuntu may not be windows, but dismissing conventions and behaviors just because the behavior is windows is the exact kind of NIHS behavior that makes dealing with windows such a pain.

---

### Post by frpaul on 2009-05-27
As for me, Ubuntu feels much like Windowd XP in almost everything, that has GUI.
This is not bad at all, considering how many ex-windows users (including me) are starting with Ubuntu experience. I even think, that Gnome is making too much effort to look like windows. Probably i'll switch to KDE or xfce later on to walk farther away :)
But whats different in Ubuntu - theres always choice of switching to command line and fixing things that dont work in GUI.

As for the Brasero - probably they should make 'multisession' option more obvious. It was meant a 'simple' application, wasnt it? Then it should act like one.

---

### Post by wsonar on 2009-05-27
I think kde is more of a windows look than gnome

the kde bar is mimicks the win7 bar with the preview and it has a real vistay look to it

---

### Post by frpaul on 2009-05-27
> **wsonar said:**
> I think kde is more of a windows look than gnome

the kde bar is mimicks the win7 bar with the preview and it has a real vistay look to it

Vista's look&feel is one of the things which maid me switch to Ubuntu :) And Im quite happy about it so far.
As for KDE - sounds interesting. But as I started to explore Gnome functionality, I'll stay with it for some time. A pity I couldnt get Compiz running (whant 3d desctop real bad!) :) It looks like it asks for Xgl and Ive no idea where to get it (got nVidia driver running). Probably I should change smth. in xorg.conf?

---

### Post by wsonar on 2009-05-27
> **frpaul said:**
> Vista's look&feel is one of the things which maid me switch to Ubuntu :) And Im quite happy about it so far.
As for KDE - sounds interesting. But as I started to explore Gnome functionality, I'll stay with it for some time. A pity I couldnt get Compiz running (whant 3d desctop real bad!) :) It looks like it asks for Xgl and Ive no idea where to get it (got nVidia driver running). Probably I should change smth. in xorg.conf?

if you video card is configured you shoulden't have to do much to get compiz to work what happens when you try to use desktop effects?

---

### Post by frpaul on 2009-05-28
> **wsonar said:**
> if you video card is configured you shoulden't have to do much to get compiz to work what happens when you try to use desktop effects?

Well, they do work (window wobbling, for example, which I hate) :D
How should I start 3d desctop properly? Sorry for noob question.
I guess I should read the man to compiz before running sudo compiz :)
But theres lots of mans to read and theres this forum, full of enlightened command line gurus ;)

Aaand going back to the topic. I've got a script for burning CD's
Any help in making it better?
Here goes:
```

#cdrecord -scanbus dev=ATAPI // find device name

echo "input iso file name"
read NAME

cdrecord dev=ATAPI:0,0,0 speed=52 -v -eject $NAME.iso0;

```

---

### Post by wsonar on 2009-05-28
> **frpaul said:**
> Well, they do work (window wobbling, for example, which I hate) :D
How should I start 3d desctop properly? Sorry for noob question.
I guess I should read the man to compiz before running sudo compiz :)

[/code]

Sounds like compiz is working the first thing I turn off is wobble windows
what kind of effect do you want a windows switcher or cube or just rendering your video properly?

---

### Post by frpaul on 2009-05-28
> **wsonar said:**
> Sounds like compiz is working the first thing I turn off is wobble windows
what kind of effect do you want a windows switcher or cube or just rendering your video properly?

Woooowww! Cant believe my own eyes! I just watched this: 
[http://www.youtube.com/watch?v=mmYIoXMA8nA&NR=1](http://www.youtube.com/watch?v=mmYIoXMA8nA&NR=1)

installed 
sudo apt-get install compizconfig-settings-manager
Woo-hoo!!! Working! wicked!!!
Man, thats the best thing that happend to me in Linux world so far!

---

### Post by anjilslaire on 2009-05-28
> **mag1 said:**
> I still think my rant is valid, multisession burning should really be standard or at least made obvious in the menu before burning, especially when done from nautilus using drag and drop like in xp.

It's all personal preference. If my system defaulted to multi-session, like XP, it would drive me crazy, and I wouldn't use it.
The built-in burner in Windows is pretty much garbage, IMO. When I used Windows, I always installed a 3rd party burner, as the multi-session discs created were junk for storage purposes.

---

