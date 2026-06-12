---
title: "How To Install Civilization: Call To Power On Ubuntu 14.04"
date: 2014-05-12
forum: Gaming &amp; Leisure
---

### Post by Alex_Baggott on 2014-05-12
This is a step-by-step guide to installing Loki Software's Linux version of **Civilization: Call To Power** on Ubuntu 14.04.

Although I haven't tested this on any other version of Ubuntu, it seems likely that this procedure will also work on Ubuntu 12.04. Perhaps others can confirm or refute this. At the time that I installed the game, my system was using kernel version 3.13.0-24-generic.

The sound does not seem to work in this game. Perhaps this can be remedied in the future.


[LIST=1]
[*]Buy the game. :) The CD used was the United States version. I don't know if this procedure will work for other versions of the CD.
Since sources will probably appear and disappear over time, it seems better to let you find somewhere that's selling the disc, rather than to provide suggestions. 
[*]Insert the CD and open its location (/media/<USER>/Linux CivCTP 1.0) in the file manager (**replacing "<USER>" with your username**). Copy the file **CivCTP.tar.gz** to a location of your choice on your machine's storage device, such as your home directory. 
[*]Go to the directory to where you copied CivCTP.tar.gz, right click on it and then choose "Extract Here". The extracted directory "CivCTP" will then be created. 
[*][**Optional**] If you'd like the videos, then copy the folder "**ctp_data**" from /media/<USER>/Linux CivCTP 1.0/runtime into the CivCTP directory. When prompted, choose to merge the existing ctp_data folder with the new one. 
[*]Now the game needs to be patched to its last version. The patch "**civctp-1.2a-english-unified-x86.run**" seems to be the one that works (with this CD, at least).
Again, since sources will probably appear and disappear over time, it seems better to let you locate the patch, rather than to provide a link. Here is its SHA512SUM to enable you to check the  validity of the file:
**SHA512SUM:** ff9b63fd036dd533449e6d0bea19ce0c0272c4509cd445fcd91cf889f188187df89e5a41cdc1e1a77b24c0ecd7a500b998afd58c108267b8346e63324240cfe3 
[*]Move the patch civctp-1.2a-english-unified-x86.run into the same directory as CivCTP. **Make the patch executable.** To do this, right click on the patch and then choose "Properties". Now go to the "Permissions" tab and then check the checkbox labelled "Allow executing file as program". 
[*]Open a terminal window and then go to the directory that contains CivCTP and civctp-1.2a-english-unified-x86.run. Enter the following command (omitting the "linux32", if your computer uses a 32-bit processor):

```
_POSIX2_VERSION=199209 linux32 ./civctp-1.2a-english-unified-x86.run --keep
```

Follow the prompts to apply the update. It will fail and return an error code, but this step is necessary to create certain files. This patch contains an incorrect version of the file "**loki_patch**", so go to civctp-1.2a-english-unified-x86/bin/Linux/x86 and remove it. Now find the correct version of loki_patch, place it in the same directory and then make it executable. Here is its SHA512SUM to enable you to check that it's the correct version:
**SHA512SUM:** 6151de17ff2be93305d3789615c303d41633e13d4280c99c193966551d04ed5ed70d2b2cd79e88f98eb26a53ae1e5ae72af2370a1a6ffb62d7893de5060a8502 
[*]In the terminal window, go back to the civctp-1.2a-english-unified-x86 directory and then enter the following command:

```
sudo ./update.sh
```

Follow the prompts to apply the update and it should complete correctly. 
[*]Now you can finally play the game. In the file manager, go into the CivCTP folder and then double click the "**civctp**" file. The game should then load. 
[*][**Optional**] In order for the game to appear in the Dash, create a file called "**civctp.desktop**" in the /usr/share/applications directory. Enter the following text inside the file, **replacing "<PATH>" with the path to the CivCTP directory**:

```
[Desktop Entry]
Version=1.2a
Name=Civilization: Call To Power
Comment=Launch Civilization: Call To Power
Exec=/<PATH>/CivCTP/civctp -f
Icon=/<PATH>/CivCTP/icon.xpm
Terminal=false
Type=Application
Categories=Utility;Application;
```

Searching for the game in the Dash should now reveal it. 
[/LIST]

I hope that this guide helps someone.

Happy Civ-ing.

---

