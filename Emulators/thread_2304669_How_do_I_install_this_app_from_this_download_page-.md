---
title: "How do I install this app from this download page- ?"
date: 2015-11-28
forum: Emulators
---

### Post by michael-piziak on 2015-11-28
I'm using Ubuntu 12.04 lts.  I had problems getting this app to work on multiple 14.04 lts, so I am sticking with 12.04 lts

I've tried to download/extract the first two on this list at:  [URL="http://ubuntuforums.org/showthread.php?t=2296918"]http://ubuntuforums.org/showthread.php?t=2296918  

I will now try to install the 4th one and link to a video of what I'm doing and I need help to download/install/extract this and get an icon for it to place on my dock:

Here is the movie:

[https://youtu.be/IUySNhjOkeE](https://youtu.be/IUySNhjOkeE)

[/URL]

---

### Post by tridentlead on 2015-11-29
The file you have there is a pre-compiled binary executable. I am not sure about that particular application but I do not believe it is an installer. You should move it to location where it will reside and be executed from (/usr/bin is a good choice). To make a desktop entry you will need to create a unity .desktop file. Additionally, I do not believe that that file is currently executable, you need to change its permissions to executable, this can be done from terminal with: > chmod 755 snes9x-gtk If you copy the file to /usr/bin, a .desktop file could be named snes9x-gtk.desktop and formatted:
> 
[Desktop Entry]
Version=1.0
Name=SNES-GTK
Comment=A GTK compatible SNES emulator
Exec=snes9x-gtk
Icon=/home/michael-piziak/Documents/snes.png
Terminal=false
Type=Application
Categories=Utility;Application;Game;


You would then follow the Ubuntu Wiki's advice for adding a .desktop file to unity

> 
You can place  your .desktop file at /usr/share/applications/ or at  ~/.local/share/applications/. After  moving your file there, search for it in the Dash (Windows key ->  type the name of the application) and drag and drop it to the Unity  Launcher. Now your launcher (.desktop file) is locked on the Unity  Launcher!  If your desktop file cannot be found by doing a search from  the Dash, you may need to read on... 


---

### Post by michael-piziak on 2015-11-29
ok, where is this /usr/bin folder at?  I currently have the downloaded file "snes9x-1.53-src.tar.bz2" sitting on my desktop.

See my screenshot of me searching for the hidden folder below:

---

### Post by howefield on 2015-11-29
> **michael-piziak said:**
> ok, where is this /usr/bin folder at?

Click on the "File System" option in the left hand window pane, then you'll see the /usr folder..

---

### Post by michael-piziak on 2015-11-29
ok howefield, thanks I found it.

However, it won't let me move the file to that folder.  See screenshot below

---

### Post by howefield on 2015-11-29
Yep, you'll need elevated permissions to write to that folder.

Either open the file manager as root or use the terminal to move the file to that folder.

```
gksudo nautilus
```

or

```
sudo cp path/to/source/file /usr/bin/
```

Close the file manager once you are done, and minimise the risk of doing something regrettable.

---

### Post by michael-piziak on 2015-11-29
ok, I did the gksudo nautilus command in terminal and was able to drag it to bin and it made a copy of it in bin.  I placed the desktop copy back in the download folder for the time being.

Now, when I type in "chmod 755 snes9x-gt" into terminal I get the following:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ chmod 755 snes9x-gtk 
chmod: cannot access `snes9x-gtk': No such file or directory
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by howefield on 2015-11-29
Is this the file that you have just moved into /usr/bin/ ?

Try 

```
sudo chmod 755 /usr/bin/snes9x-gtk
```

---

### Post by michael-piziak on 2015-11-29
> **howefield said:**
> Is this the file that you have just moved into /usr/bin/ ?

Try 

```
sudo chmod 755 /usr/bin/snes9x-gtk
```

Yes, the file was moved to bin and it made an exact copy of it in there - then I moved the file still on desktop back to the download folder.


Still can't get the command to work, I get:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo chmod 755 /usr/bin/snes9x-gtk
[sudo] password for michael: 
chmod: cannot access `/usr/bin/snes9x-gtk': No such file or directory
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 


See screenshot below:

---

### Post by howefield on 2015-11-29
The error is telling you what is wrong.. there is no file called snes9x-gtk in the folder.

There is however a file called snes9x-1.53-src.tar.bz2.

I haven't read the link you posted in the OP but suspect that you have missed a step.

---

### Post by michael-piziak on 2015-11-29
ok, I will put it on the back burner until I can get further help.

Perhaps I should have chosen a different download besides the first one - I dunno

Michael

Thanks to you and everyone that can help me with this

---

### Post by michael-piziak on 2015-11-29
How to delete this file in my bin folder?

---

### Post by michael-piziak on 2015-11-29
Interesting, I can't delete the snes9x-1.53-src.tar.bz2 file from the bin folder either.

?

---

### Post by howefield on 2015-11-29
Threads merged.

Open a terminal and type..

```
sudo rm /usr/bin/snes9x-1.53-src.tar.bz2
```

---

### Post by michael-piziak on 2015-11-29
> **howefield said:**
> Threads merged.

Open a terminal and type..

```
sudo rm /usr/bin/snes9x-1.53-src.tar.bz2
```

Result is:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo rm /usr/bin/snes9x-1.53-src.tar.bz2
[sudo] password for michael: 
rm: cannot remove `/usr/bin/snes9x-1.53-src.tar.bz2': No such file or directory
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by howefield on 2015-11-29
Sorry, confused with the first few posts.. try without the /usr part

```
sudo rm /bin/snes9x-1.53-src.tar.bz2
```

---

### Post by michael-piziak on 2015-11-29
> **howefield said:**
> Sorry, confused with the first few posts.. try without the /usr part

```
sudo rm /bin/snes9x-1.53-src.tar.bz2
```

ok that removed it - thanks!


Still, if someone can tell me some terminal code or any way to get Snes9x up and running I'd much appreciate it - I wait patiently

Michael

---

### Post by deadflowr on 2015-11-29
Sort of out from left field, but what about perhaps trying a windows version in wine.
Just a thought.
(probably not a helpful though, but a thought nonetheless)

---

### Post by michael-piziak on 2015-11-29
Perhaps I will, but I'd much prefer not to.  Snes9x for Linux worked so well in the past for me.

I have bsnes installed.  But what I really really liked about Snes9x is that I could program a gamepad button for save state and program another button for load state.

---

### Post by michael-piziak on 2015-11-29
I can get to this point, and a get info says it's executable ?

---

