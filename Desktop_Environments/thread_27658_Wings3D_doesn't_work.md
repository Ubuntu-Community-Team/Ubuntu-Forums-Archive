---
title: "Wings3D doesn't work"
date: 2005-04-17
forum: Desktop Environments
---

### Post by KDE-fan on 2005-04-17
I just tried to install Wings3D from the Ubuntu Universe, and it simply didn't work. Have anyone else managed to get this one working, or is the package broken? 
 
I have fortunately managed to install POV-Ray (my favorite renderer) on my own, but shouldn't there be a package for this great software in the Ubuntu Universe as well?

---

### Post by KDE-fan on 2005-04-17
Here is the message I get when I try to start it: 
 
 > Erlang (BEAM) emulator version 5.4.2.1 [source] [hipe] [threads:0] 
 
Eshell V5.4.2.1  (abort with ^G) 
1> Driver Failed {error,{open_error,"/usr/lib/erlang/lib/esdl-0.94.0615/priv/sdl_driver.so: cannot open shared object file: No such file or directory"}} 
 
=ERROR REPORT==== 17-Apr-2005::14:21:48 === 
Error in process <0.31.0> with exit value: {badarg,[{erlang,port_control,[esdl_port,21,<<4 bytes>>]},{sdl,init,1},{wings_init,init,0},{wings,init,1}]} 
 
Fatal internal error - log written to /home/gul/wings_crash.dump 
sh: line 0: exec: sdl_driver: not found  
 
From the wings_crash.dump 
 
> Dump written 2005-4-17_14-21 
Window: "<Unknown Window Name>" 
Crashed in: 
{badarg,[{erlang,port_control,[esdl_port,21,<<32,0,16,0>>]}, 
         {sdl,init,1}, 
         {wings_init,init,0}, 
         {wings,init,1}]}

---

### Post by KDE-fan on 2005-04-17
Seems like the Erlang package is broken...

[http://www.ubuntuforums.org/showthread.php?t=7417&highlight=wings3d](http://www.ubuntuforums.org/showthread.php?t=7417&highlight=wings3d)

---

### Post by KDE-fan on 2005-04-17
[QUOTE=KDE-fan]Seems like the Erlang package is broken...

[http://www.ubuntuforums.org/showthread.php?t=7417&highlight=wings3d](http://www.ubuntuforums.org/showthread.php?t=7417&highlight=wings3d)[/QUOTE]
 FIXED! I installed it 100% manually, and it actually worked perfectly. I still think there should be a package that can be installed through kynaptic though.

---

### Post by joebar on 2005-06-08
For what I've seen, there's just one file missing : 
/usr/lib/erlang/lib/esdl-0.94.0125/priv/sdl_driver.so
I copied it from my gentoo install and it worked :) 

So I've put it on a public repository : you get get it from [http://glcomp.free.fr/divers/sdl_driver.so](http://glcomp.free.fr/divers/sdl_driver.so) if you want to.

As there are all the sources, there sure should be a way to recompile it, but the makefile doesnt have a 'lib' or whatsoever target... 
Anyway a bug should be filed against this. I'm gonna have a look at it.

Hope it helps.

---

### Post by meldroc on 2005-06-08
[QUOTE=joebar]For what I've seen, there's just one file missing : 
/usr/lib/erlang/lib/esdl-0.94.0125/priv/sdl_driver.so
I copied it from my gentoo install and it worked :) 

So I've put it on a public repository : you get get it from [http://glcomp.free.fr/divers/sdl_driver.so](http://glcomp.free.fr/divers/sdl_driver.so) if you want to.

As there are all the sources, there sure should be a way to recompile it, but the makefile doesnt have a 'lib' or whatsoever target... 
Anyway a bug should be filed against this. I'm gonna have a look at it.

Hope it helps.[/QUOTE]
 Just tried the sdl_driver.so file.  IT WORKS!!!  By all means, file that bug report so Wings3d can be officially fixed.

---

### Post by cheleb on 2005-06-19
[QUOTE=meldroc]Just tried the sdl_driver.so file.  IT WORKS!!!  By all means, file that bug report so Wings3d can be officially fixed.[/QUOTE]
Works for me too. Thank you KDE-fan.

I filed a bug report [here](https://launchpad.ubuntu.com/malone/bugs/1088).

Cheers,
cheleb

---

