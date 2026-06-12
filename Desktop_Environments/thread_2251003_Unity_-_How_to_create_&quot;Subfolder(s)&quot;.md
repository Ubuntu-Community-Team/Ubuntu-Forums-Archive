---
title: "Unity - How to create &quot;Subfolder(s)&quot;?"
date: 2014-11-01
forum: Desktop Environments
---

### Post by Malmberg on 2014-11-01
Gents,

Excuse me if this question has been raised before - I have done several search s - without luck :-)

Here we go:
Is there a way to create a Subfolder in Unity? I would like to make a folder for - lets say - my "Audio-Video Apps"

Thanks in advance
Steen

---

### Post by mcduck on 2014-11-01
I assume you mean creating them in the Dash menu or the Launcher panel?

Neither one supports folders or submenus directly, but for the Launcher panel you can use the quicklist functionality for a similar result. I'm not sure if there's any graphiccal tool for making them, but creating/editing the .desktop flles by hand works and isn't awfully complicated...

For example, this is the .desktop file I use for my Minecraft launcher, with a right-click submenu that ahs options to launch various additional tools:
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
#Icon[en_US]=/home/mcduck/Programs/Minecraft/creeper.png
Exec=/home/mcduck/Programs/Minecraft/minecraft.sh
Name[en_US]=Minecraft
Name=Minecraft
Icon=/usr/share/icons/Moka/256x256/apps/minecraft.png

X-Ayatana-Desktop-Shortcuts=Technic;ATLauncher;Server;Minutor;

[Technic Shortcut Group]
Name=Technick Pack Launcher
Exec=/home/mcduck/Programs/Minecraft/technic.sh
OnlyShowIn=Unity

[ATLauncher Shortcut Group]
Name=ATLauncher
Exec=/home/mcduck/Programs/Minecraft/atlauncher.sh
OnlyShowIn=Unity

[Server Shortcut Group]
Name=Minecraft Server
Exec=gnome-terminal -x /home/mcduck/Programs/Minecraft\ Server/mcserver.sh
OnlyShowIn=Unity

[Minutor Shortcut Group]
Name=Minutor
Exec=minutor
OnlyShowIn=Unity
```

edit: This might be interestign option as well, although I have never tried it so I can't tell any details about how well it works: [http://www.techrepublic.com/article/the-ubuntu-unity-launcher-gets-a-facelift-with-unity-drawers/]("http://www.techrepublic.com/article/the-ubuntu-unity-launcher-gets-a-facelift-with-unity-drawers/")

---

### Post by grahammechanical on 2014-11-01
I use the file manager to open the folder and then I right click the background of the file manager window and I select New Folder. I then select the folder and a right click will give me the option to Rename the folder.

This is a function of the file manager and not necessarily of Unity. Perhaps you are meaning a sub folder in the menu that appears when we right click an icon in the Launcher. It is not clear what you want.

Regards.

---

### Post by sandyd on 2014-11-01
Moved to Desktop Environments

---

### Post by whitesmith on 2014-11-01
In the (somewhat unlikely since Unity is in your post) possibility that you want to create one from the terminal, here's how to do it. Move to the directory where you want the subdirectory to be. Let's say the directory is called **/test** and the subdirectory should be** test_1**.Now,```
cd /test
sudo mkdir test_1
```It really is that simple. The sudo part is needed because you have limited permissions outside your home directory (variously styled as ~ and $HOME). This info, and much more, is in the 2nd reference in my sig line. Remember, All directories should have 775 permissions, unless you have a good reason for something different. G'Day!

---

### Post by buzzingrobot on 2014-11-01
> **Malmberg said:**
> Gents,

Excuse me if this question has been raised before - I have done several search s - without luck :-)

Here we go:
Is there a way to create a Subfolder in Unity? I would like to make a folder for - lets say - my "Audio-Video Apps"

Thanks in advance
Steen


A "subfolder" is just a folder created "inside" another folder. As others have outlined, they can be created and named with the file manager or by using the "mkdir" command in the terminal.  The results are the same.

---

### Post by Malmberg on 2014-11-02
My mistake!

What I actually meant was "How to create a folder in The Launcher" - that could hold several programs!

Sorry for the confusion!

Cheers
Steen

---

### Post by Malmberg on 2014-11-02
Hi "mcduck"

Your hint - The "unity-drawes" did the trick!

Thanks

---

