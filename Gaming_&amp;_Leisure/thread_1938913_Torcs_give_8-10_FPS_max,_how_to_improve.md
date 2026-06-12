---
title: "Torcs give 8-10 FPS max, how to improve?"
date: 2012-03-10
forum: Gaming &amp; Leisure
---

### Post by mastablasta on 2012-03-10
So i actually can play torcs, but frame rate  (FPS) is terrible. How could i imporve it? i already tried a smaller resolution (the smallest actually), but it seems the FPS stays the same as at deafult screen sresolution which is 1680x1050. How could i improve the FPS?

```
 display:0
                description: VGA compatible controller
                product: M10 NQ [Radeon Mobility 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:b0000000-bfffffff ioport:e000(size=256) memory:feae0000-feaeffff memory:feac0000-feadffff
```

(actually the GPU is 9600XT or 9800XT with 256 MB RAM)

and CPU is dual core Intel(R) Celeron(R) CPU  E3300  @ 2.50GHz

i have 1.3 GB RAM, running Kubuntu 10.10, opensource drivers.

glxgears show FPS at about 59.
(is there another benchmarking tool i could use?!)

---

### Post by madjr on 2012-03-11
u tried playing on a window?

and do u have the open source or proprietary drivers?

---

### Post by mastablasta on 2012-03-11
yes i did. i tried with windowed mode with resolution 640x480 - gave me same FPS as with  max screen res (8-10).

opensource drivers - this card was abandoned by ATI/AMD. is there a setting that could improve FPS? usualyl commercial widnows games have a bunch of settigns you can use to tweak performance. for example i managed to run with this card Oblivion with mid-high settings using tweaks. while here in linux games i see there is often screen resolution, fullscreen/widnowed and that's usually about it in the game's menues. 

Haven't tried nexuiz (or whatever the fork is now called) but urban terror, saurebraten and similar games work OK.

---

### Post by madjr on 2012-03-11
> **mastablasta said:**
> yes i did. i tried with windowed mode with resolution 640x480 - gave me same FPS as with  max screen res (8-10).

opensource drivers - this card was abandoned by ATI/AMD. is there a setting that could improve FPS? usualyl commercial widnows games have a bunch of settigns you can use to tweak performance. for example i managed to run with this card Oblivion with mid-high settings using tweaks. while here in linux games i see there is often screen resolution, fullscreen/widnowed and that's usually about it in the game's menues. 

Haven't tried nexuiz (or whatever the fork is now called) but urban terror, saurebraten and similar games work OK.

isnt torcs kinda abandoned ?

there is a fork, called speed dreams, which you could try:

[http://www.webupd8.org/2011/10/speed-dreams-racing-game-20-released.html](http://www.webupd8.org/2011/10/speed-dreams-racing-game-20-released.html)

repost here if it worked for you :)

---

### Post by mastablasta on 2012-03-18
same issue. the configuraiton options are realyl missing stuff. such as keybaord (input) configuration.
although the game works normally in practice run (well 30-35FPS) it again runs at 5-6FPS in normal race. now considing the system requirements are much lower than this mashcine i am kind of dissapointed. 

ofcourse not having ther GPU recognised propperly is probably not helping.

---

### Post by kingtiger01 on 2012-04-12
its because youre not using the Proprietary drivers. FGLRX, has the GLX extension. The opensource one last i checked uses software-gl.

Which is about as slow as you can get depending on Cpu-ram-chipset.

Now, that is not saying, its not possible to get GLX Hardware-Rendering. You need to verify it first.

in a Terminal window, type the following(without the "")
"glxinfo | grep rendering"

if you get back 
"direct rendering: Yes"

Youre all set and we need to focus on how to improve performance of GL on youre setup.

If you get back any issues with "direct rendering:" then we need to focus on how to get Hardware Acceleration enabled.

----

Remember, for running OpenSource Drivers. Id suggest keeping youreself on the [Xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") PPA

PLEASE NOTE: though its updated more often, this also means more problems. it can be unstable and BREAK THINGS. but dont let that make you fear using it. ive been using it in my test enviorment for years, and it rarely causes problems UNLESS im running proprietary drivers(and Xserver-xorg updates a core version)

ALSO: For a more stable alternative, there is [X-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Although, there no where near as updated as Xorg-Edgers. They usually have the same packages as the Development Distribution(At this time, its [PrecisePangolin{12.04}]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule"))
-----
Note:[Radeon Driver Hompage]("http://wiki.x.org/wiki/radeon")
Note 2: I get 980+fps on glgears, when running fglrx with my 5750. But when i use the radeon drivers i get a average of 48-70, because they had to reverse-engineer the fglrx drivers.

---

### Post by kingtiger01 on 2012-04-12
> **madjr said:**
> isnt torcs kinda abandoned ?

there is a fork, called speed dreams, which you could try:

[http://www.webupd8.org/2011/10/speed-dreams-racing-game-20-released.html](http://www.webupd8.org/2011/10/speed-dreams-racing-game-20-released.html)

repost here if it worked for you :)

i decided to keep this separate.

Torcs is NOT abandoned, i get [DEV] updates bi-weekly. They dont work on performance/qaulity. But do work on adding features. But there small and lack dedicated developers.

you want to improve it be my guest... but its running OGL 1.3, and its rendering platform is EXTREMELY out of date by comparison.

Torcs vs Speed-dreams fork
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Speed_Dreams_vs_TORCS_-_reflections.png/960px-Speed_Dreams_vs_TORCS_-_reflections.png[/IMG]

Thats what i mean by example... They dont do the bleeding-edge work they were trying a long time ago now.

---

