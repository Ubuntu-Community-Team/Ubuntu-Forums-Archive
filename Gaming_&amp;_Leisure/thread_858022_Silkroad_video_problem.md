---
title: "Silkroad video problem"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by Jaxilian on 2008-07-13
Silkroad is supposed to be supported by Wine 1.1, but I just installed it and the graphic is all messed up. Missing a lot of textures and so on.

I have latest video driver from ATi. Dunno where to go now. please help :KS

---

### Post by NovruzeliH on 2008-07-13
well even tho wine supports alot of the games, they dont all work on Linux

---

### Post by LinuxGamer on 2008-07-13
Sigh.. Wine works very well, for those willing to put in a bit of work.  I have gotten games working better in Wine then I ever did in Cedega, but I had to take the time to read the winehq.org app database.. They have a lot of suggestions for fixing the problems you are having... I will start with the first message..
# Make sure that your computer meets the recommended requirements for Silkroad (Pentium 4 or higher, 512MB RAM, 3D and DirectX 9.0b compatible video card, and 3GB of free HDD space) and that you have the necessary drivers for your graphics card.
# Follow the instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) to add the wine repository, then follow the directions to use Synaptic or Terminal to download and install the package.
# Run "winecfg" in terminal (without the quotes) and set compatibility to Windows 98.
# Download the Silkroad client and unzip it if you need to. Then run "wine executable.exe" (without quotes and replace executable.exe with the silkroad installer exe)
# Run the client either from Applications>Wine>Programs>Joymax>Silkroad or from your Desktop.
# Wait for patching to complete.
# Hit play. 

Also..
# If the game runs very slowly or there are graphics issues, try these steps:

    * Match your in-game video resolution with your X resolution so it becomes full screen.
    * Install the latest drivers for your graphics card or switch to the closed-source 3rd party binary drivers (example: nVidia drivers at nvidia.com).
    * Tweak the xorg.conf (/etc/X11/) file and input your monitor's horizontal/vertical frequencies, size, etc.
    [COLOR="Red"]* Launch winecfg and in the graphics tab check the box to emulate a virtual desktop and enter a resolution so that Windows applications will run in a window controlled by your windows manager.[/COLOR]
    * Disable "bloom effect" and "water reflection" through the in-game graphics option dialog.

# As of wine 0.9.49 and Silkroad v1.131, guild emblems and character buffs should appear.
# In-game audio and video settings may not be saved after Silkroad is restarted.
# If you cannot get Silkroad to work at all, you can copy over the Silkroad folder Windows into ~/.wine/drive_c/Program Files/Silkroad. Make sure that the file names are the same when you copy the files over or rename the files so that you only have one of each file, as Linux is case-sensitive while Windows is not.
# If Silkroad is launched from Terminal, many errors will be displayed onscreen. Those are normal and can be ignored. Running Silkroad from a desktop launcher or from the launch in the Applications>Wine menu will not show the terminal.
# The launcher may need to be restarted multiple times for the "Start" button to appear.
# Fullscreen mode doesn't work properly and changing between fullscreen and windowed mode via alt+enter will result in great graphic glitches. 

The spot I highlighted in Red has been the most helpful for me in the most games.. But I would try all of these things.. You can look for more advice [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5391").

Hope this helps.

---

