---
title: "Edit Pale Moon Icon in Launcher Bar"
date: 2015-05-06
forum: Desktop Environments
---

### Post by phaedrus3 on 2015-05-06
I am running Ubuntu 14.04 Rusty Tahr with the gnome desktop.  My preferred browser is Pale Moon and I've placed an icon on the launcher that runs the executable.  Problem is it isn't the "pretty" Pale Moon icon but a gray box with a question mark on it.  How can I change this to the PM icon?  I have searched for a solution to this but can't seem to find what will work.

I appreciate your assistance.

---

### Post by deadflowr on 2015-05-06
Where is the pale moon launcher located in the system?
In the user's .local/share/applications directory or the system's /usr/share/applications directory?

Find it
open the text editor gedit
(you can either drag and drop it into gedit or run the Open dialog in gedit to search for it; typically open >> go to sidebar "Computer" >> usr >> share >> applications >> name-of-application.desktop.)

Look at the path of the icon.

Also, sometimes I've noticed that icons fail to show until a logout and login happens, so...

---

### Post by phaedrus3 on 2015-05-06
I've restarted Ubuntu before posting query.  Palemoon program executable is in /opt and icon (mozicon128.png) is at path /opt/palemoon25.1.0/browser/icons.  Gedit would not open palemoon executable (program) except in uneditable form, however.  It suggested I try a different language resulting in same.

---

### Post by ajgreeny on 2015-05-06
You will have to edit the *palemoon*.desktop file, or whatever it is called as root so try using ```
sudo nano /path/to/*palemoon*.desktop
```Save it with Ctrl+O and close nano with Ctrl+X.

The desktop file will look a bit like below with lines showing possibly for many different languages```

[Desktop Entry]
Version=1.0
Name=Firefox
Comment=Browse the World Wide Web
GenericName=Web Browser
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=firefox %u
Terminal=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
StartupNotify=false

```
Look for the line 
**Icon=path/to/icon/file**
and edit it to your own pathway
**Icon=/opt/palemoon25.1.0/browser/icons/filename**

---

### Post by phaedrus3 on 2015-05-06
> **ajgreeny said:**
> You will have to edit the *palemoon*.desktop file, or whatever it is called as root so try using ```
sudo nano /path/to/*palemoon*.desktop
```Save it with Ctrl+O and close nano with Ctrl+X.

I really do appreciate the response however - and forgive my ignorance - wouldn't this require the .exe or link to .exe to be on the desktop?  I haven't, er, fully transitioned out of windows, you see.  The program is in /opt.  I simply dragged that onto the gnome launcher on the edge of the screen.  I do know where the preferred icon is and if I could use (nano?) to open the file similar to the one you list I think I'd be there.  I searched in "computer" for "palemoon.desktop" and, of course, didn't find.  Could anyone dumb this down for me?

---

### Post by mc4man on 2015-05-06
It maybe easier if you removed your currently installed version (to /opt) & just added this palemoon ppa.
It installs normally with a proper .desktop file & icon ect.
ppa here - 
[https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon](https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon)

If you installed using the installer script then run the script, it should have an uninstall option.
After that remove launcher icon if still there
Then - 
```
sudo add-apt-repository ppa:marian.kadanka/palemoon
```
```
sudo apt-get update
```
```
sudo apt-get install palemoon
```

Then just start palemoon & lock icon that appears in the launcher  to the launcher.

If using the ppa ect. I'd also do this after install
```
sudo nano /usr/share/applications/palemoon.desktop
```
Use arrow keys to go down to the StartupNotify=true line & make it StartupNotify=false
Then save & exit nano 
ctrl+o
press enter key
ctrl+x

---

### Post by phaedrus3 on 2015-05-06
> **mc4man said:**
> It maybe easier if you removed your currently installed version (to /opt) & just added this palemoon ppa.
It installs normally with a proper .desktop file & icon ect.
ppa here - 
[https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon](https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon)

That's a good idea.  I thought to use the Synaptic Packager Manager to uninstall however Pale Moon doesn't appear there.  I honestly don't recall how I installed PM its been so long.

Can I use sudo apt-get remove palemoon? or should one use sudo apt-get --purge remove palemoon?

---

### Post by ajgreeny on 2015-05-06
As mc4man said "If you installed using the installer script then run the script, it should have an uninstall option."

You can't use **synaptic** or **apt-get remove** to uninstall something that was installed the way you installed palemoon.

---

### Post by phaedrus3 on 2015-05-06
> **ajgreeny said:**
> As mc4man said "If you installed using the installer script then run the script, it should have an uninstall option."

I guess I'm just stuck then cause I have no idea how I installed the program.  Unless you can tell me what the installer script is.  Thanks anyhow.

---

### Post by stinktier2 on 2015-05-06
> **phaedrus3 said:**
> I guess I'm just stuck then cause I have no idea how I installed the program.  Unless you can tell me what the installer script is.  Thanks anyhow.

Just get the installer here [http://sourceforge.net/projects/pm4linux/](http://sourceforge.net/projects/pm4linux/) and use it as described in the readme. It offers the options to update or remove Pale Moon.

---

### Post by mc4man on 2015-05-06
> **phaedrus3 said:**
> I guess I'm just stuck then cause I have no idea how I installed the program.  Unless you can tell me what the installer script is.  Thanks anyhow.
Probably doesn't matter as /opt isn't in the normal path. If the installer created a symlink in /usr/local/bin or /usr/bin then that should go. Otherwise just remove the launcher icon & proceed. You can always clean up /opt later
What does this command return,  if anything.
```
which palemoon
```

---

### Post by phaedrus3 on 2015-05-06
> **mc4man said:**
> What does this command return,  if anything.
```
which palemoon
```

Interesting.  command which palemoon returns /usr/bin/palemoon

---

### Post by mc4man on 2015-05-06
Then just go 
```
sudo rm /usr/bin/palemoon
```
Then go ahead with adding the ppa ect. (it may not really matter if you do the above as the ppa version would likely overwrite that file anyway..
If you want to clean out /opt/ then you can do so later, post results of below for starters on that when inclined
ls /opt

---

### Post by phaedrus3 on 2015-05-06
> **mc4man said:**
> Then just go 
```
sudo rm /usr/bin/palemoon
```
Then go ahead with adding the ppa ect. (it may not really matter if you do the above as the ppa version would likely overwrite that file anyway..
If you want to clean out /opt/ then you can do so later, post results of below for starters on that when inclined
ls /opt

Before I do this - you understand that /usr/bin/palemoon is only a shortcut to opt?  And, to clean out /opt I should merely delete the palemoon folder and all contents, after, of course, seeing what the ppa version does?

---

### Post by mc4man on 2015-05-06
> **phaedrus3 said:**
> Before I do this - you understand that /usr/bin/palemoon is only a shortcut to opt?  And, to clean out /opt I should merely delete the palemoon folder and all contents, after, of course, seeing what the ppa version does?

Correct, I understand all of that..

---

### Post by phaedrus3 on 2015-05-06
Installed new ppa using command line
Ran Synaptic Package Manager
Found new PPA, checked it and clicked install
Package downloaded and installed:

Commit Log for Wed May  6 19:43:02 2015 (from Synaptic Package Manager)


Installed the following packages:
palemoon (25.3.1-0~trusty2)

Installed files:

/.
/usr
/usr/bin
/usr/bin/palemoon
/usr/lib
/usr/lib/palemoon (I'm not copying the entire output of synaptic Package Manager Palemoon Properties here for the sake of brevity)

The executable and launcher icon didn't change to the one desired for some reason and when I run the .exe in /usr/lib/palemoon install it opens the same browser as the .exe in /opt which is to say all my bookmarks, history, etc. are there.  I'm no doubt missing something in handling this.  But at least the browser works and the operating system seems OK with all this.  I don't know what I'll do next but I'm glad to have the PPA.  Likely I'll just delete the palemoon folder in /opt and see what happens.  On this particular PC I also have Win7.  Using Grub to try Ubuntu which is not highly customized so a clean install of Ubuntu wouldn't be so bad.

I'm going to sudo pm-hibernate for now.  Thanks to all.

---

### Post by ajgreeny on 2015-05-07
Don't worry that all your bookmarks and history etc etc are still showing; they have nothing to do with the executable version of palemoon but are sitting in a user configuration folder, probably in /home/username/.config/palemoon or something similar.

These configurations are retained even after a purge of the application in order to allow you to completely remove all the system files and folders of an application, but keep all your local, user configurations.  You need to open palemoon and go to **Help ->About** in the menus to see which version is actually running.

By the way, you keep mentioning  the "**.exe in /usr/lib/palemoon**" and I wonder if this is just your way of describing an executable; linux executables are not .exe files but usually just have the name of the application, ie, in this case just "palemoon".
Files with the .exe suffix are windows executables, some of which can be run in wine, but can not, as far as I'm aware, be executed directly in Linux.

---

### Post by mc4man on 2015-05-07
> and launcher icon didn't change to the one desired for some reason 
If you mean the existing one didn't change well, it won't. (was said for you to remove it.
In any case - 
remove the palemoon launcher if still wrong/no icon
go alt+F2, type in 
gtk-launch palemoon
lock that icon in launcher

---

### Post by phaedrus3 on 2015-05-07
> **ajgreeny said:**
> Don't worry that all your bookmarks and history etc etc are still showing; they have nothing to do with the executable version of palemoon but are sitting in a user configuration folder, probably in /home/username/.config/palemoon or something similar.

These configurations are retained even after a purge of the application in order to allow you to completely remove all the system files and folders of an application, but keep all your local, user configurations.  You need to open palemoon and go to **Help ->About** in the menus to see which version is actually running.

By the way, you keep mentioning  the "**.exe in /usr/lib/palemoon**" and I wonder if this is just your way of describing an executable; linux executables are not .exe files but usually just have the name of the application, ie, in this case just "palemoon".
Files with the .exe suffix are windows executables, some of which can be run in wine, but can not, as far as I'm aware, be executed directly in Linux.

You are right and actually I knew about the config folder  but that slipped my mind.  One of my projects is to copy my config files from another computer.  I actually use four profiles - a tactic to increase privacy, combat browser finger printing, e.g. 

As for the .exe reference, I knew that too and was just being sloppy, I guess.  Old habits.  

What I think I'll do is forget about having the pretty blue moon for the Pale Moon icon and focus on cleaning up my mess beginning with changing the folder name in /opt to "palemoonold".  If everything works after that I'll delete the folder.

Puzzling over how I did the "corrupt" install of PM in the first place, a topic that came up above, I guess I downloaded a tar and extracted it and then just ran the prog from that extracted file - which seems possible I learned yesterday trying to install Fossamail, a project of Moonchild, Palemoon developers.  Couldn't find a PPA, or any install instructions so I just ran the program from the extracted folder and it worked.  Knowing this was not right I stopped right there and deleted everything I'd just done.  I'm unable to discover, at this point, the proper way to work with programs that are only available as compressed files.  I guess it takes some kind of a script (bash?)

Lessons learned.
Users can't create folders in places where that could damage the OS unless they elevate their authority.
Don't elevate your permissions without understanding what you are doing.
I need to learn how to efficiently navigate the file system using Terminal.
If you can't find a PPA for a package leave the tars alone if you don't know the proper procedure for turning them into a package.

---

### Post by phaedrus3 on 2015-05-07
First I closed PM after observing it was ver. 25.3.1 then found I don't have permission to change PM name in /opt but was able to change the program name to "programold".  However, the icon I'd locked to the launcher (with the question mark) would not then work.  I thought it pointed to the new install PM prog.  Then I searched for PM in the Dash.  The only thing that came up was the much coveted blue icon.  Clicked this shortcut and ver. 25.3.1 of PM opened and the correct icon appeared in the Launcher.  Voila!:biggrin:

Neither do I have permissions necessary to delete /opt/palemoon25.1.0, so I just need to sort that out. Whew!

---

### Post by phaedrus3 on 2015-05-08
This question came up earlier and I didn't have an answer.  I now know with pretty much certainty that I used the installer at this link. 

[http://sourceforge.net/projects/pm4linux/files/pminstaller/](http://sourceforge.net/projects/pm4linux/files/pminstaller/)

Your mileage may vary but I'd not recommend this.

---

