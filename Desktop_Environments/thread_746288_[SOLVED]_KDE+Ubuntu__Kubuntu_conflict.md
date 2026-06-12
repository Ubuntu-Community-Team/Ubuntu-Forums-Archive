---
title: "[SOLVED] KDE+Ubuntu / Kubuntu conflict"
date: 2008-04-05
forum: Desktop Environments
---

### Post by harrybazeegar on 2008-04-05
Hi all guys....

I have been dual booting with windows XP and Ubuntu 7.04 for around 6 months and at the end of it I can say happily that I can get around in linux and do all i want to do without needing to fire up windoze :) ...

Now I ran into a curious little soup... I wanted to run Amarok on my PC but its meant for KDE... 
I thought what the heck and just typed
```
sudo apt-get install amarok
```

Installation was fine... i configured it for the database stuff and the collection got added too.
But when i tried to play any stuff it just wouldn't.

So i guessed Amarok is a KDEzen and not a GNOMEzen.

I typed
```
sudo apt-get install kde-desktop
```

and a whole lot of stuff got installed( abt half a gig ).
during the process i had many occurenced of "call failed", "error code 0x.." and stuff.
and at the end, amarok wouldn't run fine.

So want to know how to run amarok....

I want to install KDE on Ubuntu but not all the KDE apps...
what should I do?
1. sudo apt-get install kde-desktop
2. sudo apt-get install kdebase
3. sudo apt-get install kde-core

what do these commands do?
are they all the same? what is the difference?

most importantly, what should I do?

can amarok be installed on ubuntu or do i have to set up kubuntu?

thanks a lot guys :)

---

### Post by benerivo on 2008-04-05
> **harrybazeegar said:**
> So want to know how to run amarok....

I want to install KDE on Ubuntu but not all the KDE apps...
what should I do?
1. sudo apt-get install kde-desktop
2. sudo apt-get install kdebase
3. sudo apt-get install kde-core

what do these commands do?
are they all the same? what is the difference?

most importantly, what should I do?

can amarok be installed on ubuntu or do i have to set up kubuntu?

You don't need anything else other than amarok, to get it to work in Gnome (or any other desktop env). It was installed correctly when you did apt-get install amarok, but the reason for it not playing audio was some other problem. Did you have any error messages when trying to play? I think if you tried to play an mp3, it may be that it was missing the 'restricted' mp3 codec. You could try installing the codec and trying again (i think the one you want is called something like 'libxine-ffmpeg' and is in the repositories).

As to installing other kde apps, you don't need to manually install other kde packages other than the ones it calls on automatically, so apt-get install digikam (for example) is all you need to do.

The differences between the three packages you mention are that kdebase is the lightest possible install of the kde desktop, and only incudes basic programs like a text editor, terminal, etc. kde-core is virtually identical although it pulls in a few more kde packages. kubuntu-desktop, is the same as the other two, plus a selection of packages made by the kubuntu team to give a full desktop suite, plus some artwork.

---

### Post by tubasoldier on 2008-04-05
If you want to use KDE on your system then all you really need is kdebase and kde-core. kde-desktop is a metapackage for loads of software.
Hope this helps

---

### Post by harrybazeegar on 2008-04-05
@benerivo
yesyes... i had an error "need mp3 play back suppor" and then it froze... i google it around and found that this is a common error... too bad i removed it immediately :(

@tubasoldier
ok... actually i installed kde using sudo apt-get install kde... and i got a whole lot of packages,..
so i removed the extra ones using sudo apt-get autoremove (this removed about 350 megs of stuff )

---

