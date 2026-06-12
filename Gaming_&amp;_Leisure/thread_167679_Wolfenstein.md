---
title: "Wolfenstein"
date: 2006-04-28
forum: Gaming &amp; Leisure
---

### Post by RobyX on 2006-04-28
Ok I just installed Wolfenstein:Enemy territory on my Ubuntubreazy. 

The video quality is OUTSTANDING I can't believe that I can play highest quality/resolution with absolutly no lag using a Geforce5200x.. I lagged to death on WinXP.

Now the problem! I have no sound, I knew my speaker's were alway's messed up but I diidnt think sound wouldent work at all in my game's. I guess it has something to do with this as well [http://ubuntuforums.org/showthread.php?t=167325](http://ubuntuforums.org/showthread.php?t=167325)

I think I need to install the drivers, the thing is though I dont know how to get the one for Linux, even if there is one?

Any help appreciated.:-D

---

### Post by minisori on 2006-04-28
As i read in the other post the sound works, right? And i guess is also integrated on the motherboard.

Try run in a console alsamixer and check how is the volumen. Maybe the controls are just messed.

As to the game without sound usually is caused for oss daemon or esd. Try killing them.

You could also post here the output in the console when you run et.

And yes you can run that game fine with the 5200 :P. Its a quake 3 based engine.

---

### Post by scooper on 2006-04-28
I wouldn't be surprised if the lack of sound partly or mostly accounts for the better video performance.  Most sound chips rely on the cpu a lot.

Searching for "AC97" lands a bunch of possibly-useful threads.  You might want to post output captured from "lspci" and "lsmod".  Another thing to try is running alsamixer from the command line.  See if you're muted.  For some reason it's often muted by default.

Good luck
Steve

---

### Post by RobyX on 2006-04-28
Ok I checked the alsamixer everything is fine. I'll try to search AC97 and see what I get on the forum.. can anyone verify if that RealtekAC97 driver come's in Linux?

---

### Post by kvonb on 2006-04-29
********     UPDATED   ********

I tore most of may hair out with this one, and (for me at least) the solution was twofold!

I have onboard AC97 sound, (SiS SI7012 with CMI9738) which works on a standard Breezy install, if your sound is working for other games or your desktop, then you are in good shape and you shouldn't need to mess around with drivers or updates etc', follow this and pray to the God of Computers for mercy ;)

You can copy and paste the following commands into a terminal, all you have to do is supply your user password.

Don't be offended, I wrote this artical with the newest of new Linux users in mind.

1) Open a terminal (click on MENU->APPLICATIONS->ACCESSORIES->TERMINAL), and paste the following into it:

sudo gedit /etc/init.d/bootmisc.sh

and press enter, when gedit opens scroll down to the bottom of the file, and just before

: exit 0

copy and paste these lines for Return to castle Wolfenstein:

echo "wolf.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "wolfmp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Or

copy and paste this line for Enemy Territory:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Save and exit gedit.

2) What I found is that when I launched Wolfenstein/ET from an Xterminal (type: wolfsp -or- et in a terminal), I got sound, when I ran it from an icon, the sound vanished!

It turns out that when you click an icon, by default a sound plays (beep or click, well a "thunk" on breezy).  What's happening is that the sound device is still being used by this "launch notification" sound when Wolfenstein starts, and it cannot access the sound card!

Now you could disable ALL desktop sounds and reboot here with success, but that is a somewhat "caveman" solution, and is not necessary, read on........

Solution: Turn off sound for menu events only, on your desktop click on:

MENU->SYSTEM->PREFERENCES->SOUND

From the applets along the top of the SOUND panel, select "Sound Events", scroll down to "User Interface Events", and remove the sound for "Choose Menu Item" and maybe also "Click on Command Button" for good measure.  My setup works with just the "Choose Menu Item" removed, suck it and see!

Quit the sound panel, you may notice that the launch sound is still there, it will be gone on the next reboot or logout/login.

3) Create an icon on your menu (if you don't already have one!), click on:

APPLICATIONS->SYSTEM TOOLS->APPLICATIONS MENU EDITOR

Click on the sub-menu on the left that you want to place the icon in, I put mine in GAMES,

Click on NEW ENTRY (bottom middle of menu editor), name it Wolfenstein -or- ET, copy and paste this: 

/usr/local/games/wolfenstein/wolfsp

or for multiplayer:

/usr/local/games/wolfenstein/wolfmp

or for Wolfenstein Enemy Territory:

/usr/local/games/enemy-territory/et


into the box that's labelled Command:,

The icon is in the same folder (/usr/local/games/wolfenstein/ -or - /usr/local/games/enemy-territory/), and is either WolfSP.xpm, WolfMP.xpm or ET.xpm, whichever you prefer.

Click OK, and quit the editor.

4) Reboot

Oh one last thing, if you have a really long startup sound, you will have to wait for it to finish before running Wolf, again it will be locking off the sound card!  I try to wait at least 10 seconds after all sounds have finished before launching Wolf.

All should be working fine now!

(Thanks go to "Drummer" for the real work behind this solution, this is merely an account of how I managed to get Wolfenstein working with help from others)

Regards,

Kev :)

---

### Post by RobyX on 2006-04-29
Hey thanks for the help I followed the step's exactly as you did.
But why hasent the icon come up in the folder?
[http://img92.imageshack.us/img92/1268/screenshot9mx.png](http://img92.imageshack.us/img92/1268/screenshot9mx.png)

Edit: And yes I did press Ok.

---

### Post by RobyX on 2006-04-29
[QUOTE=RobyX]Hey thanks for the help I followed the step's exactly as you did.
But why hasent the icon come up in the folder?
[http://img92.imageshack.us/img92/1268/screenshot9mx.png](http://img92.imageshack.us/img92/1268/screenshot9mx.png)

Edit: And yes I did press Ok.[/QUOTE]

Bump.. still stuck.

---

### Post by kvonb on 2006-04-30
From the screenshot you gave, it looks like you created a folder in the root menu, instead of a shortcut in the games sub-menu.

Try again but this time open the menu editor, first you may as well delete the entry you made yesterday.

Now click on the "GAMES" entry in the left column (where it has "ACCESSORIES DEBIAN EDUCATION GAMES etc'), then click on the "NEW ENTRY" button.

Give it a name (ie Wolfenstein) paste:

/usr/local/games/wolfenstein/wolfsp

or 

/usr/local/games/wolfenstein/wolfmp

into the "COMMAND" box, now click on the icon button "NO ICON", browse to:

/usr/local/games/wolfenstein

and choose either: WolfSP.xpm -or- WolfMP.xpm

Click on OK.

Close the menu editor (the new icon will not appear until you quit the editor!), look in the menu under games and you should now see the icon you just made.

If not, log out, then back in again and have another look.

Don't forget, I am ASSUMING that you have Wolfenstein installed in the folder /usr/local/games/wolfenstein!  If not then you will have to find the folder that contains Wolfenstein and change ALL of the above to reflect the new folder location.

You can find the folder by typing this into a terminal:

cd /
sudo find . -name wolfxp.x86

This will take some time, but will eventually spit out the install location.

And the famous last words: That should do it.

By the way, did you get your sound working with the other instructions, I think there will be a lot of people who would like to know the results?

Regards,

Kev :)

---

### Post by kvonb on 2006-04-30
OK, so I'm a loony!

I have been talking about Return to Castle Wolfenstein, rather than Wolfenstein: Enemy Territory all this time!

I have edited the instructions above to reflect the differences, the only difference (I think) is to change the command wolf.x86 for et.x86 and the install folder for Enemy Territory should be /usr/local/games/enemy-territory.

I don't have that game, so I can't give you exact instructions but you should be able to figure it out.

Regards,

Kev :D

---

### Post by RobyX on 2006-05-01
Im going to all this now I guess, since I have to start again changing the stuff to ET things.. uh lazy lol, oh well i'll edit this when im done.

---

