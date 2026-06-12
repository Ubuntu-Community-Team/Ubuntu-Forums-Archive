---
title: "Files in Home directory appearing on Desktop?"
date: 2005-07-08
forum: Desktop Environments
---

### Post by Iwantu_ubuntu on 2005-07-08
Say I create a file and save it in my home directory...for some reason it also appears on the ubuntu desktop.  If I delete it from the desktop it also deletes it from the home directory.  What is this behaviour and how can I turn it off?  TIA

---

### Post by frodon on 2005-07-08
The repertory /home/your_user_name/Desktop contain all the desktop file. If you put a file here it will appear on your desktop. If you don't want any icon on your desktop put your files in an other repertory.

---

### Post by apollo2011 on 2005-07-08
frodon: I think somehow his Desktop folder got set to his home folder.  he didn't word himself very well but he is saying that whenever he created a file in his home directory, it appears on the desktop, and when he deletes it on the desktop, it gets deleted from his home directory.  So somehow the Desktop directory is no longer set as the directory for files on the desktop.

Im not sure how you could have messed up this setting and I am not sure how you switch it back...

---

### Post by Iwantu_ubuntu on 2005-07-08
[QUOTE=frodon]The repertory /home/your_user_name/Desktop contain all the desktop file. If you put a file here it will appear on your desktop. If you don't want any icon on your desktop put your files in an other repertory.[/QUOTE]

Are you saying there's a directory called Desktop in the /home/username ?   I don't see a Desktop folder there or a .Desktop....even the amsn_received folder in the /home/username directory appears on the desktop and that directory was created by amsn not me.......or are you saying saving something in /home/username will cause it to appear on the desktop? I just saved a file in a folder called Downloads (/home/username/Downloads) and it didn't appear on the desktop.

---

### Post by frodon on 2005-07-08
[QUOTE=apollo2011]Im not sure how you could have messed up this setting and I am not sure how you switch it back...[/QUOTE]
you're right, apollo2011.
Try to locate your desktop repertory: ```
sudo updatedb
locate Desktop
```I really don't know why your Desktop repertory is not here.

---

### Post by apollo2011 on 2005-07-08
[QUOTE=Iwantu_ubuntu]Are you saying there's a directory called Desktop in the /home/username ?   I don't see a Desktop folder there or a .Desktop....even the amsn_received folder in the /home/username directory appears on the desktop and that directory was created by amsn not me.......or are you saying saving something in /home/username will cause it to appear on the desktop? I just saved a file in a folder called Downloads (/home/username/Downloads) and it didn't appear on the desktop.[/QUOTE]

Yeah there should be a folder called Desktop.  You might fix the problem simply by adding this folder because maybe then it would be detected and stuff would stop being added to the desktop just from being in the home directory.

---

### Post by Iwantu_ubuntu on 2005-07-08
[QUOTE=apollo2011]Yeah there should be a folder called Desktop.  You might fix the problem simply by adding this folder because maybe then it would be detected and stuff would stop being added to the desktop just from being in the home directory.[/QUOTE]
 Very weird.  I just created a directory called Desktop in the /home/user directory and guess what?  that desktop folder is also now on the desktop.  I rebooted the computer and still the same thing. Created a tar file as a test and it appeared on the desktop and /home/user directory....damn it!  I suppose creating a new user account might fix the prob right? but I lose all my settings etc...

---

### Post by varunus on 2005-07-08
This is a setting in Nautilus, guys, to let a user use their home folder as the Desktop.  Don't do anything drastic.  To fix it, you'll need to edit a gconf key...I can't remember which one, though, since I'm at work and in Windows.  I'll let you know this evening when I can boot Ubuntu.

---

### Post by Iwantu_ubuntu on 2005-07-08
Thanks, appreciate it.

---

### Post by varunus on 2005-07-08
Ok, now I'm at home, so I found it:

Go to Applications->System Tools->Configuration Editor

Go to apps, then nautilus, and click on the preferences folder.

Scroll down on the right side until you see the desktop_is_home_dir key and uncheck the box.  (Make sure to make a Desktop folder in your home directory before you do this so Nautilus doesn't complain.)

Enjoy.

---

### Post by mtron on 2005-07-08
[QUOTE=varunus]This is a setting in Nautilus[/QUOTE]

open gconf-editor (in Apps - System Tools) and navigate to 
apps - nautilus - preferences and unckeck the key "desktop_is_home_dir"

It might need a Ctrl Alt Backspace, but after the next login you should have a "desktop" dir under $HOME.

---

### Post by Iwantu_ubuntu on 2005-07-10
Thanks a lot guys!  Didn't have time to boot the machine up until now, so I appreciate your quick replies.  It worked and almost a eye sore relief at the same time in strange way.   Is this a default option enabled on ubuntu? or did this somehow get turned on in my particular installation?  Thanks again!

---

### Post by lukemack on 2008-05-17
I have this problem on Ubuntu 8.04 Hardy Herron Desktop. The setting mentioned above does NOT fix it.  Any other ideas?

---

### Post by wrrrrrrrrrr on 2008-06-05
hello
have the same problem. recently turned on displaying home as desktop option can't be now disabled. mentioned gconf setting does NOT do anything. using hardy, and yes - after I changed to use home as desktop, I decided not to be bothered by desktop folder even if it wasn't displayed on the desktop but existed in home. now after turning back off not to use home as desktop it doesn't matter what kind of files and folders are in my home 'cause they are all simply showed on the desktop. I did reboot several times and nothing. I think it's a bug. if someone can reproduce it in a way as I described above. I repeat: 1. install ubuntu hardy 2. install gtweakui 3. run system->settings->gtweakui nautilus, turn on "use nautilus to display  desktop" (or whatever it's called in your language - I use Polish locale and the literal translation sounds something like I wrote), 4. delete desktop folder from your home folder 5. reboot, and then 6. try revert nautilus somehow to the state where it displayed desktop and home directories separately again.
if you want to know, I did check if clicking in gtweakui makes effect on respective gconf setting and it DOES, but it does NOT actually make any effect on the nautilus behavior. I think it's a bug in gconf, for as I know gtweakui does nothing else than change the settings using gconf. I remember having earlier some similar issues with gconf when I edited some application or system options with it (don't remember which one and what version of ubuntu, gconf or gnome it was) and then that did not make any difference in the way of these application or system behaved. sometimes the logout-login or reboot procedure helped.
weird stuff. this sometimes needed feature of nautilus seems to be broken now. I think reseting nautilus configs by, ie deleting its config files would do the job, but hey, I don't want to do that, I did spent some significant time customizing my nautilus and I don't think I'm able to do that again without eventually (as I always give limited amount of patient to everyone and thing I need to work out) switching again to thunar, especially 'cause my ubuntu installation is a week old or so.
cheers.
finally: me so poor english guys is sorry =) tried my best though.


---

well I googled and found this info:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037")

this IS a bug of some kind but it can be easily fixed.
just visit the file ```
**~/.config/user-dirs.dirs **
```
and replace the entry
```
XDG_DESKTOP_DIR=""
```
with
```
**XDG_DESKTOP_DIR="[COLOR="Red"]$HOME/Desktop[/COLOR]"**
```

the file .config/user-dirs.dirs can contain some other string value after XDG_DESKTOP_DIR= but the thing is it must be the path of the folder which you want to use as your desktop

after you make above modification, open gconf-editor and turn ON and OFF the **/apps/nautilus/preferences/desktop_is_home_dir** setting and if it's needed do the same with **/apps/nautilus/preferences/show_desktop**

it did the trick for me. no more home folder content displayed on the desktop except the content of the $HOME/Desktop folder

hope this will help you

---

