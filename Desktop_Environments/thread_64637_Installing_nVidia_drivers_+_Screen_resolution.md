---
title: "Installing nVidia drivers + Screen resolution"
date: 2005-09-11
forum: Desktop Environments
---

### Post by paperless on 2005-09-11
Well... im having probes installing nVidia drivers.

It says i have to disable x server to install it correctly.

Yesterday i kinda messed around with xorg.conf so i tried a command to recover it using an utility but didnt work so i had to reinstall ubuntu.

So today i need the help of someone who installed the drivers without any problems :).


Oh and while i was installing Ubuntu i kinda didnt know how to edit the screen resolutions i wanted to use so now i cant go past 1024x768 and i would really want to use 1280x1024.


Please help im kinda noobie in Ubuntu.   \\:D/


Im using 64-Bit edition BTW.

---

### Post by defuseme2k on 2005-09-11
YES.  I have the same problem.  I know I need to edit xorg, and install the nvidia drivers.  Trying to run the package results in that same error, need to exit xserver.  I have a dell 2405.  xorg.conf shows this correctly, and it shows my monitor correctly as well, but even in xorg 1920x1200 isn't listed.  In gnome, when I go to the "screen resolution" control panel thing, it lists 1280x1024 as the highest it can do.  This is driving me crazy.  This thing makes me feel so noob haha.

---

### Post by KenLazlo on 2005-09-13
One Method is to start Ubuntu in rescue mode. 

Download the file from nvidia. 
Start Ubuntu in rescue mode
Install the driver
Restart Ubuntu 

Edit xorg.conf according to nvidia help

---

### Post by Slackitude on 2005-09-13
As far as the resolutions go, if I'm understanding you correctly all you should need to do is to open xorg.conf as root and add in the ones you want at the default depth (usually 24) provided your monitor can handle them. Mine for example looks like this
SubSection "Display"
  Depth  24
  Modes  "1600x1200" "1280x1024" "1024x768" "800x600"
(all on one line)

---

### Post by Slackitude on 2005-09-13
Quick edit, that's not all on one line, I meant the line "modes" followed by the resolutions was all one line. Before I posted it was chopped up but as it showed in the actual post it was exactly right. Sorry, I'm rambling and heading for bed.

---

### Post by frodon on 2005-09-13
If youare noob you shouldn't use this way to install nvidia drivers, there's no need to have the latest version of nvidia drivers (expept if you have the latest nvidia card) so if you're noobs please follow this [way](http://ubuntuguide.org/#installnvidiadriver), it will prevent you from getting many problems.
If you're not a noob there's a [HOWTO](http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia) about that which should help you.
For resolution problems, in most of the cases the problem is solved adding good hsync and vertsync parameters (refresh rate parametres) in the monitor section of your xorg.conf file, use the search field of the forum and you will find a huge quantity of thread about this issue.

---

