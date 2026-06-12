---
title: "howto setup gtkradiant in ubuntu"
date: 2012-05-15
forum: Gaming &amp; Leisure
---

### Post by alterpinguin on 2012-05-15
there was already such a thread, but it was closed (dont know why, cause radiant is not dead)
the old thread was there, with last valuable hint for setup:
> [http://ubuntuforums.org/showpost.php?p=11550517&postcount=23](http://ubuntuforums.org/showpost.php?p=11550517&postcount=23)

based on this last posting
there are some new changes.

first the differences between old and newer gtkradiant versions are most for the type/kind of install procedure and the supported games.

the icculus game-pack (in the posting above) shows what games possible.
( [http://svn.icculus.org/gtkradiant-gamepacks/](http://svn.icculus.org/gtkradiant-gamepacks/) )

I did use the current (date: may.10.2012) git repository for the new version (called zeroradiant - version 1.6).

the compile is still done with scons:
(if you dont have it you have to install it first, and i dont know what develop-libs all needed, because i had not to install any, but this is for my system ubuntu-10.04 64bit, where already a lot of develop-libs are installed)

If i have time (and fun) i will try a setup for openarena, but up to this
i did only a minimal setup for enemy-territory type of game.

For this one need the huge gamepack (link above in gamepacks) called ETPack and install(copy) it in the gtkradiant source in directory:
.../install/installs
so there is a
.../install/installs/ETPack

after built of gtkradiant (most time a simple "scons" does it)
in source main-directory
scons target=radiant,q3map2 config=release
and the built has all necessary dev-libs to compile
the result to start is in
.../install
named
.../install/radiant.bin

at the first start of this, it wants the setup config,
(in a graphic gui, that comes first automatic)
i did it for gametype enemy-territory and for the setting
of the path one has to enter the path to the
enemy-territory subdirectory "etmain".

If you have a default old kind enemy-territory install,
you may already know what this is.

I used etxreal, but there is an etmain directory too.

If this setup works, then radiant wants to open a
project-file. (this is a nice "ironic" thing, how to get
one, if one cannot create a new empty one?) There is
already a default project-file in the directory of
the ETPack. Select this.

After this radiant will go on, but may throw an error
if the etmain directory could not be found (from the setup).

It may run in such cryptic error message
about a missing texture setup for "notex" and i always
thought first this is a kind of "no textures available .."
But its the graphic-image called "notex" (of the default
project with some simple map and this setting).

The texture itself is in the .../installs/Q2WPack/install/default/textures/radiant/notex.tga (for example)
but the error-messages indicates that the setup (the path for the etmain directory with its subdirectories "maps" and "scripts" ?and "models" is missing. That is, normaly maps compiled to *.bsp dont need to be put into a pk3-file to be loaded, those can be loaded in the engine running the default etmain(-mod) from the path ../etmain/maps.

If i use this gtkradiant (zeroradiant) more and not only for checking my blender-3d output, then i will add new results how i use a working setup for etxreal (in old et-compat-mode).

For those interested what i do with blender-3d about this (including simple map-building) there is a thread at blenderartists.org:
> [http://blenderartists.org/forum/showthread.php?244585-md3-mdm-mdx-import-export-quake-style-models-and-etxreal(otc6-mod](http://blenderartists.org/forum/showthread.php?244585-md3-mdm-mdx-import-export-quake-style-models-and-etxreal(otc6-mod))

incl. videos and pictures etc.

about the older setup for openarena,
i did found this thread with some hints:
> [http://openarena.ws/board/index.php?action=printpage%3Btopic=2787.0](http://openarena.ws/board/index.php?action=printpage%3Btopic=2787.0)

and last,
special thanks goes to king arthurs wizard for the online help to fix my zeroradiant install.

---

