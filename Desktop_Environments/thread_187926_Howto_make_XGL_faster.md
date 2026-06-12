---
title: "Howto make XGL faster?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Tubbie on 2006-06-03
Hey,

I have installed XGL with Ubuntu Gnome on an ati 9550 videocard, but it is sooo slow.

When I try to open a program from the panel, i get a slow opening box. When bouncing with a window it also very slow at the end of the bounce.

OK, the videcard isn't really fast, but the werid thing is... that if i try the live cd from Kororaa Linux with XGL integrated, everything is really fast.

I have tried to set the texture filter on fast bij gconf-editor, but it doesn;t work and the CVS version of Compiz and XGL won't work at all by me.

Anyone has a solution of getting XGL run fast in Ubuntu Dapper Drake?

Tnx already!

---

### Post by jaymode on 2006-06-03
[QUOTE=Tubbie]Hey,

I have installed XGL with Ubuntu Gnome on an ati 9550 videocard, but it is sooo slow.

When I try to open a program from the panel, i get a slow opening box. When bouncing with a window it also very slow at the end of the bounce.

OK, the videcard isn't really fast, but the werid thing is... that if i try the live cd from Kororaa Linux with XGL integrated, everything is really fast.

I have tried to set the texture filter on fast bij gconf-editor, but it doesn;t work and the CVS version of Compiz and XGL won't work at all by me.

Anyone has a solution of getting XGL run fast in Ubuntu Dapper Drake?

Tnx already![/QUOTE]


Maybe try using AIGLX as that is supposed to be a little faster. Also, if you want you try with the cvs version of XGL/Compiz/Mesa from [www.compiz.net](www.compiz.net)

---

### Post by Tubbie on 2006-06-03
[QUOTE=jaymode]Maybe try using AIGLX as that is supposed to be a little faster. Also, if you want you try with the cvs version of XGL/Compiz/Mesa from [www.compiz.net](www.compiz.net)[/QUOTE]

I looked for this right away and this got my attention right away :???: 

My ati 9550 wil not work!

[I]Known to not work

**ATI: Radeon 9500 through X850 (r300 and r400 generations). Some issues with rectangular textures may be fixed in new DRM CVS, need to verify.**

ATI: Rage 128. Looks like driver locking issue.

ATI: Mach64. No DRM support in Fedora, still insecure.

Matrox: MGA G200 to G550. Needs at least a driver update to fix DRI locking. PCI cards probably have other issues as well.

nVidia: Any. No open DRI driver. Closed driver support coming soon though.

3dfx: Voodoo 1 and 2. No DRI driver.

ATI: Radeon 8500 through X850 with the closed fglrx driver. Uses an ancient version of the DRI driver API that can't work with the new driver loader. No ETA on closed driver support.

Anything without a free 3d driver.[/I]

---

### Post by jaymode on 2006-06-03
[QUOTE=Tubbie]I looked for this right away and this got my attention right away :???: 

My ati 9550 wil not work!

[I]Known to not work

**ATI: Radeon 9500 through X850 (r300 and r400 generations). Some issues with rectangular textures may be fixed in new DRM CVS, need to verify.**

ATI: Rage 128. Looks like driver locking issue.

ATI: Mach64. No DRM support in Fedora, still insecure.

Matrox: MGA G200 to G550. Needs at least a driver update to fix DRI locking. PCI cards probably have other issues as well.

nVidia: Any. No open DRI driver. Closed driver support coming soon though.

3dfx: Voodoo 1 and 2. No DRI driver.

ATI: Radeon 8500 through X850 with the closed fglrx driver. Uses an ancient version of the DRI driver API that can't work with the new driver loader. No ETA on closed driver support.

Anything without a free 3d driver.[/I][/QUOTE]

Ok so then I would go with trying the latest XGL/Compiz from the compiz.net; I have been using them and have seen a great improvement in usability and stability

---

### Post by Tubbie on 2006-06-03
I can't get the latest CVS version to work at all. Then my X server won't start at all :(

---

### Post by MetalMusicAddict on 2006-06-03
[QUOTE=Tubbie]Hey,

I have installed XGL with Ubuntu Gnome on an ati 9550 videocard, but it is sooo slow.

When I try to open a program from the panel, i get a slow opening box. When bouncing with a window it also very slow at the end of the bounce.

OK, the videcard isn't really fast, but the werid thing is... that if i try the live cd from Kororaa Linux with XGL integrated, everything is really fast.

I have tried to set the texture filter on fast bij gconf-editor, but it doesn;t work and the CVS version of Compiz and XGL won't work at all by me.

Anyone has a solution of getting XGL run fast in Ubuntu Dapper Drake?

Tnx already![/QUOTE]

Sounds as if your friction settings are set funny. Happened to me last time I installed Compiz. Everything is smooth right? Just _moves_ slow? Check out these [Compiz forums]("http://www.compiz.net/") for help.

---

