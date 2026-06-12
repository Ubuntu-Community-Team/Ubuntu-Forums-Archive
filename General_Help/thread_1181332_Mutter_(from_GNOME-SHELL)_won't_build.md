---
title: "Mutter (from GNOME-SHELL) won't build"
date: 2009-06-07
forum: General Help
---

### Post by damis648 on 2009-06-07
The following happens when jhbuild tries to build mutter:
```
cc1: warnings being treated as errors
default.c: In function ‘switch_workspace’:
default.c:381: error: passing argument 2 of ‘clutter_actor_get_position’ from incompatible pointer type
default.c:381: error: passing argument 3 of ‘clutter_actor_get_position’ from incompatible pointer type
default.c:382: error: passing argument 2 of ‘clutter_actor_get_size’ from incompatible pointer type
default.c:382: error: passing argument 3 of ‘clutter_actor_get_size’ from incompatible pointer type
default.c: In function ‘maximize’:
default.c:566: error: passing argument 2 of ‘clutter_actor_get_size’ from incompatible pointer type
default.c:566: error: passing argument 3 of ‘clutter_actor_get_size’ from incompatible pointer type
default.c:567: error: passing argument 2 of ‘clutter_actor_get_position’ from incompatible pointer type
default.c:567: error: passing argument 3 of ‘clutter_actor_get_position’ from incompatible pointer type
make[4]: *** [default_la-default.lo] Error 1
make[4]: Leaving directory `/home/damian/gnome-shell/source/mutter/src/compositor/mutter/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/damian/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/damian/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/damian/gnome-shell/source/mutter'
make: *** [all] Error 2
*** error during stage build of mutter: ########## Error running make   *** [4/4]
```

I have tried building it manually, with no luck. Can anybody shed some light on the situation, or is the current version of mutter in the git repo just broken?

---

### Post by Cerberus108 on 2009-06-08
Same here. Maybe in a couple of days it will be solved silently, although it is unacceptable that 4 times on 5 this program won't build. They should create a division between experimental and unstable branches.

---

### Post by [h2o] on 2009-06-08
> **Cerberus108 said:**
> Same here. Maybe in a couple of days it will be solved silently, although it is unacceptable that 4 times on 5 this program won't build. They should create a division between experimental and unstable branches.
Since it is in heavy development, I think breakage from time to time has to be accepted and expected.

---

### Post by bobbocanfly on 2009-06-08
You could try editing the Makefile so that it doesn't build with the -Werror flag (which treats warnings as errors and is being used in the build-output you posted). Not sure which files to edit (never played with editing GNOME build stuff), but I'm sure if you ask in a gnome IRC channel, they'll be able to tell you. I'd be surprised if there wasn't a gnome-shell channel full of people that would know how to do this.

You could always just wait and hope it is fixed quite soon (it is fairly likely it will be). In any case, it'd be a good idea to make sure a dev knows this is happening (filing a bug, mailing or pinging one on IRC all seem to be good options).

---

### Post by damis648 on 2009-06-09
> **bobbocanfly said:**
> You could try editing the Makefile so that it doesn't build with the -Werror flag (which treats warnings as errors and is being used in the build-output you posted). Not sure which files to edit (never played with editing GNOME build stuff), but I'm sure if you ask in a gnome IRC channel, they'll be able to tell you. I'd be surprised if there wasn't a gnome-shell channel full of people that would know how to do this.

You could always just wait and hope it is fixed quite soon (it is fairly likely it will be). In any case, it'd be a good idea to make sure a dev knows this is happening (filing a bug, mailing or pinging one on IRC all seem to be good options).

I did that before I posted this actually, it works for a period of time, but then fails to continue compiling later on.

Ah well, it looks like I will have to wait.

---

