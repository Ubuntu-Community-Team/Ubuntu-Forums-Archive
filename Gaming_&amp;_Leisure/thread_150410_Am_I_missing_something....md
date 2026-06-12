---
title: "Am I missing something...?"
date: 2006-03-26
forum: Gaming &amp; Leisure
---

### Post by Wallakoala on 2006-03-26
So I downloaded the cedega timedemo, I installed it, and registered for the 14 day trial. No problems there. So now, I see that Battlefield 2 is an officially supported game. I pop in my BF2 cd #1 and start installing the game (no problems here either). 

Here comes the problem. I installed the game, but I have no clue how to actually play it. It says "Battlefield 2" very nicely on the left side of the window, but the big button that says "Play" is grayed out, so I cannot play the game.

I am confused.

Also, when I installed the timedemo, I installed it as root, but it put the Transgaming_drive in my home directory. After looking in there, I see no signs of Battlefield 2 ever installing. I have repeating the process of installing battlefield 2, with no success.
I have also trying reinstalling the cedega timedemo, with no success.

Am I missing something? Is there something else I have to do?

---

### Post by akiro.yamamoto on 2006-03-26
This is how it should look.
Notice the icons on the right side.
When the appropriate icon is highlighted the Play button is no longer grayed out.
Hope this pic helps ;)

---

### Post by Wallakoala on 2006-03-26
[QUOTE=akiro.yamamoto]This is how it should look.
Notice the icons on the right side.
When the appropriate icon is highlighted the Play button is no longer grayed out.
Hope this pic helps ;)[/QUOTE]

yeah, I understand. The problem is, after installing this game 3+ times, the stuff on the right side is not there

---

### Post by simplyw00x on 2006-03-26
Does it actually run the BF2 installer when you've selected it?

---

### Post by DoktorSeven on 2006-03-26
The Cedega GUI is a pain.

Do:

```

mount /media/cdrom
cedega /media/cdrom/setup.exe # or whatever the setup program for BF2 is
cedega ~/TransGaming_Drive/Program\ Files/Whatever/the/path/to/battlefield.exe

```

Bypass the GUI and do it via straight commandline.  I always get the best results that way.  Bit more work, but much better results.

---

### Post by Wallakoala on 2006-03-29
[QUOTE=DoktorSeven]The Cedega GUI is a pain.

Do:

```

mount /media/cdrom
cedega /media/cdrom/setup.exe # or whatever the setup program for BF2 is
cedega ~/TransGaming_Drive/Program\ Files/Whatever/the/path/to/battlefield.exe

```

Bypass the GUI and do it via straight commandline.  I always get the best results that way.  Bit more work, but much better results.[/QUOTE]

I can't do it via command line because the cedega timedemo just installs the cedega_timedemo program which essentially the gui-ified version.

The installer ran perfectly, it just didn't install anything (it seems)

---

### Post by funkenstein on 2006-03-30
ya have to look under Transgaming_Drive (or something along those lines) in order to to see the windoz directory/file structure. 

Before you install bf2 - make sure that under the extended options you select to run the game under a winxp environment, pixel shaders 1.4 and the sound needs to be full duplex.

After that, can you pls post a screenie of what your cedega window looks like when you've installed BF2, and clicked where it says Battlefield 2 (or whatever name you called it...)


PS: A little gotcha: If you wanna install a patch, you click install and under the program name, you select the name of the game that's already installed. don't forget to set all the same options again.... it's annoying, but worth it... unless you get the unknown windows api call error from PB... but lets take it 1 step at a time...:rolleyes:

---

