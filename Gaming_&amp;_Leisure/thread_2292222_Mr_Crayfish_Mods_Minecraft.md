---
title: "Mr Crayfish Mods Minecraft"
date: 2015-08-26
forum: Gaming &amp; Leisure
---

### Post by Bigmon on 2015-08-26
Hi !
Can anyone help. My 9 year old son wants to install Mr Crayfish Furniture Mods on Minecraft on my desktop computer, but all the tutorials I can find are for windows computers. Can anyone tell me how to do it - or point me in the right direction.

Cheers

---

### Post by efflandt on 2015-08-27
Apparently you need **Forge**. I got 1.8.11.14.3.1502 from when I followed a link trying to check out shaders, but most recent version ends with 1506. Download the installer (wait for ad to finish then click the button at upper right). Then run **java -jar forge-(version)-installer.jar** See [http://files.minecraftforge.net/](http://files.minecraftforge.net/)

Then the easiest way to add mods like this is to use **MagicLauncher** [http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-tools/1262884-launcher-magic-launcher-1-3-1-mods-options](http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-tools/1262884-launcher-magic-launcher-1-3-1-mods-options) which is a jar file you run the same way. Click on Setup, give the setup a name and in the drop down list for Environment chose the 1.8-Forge... and Add the MrCrayfish mod (point it to the file you downloaded for it). If you previously filled in your login info you could Test it, but otherwise click OK and and then Login.

This is an example of desktop launcher for MagicLauncher assuming that jar is still in ~/Downloads/. For the icon I used the favicon.png that I extracted from Minecraft.jar launcher, but /image/ml.ico in the MagicLauncher jar appears to be the same thing:```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon=/home/efflandt/Pictures/Icons/minecraft.png
Name=MagicLauncher
Exec=sh -c 'java -jar ~/Downloads/MagicLauncher_1.3.1.jar'
Name[en_US]=MagicLauncher
```I have not looked up the recipes for making furniture, but the standard door recipe makes a fancier door (but with no window), so you may want to grab some sand to make glass windows, so you can see if a creeper is lurking outside your door before venturing outside in the morning.

PS: Not sure if MrCrayfish Furniture v3.4.8-build1 is still under development or finished yet (saw August reports of not being able to place some items), or if you need a different forge for the working v3.4.8 for minecraft 1.7.10

---

### Post by brian-mccumber on 2015-09-06
You can just download the forge jar file for your version of Minecraft and then right click it and under properties-->Permissions click run as application and it will install itself when you double click it after that. You have to run the version of Minecraft you are trying to mod at least once before you can install forge for it and you also need the correct version of Forge for your version of Minecraft you are using. After you install Forge it should create a folder called mods in your .minecraft folder in /home with show hidden files on. You should put all your mods in there. If the mods folder is not there right after the install then make it and put your mods in it. Then when you run Minecraft there will be a profile called Forge that is created when you install forge and you can select it when the Minecraft launcher first loads, you want to use it in order to use the mods. I am an avid Minecraft player and I have 33 mods running on my  copy of Minecraft that I run on Ubuntu. I found that Minecraft version 1.7.10  has the best and the most mods made for it but there are mods for almost all versions of Minecraft. I included some screenshots to show you where all the folders are.


[ATTACH=CONFIG]264278[/ATTACH]_____[ATTACH=CONFIG]264279[/ATTACH]_____[ATTACH=CONFIG]264280[/ATTACH]

I should mention that when you first download Minecraft for Linux you  get a minecraft.jar file. You place that where you want your shortcut to  Minecraft at then you right click it choose properties then permissions  and check the run as application box and you can run Minecraft by  double clicking the jar after you tick that box in permissions.

Eh, please ignore this message apparently you have already been playing it, unless you didn't know this.

---

### Post by Rick_Astley on 2015-09-19
Is Forge the same thing as Bukkit?  My son and I bought a book 'Adventures in Minecraft".  It says to use Bukkit.  We have been able to get the Minecraft server running, but we could not connect to the server using a Minecraft client on the same physical machine the server is on.

---

### Post by ArgentWarrior on 2015-09-20
Mod installation on Linux is pretty much the same as on Windows. The only difference is that the .minecraft folder is located hidden in your home folder (hit ctrl+h to see it) instead of "C:\Users\Username\AppData\Roaming\WhySoManyHiddenFolders\.minecraft".
Also, make sure you get the jar installer for Forge instead of the exe.

---

