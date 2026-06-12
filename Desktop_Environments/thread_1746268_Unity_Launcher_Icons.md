---
title: "Unity Launcher Icons"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Derek Karpinski on 2011-05-01
I've installed Office 2007 under wine, and would like to add launchers for Word, Excel, etc to the Unity launcher bar.

So, I've created a launcher on the Desktop that will run Word with wine.  I've changed the icon to the Word Icon and everything works great from the desktop.  If I drag that launcher to the Unity bar, it adds it, but changes the icon to the springboard default icon that new launchers use.  Please see attached picture.

As a side note, I am really starting to like Unity (puts on flamesuit), but it seems very easy to break the install of 11.04.  I've had to reinstall 4 times now.:(

Thanks!

---

### Post by Derek Karpinski on 2011-05-02
Bump for help. :)

---

### Post by epictete on 2011-05-09
I've got exactly the same problem and am very interesting in a solution!

---

### Post by Sisophon2001 on 2011-05-09
> **Derek Karpinski said:**
> Bump for help. :)

I did not see this problem when I added a wine program to my menu. From what I remember I used the finder (the search for application box - don't know hat is is called) to locate the program, and I dragged and dropped it from there. But my wine programs had a preconfigured icon from my upgrade.

Garvan

---

### Post by deaddy on 2011-05-09
I have a similar problem too, when i create a launcher for a java app it is disappearing after reboot.

How can i fix this?

---

### Post by Derek Karpinski on 2011-05-09
> **Sisophon2001 said:**
> I did not see this problem when I added a wine program to my menu. From what I remember I used the finder (the search for application box - don't know hat is is called) to locate the program, and I dragged and dropped it from there. But my wine programs had a preconfigured icon from my upgrade.
 
Garvan
 
Tried that too.  Either it wouldn't 'stick' to the launcher, or I got a wine bottle as an icon.  Could never get the Word icon.......is this some conspiracy against MS???:confused:

---

### Post by Sisophon2001 on 2011-05-10
Sorry I tried it again and I cant get it to work now. I don't understand why it appeared to work before. Sorry, I will look around to see how to solve this and let you know if I find anything.

Garvan

---

### Post by zae_bdn on 2011-05-12
> **Derek Karpinski said:**
> I've installed Office 2007 under wine, and would like to add launchers for Word, Excel, etc to the Unity launcher bar.

So, I've created a launcher on the Desktop that will run Word with wine.  I've changed the icon to the Word Icon and everything works great from the desktop.  If I drag that launcher to the Unity bar, it adds it, but changes the icon to the springboard default icon that new launchers use.  Please see attached picture.

As a side note, I am really starting to like Unity (puts on flamesuit), but it seems very easy to break the install of 11.04.  I've had to reinstall 4 times now.:(

Thanks!

THAT'S WHAT I HAD JUST GOOGLIN'...  SEE U :)

[CENTER]You problem could be beacause of the *program launcher.* I assume your *.desktop* file contains Exec=wine '/home/user/.wine/dosdevices/c:/Program...' and so on. Try making a bash binary wich contains something like this:
  #!/bin/bash cd '/home/aldomann/.wine/dosdevices/c:/Archivos de programa/Warcraft II BNE' wine 'Warcraft II BNE.exe'   
Name it for instance warcraft2 and move it to /usr/bin (or any PATH variable, wich you can know by typing echo $PATH on the Terminal)
  
Then in your *.desktop* file instead of Exec=wine '...' use Exec=warcraft2.  I think Unity will assume this is not a wine program and will use your icon, **but it is only conjecture.**
  
Hope it works ;)
  
By default your Wine apps .desktops are placed on /home/user/.local/share/applications/wine
  
Instead of modifying an existing .desktop file you can create a new one and place it on /home/user/.local/share/applications. It should be something like this:
  [Desktop Entry] Name=Application Comment=Comment Exec=app-binary Icon=app-icon Type=Application Terminal=false StartupNotify=true Categories=GTK;Utility   
*Tip:* If you place your icon on /home/user/.icons/ (i.e app-icon.png) you will only have to put Icon=app-icon.[/CENTER]

---

### Post by mcduck on 2011-05-12
In my experience the best way is to simply create the launcher like you would have done in previous Ubuntu version, by using the Main Menu editor to create a proper menu entry for your programs. After that they will appear correctly in Dash searches and you can reliably add them to the Unity Launcher as well.

---

### Post by Frogs Hair on 2011-05-12
I have the Firefox Nightly browser and to change the icon to match my set I went .icon folder in hidden / home  > Awoken . I entered  128x128 Apps folder and  selected the icon and saved to home > renamed the icon and added it back to the same folder . After this I restarted 

The trick to find the correct name and that took a few tries . If you are using Ubuntu icons the location will probably be usr/share in the file system and you could add an icon you have found on the net as well .

---

### Post by zeddock on 2011-06-06
> **mcduck said:**
> In my experience the best way is to simply create the launcher like you would have done in previous Ubuntu version, by using the Main Menu editor to create a proper menu entry for your programs. After that they will appear correctly in Dash searches and you can reliably add them to the Unity Launcher as well.

This worked for me.  Hope it sticks!

Go to System Settings via the button in the top right for Log-Off and Shutdown... (it is at the bottom of the menu.)
Now go to Main Menu

Pick an area and add a launcher, making sure you have the icon you want... (There may be an issue with whether it is 32 or 48 pixels!)

Once it is there, you can find it via a search in the upper left hand "dash" icon.  

Once you find it there, drag and release on the unity bar.

It even kept my icon!

Thanx!

zeddock

---

