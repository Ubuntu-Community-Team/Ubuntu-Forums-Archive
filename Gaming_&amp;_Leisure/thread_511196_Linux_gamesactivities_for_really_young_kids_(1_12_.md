---
title: "Linux games/activities for really young kids (1 1/2 years)"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by stuporglue on 2007-07-27
Does anyone know of good Linux activities for 18 month olds? He can move the mouse (poorly) and I'm sure he could master a couple of keys (arrows, spacebar, etc.)  I think he's too young for the gcompis stuff still.

The things I'm thinking of right now are 

1) A slideshow program that would let me record the people's names, so he'd see a picture of grandma and hear me say "Grandma" etc. 

2) A music player that could be made to have huge playlist buttons (ie. the buttons are big, the playlist is short) so he could play songs

3) Video player similar to music player -- I'll grab some youtube videos of his favorite animals and make it so they play fullscreen. 

Does anyone know of programs that would fit these needs? Any other ideas? 

My 18 month old has been in love with computers since he could stare and drool. Now he's constantly hitting the keyboard and moving/clicking the mouse. Today he pulled our new MacBook off the table (no damage, phew!), and I decided it's time to set up a computer that he can use without getting in trouble. 

My plan is to install Xubuntu and use a dock with very big icons on it so he can hit them alright, and tie the programs into different F keys so he can launch them from the keyboard as well. 

Thanks!

---

### Post by Steveway on 2007-07-27
Tuxpaint is perfect for little kids.
Try it out it's fun.

---

### Post by por100pre1 on 2007-07-27
There are many activities in GCompris, some are for older kids, but there are many for younger kids. My daughters love it!

---

### Post by stuporglue on 2007-07-27
> There are many activities in GCompris, some are for older kids, but there are many for younger kids. My daughters love it!

True, but the problem is, at 18 months, his mouse skills are marginal at best. I don't know that he's going to be able to get past the main page.

---

### Post by capturesteve on 2007-07-27
> **stuporglue said:**
> True, but the problem is, at 18 months, his mouse skills are marginal at best. I don't know that he's going to be able to get past the main page.
Wouldn't know about that kids seem to be getting smarter faster these days. Its crazy!

---

### Post by stuporglue on 2007-07-28
For future use, here's what I ended up doing. It looks like it'll work out pretty well.

I used Xubuntu as the base since this is an older computer I thought the XFCE panel lent itself to large buttons better than the Gnome panel. 


== Configuring XFCE == 
I ended up not using the panels. I couldn't figure out how to delete the last panel, I just removed everything from it, made it as small and transparent and auto-hiding as possible, and left it in a corner.  Do that last though, as having the XFCE menu available while you're setting things up is handy. 

I configured the desktop to not show filesystem icons, only launchers. I then increased the size until it would fit 9 launchers. 

I changed the desktop to a picture of my son with Grandpa, and set the XFCE sessions to auto save and not prompt. 

I set GDM to auto login, and to log in after 10 seconds if no one else logs in. There aren't any other uses at the moment, but maybe there will be some day (siblings???). 

When all the launchers were in place on the desktop, I removed write privledges to the ~/Desktop folder so he couldn't delete them anymore.

== Configuring xorg.conf == 
In the short time I let Ryan (my son) beta test the system, he managed to kill X11 twice and get to a virtual terminal once. I added the following to the bottom of my xorg.conf to avoid both of those problems: 

```
Section "ServerFlags"                                                       
    Option "DontZap" "true"                                                 
    Option "DontVTSwitch" "true"                                            
EndSection 
```

== Configuring the mouse == 
His mouse button mashing during the beta testing removed a launcher from the desktop, and he got into the contextual menu and clicked things several times, so I disabled the right mouse button and middle click.

I put this line in his .xinitrc file and made .xinitrc executable:
```
xmodmap -e "pointer = 1 12 13 4 5 6 7 8 9"
```
This maps mouse buttons 2 (middle click) and 3 (right click) to 12 and 13 respectively. Since buttons 12 and 13 don't exist, they are now useless. The scroll wheel still works. I have 9 entries because xmodmap thinks I have 9 buttons on my mouse. To see how many buttons you have, run "xmodmap -pp"

I also switched the mouse theme to WhiteGlass which supports 64x64 pixel cursors, which I hope will make it easier for him to use. 

== Chosen Programs == 
I chose the following programs:

**Abiword** -- he likes banging on the keyboard -- I used the geometry flag so it'd start fullscreen
```
abiword --geometry 1280x1024+0+0
```

**Childsplay** -- Childsplay is like GCompris, but the menus are simpler, and it includes a couple of activities targeted at the 2 year old range. Ryan isn't quite there, but he will be soon. 

**GCompris** -- This has more activities than Childsplay, but they are nested two menus deep (category --> activity). Not as good for really young kids, but some of them looked good enough that I included it and will help him when he wants to play. 

**Planet Penguin Racer **(formerly tuxracer) -- It only takes arrow keys to run this program, and it's got mountains, trees and fish in it, all of which he loves. 

**Mplayer script** -- I wrote a short script that creates a playlist of the songs in his home directory and plays them with mplayer in random order for 10 minutes. Put the script where you want and make it executable
```
 #!/bin/bash

killall mplayer
cd /home/ryan/Music
find . name '*ogg' > playlist
find . name '*mp3' >> playlist
mplayer -playlist playlist -shuffle & 
sleep 600 && killall mplayer 
```
This makes it so re-running the program has the same effect as pressing "next" with the playlist in shuffle mode. I expect that we'll be adding song fairly regularly, which is why I regenerate the playlist each time. 

**qiv slideshow** -- Script that shuffles the pictures in his Photos directory and either shows a slideshow, or advances when he presses space bar. The script also rotates and resizes the pictures to screen size if needed  so they'll load faster next time. Our 8 megapixel images were taking too long to load.
```
#!/bin/bash

cd /home/ryan/Photos/
qiv -m -t -i -s -S -d 10 -f *JPG *jpg & 
exifautotran *
for i in *jpg *JPG;do convert -resize 1280x1024 $i $i;done  
```

**tuxpaint** -- Of course. Run with the following options
```
tuxpaint --fullscreen --1280x1024 --noprint --grab
```

**tuxtype** -- He's too young for this one still, but it's ready when he is...


== Maintenance == 
Alt-F2 still works, and I can launch a terminal and configure things. If I plug in an ethernet cord at boot time, it will connect to a DHCP server and there is an SSH server running. 

Shutdown is done via Alt+F2 --> "gksudo halt"

---

### Post by Beren Camlost on 2007-07-28
> **stuporglue said:**
> For future use, here's what I ended up doing. It looks like it'll work out pretty well.

<shortened for length>

Shutdown is done via Alt+F2 --> "gksudo halt"

Aww, that is really really really really sweet you know :) <3

---

### Post by stuporglue on 2007-07-29
One more tweak...

He kept hitting the power button on the case which triggered an immediate shutdown. 

I edited /etc/acpi/powerbtn.sh and just commented out the whole file, and now it doesn't shut down right away. It still does a hard power off after 4 seconds of holding down the button, but I believe that behavior is linked to the BIOS and the hardware rather than Xubuntu's response to a certain button combination. Sadly, this computer doesn't have a BIOS option to disable this type of hard reboots.

---

