---
title: "warcraft III frozen throne in wine"
date: 2007-05-14
forum: Gaming &amp; Leisure
---

### Post by dachinster on 2007-05-14
ok, i downloaded and installed the latest wine
i have a nvidia 6600gt
i managed to install warcraft III and Warcraft III frozen throne via wine with no hassles.
i made an ISO image of the original warcraft cd and i mounted it to /media/image.

however, when i try to run:
wine "Frozen Throne.exe" -opengl

it tells me that i need to put in the cd.
i added /media/image as a device in wincfg and i made it as a cdrom but still nothing

any help?

---

### Post by GiantRobot on 2007-05-14
What I believe you need to do is download a no CD patch.

[This link ]("http://www.winehq.org/pipermail/wine-devel/2002-July/007391.html")might be helpful as well.

---

### Post by Cappy on 2007-05-15
[http://appdb.winehq.org/appview.php?iVersionId=3126](http://appdb.winehq.org/appview.php?iVersionId=3126)

You should follow the guide above if you want to play online. They may have included protection against that kind of thing [in the post above] since the post is 5 years old.

---

### Post by dachinster on 2007-05-16
thanks for the replies:
the guides just tell you how to install the game.
the game installs fine as i said.

the guide says here:
> Running the Game
If you use x86-64 kernels, you may need to use the following command:
*$ setarch i386 -X wine "Warcraft III.exe"*
 
If you use a processor with NX (no-execute bit) capabilities, you may have to turn it off. Use the noexec=off boot option.

but that command doesnt work for me and thats all that it says about running the game

also, when i put in the original warcraft reign of chaos / frozen throne cds, the game works.

based on that, i believe it is some wine configuration missing that would allow wine to point to where i have the image mounted (which is /media/image)

please note, i have also tried mounting the iso to my only cdrom drive which is /media/cdrom0 but this does not work either 
i have also tried running the "autoplay" after mounting it on the /media/cdrom0, and the autoplay works... it just asks me for the cd....

---

### Post by Cappy on 2007-05-16
The way to setup wine to see your mounted image is in the install guide I linked.

> 


Installing the Game

Launch winecfg to do the following tasks:
Make sure the Windows version for Warcraft 3 is 2000, XP, or 2003 for copy protection support. Warcraft 3 supports Win2000 or later.
Create a drive letter for your cdrom if you have not already. For each cdrom drive letter, click advanced, and set the drive type from automatic to cdrom. You *MUST* have a drive letter before installing.

It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or by viewing your boot-log.

To default the game to use OpenGL, see the registry import below. This creates HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III with new DWORD value called "Gfx OpenGL" with the value set to 1. So you may create a file using the text, or use regedit to do the same.

When the game's installer, everything should run as expected.

After installing the game, its highly recommended that you browse to your Warcraft III folder and rename the movies folder. Many people crash from the movies because of buggy sound drivers, so you should do this in case you are one of them. You can still play the movies under mplayer (or xine if you so choose)! TutorialIn.mpq is the very first cinematic of the game, and for the rest; *Op.mpq is the cinematic at the start of the campaign and *Ed.mpq is the cinematic and the end. If you wanted to follow the story, it's not hard at all to play the ones corresponding where you are at.


If you didn't follow the guide, I'm guessing you should assign your cd-rom a drive in wine and change the WCIII registry key to the new drive letter.

---

### Post by dachinster on 2007-05-16
the windows version for warcraft 3 is xp
my cdrom already has a drive letter which was d
i already made the device node symlink
i did not care to default the game to use opengl because i can just run the command switch --opengl
i already renamed the movies folder

but it still asks for a cdrom

---

### Post by dachinster on 2007-05-19
i have given up.
i will still continue to use windows to run wc3
i thought i could get rid of windows, but unlike linux... everything works for a NEW user and works well
it has periodic crashes and it has security flaws yes, but at least when i want a program to work, i dont have to jump through these hoops

---

### Post by Cappy on 2007-05-19
Blame Blizzard, not linux. They announced Starcraft II today. There might be a Linux client too. [http://ubuntuforums.org/showthread.php?t=448469](http://ubuntuforums.org/showthread.php?t=448469)
Also, if you're having trouble with wine, you might want to consider Cedega. I use Cedega for Oblivion which runs flawlessly. Would never run well on WINE for me.
[http://cedegawiki.sweetleafstudios.com/wiki/Warcraft_III:_Reign_of_Chaos](http://cedegawiki.sweetleafstudios.com/wiki/Warcraft_III:_Reign_of_Chaos)
It's $5 a month with a minimum purchase of 3 months subscription after which you won't receive updates.

---

### Post by blackjackel on 2007-05-19
I'm working on doing what you want to do right now, I'll post if I make any progress.... though I'll likely post in the threads I made on the subject.

---

### Post by Matthaeus on 2007-05-19
I made a program for online warcraft play in windows, and one of the things it did was start warcraft without a cd.
I had to make a loader for linux, as my mates computer died with MY TFT cd in it, and we can't get the stupid thing out!!

I modified a script found in the link above.
Unfortunately i changed it from creating symbolic links, to renaming it (the symbolic links refused to work).
All you have to do is:
[list=1]
[*]Create a .sh file, and copy code below into it.
[*]Read it, and modify any options.
[*]Download a war3.exe crack (has to be this type!).
[*]Rename the crack to crackwar3.exe, and copy it to your root warcraft dir
[*] Run the .sh file
[/list]

Cheers, Matt.

```
# Linux D2Loader v0.02b (any Diablo version) by hifi (Toni Spets)
# additional fixes by Merl

# Howto use:
#  1. Download a war3.exe crack (has to be this kind).
#  2. Rename the crack to crackwar3.exe
#  3. Place it in your root warcraft directory.
#  4. !!!***Make a backup of war3.exe and crackwar3.exe (in case either becomes corrupted!)***!!!!
#  5. Make sure all paths and options below are correct
#  6. Run this script and pray


#!/bin/bash
# Specify game path
D2PATH="/media/sda1/Games/Warcraft III"
# uncomment to enable
D2OPTIONS="-opengl"

# wine and system options (e.g. wine or cvswine)
WINE=wine
# if the script fails because you have a slow computer, increase this value to wait up before linking back to the original Game.exe
SLEEP_SECONDS=2

# dualhead hack (running windowed mode [see winecfg] with lower resolution)
DUALHEAD=0

# dualhead xrandr options
NATIVE_RES=0
GAME_RES=1

###
### DON'T CHANGE ANYTHING BELOW THIS LINE IF YOU DON'T KNOW WHAT YOU ARE DOING
###

echo
echo "Linux Loader v0.02b by hifi (Toni Spets)"
echo

if [ "$DUALHEAD" -eq 1 ]; then
	echo "Dualhead: Changing to game resolution..."
	xrandr -s $GAME_RES
fi


echo -n "Using cracked exe to start Warcraft..."
mv war3.exe war3_linux.exe
mv crackwar3.exe war3.exe

$WINE war3.exe $D2OPTIONS &
echo "Done"

echo -n "Waiting $SLEEP_SECONDS seconds before linking the original war3.exe back..."
sleep $SLEEP_SECONDS
echo " done"

echo "Quickly changing back to real war3.exe"
mv war3.exe crackwar3.exe
mv war3_linux.exe war3.exe

echo
echo "/////////////////////////////////"
echo "You may now connect to Battle.Net"
echo "/////////////////////////////////"
echo

echo -n "Waiting for Warcraft to exit..."

wait

echo " done"

if [ "$DUALHEAD" -eq 1 ]; then
	echo "Dualhead: Reseting resolution"
	xrandr -s $NATIVE_RES
fi

cd "$OLD_DIR"

# EOF
```

---

### Post by blackjackel on 2007-05-19
I've gotten Warcraft frozen throne to run under wine (with the cd in the cd drive)... I'm doing wine warcraft III.exe -opengl    but the FPS is not better than windows and sometimes the FPS drops to 17 and other times the game pauses here and there....

What am I doing wrong?

---

### Post by Echow on 2007-05-29
Hi i managed to get warcraft working no probs except for the text which is a bit blurry, but apart from that its good. Have you tried installing a graphics card driver? I installed mine through System>Administration>Restricted Drivers Manager. Maybe try that?
Ed

---

