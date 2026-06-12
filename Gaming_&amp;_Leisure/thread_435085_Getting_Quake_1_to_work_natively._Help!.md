---
title: "Getting Quake 1 to work natively. Help!"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by ZeroXR on 2007-05-06
I saw the article at the following link: [http://doc.gwos.org/index.php/Quake_1]("http://doc.gwos.org/index.php/Quake_1")

I have a few questions.

I have searched my Quake CD and I can't find a game.dat file. Is it somewhere else? I have tried doing a WINE install to see if it installs, but no sign of a game.dat file in the WINE directory.

With the guide, it says to install Jorgen's GLQuake front-end to play, but on running the command in terminal... It  has the following errors in the Terminal:
```

FindFile: can't find gfx/pop.lmp
Playing shareware version.
FindFile: can't find gfx.wad
Error: W_LoadWadFile: couldn't load gfx.wad
```

What am I doing wrong? Anyone want to shed some light?

---

### Post by Sindwiller on 2007-05-06
GLQuake? Lol? Get Darkplaces instead: [http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

Simply copy over all ID1 stuff into your darkplaces dir respectively the darkplaces binares into the Quake dir. Then run it.

EDIT: And it seems that this guy has a really odd version of Quake, because the standard QC data isn't called game.dat, but progs.dat.

---

### Post by Sockerdrickan on 2007-05-06
pak0.pak and etc not .dat

---

### Post by ZeroXR on 2007-05-06
Alright, I have the darkspaces front end... but on running the command of: ```
./darkplaces-linux-686-glx -quake
``` I get the following message

"You make want to make want to consider adding
-basedir /path/to/game
to your launch commandline"

My id1 folder is located in /home/zeroxr/darkplaces/ directory, but when I used the command line code of: 

```
./darkplaces-linux-686-glx -quake -basedir id1
```

It returns a message that it can't find a directory of id1/id1

Am I missing something?

---

### Post by Sockerdrickan on 2007-05-06
Just place the binary and make it a execable binary by setting up permissions and put the id1 next to it containing the 2 .pak files

---

### Post by ZeroXR on 2007-05-06
Tux0r: Could you give an example of how that would work? 

Would it be something like below?

/quake/
--id1 folder
--darkplaces binary

---

### Post by DoktorSeven on 2007-05-06
You have a quake directory.  Inside it is the binary for darkplaces, and a subdirectory id1.

In the subdirectory id1 is where you have the PAK and cfg files.

So you have
quake (directory)
|_darkplaces-linux-686-glx (binary)
|_id1(directory)
--|_*.PAK (data files)
--|_*.cfg (cfg files)

---

### Post by ZeroXR on 2007-05-07
DoktorSeven: Thanks for the clarification! The only thing is... When I run the binary without the command parameters: -basedir it still gives me the error message of

```
You make want to make want to consider adding
-basedir /path/to/game
to your launch commandline
```

But when I add the parameters of -basedir ~/quake/id1/ I get the following

```
Quake Error: base gamedir /home/zeroxr/quake/id1/id1/ not found!

```

---

### Post by DoktorSeven on 2007-05-07
basedir should be the directory the executable is in, not the id1 subdirectory.

Try just -basedir /home/zeroxr/quake/

Still, it should work anyway if you're running it from the directory; are you running it as /home/zeroxr/quake/darkplaces-(etc), or after changing to ~/quake and running ./darkplaces-(etc) ?

---

### Post by ZeroXR on 2007-05-07
./darkplaces-linux-686-glx -quake -nocdaudio -window -basedir /home/zeroxr/quake/

That's the command I just used and I got the same message of

```
You make want to make want to consider adding
-basedir /path/to/game
to your launch commandline
```

---

### Post by DoktorSeven on 2007-05-07
Strange, since it does work for me.  I did compile my own version of darkplaces (an SDL/GL version) from source so the executable has a different name, but it should run the same.

Here's what the directory structure looks like:

```
$ ls -R
.:
darkplaces-sdl  id1

./id1:
autoexec.cfg  config.cfg  PAK0.PAK  PAK1.PAK

```

---

### Post by ZeroXR on 2007-05-07
Weird...

Did an ls -R on my quake dir...
```
.:
darkplaces  darkplaces-linux-686-glx  darkplaces-linux-686-sdl  id1

./darkplaces:
BSDmakefile               glquake.h           qtypes.h
bspfile.h                 gl_rmain.c          quakedef.h
builddate.c               gl_rsurf.c          render.h
cdaudio.h                 gl_textures.c       resource.h
cd_bsd.c                  host.c              r_explosion.c
cd_linux.c                host_cmd.c          r_lerpanim.c
cd_null.c                 image.c             r_lerpanim.h
cd_sdl.c                  image.h             r_light.c
cd_shared.c               image_png.c         r_light.h
cd_win.c                  image_png.h         r_lightning.c
ChangeLog                 input.h             r_modules.c
cl_collision.c            jpeg.c              r_modules.h
cl_collision.h            jpeg.h              r_shadow.c
cl_demo.c                 keys.c              r_shadow.h
client.h                  keys.h              r_sky.c
cl_input.c                lhfont.h            r_sprites.c
cl_main.c                 lhnet.c             r_textures.h
cl_parse.c                lhnet.h             sbar.c
cl_particles.c            libcurl.c           sbar.h
clprogdefs.h              libcurl.h           screen.h
cl_screen.c               makefile            server.h
cl_screen.h               makefile.inc        snd_alsa.c
cl_video.c                mathlib.c           snd_bsd.c
cl_video.h                mathlib.h           snd_coreaudio.c
clvm_cmds.c               matrixlib.c         snd_main.c
cmd.c                     matrixlib.h         snd_main.h
cmd.h                     mdfour.c            snd_mem.c
collision.c               mdfour.h            snd_mix.c
collision.h               menu.c              snd_null.c
common.c                  menu.h              snd_ogg.c
common.h                  meshqueue.c         snd_ogg.h
conproc.c                 meshqueue.h         snd_oss.c
conproc.h                 mingw_note.txt      snd_sdl.c
console.c                 model_alias.c       snd_wav.c
console.h                 model_alias.h       snd_wav.h
COPYING                   model_brush.c       snd_win.c
csprogs.c                 model_brush.h       sound.h
csprogs.h                 model_dpmodel.h     spritegn.h
curves.c                  modelgen.h          svbsp.c
curves.h                  model_psk.h         svbsp.h
cvar.c                    model_shared.c      sv_main.c
cvar.h                    model_shared.h      sv_move.c
darkplaces16x16.png       model_sprite.c      sv_phys.c
darkplaces24x24.png       model_sprite.h      sv_user.c
darkplaces32x32.png       model_zymotic.h     svvm_cmds.c
darkplaces48x48.png       mprogdefs.h         sys.h
darkplaces64x64.png       mvm_cmds.c          sys_linux.c
darkplaces72x72.png       netconn.c           sys_sdl.c
Darkplaces.app            netconn.h           sys_shared.c
darkplaces-dedicated.dev  nexuiz.ico          sys_win.c
darkplaces-dedicated.dsp  nexuiz.rc           todo
darkplaces.dev            palette.c           vid_agl.c
darkplaces.dsp            palette.h           vid_agl_mackeys.h
darkplaces.dsw            polygon.c           vid_glx.c
darkplaces.ico            polygon.h           vid.h
darkplaces.rc             portals.c           vid_null.c
darkplaces-sdl.dsp        portals.h           vid_sdl.c
darkplaces.txt            pr_comp.h           vid_shared.c
dpvsimpledecode.c         progdefs.h          vid_wgl.c
dpvsimpledecode.h         progs.h             view.c
draw.h                    progsvm.h           wad.c
filematch.c               protocol.c          wad.h
fractalnoise.c            protocol.h          world.c
fs.c                      prvm_cmds.c         world.h
fs.h                      prvm_cmds.h         zone.c
gl_backend.c              prvm_edict.c        zone.h
gl_backend.h              prvm_exec.c
gl_draw.c                 prvm_execprogram.h

./darkplaces/Darkplaces.app:
Contents

./darkplaces/Darkplaces.app/Contents:
Info.plist  PkgInfo  Resources

./darkplaces/Darkplaces.app/Contents/Resources:
Darkplaces.icns  English.lproj

./darkplaces/Darkplaces.app/Contents/Resources/English.lproj:
InfoPlist.strings

./id1:
config.cfg;1  glquake  PAK0.PAK;1  PAK1.PAK;1

./id1/glquake:
15to8.pal;1     flame.ms2;1    h_guard.ms2;1   quaddama.ms2;1  v_rock.ms2;1
armor.ms2;1     gib1.ms2;1     h_ogre.ms2;1    soldier.ms2;1   v_shot2.ms2;1
backpack.ms2;1  gib2.ms2;1     h_player.ms2;1  spike.ms2;1     v_shot.ms2;1
bolt2.ms2;1     gib3.ms2;1     h_wizard.ms2;1  s_spike.ms2;1   w_g_key.ms2;1
bolt3.ms2;1     g_nail.ms2;1   h_zombie.ms2;1  suit.ms2;1      wizard.ms2;1
bolt.ms2;1      grenade.ms2;1  invisibl.ms2;1  v_axe.ms2;1     w_spike.ms2;1
demon.ms2;1     g_rock.ms2;1   lavaball.ms2;1  v_light.ms2;1   zombie.ms2;1
dog.ms2;1       g_shot.ms2;1   missile.ms2;1   v_nail2.ms2;1   zom_gib.ms2;1
eyes.ms2;1      h_demon.ms2;1  ogre.ms2;1      v_nail.ms2;1
flame2.ms2;1    h_dog.ms2;1    player.ms2;1    v_rock2.ms2;1

```

I can't figure out what is wrong...

---

### Post by DoktorSeven on 2007-05-07
```
./id1:
config.cfg;1  glquake  PAK0.PAK;1  PAK1.PAK;1
```

My guess is right here.  Your PAK files have a ;1 after them for some reason, and I'll bet darkplaces can't find them for that reason.  (glquake directory too, but I don't think darkplaces uses it.)

cd to the id1 directory and do

mv PAK0.PAK\;1 PAK0.PAK 
mv PAK1.PAK\;1 PAK1.PAK
mv config.cfg\;1 config.cfg

(or just rename them from a GUI file browser)

---

### Post by ZeroXR on 2007-05-07
Doktor Seven: I am not sure what that command did, but it solved it all!

One final question and I'm pretty much done... How to I fix the flickering display? Is it because Beryl is running?

---

### Post by DoktorSeven on 2007-05-07
Probably because of Beryl, yes.  Best not to run Beryl when running 3d games.

---

### Post by porphiron on 2007-08-15
lo folks!,

have managed to get darkplaces running, i just unzipped the contents into my home dir, dragged the id1 folder from the cd into the darkplaces directory and  after following the quake on linux how-to i managed to get it running ish, I must admit the darkplaces page has very little in the way of help for folk that are stuck, or general info.

Has anyone got the music working??, i've ogg-ed up the cd's soundtrack and placed it all over the darkplaces directory, to no avail

and also, which is the better option glx or sdl??

---

### Post by ThrashJazzAssassin on 2007-11-05
Whenever I get a quad damage, the frame rate drop from about 40fps to 15 fps... What frame rate is everyone else getting?

I've got a sempron 2500+/GeForce FX5600

Surely it should be running >100fps??? It's only quake. I used to play Quake on my 486 10 years ago

---

