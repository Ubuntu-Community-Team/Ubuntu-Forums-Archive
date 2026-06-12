---
title: "Shutdown and reboot buttons are missing"
date: 2006-08-26
forum: Desktop Environments
---

### Post by misosofos on 2006-08-26
Hi all:

I don't know why, but instead of a shutdown or reboot button, now just appears a very large "hibernate" button on my exit menu.
I think it happened when I tried to hiberate unsuccesfully or maybe in the moment I installed ntfs-g3.

Anyone else having the same problem?

I found out a thread in this forum explaining the solution, but it's gone.

Thanks you all in advantage.

---

### Post by szvosec on 2006-08-26
The reason why they are not there is because you need to be in sudo (root) mode to shut down or reboot your computer. You can turn off the your computer by going to the terminal and typing: sudo halt , or if you want to reboot: sudo reboot . Either one will ask you for your password.

---

### Post by misosofos on 2006-08-26
I completly disagree with you!
This morning it worked perfectly several times!

But thanks you anyway.

---

### Post by dannyboy79 on 2006-08-26
Have you been playing around with Xgl and Compiz? After I set it up as an alternate way to log into a new session, my Shutdown and Restart buttons went away, I have to log off first and then hit Shutdown from the options button in the lower left hand corner of the login screen.

---

### Post by mackinax on 2006-08-26
One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

---

### Post by RRS on 2006-08-26
Did you shut down or reboot after your hibernation failure or did the buttons dissapear during that session?

It's possible that gdm failed to restart after the hibernation. If so "sudo gdm restart" from the terminal my restore your buttons or simply "sudo reboot".

I haven't had any problems with ntfs-g3 but I don't use hibernate but I doubt the problems are related.

---

### Post by jonboy99 on 2006-08-26
Installing kubuntu desktop on an ubuntu (gnome) install does this IIRC.

---

### Post by misosofos on 2006-08-27
Thanks you a lot mackinax!

It worked for me!

---

### Post by Indigo23 on 2006-08-27
> **mackinax said:**
> One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

Hi I have that checked and it still doesn't work.  Any other suggestions?


Thanks.

---

### Post by misosofos on 2006-08-30
Well... Now I have installed xgl compiz...

And the buttons are missing again!

Mackinax solution isn't useful now...

Any other suggestion?

---

### Post by marcus2004 on 2006-10-06
Same problem, missing buttons, with me as well. Rather annoying. Any solutions would be great. And yes I know I can log off and then reboot or shut down.

---

### Post by JamesBond on 2006-10-08
i am having this same issue, i installed Beryl and Xgl and now i only see suspend and hibernate when i click the power button in Gnome

---

### Post by Charles Hand on 2006-10-10
Same problem. I can start a metacity session and I get the shutdown and reboot buttons. With the beryl session, no shutdown and reboot buttons.

OK, I'm changing my story.

If I start the XGL session, there is no shutdown and reboot buttons, no matter whether I run metacity or beryl.

If I start the Gnome session, the buttons appear.

Here is how the xgl session is started:
```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

Here is startxgl.sh:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session

```

Here is how the gnome session is started:

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME
Name[az]=GNOME
Name[be]=GNOME
Name[ca]=GNOME
Name[cs]=GNOME
Name[cy]=GNOME
Name[da]=Gnome
Name[de]=GNOME
Name[el]=GNOME
Name[es]=GNOME
Name[et]=GNOME
Name[fi]=Gnome
Name[fr]=GNOME
Name[he]=GNOME
Name[hi]=&#2327;&#2344;&#2379;&#2350;
Name[hu]=GNOME
Name[it]=GNOME
Name[ja]=GNOME
Name[ko]=&#44536;&#45448;
Name[lt]=GNOME
Name[mn]=&#1043;&#1053;&#1054;&#1052;&#1045;
Name[ms]=GNOME
Name[nl]=GNOME
Name[nn]=GNOME
Name[no]=GNOME
Name[pl]=GNOME
Name[pt]=GNOME
Name[pt_BR]=GNOME
Name[ro]=GNOME
Name[ru]=GNOME
Name[sk]=GNOME
Name[sl]=GNOME
Name[sq]=GNOME
Name[sr]=&#1043;&#1085;&#1086;&#1084;
Name[sr@Latn]=Gnom
Name[sv]=GNOME
Name[tr]=GNOME
Name[uk]=GNOME
Name[vi]=GNOME
Name[wa]=GNOME
Name[zh_CN]=GNOME
Name[zh_TW]=GNOME
Comment=This session logs you into GNOME
Comment[az]=Bu iclas sizi GNOME'a daxil ed&#601;c&#601;k
Comment[be]=&#1043;&#1101;&#1090;&#1072;&#1103; &#1089;&#1101;&#1089;&#1099;&#1103; &#1079;&#1072;&#1074;&#1103;&#1076;&#1079;&#1077; &#1074;&#1072;&#1089; &#1091; GNOME
Comment[ca]=Aquesta sessió entra en GNOME
Comment[cs]=Toto sezení vás p&#345;ihlásí do GNOME
Comment[cy]=Mae'r sesiwn hwn yn eich mewngofnodi i GNOME
Comment[da]=Denne session logger dig på Gnome
Comment[de]=Diese Sitzung meldet Sie an GNOME an
Comment[el]=&#913;&#965;&#964;&#942; &#951; &#963;&#965;&#957;&#949;&#948;&#961;&#943;&#945; &#963;&#945;&#962; &#949;&#953;&#963;&#940;&#947;&#949;&#953; &#963;&#964;&#959; GNOME
Comment[es]=Con esta sesión accede a GNOME
Comment[fi]=Tämä istunto kirjaa sisään Gnomeen
Comment[fr]=Cette session vous connectera dans GNOME
Comment[he]=&#1514;&#1510;&#1493;&#1512;&#1514; &#1492;&#1508;&#1506;&#1500;&#1492; &#1494;&#1493; &#1502;&#1495;&#1489;&#1512;&#1514; &#1488;&#1493;&#1514;&#1498; &#1500; GNOME
Comment[hi]=&#2351;&#2361; &#2360;&#2340;&#2381;&#2352; &#2327;&#2344;&#2379;&#2350; &#2350;&#2375;&#2306; &#2354;&#2377;&#2327;&#2367;&#2344; &#2361;&#2379;&#2327;&#2366;
Comment[hu]=Ez a környezet a GNOME-ba jelentkeztet be
Comment[it]=Sessione di lavoro con GNOME
Comment[ja]=GNOME &#12475;&#12483;&#12471;&#12519;&#12531;&#12395;&#12525;&#12464;&#12452;&#12531;&#12375;&#12414;&#12377;
Comment[ko]=GNOME&#49464;&#49496;&#51004;&#47196; &#47196;&#44536;&#51064;&#54633;&#45768;&#45796;
Comment[lt]=Ši sesija prijungia Jus &#303; GNOME
Comment[mn]=&#1069;&#1085;&#1101; &#1089;&#1091;&#1091;&#1083;&#1090;&#1072;&#1072;&#1088; &#1090;&#1072; &#1043;&#1053;&#1054;&#1052;&#1045; &#1088;&#1091;&#1091; &#1085;&#1101;&#1074;&#1090;&#1088;&#1101;&#1085;&#1101;.
Comment[ms]=Sesi ini akan log anda  ke GNOME
Comment[nl]=Deze sessie meldt u aan bij GNOME
Comment[nn]=Denne økta loggar på GNOME
Comment[no]=Denne sesjonen logger deg inn til GNOME
Comment[pl]=Sesja logowania do GNOME
Comment[pt]=Esta sessão inicia-o no GNOME
Comment[pt_BR]=Logar no ambiente GNOME
Comment[ro]=Aceast&#259; sesiune v&#259; va loga în GNOME
Comment[ru]=&#1053;&#1072;&#1095;&#1072;&#1090;&#1100; &#1089;&#1077;&#1072;&#1085;&#1089; GNOME
Comment[sk]=Toto sedenie vás prihlási do prostredia GNOME
Comment[sl]=Ta seja vas prijavi v GNOMe
Comment[sq]=Kjo seancë do t'ju fusë në GNOME
Comment[sr]=&#1054;&#1074;&#1072; &#1089;&#1077;&#1089;&#1080;&#1112;&#1072; &#1074;&#1072;&#1089; &#1087;&#1088;&#1080;&#1112;&#1072;&#1074;&#1113;&#1091;&#1112;&#1077; &#1085;&#1072; &#1043;&#1085;&#1086;&#1084;&#1072;
Comment[sr@Latn]=Ova sesija vas prijavljuje na Gnoma
Comment[sv]=Denna session loggar in dig i GNOME
Comment[tr]=Bu oturum ile GNOME'a giri&#351; yapars&#305;n&#305;z
Comment[uk]=&#1057;&#1077;&#1072;&#1085;&#1089; &#1088;&#1086;&#1073;&#1086;&#1090;&#1080; &#1074; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1110; GNOME
Comment[vi]=Session này cho b&#7841;n &#273;&#259;ng nh&#7853;p vào GNOME
Comment[zh_CN]=&#27492;&#20250;&#35805;&#20351;&#24744;&#30331;&#24405;&#21040; GNOME
Comment[zh_TW]=&#36984;&#21462;&#36889;&#20491;&#20316;&#26989;&#38542;&#27573;&#24460;&#26371;&#36914;&#20837; GNOME &#29872;&#22659;
Exec=/usr/bin/gnome-session
# no icon yet, only the top three are currently used
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```

---

### Post by neymac on 2006-10-22
The same here.
When I start a gnome session without XGL, I have the restart and shutdown buttons.

---

### Post by lassegs on 2006-10-28
Same problem. Any fixes?

---

### Post by sign on 2006-11-04
i've got the same problem ... still waiting:-k

---

### Post by Boonerball on 2006-11-24
I also have lost the shutdown buttons.

The last thing I did prior to losing these was install easy ubuntu

---

### Post by tomcheng76 on 2006-11-24
echo $DISPLAY
if it is not :0.0
then you dont got a shutdown and restart button

---

### Post by HoTseChu on 2006-11-27
I got the same problem installing ubuntu-desktop on a Kubuntu, but finally found the solution editing the file /etc/gdm/gdm.conf
and changing the line with
#SystemMenu=true
to:
SystemMenu=false

Didn't work at a first instance, only after reboot.

---

### Post by HoTseChu on 2006-11-27
> **HoTseChu said:**
> I got the same problem installing ubuntu-desktop on a Kubuntu, but finally found the solution editing the file /etc/gdm/gdm.conf
and changing the line with
#SystemMenu=true
to:
SystemMenu=false

Didn't work at a first instance, only after reboot.
Oops! I mean ...
and changing the line with
#SystemMenu=false
to:
SystemMenu=true

Excuse me ...

---

### Post by xvladi on 2006-12-07
Hi!
I have installed XGL and Beryl on Kubuntu 6.10.

When I start a "XGL"-session in KDM there are no "Shutdown","Reboot",... Buttons in the K-Menu "Logout" anymore!

Did you know the solution???

---

### Post by jjesena on 2006-12-13
I'm having the same problem - been stuck trying to fix it for about 3 days now. I've messed with the /etc/gdm/gdm.conf file with the "SystemMenu=true" but that didn't help at all.

The restart and shutdown buttons would only show up if beryl was not running.

---

### Post by ianare on 2006-12-17
if you run the Xgl server after GDM is started, you will lose the power/restart buttons. The fix is to start Xgl from the very beginning. Here is a configuration that worked for me (you mileage will vary).

Specs - ATI video using flgrx drivers, Beryl, ubuntu 6.10

contents of /etc/X11/gdm/gdm.conf-custom :
```

[daemon]
GdmXserverTimeout=35

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=inactive
1=Xgl

[server-Xgl]
name=Xgl
command=/usr/bin/Xgl -fullscreen :1 -audit 0 -ac -br -accel glx:pbuffer -accel xv:pbuffer
chooser=false
handled=true
flexible=true
priority=0
```

make sure 'command=' is set to the proper settings of your video card! I'm assuming most of you did the same thing I did and used a startup script like this:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

Use the command from the 2nd line as a base for your 'command=' line... I made some tweaks to mine.

After making changes, reboot. If things were working before, except for the power button, you should be fine. Use a regular GNOME session, not an Xgl session (otherwise you load Xgl twice).

more info here:
[http://gentoo-wiki.com/XGL](http://gentoo-wiki.com/XGL)

---

### Post by Zoogie on 2006-12-20
For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

---

### Post by Mazen on 2006-12-20
> **mackinax said:**
> One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

i know im kinda late here but i have the same problem and i have a problem that the Login Window does not open! how can i solve that?

---

### Post by raul_ on 2006-12-28
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

Make it three :)  i must say, i have no idea what you've just done

---

### Post by Mazen on 2006-12-29
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

uhm, where exactly is the Xgl startup script?? sorry for the dumb question!

---

### Post by raul_ on 2006-12-29
Do you use ATI or Nvidia?

---

### Post by Mazen on 2006-12-29
ATi

---

### Post by raul_ on 2006-12-29
do you still have the link to the guide you followed? There should be a step where you have to create a startup script called "startxgl.sh" or something like that.

---

### Post by Mazen on 2006-12-29
yeah i know that so i just add it there? at the end and it should run the "cookie"....i'll try it n get back to u 
thanks

---

### Post by raul_ on 2006-12-29
before the "start-gnome" command

---

### Post by Mazen on 2006-12-29
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

```
is this right?

---

### Post by raul_ on 2006-12-29
here's mine:

```

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
# Start GNOME
exec gnome-session

```

---

### Post by sjust on 2006-12-29
Zogie you are the man! I have been searching for a solution for this for a couple of months now. Your dirty hack worked like a charm. =D>

---

### Post by mgrusin on 2006-12-30
Worked for me too, thanks very much!

PS, here's my /usr/local/bin/startxgl.sh if it helps anyone (I'm using fglrx and a [Beryl install from thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_%28Edgy_Eft%29_on_a_ThinkPad_T60"):

> #!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session


---

### Post by slow learner on 2007-01-04
> **Mazen said:**
> i know im kinda late here but i have the same problem and i have a problem that the Login Window does not open! how can i solve that?


I have the exact same issue. Can someone please help a brother out ?


Thanks in advance

---

### Post by slow learner on 2007-01-08
Hi

I still have the same problem. 

Can someone please tell me the command to startup the 'Login Window' ?



thanks

---

### Post by Grayscale on 2007-01-16
Thanks ianare, I saw that method on the guide and decided since my system is stable I'd go for that...works like a acharm!

---

### Post by webdr on 2007-01-19
> **mackinax said:**
> One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

Mackinax's suggestion worked perfect for me. I had changed the options inadvertently when resetting login theme. Thanks for this thread.

---

### Post by Bordy on 2007-02-04
So yeah... I have no idea what you guys are talking about, honestly... I don't (intentionally) run those programs you are saying have an effect on my shut down and reboot buttons, nor do I really know how to mess with the code.

Truthfully, its slightly scary without any help.

Anyone have the time to slow it down a bit and explain how to fix this? I'd really appreciate it!

Chris

---

### Post by Bordy on 2007-02-06
Alright, so feeling pretty stupid...

Went to System > Administration > Login Window and clicked "Show Actions Menu."

Fixed. Sorry.

---

### Post by dkbg on 2007-02-10
Haha Bordy, glad you got it fixed! As for me, Zoogie's suggestion on page 3 fixed the problem, thanks!

---

### Post by g3k0 on 2007-02-12
I was just wondering why the script sets the display variable to :1 in the first place.  I just changed mine to 0 and it seemed to fix the problem.  I don't notice anything different.
Heres what I did to mine..
```

#!/bin/sh
Xgl -fullscreen :0 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:0 
exec gnome-session

```

Is there anything wrong with doing this?  Why is it being set to something else?

**Lol nevrmind.  I see what happened.  It killed my beryl lol**

---

### Post by adam.tropics on 2007-02-13
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```This clones the xauth cookie from :0 into :1.


Very neat, since it also sorts out being able to start a nested session while in xgl, thanks.

---

### Post by Loonux on 2007-02-13
None of the suggestions ive read about have cured the problem for me thus far (using KDE). Is there anything else i can try?

My startxg.sh looks like this:

> 
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer & sleep 4
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"


---

### Post by 7creature on 2007-02-14
Maybe here? Hmmm...  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting)

---

### Post by Loonux on 2007-02-15
> **7creature said:**
> Maybe here? Hmmm...  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Troubleshooting)

Ive read that and it offers nothing that i havne't trired as far as i can see

---

### Post by 7creature on 2007-02-15
My startgl looks like this and I certainly have Shutdown and Reboot buttons. Thought sometimes Xgl session starts with 100% CPU load and I am forced to log-out...

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by Loonux on 2007-02-15
Seems like it may not be a solution to those of use using KDE though.

---

### Post by 7creature on 2007-02-15
> **Loonux said:**
> Seems like it may not be a solution to those of use using KDE though.

Well, just replace gnome-session with startkde.

---

### Post by Loonux on 2007-02-15
> **7creature said:**
> Well, just replace gnome-session with startkde.
I did and it made no difference. still the same two buttons :(

---

### Post by Pat.Hat on 2007-02-25
If there's anyone out there who attempted to install beryl with compiz or xgl, and then promptly decided it was too complicated to get working (as I did), you may find this of use... it worked for me. 

[http://www.ubuntuforums.org/showthread.php?p=1394518]("http://www.ubuntuforums.org/showthread.php?p=1394518")

The gdm.conf-custom file is located at /etc/gdm/gdm.conf-custom .

---

### Post by B-Con on 2007-02-25
I have the same lack of shutdown/reboot button problem, only I haven't done anything with Beryl or Compiz or XGL. All I did was run "killall gdm" and ever since I haven't had those options. (Did the same thing twice, just to be sure that was the problem.)

---

### Post by Loonux on 2007-03-04
Still struggling along with no shutdown/reboot buttons. has a solution been found yet?

Thanks

---

### Post by ComplexNumber on 2007-03-04
> **B-Con said:**
> I have the same lack of shutdown/reboot button problem, only I haven't done anything with Beryl or Compiz or XGL. All I did was run "killall gdm" and ever since I haven't had those options. (Did the same thing twice, just to be sure that was the problem.)
no wonder you haven't got the shutdown/reboot buttons. they depend on gdm running.


> **Loonux said:**
> Still struggling along with no shutdown/reboot buttons. has a solution been found yet?

Thanks
did you log in with gdm?

---

### Post by MueasA on 2007-03-08
Hi everyone,

Yesterday I nstalled Beryl + xgl @@ I couldn't getup from the laptop, I spent the whole night to get used to. anyway , when its time to shutdown the PC, there is no more shutdown or restart buttons !! hibernate and standby are still there but not working , I get error when trying to hibernate but it was so fast that I couldn't read it,

I am using dapper.  I aleady reinstalled it 5 time due to some errors , and now theyr all gone execpt this problem.


Thanks in advance

---

### Post by kinson on 2007-03-08
Though I'm not solving the problem here, but until someone else helps you, you can shutdown by entering this into the terminal:

```
sudo shutdown -h now
```

Cheers,
Kinson :)

---

### Post by AtrejuT on 2007-03-08
Thats a well know problem with beryl. The solution can be found here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
There is a point saying "Shutdown and reboot buttons in GNOME" where it explains everything you need to do (dpending on the way you set up xgl)

good luck

atreju

---

### Post by bapoumba on 2007-03-08
@ MueasA: merged your thread in here.

---

### Post by mintcoffee on 2007-03-13
> **Loonux said:**
> Still struggling along with no shutdown/reboot buttons. has a solution been found yet?

Thanks

I'm running Kubuntu (KDE) and the authentication hack posted earlier doesn't seem to enable the shutdown options. Anyone on KDE know how to fix this issue?

---

### Post by AlwaysLearning on 2007-03-17
Rather than mucking around with Xgl settings I found a simpler solution that worked for me under GNOME/Beryl. It *may* also work under Kubuntu. Here's what I did...

In a Terminal window:

```
sudo touch /usr/local/bin/fix-logout-dialog.sh
sudo chmod 755 /usr/local/bin/fix-logout-dialog.sh
sudo gedit /usr/local/bin/fix-logout-dialog.sh
```

Then, inside fix-logout-dialog.sh I have:

```
#!/bin/sh

# Get my cookies in place for Restart and Shutdown buttons on Logout Window...
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

As a simple test, click your "Log off" button and make sure that the Restart and Shutdown buttons are *NOT* there. Then, in the Terminal window run:

```
/usr/local/bin/fix-logout-dialog.sh
```

Note, you don't need to sudo it. Click your "Log off" button again and the Reboot and Shutdown buttons should now be there.

As a final step, go to System/Preferences/Sessions, select the Startup Programs tab and add an entry for /usr/local/bin/fix-logout-dialog.sh - the Restart and Shutdown buttons should now stay there consistently.

Could someone try this out under Kubuntu and let me know if it works?

---

### Post by AlwaysLearning on 2007-03-17
Oops. The "export DISPLAY=:1" line is a typo - it's not needed and shouldn't be there!

---

### Post by Orejapico on 2007-03-17
AlwaysLearning:

>  "Could someone try this out under Kubuntu and let me know if it works?"

No. It doesn't. I think it's something related with GMD and not with KDM.

---

### Post by kolslorr on 2007-03-17
> **AlwaysLearning said:**
> Rather than mucking around with Xgl settings I found a simpler solution that worked for me under GNOME/Beryl. It *may* also work under Kubuntu. Here's what I did...

In a Terminal window:

```
sudo touch /usr/local/bin/fix-logout-dialog.sh
sudo chmod 755 /usr/local/bin/fix-logout-dialog.sh
sudo gedit /usr/local/bin/fix-logout-dialog.sh
```

Then, inside fix-logout-dialog.sh I have:

```
#!/bin/sh

# Get my cookies in place for Restart and Shutdown buttons on Logout Window...
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

As a simple test, click your "Log off" button and make sure that the Restart and Shutdown buttons are *NOT* there. Then, in the Terminal window run:

```
/usr/local/bin/fix-logout-dialog.sh
```

Note, you don't need to sudo it. Click your "Log off" button again and the Reboot and Shutdown buttons should now be there.

As a final step, go to System/Preferences/Sessions, select the Startup Programs tab and add an entry for /usr/local/bin/fix-logout-dialog.sh - the Restart and Shutdown buttons should now stay there consistently.

Could someone try this out under Kubuntu and let me know if it works?


This method works like a charm for me. 

Ubuntu + xgl + beryl

---

### Post by jtchupp on 2007-03-22
good stuff! thanks!

---

### Post by gummo on 2007-03-25
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

This did it for me too, thanx alot.

---

### Post by lolcese on 2007-03-26
Using KDE and Beryl, I tried all the methods presented here and still no buttons.  How can I suspend my laptop from the command line?

---

### Post by useResa on 2007-03-27
> **lolcese said:**
> Using KDE and Beryl, I tried all the methods presented here and still no buttons.  How can I suspend my laptop from the command line?
To shutdown your computer use
```
sudo shutdown -h now
```
to restart use
```
sudo shutdown -r now
```

---

### Post by bikes302 on 2007-03-31
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

This solution worked for me as well!

---

### Post by Skukfas on 2007-04-05
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

this worked for me too... thx a lot

here is my /usr/bin/startxgl
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

exec dbus-launch --exit-with-session gnome-session

```

\m/

---

### Post by annihilus06 on 2007-04-06
> **AlwaysLearning said:**
> Rather than mucking around with Xgl settings I found a simpler solution that worked for me under GNOME/Beryl. It *may* also work under Kubuntu. Here's what I did...

In a Terminal window:

```
sudo touch /usr/local/bin/fix-logout-dialog.sh
sudo chmod 755 /usr/local/bin/fix-logout-dialog.sh
sudo gedit /usr/local/bin/fix-logout-dialog.sh
```

Then, inside fix-logout-dialog.sh I have:

```
#!/bin/sh

# Get my cookies in place for Restart and Shutdown buttons on Logout Window...
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

As a simple test, click your "Log off" button and make sure that the Restart and Shutdown buttons are *NOT* there. Then, in the Terminal window run:

```
/usr/local/bin/fix-logout-dialog.sh
```

Note, you don't need to sudo it. Click your "Log off" button again and the Reboot and Shutdown buttons should now be there.

As a final step, go to System/Preferences/Sessions, select the Startup Programs tab and add an entry for /usr/local/bin/fix-logout-dialog.sh - the Restart and Shutdown buttons should now stay there consistently.

Could someone try this out under Kubuntu and let me know if it works?


Thanks alot, this is what worked best for me.  I had tried the solution of adding a file under /etc/X11/sessions and that worked also, but for some reason this method disabled my icon theme.  The above method did only what was wanted, enabled my shutdown/restart.  

Thanks again AlwaysLearning!

---

### Post by maver1ck on 2007-06-12
> **annihilus06 said:**
> Thanks alot, this is what worked best for me.  I had tried the solution of adding a file under /etc/X11/sessions and that worked also, but for some reason this method disabled my icon theme.  The above method did only what was wanted, enabled my shutdown/restart.  

Thanks again AlwaysLearning!

I tried those solution on kubuntu and it doesn't work.

My scripts:

 maverick@maverick:~% cat /usr/share/xsessions/xgl.desktop                                                                                                                                  3:23
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl
Icon=
Type=XSession

maverick@maverick:~% cat /usr/bin/startxgl                                                                                                                                                 3:24
#!/bin/bash
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer  -br &
DISPLAY=:1
export KDEWM="/usr/bin/beryl-manager"
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec startkde

Any idea what could be wrong ?

Regards,
Maciek

---

### Post by maver1ck on 2007-06-12
I found a solution:

In /var/run/xdmct directory you should make some symbolic links:
(if you xserver is on :0 and xgl on :1)

maverick:/var/run/xdmctl# ln -s dmctl-:0 dmctl-:1                                                                                                                                            
maverick:/var/run/xdmctl# ln -s xdmctl-:0 xdmctl-:1   

That's all. 

Regards,
Maciek

---

### Post by stepol on 2007-06-20
> **maver1ck said:**
> I found a solution:

In /var/run/xdmct directory you should make some symbolic links:
(if you xserver is on :0 and xgl on :1)

maverick:/var/run/xdmctl# ln -s dmctl-:0 dmctl-:1                                                                                                                                            
maverick:/var/run/xdmctl# ln -s xdmctl-:0 xdmctl-:1   

That's all. 

Regards,
Maciek

The first solution that works on KDE .:D:D 
Thanks Maverick

---

### Post by K_Soze on 2007-07-03
> **maver1ck said:**
> I found a solution:

In /var/run/xdmct directory you should make some symbolic links:
(if you xserver is on :0 and xgl on :1)

maverick:/var/run/xdmctl# ln -s dmctl-:0 dmctl-:1                                                                                                                                            
maverick:/var/run/xdmctl# ln -s xdmctl-:0 xdmctl-:1   

That's all. 

Regards,
Maciek

I am running KUBUNTU but I don't see a xdmct directory, I see a xdmctl directory?

The other question I have is how exactly and where do I make these links?

Can anyone help?

---

### Post by the_saint07 on 2007-07-04
Please help...

When I originally instaled beryl i encountered this problem and applying the first solution mentioned could deal with it.

But now after some updates or something my two buttons are gone again. i check all the scripts i made the first time and all of them are intact. I tryed the solution on post 62 but it didn't work for me.

I couldn't apply the last maverick solution  because didn't find the xdmcl directory.

---

### Post by sambehera on 2007-07-16
> **maver1ck said:**
> I found a solution:

In /var/run/xdmct directory you should make some symbolic links:
(if you xserver is on :0 and xgl on :1)

maverick:/var/run/xdmctl# ln -s dmctl-:0 dmctl-:1                                                                                                                                            
maverick:/var/run/xdmctl# ln -s xdmctl-:0 xdmctl-:1   

That's all. 

Regards,
Maciek

thanks... this does solve the problem ... but only for my root account.. 

i added the following lines to my "startxgl.sh" script...
```

ln -s /var/run/xdmctl/dmctl-:0 /var/run/xdmctl/dmctl-:1
ln -s /var/run/xdmctl/xdmctl-:0 /var/run/xdmctl/xdmctl-:1
```

the soflink (symlink) happens through this script only when i log in as root... else i have to create the symlinks myself (as root) in order to see the buttons.... 
the symbolic links also disappear every time i reboot... is there any way to make them stay permanently in "/var/run/xdmctl" ? 

if not, then is there any other script (which is always run with root privelages at startup)  that i can append these lines to :

```

ln -s /var/run/xdmctl/dmctl-:0 /var/run/xdmctl/dmctl-:1
ln -s /var/run/xdmctl/xdmctl-:0 /var/run/xdmctl/xdmctl-:1
```

so that the symbolic links are always created in /var/run/xdmctl  at startup?

is there any way i can add these commands to a script and have them create the symlinks at startup (as root) so that i can see the buttons as any user running xgl?

---

### Post by sambehera on 2007-07-16
some progress... but no solution...

in KDE ...

creating hard links instead of a soft links also does the trick... 

but the hard links dont survive the reboot either...

---

### Post by eidauk on 2007-07-16
Here's what worked for me:

I have Kubuntu over Ubuntu 7.04  installation, by the way. I was only getting a logout option like others on this thread. But all the solutions told me to run:
```
sudo dpkg-reconfigure gdm
```
and choose KDM, which didn't solve my problem. However, I tried choosing GDM and that fixed it. The only quirk is that I now have an Ubuntu login screen to get into KDE.

So it truly was KDM getting confused with GDM.

---

### Post by sambehera on 2007-07-16
yes... that could be a good solution too but i really like my kdm ... and have customized it to my needs... however i also have gnome on my system but use kde on a regular basis... gdm does have some really nice themes though and i may consider using it... thanks for the info

---

### Post by sambehera on 2007-07-17
im using gdm now... but still no restart or shutdown buttons :( (only logout)... after running gdm i noticed that there is no /var/run/xdmctl directory .... im guessing its a temporary directory created by kdm...

could someone please help me get my restart/shutdown buttons back in kde?

---

### Post by mtbsoft on 2007-07-29
> **annihilus06 said:**
> Thanks alot, this is what worked best for me.  ...  The above method did only what was wanted, enabled my shutdown/restart. 

Worked perfectly for me too, thanks heaps AlwaysLearning

---

### Post by argo navis on 2007-08-10
Good news Sambehera, I have your fix, had the same problem myself.

kdm indeed creates that folder everytime it is started.
You need a script to run automatically after login.

For me, I relied on the kde autostart script, I did the following :

1) make a script in /home/username/.kde/Autostart/ called startup.sh.

2) In this script, sudo the ln commands that create dmctl and xdmctl entries for display one, my script looks like :

```
#!/bin/sh
sudo ln -s /var/run/xdmctl/dmctl-:0 /var/run/xdmctl/dmctl-:1
sudo ln -s /var/run/xdmctl/xdmctl-:0 /var/run/xdmctl/xdmctl-:1
```

3) Edit the file /etc/sudoers to change permissions for users running sudo (otherwise the script autostarts, but needing a password for ln, it doesn't work automatically).

To edit that file, I used the command visudo (sudo visudo).

And I appended the following entry **at the end** (very important, because entries are applied in order and can override one another, so this should be the last entry to be always effective) :

```
username         ALL=NOPASSWD:/bin/ln
```

Of course you should change username to meet your needs.

With these in place, restart-> bam! All my session change, shutdown, restart, hibernate options are availabe when I start a kde session, and I can still swap between session types.

Privileges are only modified for sudo when linking, so anyone accessing my account can sudo ln, and who gives a damn? Not me.

---

### Post by hyperfocus on 2007-08-11
> **Zoogie said:**
> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

:guitar:
Thank you, thank you, thank you.... put it in my .Xsession script before exec gnome-session. Got my buttons back!

 
ATI Radeon Xpress 200M card............

```
#!/bin/sh
Xgl :1 -br -fullscreen -ac -accel xv -accel glx:pbuffer -fp /usr/share/fonts/X11/misc &
DISPLAY=:1
gnome-settings-daemon &
compiz --replace -c emerald &
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```

---

### Post by Guitar John on 2007-08-20
> **mackinax said:**
> One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

I noticed that the *Shutdown* button was missing on my desktop, but not missing on my wife's laptop.  It kind of bothered me but not enough to do any serious probing.  Turns out, this was the solution.  

Thank you sir....

....may I please have another!  #-o

---

### Post by Zaneyard on 2007-09-13
> **AlwaysLearning said:**
> Rather than mucking around with Xgl settings I found a simpler solution that worked for me under GNOME/Beryl. It *may* also work under Kubuntu. Here's what I did...

In a Terminal window:

```
sudo touch /usr/local/bin/fix-logout-dialog.sh
sudo chmod 755 /usr/local/bin/fix-logout-dialog.sh
sudo gedit /usr/local/bin/fix-logout-dialog.sh
```

Then, inside fix-logout-dialog.sh I have:

```
#!/bin/sh

# Get my cookies in place for Restart and Shutdown buttons on Logout Window...
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

As a simple test, click your "Log off" button and make sure that the Restart and Shutdown buttons are *NOT* there. Then, in the Terminal window run:

```
/usr/local/bin/fix-logout-dialog.sh
```

Note, you don't need to sudo it. Click your "Log off" button again and the Reboot and Shutdown buttons should now be there.

As a final step, go to System/Preferences/Sessions, select the Startup Programs tab and add an entry for /usr/local/bin/fix-logout-dialog.sh - the Restart and Shutdown buttons should now stay there consistently.

Could someone try this out under Kubuntu and let me know if it works?

This worked for me! thanks always learning

---

### Post by TechnoBabble4444 on 2007-10-16
that worked perfectly, thanks

---

### Post by geokker on 2008-02-05
> **mackinax said:**
> One possibility -

Menu: System > Administration > Login Window 

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

Worked a treat for me. Cheers.

---

