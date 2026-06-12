---
title: "Savage: The Battle for Newerth [FREE]"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by chrome307 on 2007-08-27
[IMG]http://www.armchairempire.com/images/Reviews/pc/savage-battle-newerth/savage-2.jpg[/IMG]

[IMG]http://www.tuxresources.org/portal/modules/wfdownloads/images/screenshots/savage.jpg[/IMG]

**System Requirements:**

128 MB RAM, 600 MB Hard Drive, network connection, 3 button mouse

Savage: 

The Battle for Newerth is a fantasy/sci-fi computer game that combines aspects of Real-time strategy and First-person shooter into one game. The producers of the game define it as a 'Real Time Strategy Shooter', or 'RTSS'. It takes place in the far future where man has (after an apocalypse) rebuilt society, but is now threatened by intelligent beasts. On September 1st 2006, S2Games made the game FREE to download on their website. 

More info on:

```


http://en.wikipedia.org/wiki/Savage:_The_Battle_for_Newerth


```

Download the file: Savage_with_sep3t.run

```


http://www.s2games.com/savage/downloads.php


```

At the end of the download write on Konsole/Terminal;

```


chmod +x Savage_with_sep3t.run
sh Savage_with_sep3t.run


```

Before start playing the game, do the download of the patch.

```


http://www.notforidiots.com/SFE/SFE-Patch.tar.gz


```

Now the unpacking:

```


sudo mv SFE-Patch.tar.gz /home/usuary name/Savage
cd /home/usuary name/Savage
sudo tar xvzf SFE-Patch.tar.gz


```

Now the game is working !!! Let's create an icon on Applications>Games

```


Alt+F2
gksu gedit /usr/share/applications/savage.desktop


```

Add this lines:

```


[Desktop Entry]
Name=Savage
Comment=Ação Estratégico
Encoding=UTF-8
Exec=/home/usuary name/Savage/Savage
Icon=/home/usuary name/Savage/icon.xpm
Terminal=false
Type=Application
StartupNotify=false
Categories=Application;Game;


```

Done just play now!!!

---

### Post by UbuntuniX on 2007-08-27
Looks like WoW.

---

### Post by Perfect Storm on 2007-08-27
It's not anything like WoW.

Also Pre beta testing of Savage 2 will be available in a couple of days for the luckies who pre-ordered it.


Going to test the howto, before adding it to the guides/howto sticky list.

---

### Post by Adrian_b on 2007-08-30
Something you might need to add:

You need libgtk1.2 in order to run the installer.
So just do a 'sudo apt-get install libgtk1.2' before you run it.

---

### Post by HarshReality on 2007-09-11
Anybody know how to cure choppy audio?

---

### Post by KingHanco on 2007-09-12
I play this while back after install it on Ubuntu.

The update crashes the game. But I didn't patch it before start the game last time. Does the patch fix the update?

---

### Post by deadlydeathcone on 2007-09-12
There's actually a much easier way to do this: just go to the[ SFE homepage]("http://www.notforidiots.com/SFE/") and download the standalone Linux client. Zero patching required, and it's the method I used when I used to play.

This is a very, very fun game, by the way.

---

### Post by 71CH on 2007-09-12
the game installed fine but when I turn it on all I see are some video options which fade away after two seconds then a white screen.  i want to play this but if i can't get it to work i'd like to remove it.  can somebody please tell me how i can completely remove it?  thanks.

---

### Post by @vijay@ on 2007-09-15
im also getting the white screen wht to do?

---

### Post by Baby Boy on 2007-09-17
> **deadlydeathcone said:**
> There's actually a much easier way to do this: just go to the[ SFE homepage]("http://www.notforidiots.com/SFE/") and download the standalone Linux client. Zero patching required, and it's the method I used when I used to play.

This is a very, very fun game, by the way.
I've just downloaded standalone Linux client from the that link. How do I install the game?

---

### Post by Perfect Storm on 2007-09-17
[http://gaming.gwos.org/doku.php/guides:savage](http://gaming.gwos.org/doku.php/guides:savage)

---

### Post by Sikarian on 2007-09-17
> **Baby Boy said:**
> I've just downloaded standalone Linux client from the that link. How do I install the game?


EDIT: I'm retarded.


./silverback.bin

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> [http://gaming.gwos.org/doku.php/guides:savage](http://gaming.gwos.org/doku.php/guides:savage)

Looks like a great guide, I did all as instructed, but when I try to run it from *Applications->Games* nothing happens. What's wrong?

EDIT: Also, what I've noticed in your guide is that in the command area when creating the game shortcut it says 

> sh /home/USERNAME/.Games/SavageSF/Launch-SavageSF.sh

but there is no such directory. Only
> 
/SavageFE/Launch-SavageFE.sh

Changing the path to that doesn't work either though.

---

### Post by Perfect Storm on 2007-09-17
Where it says USERNAME you have to put in the users name ;)

Like
sh /home/USERNAME/.Games/SavageSF/Launch-SavageSF.sh

becomes

sh /home/john/.Games/SavageSF/Launch-SavageSF.sh

Note all the guides are only tested on 32but version.

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> Where it says USERNAME you have to put in the users name ;)

Like
sh /home/USERNAME/.Games/SavageSF/Launch-SavageSF.sh

becomes

sh /home/john/.Games/SavageSF/Launch-SavageSF.sh

Note all the guides are only tested on 32but version.
I did put my actual username where it says USERNAME. 
I'm running Feisty Fawn 64bit, is there a 64bit version of Savage?

---

### Post by Perfect Storm on 2007-09-17
Lets see if this work on 64bit;

```
sh ~/.Games/SavageSF/Launch-SavageSF.sh
```

please post output.

Also recheck if you follow the guide completly, you could misspell or overseen something.

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> Lets see if this work on 64bit;

```
sh ~/.Games/SavageSF/Launch-SavageSF.sh
```

please post output.

Output:
> sh: Can't open /home/guru/.Games/SavageSF/Launch-SavageSF.sh


This is probably due to the fact that my game is installed in 
> 
/home/guru/.Games/SavageFE/Launch-SavageFE.sh

I don't see how could I get that with SF instead of FE when by following the guide the game installs the FE way. BTW, as I've already said, I've tried to replace it with my path in the command line but it still doesn't run.

---

### Post by Perfect Storm on 2007-09-17
Wait.....checking the guide for typo error.

Thanks. Sometimes the obvious is hidden LOL.

---

### Post by Perfect Storm on 2007-09-17
typo corrected, try again, using the guide.

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> typo corrected, try again, using the guide.
I'm glad I've helped with the typo, but alas, nothing still happens after following the guide again.
How should I save the file where I add the commands during install? The default name right (Launch-SavageFE.sh)?

---

### Post by Perfect Storm on 2007-09-17
Aye.

Can you post or attach all the step'n'output. It will help alot to narrow down the problem.

---

### Post by Baby Boy on 2007-09-17
Sure, here it is:

> guru@Inspiron1501:~$ cd ~/Desktop
guru@Inspiron1501:~/Desktop$ mkdir -p ~/.Games/SavageFE
guru@Inspiron1501:~/Desktop$ tar zxfv SFE-Standalone.tar.gz -C ~/.Games/SavageFE./
./game/
./game/devnormal.cfg
./game/TS_DCM.cfg
./game/rotation.cfg
./game/savage0.s2z
./game/TS_DC.cfg
./game/savage9.s2z
./game/SEP.cfg
./game/TS_CTF.cfg
./game/demos/
./game/demos/demos.txt
./game/music/
./game/music/menu.ogg
./game/music/victory.ogg
./game/music/bg_test.ogg
./game/music/the_savage_age.ogg
./game/music/to_rebuild_and_restore.ogg
./game/music/lost_hills.ogg
./game/music/the_legion_advances_by_moonlight.ogg
./game/music/a_new_earth.ogg
./game/world/
./game/world/3_junctionB.s2z
./game/world/battlefront_overhead.tga
./game/world/losthills_overhead.tga
./game/world/dryhills.s2z
./game/world/losthills.s2z
./game/world/crossroads.s2z
./game/world/mosswoods_sep.s2z
./game/world/eden_overhead.tga
./game/world/aftermath2_sep.s2z
./game/world/thorn_sep.s2z
./game/world/blood.s2z
./game/world/rainforest3.s2z
./game/world/riverbend_sep.s2z
./game/world/alpinevalley.s2z
./game/world/tropical_overhead.tga
./game/world/sandbreak2_sep.s2z
./game/world/cloverridge.s2z
./game/world/alpinevalley_overhead.tga
./game/world/alpenglow_b.s2z
./game/world/snowblind_overhead.tga
./game/world/coastal2.s2z
./game/world/sacrificeledge_overhead.tga
./game/world/avalanche4_sep.s2z
./game/world/fourthcourt2.s2z
./game/world/lost2.s2z
./game/world/omo_tehe_dero2_overhead.jpg
./game/world/glacierpoint_overhead.tga
./game/world/alpenglow.s2z
./game/world/3_snowdeath.s2z
./game/world/circleattack2_sep.s2z
./game/world/eden2_overhead.s2g
./game/world/eden2_overhead.tga
./game/world/morning.s2z
./game/world/oceanv5.s2z
./game/world/evergreen2.s2z
./game/world/the_gate_beta.s2z
./game/world/sacrificeledge.s2z
./game/world/watershipdownb.s2z
./game/world/bunker.s2z
./game/world/redmeridian.s2z
./game/world/moss_overhead.tga
./game/world/utsacledge4.s2z
./game/world/utsacledge5.s2z
./game/world/omo_tehe_dero2.s2z
./game/world/3_snowdeath.mcfg
./game/world/tropics.s2z
./game/world/demonsnest4_sep.s2z
./game/world/evening_sep.s2z
./game/world/snowblind.s2z
./game/world/futile_sep.s2z
./game/world/standard.cfg
./game/world/eden2.s2z
./game/world/savagegrounds.s2z
./game/world/savagegrounds_overhead.tga
./game/world/moss.s2z
./game/world/moonlight_sep.s2z
./game/world/pirate2_sep.s2z
./game/world/zarrocks_sep.s2z
./game/world/ambushgrounds_sep.s2z
./game/world/morning_overhead.tga
./game/world/forestbridge4b.s2z
./game/world/bunker_overhead.tga
./game/world/frontline_sep.s2z
./game/world/jaws2_sep.s2z
./game/world/3_addisabeba05.s2z
./game/world/ancient_sep.s2z
./game/world/choke_fixed.s2z
./game/world/alpenglow_overhead.tga
./game/world/3_kingdoms2.s2z
./game/world/edge_1a.s2z
./game/world/_undo_.s2z
./game/world/2towers.s2z
./game/world/borderwar_overhead.tga
./game/world/redwood_canyon_sep.s2z
./game/world/frenzy_burninghot.s2z
./game/world/crossroads_overhead.tga
./game/world/3_torque_sep.s2z
./game/world/hurtgen5_sep.s2z
./game/world/necropolis_sep.s2z
./game/world/omo_sep.s2z
./game/world/glacierpoint.s2z
./game/world/nightsight3_sep.s2z
./game/world/the_gate_beta_overhead.jpg
./game/world/whiteout2b.s2z
./game/world/serilian.s2z
./game/world/3Tiny_Beta.s2z
./game/world/alpenglow_b_overhead.jpg
./game/world/snow1_sep.s2z
./game/world/senlar2_sep.s2z
./game/world/tiny2_sep.s2z
./game/world/battlefront.s2z
./game/world/tuskanflats_overhead.tga
./game/world/head2headb.s2z
./game/world/morning_sep.s2z
./game/world/tuskanflats.s2z
./game/world/avenue_sep.s2z
./game/world/island_sep.s2z
./game/world/3_mayhem2.s2z
./game/world/duel_dj.s2z
./game/world/tenshi.s2z
./game/world/tropical.s2z
./game/world/3_mayhem2.mcfg
./game/world/falls2.s2z
./game/world/eden.s2z
./game/world/nohope.s2z
./game/world/bigbridge_b.s2z
./game/world/doublehead_sep.s2z
./game/world/2castles.s2z
./game/world/chasmv15.s2z
./game/world/borderwar.s2z
./game/ui_game.cfg
./game/banlist.cfg
./game/default.cfg
./game/TS_frenzy.cfg
./game/commander_keys.cfg
./game/game.so
./game/normal.cfg
./game/buddies.cfg
./game/TS_duel.cfg
./game/screenshots/
./game/screenshots/screenshots.txt
./game/MapsSEP.cfg
./game/ui_main.cfg
./game/TS_devnormal.cfg
./game/settings/
./game/settings/default_vidsettings.cfg
./game/settings/default_playerkeys.cfg
./game/settings/user_sound_options.cfg
./game/settings/default.cfg
./game/settings/userkeys.cfg
./game/settings/user_clgraphics_options.cfg
./game/settings/default_gfxsettings_med.cfg
./game/settings/current.cfg
./game/settings/default_gfxsettings_low.cfg
./game/settings/user_graphics_options.cfg
./game/settings/commander_keys.cfg
./game/settings/profile.cfg
./game/settings/set_options.cfg
./game/settings/user_network_options.cfg
./game/settings/user_tlgraphics_options.cfg
./game/settings/default_gfxsettings_high.cfg
./game/duel.cfg
./game/bans.cfg
./game/playerkeys.cfg
./game/DCM.cfg
./game/gamefont.ttf
./game/autoexec.cfg
./game/TS_normal.cfg
./game/CTF.cfg
./game/presets/
./game/presets/beast/
./game/presets/beast/presets-are-here
./game/presets/human/
./game/presets/human/presets-are-here
./game/DC.cfg
./game/frenzy.cfg
./libs/
./libs/libssl.so.0.9.8
./libs/libkrb5support.so.0
./libs/libfmod.so
./libs/libcrypto.so.0.9.8
./libs/libk5crypto.so.3
./libs/libstdc++.so.6
./libs/libkrb5.so.3
./libs/libgssapi_krb5.so.2
./libs/libfmod-3.75.so
./libs/libidn.so.11
./libs/libpng12.so.0
./libs/libcurl.so.3
./silverback.bin
./licenses.txt
./savage.sh
./autoupdater/
./graveyard/
./graveyard/gui/
./graveyard/gui/graveyard/
./graveyard/gui/graveyard/ui_object_mode.cfg
./graveyard/gui/graveyard/createvars.cfg
./graveyard/gui/graveyard/ui_frame.cfg
./graveyard/gui/graveyard/br_jesse.tga
./graveyard/gui/graveyard/ui_hider.cfg
./graveyard/gui/graveyard/ui_util_mode.cfg
./graveyard/gui/graveyard/ui_setuplights.cfg
./graveyard/gui/graveyard/sliderfill.tga
./graveyard/gui/graveyard/brushselected.tga
./graveyard/gui/graveyard/button120x16_down.tga
./graveyard/gui/graveyard/ui_occluders_mode.cfg
./graveyard/gui/graveyard/ui_swatchpanel.cfg
./graveyard/gui/graveyard/ui_startup.cfg
./graveyard/gui/graveyard/hsliderbg.tga
./graveyard/gui/graveyard/hsliderfill.tga
./graveyard/gui/graveyard/ui_occludertools.cfg
./graveyard/gui/graveyard/ui_enviro_mode.cfg
./graveyard/gui/graveyard/r_jesse.tga
./graveyard/gui/graveyard/tl_jesse.tga
./graveyard/gui/graveyard/spinner.tga
./graveyard/gui/graveyard/ui_brushrows.cfg
./graveyard/gui/graveyard/checkbox_checked.tga
./graveyard/gui/graveyard/ui_util.cfg
./graveyard/gui/graveyard/spinner_down.tga
./graveyard/gui/graveyard/ui_brushes.cfg
./graveyard/gui/graveyard/ui_background.cfg
./graveyard/gui/graveyard/ui_sky.cfg
./graveyard/gui/graveyard/button120x16_over.tga
./graveyard/gui/graveyard/ui_texture_mode.cfg
./graveyard/gui/graveyard/selected120x16.tga
./graveyard/gui/graveyard/checkbox_empty.tga
./graveyard/gui/graveyard/tr_jesse.tga
./graveyard/gui/graveyard/ui_texture.cfg
./graveyard/gui/graveyard/ui_fog.cfg
./graveyard/gui/graveyard/b_jesse.tga
./graveyard/gui/graveyard/ui_objects.cfg
./graveyard/gui/graveyard/ui_paint_mode.cfg
./graveyard/gui/graveyard/ui_mode.cfg
./graveyard/gui/graveyard/button120x16_selected.tga
./graveyard/gui/graveyard/ui_grass.cfg
./graveyard/gui/graveyard/ui_deform_mode.cfg
./graveyard/gui/graveyard/t_jesse.tga
./graveyard/gui/graveyard/hsliderhandle.tga
./graveyard/gui/graveyard/ui_paint.cfg
./graveyard/gui/graveyard/bl_jesse.tga
./graveyard/gui/graveyard/ui_light.cfg
./graveyard/gui/graveyard/button120x16.tga
./graveyard/gui/graveyard/sliderhandle.tga
./graveyard/gui/graveyard/1_nl_selected120x16.tga
./graveyard/gui/graveyard/black.tga
./graveyard/gui/graveyard/sliderbg.tga
./graveyard/gui/graveyard/keys.cfg
./graveyard/gui/graveyard/l_jesse.tga
./graveyard/gui/graveyard/ui_deform.cfg
./graveyard/world/
./graveyard/world/blank384.s2z
./graveyard/world/blank32.s2z
./graveyard/world/blank64.s2z
./graveyard/world/blank96.s2z
./graveyard/world/blank512.s2z
./graveyard/world/blank128.s2z
./graveyard/world/blank192.s2z
./graveyard/world/blank256.s2z
./graveyard/ui_game.cfg
./graveyard/startup.cfg
./graveyard/game.so
./graveyard/groups/
./graveyard/groups/NPCs/
./graveyard/groups/NPCs/Monkits.objgroup
./graveyard/groups/Water/
./graveyard/groups/Water/Waterfall 3.objgroup
./graveyard/groups/Water/Waterfall 4.objgroup
./graveyard/groups/Water/Waterfall 5.objgroup
./graveyard/groups/Water/Waterfall 1.objgroup
./graveyard/groups/Water/Waterfall 2.objgroup
./graveyard/buddies.cfg
./graveyard/ui_main.cfg
./graveyard/game.dll
./graveyard/bans.cfg
./graveyard/gamefont.ttf
./graveyard/autoexec.cfg
./graveyard/brushes/
./graveyard/brushes/standard/
./graveyard/brushes/standard/brush1.tga
./graveyard/brushes/standard/brush2.tga
./graveyard/brushes/standard/brush3.tga
./graveyard/brushes/standard/brush4.tga
./graveyard/brushes/standard/brush5.tga
./graveyard/brushes/standard/brush6.tga
./graveyard/brushes/standard/brush7.tga
./graveyard/brushes/standard/brush8.tga
./graveyard/brushes/standard/brush9.tga
./graveyard/brushes/standard/brush10.tga
./graveyard/brushes/standard/brush11.tga
./graveyard/brushes/standard/brush12.tga
./graveyard/brushes/standard/brush13.tga
./graveyard/brushes/standard/brush14.tga
./graveyard/brushes/standard/brush15.tga
./graveyard/brushes/standard/brush16.tga
./graveyard/brushes/standard/brush17.tga
./graveyard/brushes/standard/brush18.tga
./graveyard/brushes/standard/brush19.tga
./graveyard/brushes/standard/brush20.tga
./graveyard/brushes/standard/brush21.tga
./graveyard/brushes/standard/brush22.tga
./graveyard/brushes/standard/brush23.tga
./graveyard/brushes/standard/brush24.tga
./graveyard/brushes/standard/brush25.tga
./graveyard/brushes/standard/brush26.tga
./graveyard/brushes/standard/brush27.tga
./graveyard/brushes/standard/brush28.tga
./graveyard/brushes/standard/brush29.tga
./graveyard/brushes/standard/brush30.tga
./graveyard/brushes/standard/brush31.tga
./graveyard/brushes/standard/brush32.tga
./graveyard.sh
guru@Inspiron1501:~/Desktop$ cd ~/Desktop
guru@Inspiron1501:~/Desktop$ mv savage.png ~/.Games/SavageFE
mv: cannot stat `savage.png': No such file or directory
guru@Inspiron1501:~/Desktop$ nano ~/.Games/SavageFE/Launch-SavageFE.sh
guru@Inspiron1501:~/Desktop$ chmod +x ~/.Games/SavageFE/Launch-SavageFE.sh
guru@Inspiron1501:~/Desktop$ alacarte
guru@Inspiron1501:~/Desktop$ 


Here are also the screenshots of that file you have to make during the install and add the command lines:

NOTE: That line in the output I've posted that says that icon file cannot be moved is because it's already in the game folder.

---

### Post by Perfect Storm on 2007-09-17
The icon need to renamed. The wiki saves them with "guide" infront of their real name.

Lets take a one step at the time (if you want to help me ;) )

```
cd ~/.Games/SavageFE
./silverback.bin
```

Does the game Launch?

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> The icon need to renamed. The wiki saves them with "guide" infront of their real name.

Yeah, I've noticed that and renamed it ;).

> Lets take a one step at the time (if you want to help me ;) )

```
cd ~/.Games/SavageFE
./silverback.bin
```
Does the game Launch?
Nope. Here's what I get:
> guru@Inspiron1501:~$ cd ~/.Games/SavageFE
[email]guru@Inspiron1501:~/.Game[/email]s/SavageFE$ ./silverback.bin
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory

The file IS there though, I've checked.

---

### Post by Perfect Storm on 2007-09-17
It could be because you're using 64bit, I'm not sure....


I properly get a 64-bit computer 6 month from now, so I can make guides for it.

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> It could be because you're using 64bit, I'm not sure....


I properly get a 64-bit computer 6 month from now, so I can make guides for it.

You don't happen to know what that shared file *libcom_err.so.2* that can't be found is? (I didn't mean that I found *this* file, I meant that silverback.bin exists)

Oh, well, if nothing else comes up, I guess it's not my destiny to play Savage :|. Thanks for taking your time to help me, AI.

---

### Post by Perfect Storm on 2007-09-17
There's properly a 64-bit solution out there. If we both search for it on the forums we might come up with something.

---

### Post by Perfect Storm on 2007-09-17
Found this might be a bit old;

```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb
dpkg -x libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb libcom
sudo mv libcom/lib/* /lib32
```

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> Found this might be a bit old;

```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb
dpkg -x libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb libcom
sudo mv libcom/lib/* /lib32
```
It works now, that was it! Thanks a lot mate, problem solved.

---

### Post by Perfect Storm on 2007-09-17
Also the menu link?

---

### Post by Baby Boy on 2007-09-17
> **Artificial Intelligence said:**
> Also the menu link?
Yep. :)

---

### Post by Perfect Storm on 2007-09-17
Great! ^_^

I have added the 64-bit stuff to the guide.

---

### Post by olieviya on 2007-09-18
> **Baby Boy said:**
> Looks like a great guide, I did all as instructed, but when I try to run it from *Applications->Games* nothing happens. What's wrong?


I had that! I solved it by not running compiz at the same time as the game, maybe log out and log back in to a GNOME without XGL, if you are using Compiz that is. 

> **HarshReality said:**
> Anybody know how to cure choppy audio?

I nees help with that, anybody???:(
My audio is choppy and it sounds pretty bad.

---

### Post by darkadvice on 2007-09-18
Well download and install work fine, but when i run game i get music and a "Input Signal out of Range please change to 1280x1024 -60Hz" anyone know how to fix that?

---

### Post by Ripfox on 2007-09-18
Bump on the white screen thing. The only posted solution on the forum doesn't work for me. 

[http://ubuntuforums.org/showthread.php?t=313933](http://ubuntuforums.org/showthread.php?t=313933)

---

### Post by tcpip4lyfe on 2007-09-19
It's a weird game.  Kind of fun though.

---

### Post by olieviya on 2007-09-20
Bump on the choppy audio issues :(

---

### Post by mesilliac on 2007-10-03
I managed to fix the choppy sound :)

I have Intel integrated audio if it matters. The way I fixed the audio was to edit ```
Savage/game/startup.cfg
```
and change the relevant entries to read
```
setsave sound_output alsa
setsave sound_mixrate 48000
```

I think this was all that needed to be done. I changed a couple other config files too, but I think those changes had no effect. Anyone else having this problem, let me know if this works for you.

---

### Post by disposition on 2007-10-05
Ooo! I'll have to check this out!

What's the multiplayer crowd like? Are there a decent number of players online at any given time?

---

### Post by antmangaka on 2007-10-06
Thanks! the Alsa thing worked for the choppy sound, :D
But... after 30 seconds of gameplay sound turns off. I have to restart the game to get sound working for another 30 secs.
any ideas? :(

---

### Post by Ripfox on 2007-10-06
Is this an mmorpg?

---

### Post by antmangaka on 2007-10-06
nope, Counter Strike style multiplayer.

---

### Post by Breepee on 2007-10-07
From what I understand its an RTS with someone doing the RTS bit, and real people instead of computers moving your soldiers in a FPS fashion.

---

### Post by Hooloovooloo on 2007-10-07
> **antmangaka said:**
> nope, Counter Strike style multiplayer.

Hehehe, that was probably the worst comparison imaginable. :P

It is a quake style fps mixed with RTS (warcraft style)

---

### Post by antmangaka on 2007-10-07
hehe, well like command and conquer renegade? :P
hmm no ideas for my sound problems? it turns off :( (30 secs in game and sound shuts down :( )

---

### Post by Ripfox on 2007-10-08
Oh well then I don't care if it works :popcorn:

---

### Post by Betatestermatt@gmail.com on 2007-11-08
I had no problem getting it to run, however when I start this game, it goes to a black screen with the only visible word being quit, login, and initializing. the cursor leaves a trail, and I can't see and username or password boxes. Anyone also have this problem, like the graphics aren't working quite right?

---

### Post by jscinoz on 2008-04-14
I found a fix for the crackly/laggy sound and also stops the sound from cutting out after 30 or so seconds. Simply do what mesilliac suggested, but instead of alsa, say esd (so it should say "setsave sound_output esd") This is what I did on hardy to make it work. Also ensure you have the package pulseaudio-esound-compat installed or it won't work.

---

### Post by Geek506 on 2008-04-27
Ok ... installed game, created icon in Games Menu, loaded game ... have sound, but then it goes to a white screen. I have to ~ and 'exit'. Read lots of comments here on the boards, but I was wondering is there some way to disable pixel shading in a config somewhere? My vid card doesn't support it. Need help, thanks :-)

*quick edit: When I ~ out of that white screen I see that "attempt to compress texture failed ... blah blah blah ... *.tga" Is there something in my startup.cfg file I can tweak?

---

### Post by ginderhulk on 2008-08-19
I installed it but i get this blank whote screen can some one help

---

### Post by Vadi on 2008-08-19
Means your graphics card is too old I think

---

### Post by eragon100 on 2008-08-19
Disable compiz fusion :wink:

It only needs a 32 mb geforce 256 or geforce 2 as minimum (I don't remember which one), so I don't think it's "too old" :lolflag:

---

### Post by VitaminG on 2008-08-31
When I try to launch it, I get this error:

```
gregg@gregg-laptop:~$ /media/Media/Wine\ Programs/Savage/silverback.bin
/media/Media/Wine Programs/Savage/silverback.bin: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory

```

The file is in the libs folder, but is it possible it needs a 32-bit version, like the problem Baby Boy had? If so, does anyone know where I could get it? I googled it, but I couldn't find any workable downloads.

---

