---
title: "Underperforming computer"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by spadewarrior on 2008-12-29
I am getting a lot of slowdown/framedrop in Urban Terror 4.1 on my computer. My computer's specs are listed below in my signature. 

Although a few years old, I would have thought that I should get a fairly constant 70FPS+ on my computer. In fact, many people I have spoken to in-game have said as much. Instead I get about 50-60 when, say, facing a wall, and drops to as low as 20FPS on a full server. This is extremely noticeable and makes playing difficult even after downgrading the graphics and playing in 800x600...:(

Any ideas?
edit:
Oh, also, glxgears gives me
[PHP]
32954 frames in 5.0 seconds = 6590.613 FPS
32817 frames in 5.0 seconds = 6563.379 FPS
32905 frames in 5.0 seconds = 6580.830 FPS
32835 frames in 5.0 seconds = 6566.981 FPS
32802 frames in 5.0 seconds = 6560.230 FPS
32908 frames in 5.0 seconds = 6581.516 FPS
32875 frames in 5.0 seconds = 6574.978 FPS[/PHP]

---

### Post by curvedinfinity on 2008-12-29
What resolution are you playing the game at? I have a 7600GT on my desktop, so I'm familiar with its performance -- those numbers sound about right for something like 1440x900. Try running at a lower resolution if that's the case. :)

---

### Post by spadewarrior on 2008-12-29
Hello, thanks for the reply.

My monitor (Proview 565 LCD) is quite unsophisticated and the only resolutions I can get are 800x600 and 1024x768... I tried turning down to 600x480(?) but it was 'out of range' (800 looked bad enough...).

---

### Post by curvedinfinity on 2008-12-29
Hmm ... that resolution should be good. Your problem has me stumped. I seem to remember playing Urban Terror at reasonable performance (though it was sluggish in some big outdoors scenes).

Perhaps its time for an upgrade? A 9800 GT is like $100 and about four times faster than a 7600 GT.

Maybe someone else has a suggestion...

---

### Post by spadewarrior on 2008-12-29
Can't afford it, unfortunately. Plus, I don't have PCI-Express.

---

### Post by Coreigh on 2008-12-29
I am not familiar with the game but is it possible the slowdown/bottleneck is not the video card? Your GLXGears numbers seem pretty good and unless I really don't understand something ~70fps should give smooth playback BUT... if the bottleneck is not the video card it won't matter how smooth the playback is if the game engine or some other process is getting bogged down.

---

### Post by spadewarrior on 2008-12-29
Is there any way to work out what it might be?

---

### Post by maddog46113 on 2008-12-29
> **spadewarrior said:**
> I am getting a lot of slowdown/framedrop in Urban Terror 4.1 on my computer. My computer's specs are listed below in my signature. 

Although a few years old, I would have thought that I should get a fairly constant 70FPS+ on my computer. In fact, many people I have spoken to in-game have said as much. Instead I get about 50-60 when, say, facing a wall, and drops to as low as 20FPS on a full server. This is extremely noticeable and makes playing difficult even after downgrading the graphics and playing in 800x600...:(

Any ideas?
edit:
Oh, also, glxgears gives me
[PHP]
32954 frames in 5.0 seconds = 6590.613 FPS
32817 frames in 5.0 seconds = 6563.379 FPS
32905 frames in 5.0 seconds = 6580.830 FPS
32835 frames in 5.0 seconds = 6566.981 FPS
32802 frames in 5.0 seconds = 6560.230 FPS
32908 frames in 5.0 seconds = 6581.516 FPS
32875 frames in 5.0 seconds = 6574.978 FPS[/PHP]

It might be a problem with your overclock. My p4 was overclocked to 2.8 and it actually performs better at 2.6 it is 2.4 orig. Your processor might be throttling or your memory isnt handling it right. Do you have problems with things crashing out of nowhere? I would try taking your clock down to 2.8 or 2.9 and see if that helps any. If your process reaches 70oC it throttles. So if your running a stock heatsink that could be creating your problem and possibly cause damage eventually. Try running the memtest86 at boot to see if its a memory problem. I dont think its your video card.


EDIT** Also check your bios make sure spread spectrum is off. and lock your clocks If its agp/pci motherboard, then lock your pci/agp speeds. It possibly could be your agp overclock. When your hardware gets too much juice it under-performs. Ive been an overclocker for years.

---

### Post by spadewarrior on 2008-12-29
I'll give it a go. Thanks.

---

### Post by spadewarrior on 2008-12-30
OK, I've had a fiddle with various different combinations of overclocked/non-overclocked between the GPU and CPU. Still no real difference unless I crank up the GPU, but then it crashes. About to investigate the memtest cd.

---

### Post by maddog46113 on 2008-12-31
Thats odd, Make sure your drivers are up to date. Turn off compiz when running the game. I use Compiz Fusion Icon. Urban terror runs fine on my old *** Radeon 9200. If you still have problems try running prime95 Torture test on your PC while its overclocked. The only thing about prime95 is that you need to let it run a long time. It will report any processor related problems to you. I always let prime95 run for at very very least 6 hours on a newly overclocked PC. I recomend letting it run for 24 hours though. 

[http://www.mersenne.org/ftp_root/gimps/mprime258.tar.gz](http://www.mersenne.org/ftp_root/gimps/mprime258.tar.gz)

run it from your home folder. 

```
./prime95 -t
```

Watch your temps for about 30 minutes make sure you dont overheat it will torture the hell out of your PC. If you overheat that right there tells you your clock is too high.

---

### Post by spadewarrior on 2008-12-31
Thanks, looks like a good program to set running before I go out tonight....

I never run compiz; normally I use openbox or xfwm which I think have fairly low requirements. Also, I just cleaned out my computer with a can of compressed air. I'm not sure it's made any performance difference but the fans sound less tortured...

Not tried a memtest yet. How long should I run one for?

---

### Post by grazzt on 2008-12-31
I have a computer very similiar to yours (amd 3200, ati 800xl agp card) with very similiary glxgear results (ie 6500-6900 fps), and I just ran the game, and on an 18 player ctf server I was getting minimum 70 fps, and most of the time 90 fps.

Maybe try reinstalling the game and/or drivers?

(just posting this to let you know similiar hardware and the game should be playable)

---

### Post by spadewarrior on 2008-12-31
Hmm. Interesting. What resolution was that at? 

I've reinstalled the game countless times - mainly just trying to fix a different issue. I might try installing the driver with Envy to see if that improves anything.

---

### Post by grazzt on 2008-12-31
Whatever the defaults were.. Im guessing 800x600 @ 32 bpp or whatever.

And this is with compiz still running.  I just played it again, 24 player ctf, and once again, rarely went below 60, most of the time 90s. <shrug>

---

### Post by maddog46113 on 2009-01-01
> **spadewarrior said:**
> Thanks, looks like a good program to set running before I go out tonight....

I never run compiz; normally I use openbox or xfwm which I think have fairly low requirements. Also, I just cleaned out my computer with a can of compressed air. I'm not sure it's made any performance difference but the fans sound less tortured...

Not tried a memtest yet. How long should I run one for?

Run the memtest86 option on grub let it complete it will take a while.

---

### Post by sad_iq on 2009-01-02
Urban Terror is a pretty stressing application on the videocard(might be an OpenGL issue), make sure you use 16 bpp xorg, and ingame. Also...turn off blood, particles, smoke and any other eyecandy that this game has, they help a bit in gettin some extra FPS :P
 I have a P4 2800 and a 7800GS(slightly better than yours), and I have tweaked my autoexec.cfg and I play at pretty much stable 100-125 FPS on this baby :)
 Here's my 2 configs...do read the warnings!!!
 Autoexec.cfg--->[http://paste.ubuntu.com/98330/](http://paste.ubuntu.com/98330/)
 mouseconfig.cfg--->[http://paste.ubuntu.com/98332/](http://paste.ubuntu.com/98332/)

Use some of what I tested, test some on your own and tell me if any improvements were made.Also note I use a BIG resolution, anisotropy filtering, and 24 bpp ingame....TWEAK those files!!!

---

### Post by spadewarrior on 2009-01-02
Thanks for that. I've started tinkering with the autoexec file. Is there anything I'm obviously missing here?

Also, I took my HD and GPU round to a friend's house (who has 1gb RAM and an Athlon XP 2400ghz processor) and the game ran a lot smoother. So it's presumably either my cpu or ram...

[PHP]//In this file you can do settings that will be executed everytime Urban Terror is started. It will not get overwritten.

//Lines starting with // are ignored.

//Example1: exec yourconfig.cfg

//Example2: set cg_fov "110"



bind x ut_weaptoggle knife



//TWEAK to YOUR needs...DON'T COPY-PASTE this as it will have severe 

//consequences



//set r_customwidth "1680" // custom resolution...you don't need this

//set r_customheight "1050" // custom resolution...you don't need this

set r_picmip                          "0" // 1 and 2 look horrible

set com_blood                         "0" // turns to 1 in mouseconfig

set com_maxfps                        "125"

//set com_hunkMegs                      "786" //saves 786 MB from memory for URT

set cg_shadows                        "2"

set ui_smallFont                      "0.25"

set ui_bigFont                        "0.4"

set s_useopenal                       "0"

set r_displayrefresh                  "0"

//set r_textureMode                     "Low Billinear" //283 FPS

//set r_textureMode                   "GL_LINEAR_MIPMAP_LINEAR" //273

//set r_textureMode                   "GL_LINEAR_MIPMAP_NEAREST"  //263

set r_decals                          "0"

set r_flares                          "1"

set cg_marks                          "0"

set cg_brasstime                      "0"

set r_primitives                      "2"// 1 really kills FPS...3 really screwes textures up(90%black)

set r_lodbias                         "1"// 0 makes no difference--->needs more testing

set cg_sfxbrasstime                   "0"

//set net_port                          "27961"

set cg_marktotaltime                  "0"

set cl_lanForcePackets                "1"



//nexu's config - modified



set cl_maxpackets                     "42"

set rate                              "25000"

set snaps                             "20"

set cg_antilag                        "1"

set cl_packetdup                      "1"

set ut_timenudge                      "0"

set ttycon_ansicolor                  "1"

set cl_drawclock                      "1"

set cg_maxFragments                   "16"

set cg_predictitems                   "1"

set cg_smoothClients                  "1"

set cg_zoomfov                        "22.5"

set cg_zoomWrap                       "1"

seta r_maxpolys                       "1100" //was 1200

seta r_maxpolyverts                   "6000"

set r_customPixelAspect               "0"//1 is about 0.01% worse

set r_swapinterval                    "0"

set r_dlightBacks                     "0" //1 is worse

set r_dynamiclight                    "0"

set r_vertexLight                     "0"//1 is about 0.01% worse

set r_depthbits                       "24" //was at 16--->needs more testing

set r_detailtextures                  "0"//0 is about 0.01% worse

set r_directedScale                   "1"//0 is about 0.01% worse

set r_ext_compiled_vertex_array       "1"

set r_ext_compressed_textures         "1" // 0 is worse

set r_ext_gamma_control               "1"

set r_ext_max_anisotropy              "0"// was at 0....USE 0 on low-end PC's

set r_ext_multitexture                "1"

set r_ext_texture_env_add             "1"//0 doesn't change FPS

//set r_ext_texture_filter_anisotropic  "0"

set r_facePlaneCull                   "1" // 0 is worse

set r_fastsky                         "1"// 0 is worse

set r_finish                          "0"// 0 really boosts FPS (from 283 to 357)

set r_flares                          "1"//0 is worse

set r_gamma                           "1.55"

set r_ignoreFastPath                  "0"//1 is worse

set r_ignorehwgamma                   "0"//1 is about 0.01% worse--->needs more testing

set r_intensity                       "1"//0 is about 0.01% better!!!

set r_lightmap                        "0"//1 makes all textures white--->interesting???

set r_lodbias                         "2"//0 really kills FPS,1 is about 0.01% worse,2 is ok

set r_stencilbits                     "8"// 0 has no FPS impact 

set r_allowExtensions                 "1"//0 really kills FPS

set r_ambientScale                    "0.6"

set r_colorMipLevels                  "0"//0  is about 0.01% worse--->1 causes corruption in the Start Menu

set r_inGameVideo                     "0"

set r_roundImagesDown                 "0"//1 and 2 are about 0.01% worse

set cg_showbullethits                 "2"

set cg_sfxParticles                   "0"// turns to 1 in mouseconfig

set cg_sfxSurfaceImpacts              "0"// turns to 1 in mouseconfig





//exec mouseconfig.cfg

[/PHP]

---

### Post by sad_iq on 2009-01-02
It seems you're also using a really old driver version for your card...can u update them??
 My glxgears have waay better numbers there(I use latest beta driver from nvidia.com):```
52666 frames in 5.0 seconds = 10533.147 FPS
52764 frames in 5.0 seconds = 10552.682 FPS
52697 frames in 5.0 seconds = 10539.335 FPS
52626 frames in 5.0 seconds = 10525.147 FPS
``` so maybe your card is the bottleneck for this game.
 Also...from my autoexec config you removed **set r_textureMode                     "High Trillinear"**, which made UrT run better for me...try to add it back and see if it works better.You could try to modify theese things, one at a time!!!, and do a ```
/timedemo 1
/demo tutorial
``` in urt to see how many FPS you get:
```
set r_picmip                          "2"//try with 1 also
set cg_shadows                        "0"//disable any shadows
//set r_textureMode                     "Low Billinear" //do you get more FPS with this????if so uncoment the line for it to work
set r_maxpolys                       "1100" //revert to 1200???
set r_depthbits                       "16"//16bpp color...you were using 24
set r_detailtextures                  "1"

```
Like I said...add or modify those lines one at a time...and don't enter random numbers in there, since UrT will use the defaults for the option you use which is not always better for low-end pc's :(
Also test the frames you get after every modification of your autoexec.cfg or all this is useless :(

---

