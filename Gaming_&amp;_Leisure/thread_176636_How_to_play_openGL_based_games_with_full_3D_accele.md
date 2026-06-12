---
title: "How to play openGL based games with full 3D acceleration on XGL/compiz"
date: 2006-05-15
forum: Gaming &amp; Leisure
---

### Post by arnieboy on 2006-05-15
FULL credit goes to "**jesper**" from the compiz forums ( [http://compiz.net](http://compiz.net) ) for the following work. I have tested it and it works and hence warrants a complete howto here.
The original howto is [here]("http://www.compiz.net/viewtopic.php?id=175")

[B]CAVEAT:
1) I have only tested this on GNOME.
2) [lithorus]("http://ubuntuforums.org/member.php?u=5670") has reported that this does not work with the fglrx (ATI) driver. Trying the below with the same will result in an XGL crash.[/B]

First of all, do the following:
```
sudo visudo
```
and add the following to the end of the file:
> %user_name  ALL=NOPASSWD: /usr/bin/Xorgallowlocal
where user_name is the group to which your user_name belongs (generally they go by the same name on a default Dapper install)
press ctrl-X and hit "Y" to save and exit.
now do the following:
```
sudo gedit /usr/bin/Xorgallowlocal
```
and paste the following:
> #!/bin/sh
DISPLAY="$2" XAUTHORITY="$1" xhost local:
save and exit and do the following:
```
sudo gedit /usr/bin/nonXgl
```
and paste the following:
> #!/bin/sh

DISPLAY=":93"

if [ -z "$1" ]; then
        echo "Usage: nonXgl <command>"
        exit 1
fi

isdisplay=0; isauth=0; for test in $(ps ax | grep "$DISPLAY" | grep Xorg ); do if [ $isauth -eq 1 ]; then export XAUTHORITY="$test"; isauth=0; fi; if [ "$test" = "-auth" ]; then isauth=1; fi; done;


sudo /usr/bin/Xorgallowlocal "$XAUTHORITY" "$DISPLAY"

exec $@

save and exit.
IN the above one thing needs to be kept in mind. you need to be sure that your display number is indeed "93" (by default it is 93 on almost all systems). To double check however, do the following:
```
ps uax | grep Xorg | grep Xgl
```
and look at the end of the line just before "terminate". There you will see your screen number. If it is anything other than 93, change the value of DISPLAY accordingly in "/usr/bin/nonXgl" 

Now do the folllowing:
```
sudo chmod 755 /usr/bin/nonXgl
sudo chmod 755 /usr/bin/Xorgallowlocal

```
Now you are all set.
To run any openGL based game, play it as follows:
```
nonXgl <game>

```
for example: 
```
nonXgl ppracer
```
and enjoy full 3D acceleration!

If it works for you, you can go a step further and change the path of the game executable in your menu by using alacarte or some other way to be able to launch it from menu.

We can get this thread stickied if it works for others.

---

### Post by lithorus on 2006-05-15
Would just like to add that this does NOT work with fglrx(ATI). Fglrx doesn't support acceleration on 2 X servers at once. If you try the above it'll just crash your XGL session...

---

### Post by arnieboy on 2006-05-15
[QUOTE=lithorus]Would just like to add that this does NOT work with fglrx(ATI). Fglrx doesn't support acceleration on 2 X servers at once. If you try the above it'll just crash your XGL session...[/QUOTE]
thanks for the update will add that.

---

### Post by mithras86 on 2006-05-25
Realy awesome!:-D Never thought how I could solve the ploblem: eye candy with compiz/xgl and still have the possibility to play ET! 
Thanks!

---

### Post by grendelkhan on 2006-05-25
I've added the files remotely, I am so going to test this tonight when I get home from work!

---

### Post by kno on 2006-05-25
> Would just like to add that this does NOT work with fglrx(ATI). Fglrx doesn't support acceleration on 2 X servers at once. If you try the above it'll just crash your XGL session...

Maybe fixed in the latest drivers :

> ATI 8.25.18 drivers
Resolved Issues

The following section provide a brief description of resolved issues with the latest version of the ATI Proprietary Linux driver. These include:

* Running two X servers simultaneously no longer results in the system failing to respond. Further details can be found in topic number 737-220
[...]


---

### Post by leech on 2006-05-25
That truly is a thing of beauty!  Also another great reason to use an nVidia card over ATI.  Anyone tested the latest ATI drivers to see if it will work on it?  

Hopefully now that AIGLX stuff is fully in X.org 7.1, the next revision of all the nVidia and ATI drivers will have the proper extensions, and the next release of Ubuntu will have native XGL.

Speaking of which, I'm sure this has been discussed elsewhere, but with Dapper's delay, does that mean that the next Ubuntu release will be in December?

Leech

---

### Post by SqRt7744 on 2006-05-25
[QUOTE=arnieboy]
First of all, do the following:
```
sudo visudo
```
...
press ctrl-X and hit "Y" to save and exit.
[/QUOTE]

this only works if nano or pico is called by visudo, but by default visudo uses vi, as the name implies.  So to ensure that nano is used, your instuctions *must* look like this
```

export VISUAL="nano"
sudo visudo

```

otherwise nice, thanks.

---

### Post by arnieboy on 2006-05-25
[QUOTE=SqRt7744]this only works if nano or pico is called by visudo, but by default visudo uses vi, as the name implies.  So to ensure that nano is used, your instuctions *must* look like this
```

export VISUAL="nano"
sudo visudo

```

otherwise nice, thanks.[/QUOTE]
on Ubuntu, visudo does indeed call nano (not vi/vim).

---

### Post by QuacoreZX on 2006-05-25
I just tried integrating this into Cedega, I do say that direct rendering DOES indeed function, but it doesn't exactly work and look how I would like it (I didn't have time to boot up a game, but the menu alone looked sorry to say the least).

---

### Post by jecos on 2006-05-25
anyone try this with fglrx 8.25.18? or should I test it myself?

---

### Post by sciyoshi on 2006-05-25
Ok, I tried this with a NVidia GeForce FX 5200, and the acceleration works great, but the graphics don't work very well. For example, running 'nonXgl glxgears' looks like the attached screenshot...

---

### Post by Jedeye on 2006-05-25
worked like a charm with quake4! thanks! :-D

---

### Post by SqRt7744 on 2006-05-26
[QUOTE=arnieboy]on Ubuntu, visudo does indeed call nano (not vi/vim).[/QUOTE]

Maybe on 5.10, but on my 6.06 the first time I called visudo it used vi.  However, after loading nano for some completely unrelated task it seems to have made itself the default such that the next call to visudo used nano.  I found that somewhat irksome, as I prefer vim to nano, but it's the truth!  To be safe, the export visual command should be called...  though I trust few people will be confused should they indeed be presented with vi.

---

### Post by vrunner on 2006-05-26
[QUOTE=lithorus]Would just like to add that this does NOT work with fglrx(ATI). Fglrx doesn't support acceleration on 2 X servers at once. If you try the above it'll just crash your XGL session...[/QUOTE]
I've been using this method for weeks now on a Mobility Radeon 9600.

---

### Post by Bazon on 2006-05-26
Sounds interesting.:)

Does it work for videoplayers and resizeable windows, too?

---

### Post by Bazon on 2006-05-26
Got time to test it now...:)
[QUOTE=Bazon]Does it work for videoplayers?[/QUOTE]Yes, tested it with kaffeine.
[QUOTE=Bazon]...and resizeable windows, too?[/QUOTE]Yes and no:
In Kaffeine I could switch to fullscreen mode; which worked. But normal resizing wasn't possible because of missing windowborders.
I also couldn't move that window, not even with ALT+Leftclick+Move_mouse

Also, I wasn't able to put this screen in the background, it's always in front of all other windows.

Worst of all, my keyboard didn't worked after starting nonXgl. Only CTRL+ALT+x Combinations worked (and so I could shutdown that server....), but no normal keys.


So I'll stay with starting [Xorg and Xgl parallel at the same time](http://ubuntuforums.org/showthread.php?t=180545), it's far more flexible for me. :)

---

### Post by jbus on 2006-05-26
Has anyone tried this with the newest ATI drivers?

---

### Post by grendelkhan on 2006-05-31
Just wanted to add a Me Too! to this thread, these scripts rock!  Working perfectly on the latest Nvidia drivers from repos.

---

### Post by BanskuZ on 2006-06-02
Awesome script.

---

### Post by kombipom on 2006-06-02
This method works for me also but I'd just like to say that if you don't have a crash hot graphics card you might want to disable the screensavers as this slowed NWN down to a crawl after a few minutes.  I assume that they are still being rendered by the card even though they are not being displayed and my poor MX4000 couldn't cope with both.

Hope this helps.

---

### Post by SeTsU on 2006-06-02
Thanks this script is really great! :D

Too bad the window decorations go missing in windowed applications, but hey at least most games don't need the title bar buttons to exit. :P

---

### Post by Thoop on 2006-06-02
it takes 15 minutes to start up guild wars from cedega using this :(

---

### Post by sudomania4 on 2006-06-02
i get no input from the following command
```
clay@atlantis:~$ ps uax | grep Xorg | grep Xgl
clay@atlantis:~$

```
and the following command
```
clay@atlantis:~$ nonXgl ppracer
xhost:  unable to open display ":93"
PPRacer 0.3.1 --  http://racer.planetpenguin.de
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

*** ppracer error: Couldn't initialize SDL: No I/O port permissions
clay@atlantis:~$

```

any ideas?

EDIT: problem solved
i simply changed the display in /usr/bin/nonXgl to 0, rather than 93
```
#!/bin/sh

DISPLAY=":0"

if [ -z "$1" ]; then
echo "Usage: nonXgl <command>"
exit 1
fi

isdisplay=0; isauth=0; for test in $(ps ax | grep "$DISPLAY" | grep Xorg ); do if [ $isauth -eq 1 ]; then export XAUTHORITY="$test"; isauth=0; fi; if [ "$test" = "-auth" ]; then isauth=1; fi; done;


sudo /usr/bin/Xorgallowlocal "$XAUTHORITY" "$DISPLAY"

exec $@
```

now i can run gl apps/games with the script. thanks!

---

### Post by jakster on 2006-06-02
Oke first I'm jesper on the compiz forums. Second I will like to add this DOES NOT start a new X server so it works on ati cards. I wrote this from an ati card.

Third, there is a better method, it involves changing the line for xgl, adding **-xorgAc** to the end. 

It becomes something like this (yes this is for an ATI card, fbo works as well now)

```

/usr/bin/Xgl :0 -fullscreen -br -accel glx:pbuffer -accel xv:fbo -xorgAc

```

run the program like DISPLAY=:93 ppracer

now using the nonXgl script is handy when you use the run command so you can save this code as nonXgl ::
```

#!/bin/sh

DISPLAY=":93"

if [ -z "$1" ]; then
        echo "Usage: nonXgl <command>"
        exit 1
fi

LD_PRELOAD=/usr/lib/libGL.so.1.2 $@
```

It also makes sure you load the correct libGL.so.1.2 for your games (what should be but still)

---

### Post by riq on 2006-06-03
Works fine with nvidia fx 5200, I'm able to play ET again, thanks!

---

### Post by Zeroedout on 2006-06-04
[quote=jakster]Oke first I'm jesper on the compiz forums. Second I will like to add this DOES NOT start a new X server so it works on ati cards. I wrote this from an ati card.

Third, there is a better method, it involves changing the line for xgl, adding **-xorgAc** to the end. 

It becomes something like this (yes this is for an ATI card, fbo works as well now)

```

/usr/bin/Xgl :0 -fullscreen -br -accel glx:pbuffer -accel xv:fbo -xorgAc

``` 
run the program like DISPLAY=:93 ppracer

now using the nonXgl script is handy when you use the run command so you can save this code as nonXgl ::
```

#!/bin/sh

DISPLAY=":93"

if [ -z "$1" ]; then
        echo "Usage: nonXgl <command>"
        exit 1
fi

LD_PRELOAD=/usr/lib/libGL.so.1.2 $@
``` 
It also makes sure you load the correct libGL.so.1.2 for your games (what should be but still)[/quote]

Perhaps I missed it from your post, but where do we change the line for Xgl (the first line of code in your post)? Is that the /usr/bin/Xgl script, or if we install xgl  with an ATI card will it just drop us to a command line and we start Xgl like that?

---

### Post by palermi on 2006-06-04
can play 3D games based in wine and cedega with this method ?

---

### Post by wakady on 2006-06-04
Great didn't try it yet bec. i messed up my  *Dapper RC* upgraded to final trying to get the DRI driver to work with my ATI 9600XT & i failed totally :(
but i'll test it when i reinstall clean Dapper final later on
what i wanna ask is Will it work with the ATI driver 8.25.18 from repso
also jakster didn't say what happens when adding 
> -xorgAc 
to the end of the Xgl script & what exactlly does it do..

---

### Post by munkymonkjr on 2006-06-04
first of all i'd like to announce that nonXgl script does work with the latest ati drivers (i use 9700 for those who care).  i ran ET and it looks to run OK. Though when running glxgears it looks something like that screenshot on the previous page.

---

### Post by firezip on 2006-06-04
ET runs much better now. I am going to test Nexuiz now

BTW I'm running a 6800gs

---

### Post by Zeroedout on 2006-06-04
got compiz and Xgl working great, with the non Xgl script I had to put the DISPLAY=":0" and openGL games run okay. This is with a radeon 9800 np. The only problem (and I'm guessing is a bug in compiz), if I right click an icon and hit properties, then hit close, my session crashes and brings me back to GDM. This happens when I hit the close button with screen resolution and other programs as well, however if I hit the X at the top right of the window, it's fine. Is anyone else having this same problem?

---

### Post by wakady on 2006-06-05
Wooow ATI XGL ON DISPLAY :0
I tried it yesterday & its amazing i also thought to run XGL on DISPLAY :0 & see if ATI fixed there issue & use tried
> xv:fbo instead of > xv:pbuffer
& guess what
IT WORKED as well as the script arnieboy made *thx man great work* 
So the full line i used is 
> /usr/bin/Xgl :0 -fullscreen -br -accel glx:pbuffer -accel xv:fbo -xorgAc

But still wondering what is -xorgAc do???

Thanks jakster for the tip

BTW i'm using ATI RADEON 9600 XT 256

**PS ONLY WORKS WITH ATI 8.25.18 DRIVER**

---

### Post by klisics on 2006-06-07
[QUOTE=Zeroedout]hit close, my session crashes and brings me back to GDM. This happens when I hit the close button with screen resolution and other programs as well, however if I hit the X at the top right of the window, it's fine. Is anyone else having this same problem?[/QUOTE]

unselect the Dock plugin. that's very unstable. this solved my "quit to GDM" problem...

---

### Post by wakady on 2006-06-07
hay guys no one told me anything about adding -xorgAc ????
what does it do!!??

---

### Post by Zeroedout on 2006-06-08
[quote=klisics]unselect the Dock plugin. that's very unstable. this solved my "quit to GDM" problem...[/quote]

Thank you for the info, however, an upgrade to the latest packages also fixes the problem.

---

### Post by MetalMusicAddict on 2006-06-08
Heres what Im getting when trying to launch UT2004. I followed this easy guide to a "T".

**nonXGL /home/atm/.ut2004/ut2004** is the command.

```

**Could not launch menu item**

Details: Failed to execute child process "nonXGL" (No such file or directory)
```

---

### Post by spacey on 2006-06-10
[QUOTE=wakady]hay guys no one told me anything about adding -xorgAc ????
what does it do!!??[/QUOTE]

From Xgl --help:
-xorgAc                disable access control restrictions

I read on the Compiz forum, that it enables you to do DISPLAY=:93 <program> without being root.

---

### Post by Thoop on 2006-06-19
just tried it with warsow, the game runs fine, but my mouse movement is inverted (which is very annoying) does anyone know how to prevent this?

---

### Post by Somatik on 2006-06-19
[QUOTE=SeTsU]Thanks this script is really great! :D

Too bad the window decorations go missing in windowed applications, but hey at least most games don't need the title bar buttons to exit. :P[/QUOTE]

I used this for running Netbeans 5.5, but indeed annoying that I can't maximize the window & stuff

---

### Post by Hibountu on 2006-06-20
Ok, thanks a lot, i'ts working. :D
But now, I don't have sound... :( 

Any workaround for that ?

---

### Post by haani on 2006-06-24
[QUOTE=wakady]Wooow ATI XGL ON DISPLAY :0
I tried it yesterday & its amazing i also thought to run XGL on DISPLAY :0 & see if ATI fixed there issue & use tried
 instead of 
& guess what
IT WORKED as well as the script arnieboy made *thx man great work* 
So the full line i used is 


But still wondering what is -xorgAc do???

Thanks jakster for the tip

BTW i'm using ATI RADEON 9600 XT 256

**PS ONLY WORKS WITH ATI 8.25.18 DRIVER**[/QUOTE]

can u explain it in more details how did u manage to work it thanks i also have the latest drivers for ATI

---

### Post by maschbaer on 2006-06-25
Hi,
the script works fine on radeon 9700 mobile with latest ati driver.

However, after about 15-20min it seems to crash and I am sended back to gdm to login. 
I am playing WarcraftIII via wine. When I start Warcraft with the script on normal gnome this problem does not ocure.
I heard that someone from the German forum has a similar porblem. In his case he is sended back to gdm when his screensaver (opengl) starts.

Any suggestions?

moi moi

---

### Post by galv on 2006-06-26
Hello I just want to say that this script works with me.
I used it to run powerpointviewer through CrossOver. It has issues with XGL, but I just manages to resolve them:

```
nano ~/bin/pptviewer
```
and then just add the following line:
```
nonXgl /opt/cxoffice/bin/pptview $1
```
(Save it!)

and then associated _pptviewer_ to the .pps and .ppt extension.

It works :)

---

### Post by Gorbachev on 2006-06-27
I don't really understand what I did whilst following the directions given here.. but, Wolf ET launched for the first time since I've had it installed, so I'm happy..

Also, I just went to Applications > other > wolf et and it works. I didn't launch it with terminal..

I may or may not be getting 3d acceleration but, at least it runs !! Finally!

---

### Post by FallenWizard on 2006-06-27
I have just tried it in UT2004, it works but the fps is really, really slow and i have a little graphic error. (Look at the minigun.)


Screenshot:
[http://img297.imageshack.us/img297/7822/shot000039fi.png](http://img297.imageshack.us/img297/7822/shot000039fi.png)

---

### Post by Grimmeehh on 2006-06-29
[QUOTE=FallenWizard]I have just tried it in UT2004, it works but the fps is really, really slow and i have a little graphic error. (Look at the minigun.)

Screenshot:
[http://img297.imageshack.us/img297/7822/shot000039fi.png](http://img297.imageshack.us/img297/7822/shot000039fi.png)[/QUOTE]

How did you install ut2004 so it runs? i have installed it and followed this guide, but the game will not load..

```

colzybub@colzybub-desktop:~$ nonXgl /vFATPartition/ut2004/ut2004
non-network local connections being added to access control list
/usr/bin/nonXgl: /vFATPartition/ut2004/ut2004: /bin/sh: bad interpreter: Permission denied
/usr/bin/nonXgl: line 15: /vFATPartition/ut2004/ut2004: Success

```

im guessing ive installed it wrong, or got permissions messed up? should it work with just "nonXgl ut2004" ?

the opengl script works anyway, as i can load little opengl games such as some breakout clone :) (incidentally i had to change the "screen number" to 0 as mentioned earlier in this thread)

can anyone steer me right ? thanks !

edit-
Ive just installed UT (as in the original) as well, but ive got the same problem. 
```

colzybub@colzybub-desktop:~$ nonXgl ut
non-network local connections being added to access control list
/usr/bin/nonXgl: /usr/local/bin/ut: /bin/sh: bad interpreter: Permission denied
/usr/bin/nonXgl: line 15: /usr/local/bin/ut: Success

```

but the program does not run, i cant find what to do. help me out please !

---

### Post by gschoper on 2006-07-01
Great guide. Worked perfectly. ut2k4 runs flawlessly with all video options maxed out.

Thanks,

gschoper

---

### Post by miltiad on 2006-07-01
Work fine for me, but just one problem.

Is there any way to switch desktop while playing ? ALT+Left/Right Arrow don't seem to work.

---

### Post by tokez on 2006-07-02
This howto was excellent. It got me started on my path to successfully playing Quake on top of XGL without having to log out into a normal GNOME default session each time.

However, I must point out that this howto did not completely work for me. In order to successfully laun Quake without it shutting down due to segmentation fault, I had to initiate the command 
```

DISPLAY=:0 sudo quake4

```

If i am not mistaken, the created scripts should have taken care of that when I typed 'nonXgl quake4' however they did not.

Also, notice that my XGL uses DISPLAY=:1 .. therefore my games must NOT use display 1.

---

### Post by tokez on 2006-07-02
In addition -- if i change my DISPLAY in '/usr/bin/nonXgl' to 0 (the display my XGL is *NOT* running on), then 'nonXgl quake4' successfully launches my game.

Thanks for this HOWTO!

---

### Post by Hg80 on 2006-07-03
would xgl stop cedega loading games too?

---

### Post by patrick295767 on 2006-07-03
Is there someone who by chance could have running XGL/compiz under fvwm desktop ? I read that was tough to do so, but someone managed. 
by chance.

Greetings

---

### Post by silvercliff on 2006-07-03
sweet, now i can run my games using fsaa and stuff. BUT i have probs with World of Warcraft, this is what i get:

[I]non-network local connections being added to access control list
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c560000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c560000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  470
  Current serial number in output stream:  470
[/I]

does this mean anything to anyone?  i can run WoW in D3D9, but everyone knows about the framerate probs :)  this is the last thing on my Linux total conversion list :)

---

### Post by robinl on 2006-07-04
So far this script had worked for me except that it can't see anything with a space in its name like "Frozen Throne.exe". Wine will just say Frozen not found and refuses to work. Now I have to use war3.exe to launch but it's no big problem.
Also can anyone explain the visudo part? Am I supposed to direct copy and paste or am I supposed to change the user_name to my username? Thanks.

---

### Post by kundalinikat on 2006-07-10
I tried to run Lugaru and I seem to be getting a problem that could be fixed by removing access control:
> ~/the/game/lugaru$ nonXgl lugaru
non-network local connections being added to access control list
/usr/bin/nonXgl: line 15: exec: lugaru: not found

I'm confused... would like to add "-xorgAc" somewhere but I can't figure out where. What line do I add "-xorgAc" to?

---

### Post by jharris on 2006-07-11
Thanks so much for this guide, I got everything working first time!

---

### Post by LinuxRocks on 2006-07-12
For Cedega, all you have to do is launch nonXgl with cedega and use the -run command.

For example... On my setup, I can run cedega like so:

nonXgl cedega -run Steam Steam

Use cedega --help for all the command line parameters.

You might be able to run cedega and its gui this way as well, but I have not tried this.

Another note...

If you have AA and AF set up for your nVidia graphics card, you can use the settings by adding nvidia-settings -l before the exec line in the nonXgl script. This will call the .nvidia-settings-rc file and kick off your game. It must be done after all the display env. vars are set or it won't work; therefore, just set the command just before you exec your external command.

Good work on this script. Its really nice!!!

Joe

---

### Post by Towncivilian on 2006-07-12
I also had to set my display to 0.

Also,

```

ps uax | grep Xorg | grep Xgl
```

didn't show any output.

Me, being a linux noobie, thought that "ps uax" was a typo, and tried

```

ps aux | grep Xorg | grep Xgl
```

and that did not give any input either.

Running Ubuntu 6.06 AMD64 with an eVGA 7800GT if it matters.

---

### Post by nickless on 2006-07-15
Does this work in Xubuntu? :)

---

### Post by qrm on 2006-07-18
Hi! ive ran into a problem. I tried to edit the sudoers file with "sudo visudo" , added the line with my user name/group to teh end of the file and it told me that there was a syntax error near line 18. I checked and double checked the last line and couldnt figure out what was wrong, so i saved the file. Now i cant edit the sudoers file nor anything else.
```
aadam@atsimasin:~/Desktop$ sudo visudo
>>> sudoers file: syntax error, line 18 <<<
sudo: parse error in /etc/sudoers near line 18
aadam@atsimasin:~/Desktop$ sudo gedit /etc/X11/xorg.conf
>>> sudoers file: syntax error, line 18 <<<
sudo: parse error in /etc/sudoers near line 18

```

EDIT: fixed it by logging in as root and editing the sudoers file, somehow there was one # missing

---

### Post by jgalvin on 2006-07-25
Thanks arnieboy, this fix worked perfectly for me on the first try.

James

---

### Post by hereitcomes on 2006-07-31
this worked excellently to allow me to use mythtv on top of compiz+xgl
when i quit mythtv however, my keyboard stops responding.... i can still press CTRL+ALT+Backspace though.. cant type letters or anything
any ideas?
thanks for the excellent script, was really grinding my gears with mythtv crashing X!

---

### Post by Domi2006 on 2006-08-04
Hi,
this script is really cool, it is possible to play Coldwar. But, it is really slow an that in use of a GeForce 6600 GT. I suggest you should add something to that script, which disables Xgl and switches to metacity while the game is running, so the graphic card's videoram is fully available for the game. When game is exited, the script shoud reenable Xgl. While you play, Xgl is not really important because you don't see your desktop. And users of medium-end graphic cards need every megabyte of their videoram for playing.

---

### Post by jheagney on 2006-08-04
The second nonxgl script (with -xorgAc) added to the /etc/gdm/gdm.conf-custom file works excellently. However, I am having much difficulty with blender.

Here's the situation.
blender won't work with xorg as is.
It will work with nonxgl, but ignores mouse events.

It also works on a second normal X window started in :1, but again ignores mouse events.
It picks up the mouse events if I start metacity on display :1 and then blender.
However, if I try nonxgl metacity, Xgl get's a metacity decoration across the entire screen.

So here's the steps I know work.

sudo X :1 -ac &
DISPLAY=":1" metacity &
DISPLAY=":1" blender

The problem with this approach is that I do have to start a new X server, and I haven't had much luck with making a script that would automatically switch off metacity and X when I close blender.

The other option, which is somewhat more cringeworthy - is there a way to get compiz to correctly feed mouse events to blender when blender is run on :93?

Anyone got any suggestions?

---

### Post by aceracer24 on 2006-08-11
Is it possible to add a way to turn off screensavers when you execute the nonXgl? It's not hard but annoying to have to remember to turn off screensavers when I want to play a game. Was hoping for a way that was slightly faster/easier.

---

### Post by superm1 on 2006-08-12
Guys, given that this guide is a bit dated (look at its sources), I should point out my guide for doing this.  I actively use it on two of my machines to still be able to watch videos and play games with full acceleration.

[http://www.compiz.net/viewtopic.php?pid=11827#p11827](http://www.compiz.net/viewtopic.php?pid=11827#p11827)

---

### Post by SCD on 2006-08-13
jheagney wich video card do you have? I use blender without nonXgl and works well, i have no problems. I use a gf4ti4200, on 6.06

---

### Post by Sammi on 2006-08-13
I like your guide Superm1. Very progressiv in Xgl/Compiz installation and customation ;)

---

### Post by superm1 on 2006-08-13
> **Sammi said:**
> I like your guide Superm1. Very progressiv in Xgl/Compiz installation and customation ;)

Thanks, lots of time put into it the last few weeks :)

---

### Post by Kratos on 2006-08-19
Hi all! I'd just like to confirm that this script does work on KDE with an nVidia 6200 AGP. Thanks for the script!

---

### Post by anaoum on 2006-08-19
this doesnt work for me at all. Im running xgl as a gnome session.

when i try use `nonXgl ppracer` it returns:
andrew@francis:~$ nonXgl ppracer
xhost:  unable to open display ":93"
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de) 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

and when i type `ps uax | grep Xorg | grep Xgl' it returns nothing:
andrew@francis:~$ ps uax | grep Xorg | grep Xgl
andrew@francis:~$ 

any suggestions?

---

### Post by dabros on 2006-08-23
Hi,

did anyone try to follow the instructions with the 8.27.10 ATI-drivers installed?

dabros

---

### Post by stalefries on 2006-09-08
leech: As far as I know, Edgy Eft is still scheduled for October 26th.

---

### Post by Grog140 on 2006-09-08
My display is appearently not 93 but when I do the 

```
sudo gedit /usr/bin/nonXgl
```

like you said it comes back with nothing.

---

### Post by lunarcloud on 2006-09-08
Okay, I got it working with server 1.0 BUT stepmania shows up with:

```

non-network local connections being added to access control list
Couldn't open log.txt: Permission denied
Couldn't open info.txt: Permission denied
StepMania 3.9
Log starting 2006-09-08 20:55:32
Loading window: gtk
OS: Linux ver 020617
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.4
Threads library: NPTL 2.4
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
ALSA Driver: 0: Audigy 1 [SB0090] [Audigy], device 0: emu10k1 [ADC Capture/Standard PCM Playback], 31/32 subdevices avail
ALSA Driver: 0: Audigy 1 [SB0090] [Audigy], device 2: emu10k1 efx [Multichannel Capture/PT Playback], 8/8 subdevices avail
ALSA Driver: 0: Audigy 1 [SB0090] [Audigy], device 3: emu10k1 [Multichannel Playback], 1/1 subdevices avail
ALSA: dsnd_pcm_hw_params: Cannot allocate memory
ALSA: Got 20 hardware buffers
Sound driver: ALSA
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Dance Anarchy/oz/'.  This is not a valid song directory.
/////////////////////////////////////////

(stepmania:32538): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
SDL version: 1.2.10
Got 32 bpp (8888), 24 depth, 8 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: NVIDIA Corporation
OGL Renderer: GeForce 6800 XT/PCI/SSE2/3DNOW!
OGL Version: 1.2 (2.0.2 NVIDIA 87.74)
OGL Extensions: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_fragment_program GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
OGL Max texture size: 4096
GLU Version: 1.3
Display: :1.0 (screen 0)
Direct rendering: no
X server vendor: The X.Org Foundation [7.0.0.0]
Server GLX vendor: SGI [1.2]
Client GLX vendor: NVIDIA Corporation [1.4]
Language: english
Current renderer: OpenGL
Theme: Step-box
Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
Your system is reporting that direct rendering is not available.  Please obtain an updated driver from your video card manufacturer.

```

---

### Post by s10n on 2006-09-08
well, performance is HORRIBLE even with high end graphic cards, but I guess it's a start

---

### Post by snop3 on 2006-09-10
this is functional for ati cards on dapper and i have 8.25.18 ati drivers
i have this script in /ust/local/bin/nonXgl

```

#!/bin/sh
DISPLAY=":0"
if [ -z "$1" ]; then
        echo "Usage: nonXgl <command>"
        exit 1
fi

LD_PRELOAD=/usr/lib/libGL.so.1.2 $@

```

i mean this is functional with other ati drivers
that is all what do you need for run opengl applications in Xgl with opengl acceleration

---

### Post by skeja on 2006-09-12
> **snop3 said:**
> this is functional for ati cards on dapper and i have 8.25.18 ati drivers
i have this script in /ust/local/bin/nonXgl

```

#!/bin/sh
DISPLAY=":0"
if [ -z "$1" ]; then
        echo "Usage: nonXgl <command>"
        exit 1
fi

LD_PRELOAD=/usr/lib/libGL.so.1.2 $@

```

i mean this is functional with other ati drivers
that is all what do you need for run opengl applications in Xgl with opengl acceleration

I have an ATI radeon x800 xl agp card and Kubuntu dapper
It works perfectly, but i change 

LD_PRELOAD=/usr/lib/libGL.so.1.2 $@

with

LD_PRELOAD=/usr/lib/libGL.so $@

cause libGL.so.1.2 don't exist in my /usr/lib folder

i try also libGL.so.1


generaly this method works but it reduce more the performace of game than without Xgl, loading and after when u play the perfomace are not acceptable in my computer (2gb ram, athlon xp 2600, 120gb hd).

---

### Post by DigitalStimulus on 2006-09-12
if you are having trouble running a command such as (with spaces and/or quotes):

```

nonXgl wine "C:\Program Files\Steam\steam.exe"

```

modify your /usr/bin/nonXgl exec line to this:

```

exec "$@"

```

---

### Post by handy on 2006-09-12
I tried out **XGL/compiz**, & found that it was not worth the trouble...

Which is the result I feared that I would get before I started **= unstable machine**.  My machine was perfectly stable before **XGL/compiz**!

I will be waiting until the technology is bullet proof, & is part of the initial install of whatever version of Ubuntu it is incorporated into before I touch it again.

Quite honestly, I don't see what all the fuss is about? :confused: 

This is just from my experience. :(

---

### Post by vico on 2006-09-13
> **jheagney said:**
> The second nonxgl script (with -xorgAc) added to the /etc/gdm/gdm.conf-custom file works excellently. However, I am having much difficulty with blender.

Here's the situation.
blender won't work with xorg as is.
It will work with nonxgl, but ignores mouse events.

It also works on a second normal X window started in :1, but again ignores mouse events.
It picks up the mouse events if I start metacity on display :1 and then blender.
However, if I try nonxgl metacity, Xgl get's a metacity decoration across the entire screen.

So here's the steps I know work.

sudo X :1 -ac &
DISPLAY=":1" metacity &
DISPLAY=":1" blender

The problem with this approach is that I do have to start a new X server, and I haven't had much luck with making a script that would automatically switch off metacity and X when I close blender.

The other option, which is somewhat more cringeworthy - is there a way to get compiz to correctly feed mouse events to blender when blender is run on :93?

Anyone got any suggestions?


maybe this will help:

sudo xinit /usr/bin/blender -- :1 -ac &>/dev/null & DISPLAY=:1 flwm &

flwm is "fast light window manager" you can use here any window manager you want.

---

### Post by DigitalStimulus on 2006-09-14
OK, remodified `nonXgl` script to this

*last 3 lines are what's changed, it allows:*
**1.** Screensaver process ended, then started again after game.
**2.** "$@" allows spaces and quotes in the run command such as:
```
nonXgl wine "C:\Program Files\Some Game\Start Game.exe"
```
make sure to replace `gnome-screensaver` with whatever screensaver you are using!```
#!/bin/sh
#/usr/bin/nonXgl

DISPLAY=":93"

if [ -z "$1" ]; then
echo "Usage: nonXgl <command>"
exit 1
fi

isdisplay=0; isauth=0; for test in $(ps ax | grep "$DISPLAY" | grep Xorg ); do $

sudo /usr/bin/Xorgallowlocal "$XAUTHORITY" "$DISPLAY"
[COLOR="DarkRed"]
killall gnome-screensaver
"$@"
gnome-screensaver[/COLOR]
```

---

### Post by Daniel15 on 2006-09-17
Hi,
 I tried this with the latest ATI FGLRX drivers (8.28.8 I think), and it seems to work fine (for the most part). However, I am experiencing a problem: If I try to play *Unreal Tournament*, the game goes way too fast (like it's at 300% speed or something!!). Does anyone know what's wrong?

EDIT: I found another tutorial at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still) . That tutorial worked excellently for me, and I was able to get everything working.
In summary: If this tutorial doesn't work for you, try the one at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still) :)

---

### Post by Gnobody on 2006-09-25
Would this work with AIGLX with the new Nvidia drivers on Edgy?

---

### Post by Aberrix on 2006-10-13
tagged.

---

### Post by jdunn on 2006-10-14
> **Daniel15 said:**
> 
If I try to play *Unreal Tournament*, the game goes way too fast (like it's at 300% speed or something!!). Does anyone know what's wrong?


Never heard of that problem.  I suggest using max game resolution with the largest texture sizes possible to slow it down.  j/k.  Smartass comments aside, sorry I don't know the answer to your problem.

---

### Post by enigma_0Z on 2006-10-20
Confirmed to work with KDE/vidia and Beryl instead of compiz.

Just wanted to let y'all know that I got this same thing working (w/o any modifications) on KDE.

---

### Post by KhaaL on 2006-10-24
Has anyone tried Xgame as a alternative solution to this? 

[http://xgame.tlhiv.org/home.html](http://xgame.tlhiv.org/home.html)

---

### Post by megamaced on 2006-10-24
W00t! Works for me using Ubuntu 6.06 with XGL+Beryl. GFX is nVidia Geforce2 Ultra 64MB using legacy drivers

---

### Post by CHUCKYCHUCK on 2006-10-27
i read in the 1st that this tip doesn't work with the fglrx drivers, even with the newest ones ??
thx, do u know anyway for playing opengl games with fglrx/xgl ??
thx

---

### Post by h0ser81 on 2006-10-27
Ok this scripted posted in the very first post works for me now being able to install games via Cedega but is there any way to have some sort of window manager/ decorations availabe? Also is there anyway to prevent the windows, ie Cedega be always being on top?

---

### Post by kabben on 2006-10-28
I dont reply to much as I simply dont have anything constructive to say mostly.

But i felt i had too for this guide.

It works straight off the forum. no amendments or having to guess what comes next. took me 5mins and 3 months worth of frustration was delt with.

one small amendment. change in game colour depth from the menus to what your desktop is or it all seems black. you'll know what i mean when you see it.

Thanks a ton to the OP and the guy with the credit.  

I am not an advanced ubuntu user but a damned happy one here.


Dean

---

### Post by ironfistchamp on 2006-11-02
Does anyone know how to get sound with this workaround? UT2004 complains that "/dev/[sound/]dsp: Device or resource busy"

There isn't much point playing games if you can't hear them.

Thanks

Ironfistchamp

---

### Post by reiki on 2006-11-02
Ok this bring me to a question. I have not messed with xgl and compiz (or Beryl) because I play World of Warcraft in Wine. I learned very quickly that with xgl active, WoW just plain didn't work.

So could this script be used to run an opengl app in wine? I guess the launcher would look like:

nonxgl wine WoW.exe

This is like a script preparing to run a program that runs a program... see what I mean? WoW is the only game I play (my kids got me addicted) and one of my conditions while modifying anything on the computer is, "Will I still be able to play WoW?" 

:)

---

### Post by ironfistchamp on 2006-11-02
@ reiki

You should be able to do that. I tried running Guild Wars through cedega using this and it worked. Although there is no sound but someone must have a fix.

---

### Post by notebook_ftw on 2006-11-17
Well, it doesn't work for me.  I have an nVidia Quadro FX 1500M (Dell Precision M90).  I can't get any games to work.  Apparently, my display is not 93, but as another user noted, nothing happens when I type 
```
ps uax | grep Xorg | grep Xgl
```or whatever that was.  Besides that, I have not been able to get either the UT2004 demo or the Quake4 demo to work.  And yes, I have nVidia drivers installed.

---

### Post by Lem on 2006-11-19
Excellent - this solves my mythtv issues. However, like some other users, I lose control of the keyboard when I exit the non-xgl program.

Anyone found a fix for this?

---

### Post by Zaggy on 2006-11-22
This method works good indeed :D
GF6600GT Nvidia user here.

Has anyone tried AIGLX + Beryl on Dapper?

---

### Post by cmulax on 2006-12-04
i just wanted to say that this script works perfectly well on my 6.06, but i wanted to upgrade everything to 6.10 and it is not working!

i get the same error as some ppl have posted (but no ones answered...) which is that apparently my display is not :93 and the 
ps uax | grep Xorg | grep Xgl 
does not return anything!

could anyone help with this problem?

---

### Post by Eazy© on 2006-12-09
same here, would bee cool to know why

---

### Post by AndyW on 2006-12-12
Yes please help I am having the say problem with Edgy. 

```
ps uax | grep Xorg | grep Xgl
```
does nothing and it gives me this

```
xhost:  unable to open display ":93"

```

---

### Post by AndyW on 2006-12-13
Please can anybody help :( 
I really want this to work;)

---

### Post by chadk on 2006-12-19
adding my frustration with the ps uax | grep doing nothing and when I try:
```

nonXgl wine /pathtowow/WoW.exe

```
Causes xserver to reboot then when I try to log in it just hangs on a blank screen forever.

---

### Post by rod.naph on 2007-01-07
I'm using an ATI mobility X1400 card with the 8.32.5 drivers, and latest beryl svn (version 0.1.4 i think) and this **DOES** work like for me!

thanks so much!
:D

---

### Post by supertux on 2007-01-11
can this also be done with the new X server running on another terminal(ctrl+alt+f9 ?)

---

### Post by rigol on 2007-01-12
> **AndyW said:**
> Yes please help I am having the say problem with Edgy. 

```
ps uax | grep Xorg | grep Xgl
```
does nothing and it gives me this

```
xhost:  unable to open display ":93"

```

Same here with 6.06!

---

### Post by haani on 2007-01-28
> **rigol said:**
> Same here with 6.06!


just replace the display:93 with display:0 then it should work!!

---

### Post by haani on 2007-01-28
> **h0ser81 said:**
> Ok this scripted posted in the very first post works for me now being able to install games via Cedega but is there any way to have some sort of window manager/ decorations availabe? Also is there anyway to prevent the windows, ie Cedega be always being on top?

yeh is there any way to get window decorations in programs like google earth and cedega??!!

---

### Post by rigol on 2007-02-01
> **haani said:**
> just replace the display:93 with display:0 then it should work!!

Thanks, that did the trick!

---

### Post by dinkins on 2007-02-14
> **haani said:**
> yeh is there any way to get window decorations in programs like google earth and cedega??!!

This. If anyone knows of any way to even make it possible to be able *move* the window, or at least have it sit on only one cube side, that would be awesome. This ability nonXgl gives us is awesome, don't get me wrong, but running games in XGL with beryl is pointless if they can not be windowed or moved... we might as well run them in a default gnome session.

Again, if anyone knows how to do this, I'd really appreciate it. I've looked everywhere, and several times people claiming to have found a solution, but no guides or even direction is given in their claims. 

Help :(

---

### Post by crashzor on 2007-02-17
after starting wine i notice it was not working just change exec $@ to exec "$@"
you can on paper start a window manager in nonXgl now you just need to tell it to put the xgl window on fullscreen

---

### Post by syronth on 2007-02-22
ppracer runs smooth at ~100FPS on my rig - without(!) this trick. There's just no problem, no glitches, no nothing. Some other run as well - but SecondLife on the other hand is awfully slow like with no acceleration at all. This one I need to start via "DISPLAY=:0 secondlife" which simply does the same trick as the whole complex nonXGL thingy.

Why's that? I don't get it, Im trying, Im googling, but where's the problem in general? It seems as more as I read the less I understand. Is there any clear explanation? I just like to understand ...

Edgy (Ubuntu 6.10)
ATi 800 w/ fglrx driver
GLX + Beryl 0.1.99.2

I start GLX/Beryl via GDM menu entry, so the X server runs on :0 and GLX on :1.

A little tipp btw (dont know if someone mentioned before): look for devilspie (synaptic, this forums and/or google) if you want have borders around windows which are running on display :0 (or :93). Ive found a great post about but unfortunately lost it.

---

### Post by damvcoool on 2007-02-22
will this get add to Feisty?? or next version?? so we can have eye candy and games like nexuiz, or openarena :D

---

### Post by Tyr_7BE on 2007-02-26
> **SeTsU said:**
> 
Too bad the window decorations go missing in windowed applications


Is there any way around this?  I'm using this to play video.  It's the ONLY way I've been able to play video, AT ALL with XGL.  And the video playback is perfect.  However, I can't seem to fullscreen the video.  I'm wondering if the presence of a window manager would help.

---

### Post by philipacamaniac on 2007-03-03
Confirmed working using latest ATI drivers from ATI.com - 8.34, I believe. Here's another vote for figuring out the window manager situation. 

I played with the nonXgl script to start metacity, but what that does is put (for example) Google Earth in one window, and your entire Xgl session in another window. Not terribly useful. The whole idea is great for fullscreen 3D games, though.

---

### Post by Tyr_7BE on 2007-03-03
Also, does anyone have a reason why the keyboard stops working after you exit this script?  It's VERY annoying to have to log out and log back in again every time I watch a movie.

---

### Post by philipacamaniac on 2007-03-03
> **Tyr_7BE said:**
> Also, does anyone have a reason why the keyboard stops working after you exit this script?  It's VERY annoying to have to log out and log back in again every time I watch a movie.

My keyboard doesn't stop working. What movie playing software are you using? You shouldn't need acceleration to watch, unless you've configured to use Xv or GL to render the movie.

---

### Post by Tyr_7BE on 2007-03-06
> **philipacamaniac said:**
> My keyboard doesn't stop working. What movie playing software are you using? You shouldn't need acceleration to watch, unless you've configured to use Xv or GL to render the movie.

I'm using vlc.  It only happens after I enter the fullscreen mode, and then exit vlc.  Then the keyboard stops working.

I'm doing this on top of XGL with the nvidia legacy drivers.  I think that might be an issue.  I've heard of the video just working for some people, but not me.  I've tried X11 shared mem, Xv, and SDL outputs...all of them are choppy to the point of unwatchable (even with the video at small sizes), and all of them send the CPU usage spiking to 100%.  Happens with totem-xine, totem-gstreamer, democracy player, and vlc.  The only way I can get smooth playback is to run the video player through this script, in which case I get minimal resource usage and great video playback (as I normally do with straight up Xorg).

If anyone knows how to get video playback working on my setup without this script I'd LOVE to hear it.

---

### Post by negi on 2007-05-15
I would like to propose a methodology whereby one can switch between programs run on the nested Xgl server and the standard Xorg server. The trick is to start a second window manager (WM) on the Xorg server using the scripts detailed in the first post of this thread. However, launching a second copy of the same WM that is being used by Gnome or KDE can cause complications with respect to key mappings and etc. You may intend to Alt-Tab or Alt-F4 on programs in the Xgl server only to find that you closed the Xgl server itself since the keys were intercepted by the second WM. The answer is to use a lightweight WM that can be properly crippled. Lastly, you need a WM that can run programs full screen to get rid of that ugly window border that is inevitable around the Xgl session.

I employed blackbox (WM), bbkeys (configures keymapping and etc in blackbox), and wmctrl (sets window properties in blackbox) to accomplish this. The following script will, more or less, accomplish the task all in one go:

```

#!/bin/sh

# Start a second, crippled window manager that runs on the Xorg
# server in which Xgl is nested to allow for switching between
# programs run on the standard Xorg server and the Xgl one.
#
# This script requires blackbox, bbkeys, and wmctrl.

# Location of script to launch programs in background Xorg server.
NONXGL=/usr/local/bin/nonXgl

# blackbox is lightweight and completely indenpendant of Gnome.
exec $NONXGL blackbox &

# bbkeys is used to remove all keybindings except one to switch
# between windows -- something other than Alt-Tab.
exec $NONXGL bbkeys &

sleep 3

# Make the Xgl "window" full screen so it does not have a title bar.
# The timing of this call may need to be tweaked.
exec $NONXGL wmctrl -r Xglx -b toggle,fullscreen &

```

My nonXgl script lives in /usr/local/bin so you may need to change the value of NONXGL to match where yours lives.

You may want to cripple blackbox so that Alt-Tab is replaced by something not used in your normal session. My .bbkeysrc (lives in your home directory) is as follows:

```

[begin] (bbkeys configuration file)

  [config]
    [option] (honorModifiers) {false}
    [option] (raiseWhileCycling) {true}
    [option] (showCycleMenu)  {true}
    [option] (autoConfig)   {true}
    [option] (autoConfigCheckTimeout) {2}
    [option] (workspaceColumns) {1}
    [option] (cycleMenuX) {20}
    [option] (cycleMenuY) {20}
  [end]

  [keybindings] (begin keybindings)
    [NextWindow]  (Mod1-F12)
  [end] (end keybindings)
[end] (end bbkeys configuration)

```

Among other things, this sets the Alt-Tab equivalent to Alt-F12 so that key sequence is used to switch between programs running in the Xorg server -- and the Xgl desktop is one of them.

I use Gnome so KDE interactivity was not tested.

---

### Post by macabro22 on 2007-06-18
I will try that.
CAn you be more detailed? How exactly do I use the script to launch a program like google earth? What about the blackbox window manager, the bbkey thingy and whatever? Do I have to install it via synaptic or google for it?

---

### Post by aribender on 2007-07-02
I followed this tutorial, and this is what I get when running nonXgl neverball:

```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0"

```

If I change the display to :1 or :93 on my nonXgl I get:

```

xhost:  unable to open display ":1"

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-20 21:25)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
neverball: DirectFBCreate: Initialization error!


```

Any ideas?

I'm using Feisty, with nvidia drivers working fine.

Thanks!

---

### Post by Seine on 2007-07-13
To the OP. This tip worked a treat, thanks VERY much.

---

### Post by wconstantine on 2007-07-15
It was kind of laggy but then I added a line into my xorg.conf:

Option "UseFastTLS" "2"

under "Devices". 

So now it looks like this:

```

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "UseFastTLS" "2"

```

I dunno if that really was the thing that did the trick but I figured that was the only change I've made with my drivers. So ATI users that experience laggy gaming under the ATI drivers, try this trick!

I got the tips from browsing this site:
[http://wiki.cchtml.com/index.php/Performance_Issues](http://wiki.cchtml.com/index.php/Performance_Issues)

Thanks for the tip threadmaker, now I don't need to relog to change session when playing. :popcorn:

---

### Post by scottDkoDer on 2007-07-21
I'm impressed. This is the first time I've seen goole earth run in an Xgl session. I am using fglrx driver version 8.38.6 on feisty with i386 kernel - ATI 9600 256 MB. Runs with out window, sort of fullscreen style, but everything works as it should; just like in a GNOME session. I haven't tested this thoroughly, but I will try next with WET. I actually have seen numerous improvements in the fglrx driver, feisty, xorg, and xgl over the past year. Much credit to the ubuntu team and users like arnieboy and jesper that make this possible; even easy for users to get it working. Thanks!

Oh. btw:

Instead of using display '93' i just used '0'

---

### Post by maxrisc on 2007-08-10
> **sudomania4 said:**
> i get no input from the following command
```
clay@atlantis:~$ ps uax | grep Xorg | grep Xgl
clay@atlantis:~$

```
and the following command
```
clay@atlantis:~$ nonXgl ppracer
xhost:  unable to open display ":93"
PPRacer 0.3.1 --  http://racer.planetpenguin.de
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

*** ppracer error: Couldn't initialize SDL: No I/O port permissions
clay@atlantis:~$

```

any ideas?

EDIT: problem solved
i simply changed the display in /usr/bin/nonXgl to 0, rather than 93
```
#!/bin/sh

DISPLAY=":0"

if [ -z "$1" ]; then
echo "Usage: nonXgl <command>"
exit 1
fi

isdisplay=0; isauth=0; for test in $(ps ax | grep "$DISPLAY" | grep Xorg ); do if [ $isauth -eq 1 ]; then export XAUTHORITY="$test"; isauth=0; fi; if [ "$test" = "-auth" ]; then isauth=1; fi; done;


sudo /usr/bin/Xorgallowlocal "$XAUTHORITY" "$DISPLAY"

exec $@
```

now i can run gl apps/games with the script. thanks!


Bless you brother.

Mobility 9600 Xgl/Compiz-Fusion- Latest
Gateway 7422GX

UrbanTerror4 is perfect now. :)

---

### Post by XTREEM|RAGE on 2007-08-25
hmm i dont know where to find my display nr:

```
ps uax | grep Xorg | grep Xgl
```

i tried the code in the terminal but it didn't work for me, i couldn't find it(it didn't give a single feedback). Even i tried them separately but no avail. When i try to run a game with the code, I get this:

```
nonXgl quake4
xhost:  unable to open display ":93"
exec: 15: quake4: not found

```

Cant find my display..where can i find it?

-edit
The above solution worked for me. I just changed the 93 to 0 and it worked :D:D

---

### Post by chessercizes on 2007-09-08
Hey!!

Thank you soo much! This is absolutely amazing!

=)

---

### Post by sirgogo on 2007-11-18
> **arnieboy said:**
> 
Now you are all set.
To run any openGL based game, play it as follows:
```
nonXgl <game>

```
for example: 
```
nonXgl ppracer
```
and enjoy full 3D acceleration!


How do I do this for games that I run in Steam, such as CS:S?

Thanks.

---

### Post by NineseveN on 2008-01-01
I had to set my display to 0 instead of 93, but otherwise, this works like a charm on my ATi 9600 Pro for Alien Arena, OpenArena, Sauerbraten and Chromium...Tremulous and Nexuiz are giving me a hard time with severely messed up textures though.

---

### Post by gsiliceo on 2008-01-18
I have an Nvidia FX5200 and compiz-fusion in gutsy, and this didnt worked for me in tremulous im still getting less fps but the command nonXgl sens no error and i can't see the number of my display because this command > ps uax | grep Xorg | grep Xgl returns nothing.
I still have to 
metacitiy --replace
Before playing trem

---

### Post by slick666 on 2008-02-23
gsiliceo,

I entered 0 for my display number and doom3 worked like a charm :)

---

### Post by gsiliceo on 2008-02-23
Thats what i had and it didnt worked, i have ubuntu gutsy, maybe thats the problem. Because i can't know my display number as i said before.

---

### Post by Muscar on 2008-02-23
Yeah, ps uax | grep Xorg | grep Xgl
gives me nothing eather

---

### Post by firefeather on 2008-05-03
Will this work with fglrx now that it doesn't use XGL? i.e. was XGL the only problem?

---

### Post by Jack_Payne on 2008-05-24
Well crap.  I made a rather dumb move and thought I would simplify having to sudo visudo and just chgrp it to my user name.  That backfired and now all it ever says is "gid is 1000, should be 0".

:(  also, while this might be a rather dumb question, while I could access /etc/sudoers i couldn't add the line to it? any help on either of these issues would be AWESOME!

---

### Post by Jack_Payne on 2008-06-10
Okay, can I PLEASE get some help.  I've been trying to do this forever.
I can not edit my sudoers folder.  i've tried ```
export EDITOR=nano
```, then ```
sudo visudo
``` and everything is the same! i've tried g editing it and then it won't let me back out and save! I'm completely lost for ideas.

---

### Post by wyth on 2008-08-31
For those having trouble with sudo visudo, try either

```
sudo nano /etc/sudoers
```

or

```
sudo gedit /etc/sudoers
```

---

### Post by wyth on 2008-08-31
Also, if can't find your display number, try this in the terminal:

```
 glxinfo | grep display
```

That should give you the correct display.

---

### Post by NinjaCodemonkey on 2008-11-03
Running Compiz, on Intrepid, fglrx drivers (Radeon 2600, 512MB) with latest everything.

How would I go about starting screensavers with this?

I installed the compiz fusion icon from Add/remove on main menu, so if I want to game, I just need to switch the window manager to metacity (this generally works). But obviously I can't do that when screensavers come on...

---

### Post by erlguta on 2008-11-24
So the first post is from May 15th, 2006 !!!
I can not believe that 2 ½ years after this workaround has not been included in compiz or X.
My ATI still can not run GoogleEarth and compiz.
Frustrating.

---

### Post by klhtaar on 2009-03-17
Didn't help me with Intel built-in video card. Any suggestions please?

---

### Post by cr0atian on 2009-04-08
I have an Intel card and if I have compiz running - forget it! GoogleEarth on another system with an older ATI Radeon 7000 (dual head) card works beautifully, although in Jaunty. Is anyone out there with Jaunty on an Intel card that can share some experiences with us?

---

### Post by mdgill on 2009-05-29
This does not work for me with display set to either 93 or 0.  I'm on a MacBook 4,1, but I don't know what kind of video card it has.  I have Jaunty, Gnome, Compiz.  I'm trying to get Google Earth up and running, but the best I get is program running with the earth badly flickering with display set to 0 or using "DISPLAY=:0 sudo googleearth".

Any ideas?

---

### Post by Razor338 on 2010-12-27
dont waste your time following those steps,use "3D Acceleration".You can find it in the ubuntu software center!

---

### Post by thatguruguy on 2010-12-27
Necromancy!

---

