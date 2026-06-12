---
title: "Minecraft Flan's Mod"
date: 2013-09-13
forum: Gaming &amp; Leisure
---

### Post by l-f-kempe on 2013-09-13
I am not a minecraft gamer but i installed ubuntu on my 10 year old brother computer and he is. He has been using flans mod on minecraft for windows and he wants to install it on Ubuntu to, but i cant seem to get it working. Is there any minecraft gamers here that knows how to get this done, and if there is some script/program one can use to ease the installation of mods. I installed minecraft from this ppa: ppa:minecraft-installer-peeps/minecraft-installer. From what I can understand one should use **[Minecraft Forge]("http://www.minecraftforge.net/forum/index.php/topic,10075.0.html") **to install the mod but I cant get that to work ether. a short how to would be much appreciated.

---

### Post by DarkAmbient on 2013-09-13
Don't take my words on this one, I havn't tried with 1.6.2. But...

Download the forge-files for your version of Minecraft (which probably is 1.6.2)

Go into your homefolder, press CTRL+h to show hidden files, enter .minecraft/versions/1.6.2 and open 1.6.2.jar with the archivemanager. Then drag the (extracted) forge-files into 1.6.2.jar.

To install mods look for instructions whereat you downloaded the mod. Could be same approach as installing Forge...

edit: think you need to delete 2 files below META-INF in 1.6.2.jar for it to work to. Do it easily in a terminal: **zip -d ~/.minecraft/versions/1.6.2/1.6.2.jar META-INF/MOJANG***

---

### Post by l-f-kempe on 2013-09-14
Thank you this was almost what i tryed but i added files to /usr/share/minecraft/minecraft.jar. anyway i cant get it to work. it seams like 1.6.2.jar get overwriten by a clean version every time i launch the game. anyway to stop the launcher from doing that?

EDIT:
I also tried install minecraft with your footer link, but i get an error when pressing login. login failed (Not downloaded)

---

### Post by R33D3M33R on 2013-09-14
Use [MCPatcher]("http://www.minecraftforum.net/topic/1496369-163-and-earlierupdate-94-mcpatcher-hd-fix-422/"). I also had problems with some mods not registering, but after adding them with MCpatcher, everything seem to work.

---

### Post by DarkAmbient on 2013-09-14
Aight. Oh my bash-app Minecraftier is for 1.5.2 only. Will update it when I got the time. Might start from scratch in python as well.

---

### Post by ueli-ton on 2013-12-29
I have minecraft forge 1.5.2, you can install SP, and forge pro upgrade, following the commands in terminal.


It's in Portuguese, but gives to understand:
[URL="http://www.vivaolinux.com.br/topico/Emulacao-de-jogos/MinecraftSPjar-no-Ubuntu-pra-servidores-nao-oficiaisPirata"]
http://www.vivaolinux.com.br/topico/Emulacao-de-jogos/MinecraftSPjar-no-Ubuntu-pra-servidores-nao-oficiaisPirata[/URL]

---

