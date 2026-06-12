---
title: "Failed to install World of Warcraft!"
date: 2005-07-04
forum: Gaming &amp; Leisure
---

### Post by granite230 on 2005-07-04
*removed*

---

### Post by granite230 on 2005-07-04
Hm never mind... I put cd 1 back in, tried to run the installer again and now the screen says: Play World of Warcraft. Not Install World of Warcraft.
I'm downloading the updates as we speak.

---

### Post by granite230 on 2005-07-04
Okay I'm done with the updates, I changed screen resolution to 1024x768, everything looks perfect now. BUT!

I can't select enemies with my right mouse button, so I have to use tab instead to select the nearest enemy. Also, I can't loot anything... plus I cant talk to quest-givers. That doesn't mean my right mouse button is broken because I also cant select enemies/friends with my left mouse button and I do have the possibility to whisper to friends using my right mouse button.

Anyone knows how to fix this?

---

### Post by Gags666 on 2005-07-05
Yes, there's a fix for this problem:

[quote="[Gentoo-Forum](http://forums.gentoo.org/viewtopic-t-246098-postdays-0-postorder-asc-start-200.html)"]Ello there,

Looks like i have been a bit rash with my conclusions as to what is going
on and why. After some more testing, it appears, that the printf in the init
function somehow makes the problem disappear, but the conclusion remains
the same in my view: memory corruption.

Any way, i have reduced my little workaround to this:
---------------libmemwrapper.c-------------------------------------
#include <stdio.h>
#include <malloc.h>

/* Prototypes for our hooks. */
static void my_init_hook(void);

/* Override initialising hook from the C library. */
void (*__malloc_initialize_hook) (void) = my_init_hook;

static void
my_init_hook(void)
{
printf("using wrapped malloc\n");
}
----------------------------------------------------------------------------

compile with:

gcc -fPIC -shared -o libmemwrapper.so libmemwrapper.c

and

export LD_PRELOAD="path to lib"/libmemwrapper.so

in the terminal window, where you start wine. Dont put
it in your login shell init scripts of course, should only
be loaded for wine when running wow.
Give it a try and see, if it works for you.

Yours sincerely,

Shamus[/quote]

---

### Post by granite230 on 2005-07-05
okay that's nice to hear!

I made a file with gedit and named it libmemwrapper.c, I saved it in my home folder. Then I tried: 

granite@granite:~ $ gcc -fPIC -shared -o libmemwrapper.so libmemwrapper.c
libmemwrapper.c:1:19: stdio.h: No such file or directory
libmemwrapper.c:2:20: malloc.h: No such file or directory

how is this possible?

---

### Post by Gags666 on 2005-07-06
Mhm... don't know exactly. Do you have the *build essentials* installed? Maybe this helps.

---

### Post by granite230 on 2005-07-06
I received this message from the person who also gave us the tip mentioned above.
He says:

It looks like, you
only have the core compiler installed and none of the
standard libraries. This is possible to do, but it only makes
sense, when you are compiling for embedded systems and
such.
You need to find install the packages with these libraries,
before you can compile much at all. I cant tell you which
packages to install, i only know ubuntu by name and rep. 

So, here in the Ubuntuforums I hope somebody can tell me what this guy is actually talking about. I don't know what to do with this tip. Maybe anyone can give me a detailed explanation what to do now?

I'm almost there! If I can get my compiler to work, I can also get WoW to work!

---

### Post by rutty on 2005-07-07
You might not need to compile anything. What are you running WoW under? Cedega/Point2Play or the WineX CVS? There's a FAQ on the transgaming forum on how to fix the mouse issue:

[http://transgaming.org/forum/viewtopic.php?t=3149](http://transgaming.org/forum/viewtopic.php?t=3149)

It's fairly simple to implement and doesn't require any compilation.

---

### Post by granite230 on 2005-07-07
It works!!

Here's the solution: 

Two work arounds have been discovered for the mouse selecting issue that has occurred since the World of WarCraft 1.5.1 patch.

1) This workaround may not work on all distros, may prevent other games (such as Half-Life 2) from running but should not cause a speed decrease.
open a console/terminal window and run
export WINEPRELOADER_SETVALEGACY="no"
then launch Cedega or Point2Play from the same terminal window.
This would need to be set each time you open a new terminal window to play the game.

2) This workaround should work for all users on all distros but may cause a frame rate drop.
Edit the World of WarCraft configuration file with your favorite text editor:
command line users: /home/USERNAME/.transgaming/config
Point2Play users: /home/USERNAME/.point2play/configuration_profiles/NAME_OF_WOW_CONFIG
Add the following section to the config file:
[AppDefaults\\wow.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
This change will remain persistent as long as you continue to use that configuration file for World of WarCraft. This change may need to be removed for future versions of Cedega.

The first one worked for me!  :grin:

---

