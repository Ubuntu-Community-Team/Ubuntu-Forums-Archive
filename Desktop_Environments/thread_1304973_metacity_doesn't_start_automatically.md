---
title: "metacity doesn't start automatically"
date: 2009-10-29
forum: Desktop Environments
---

### Post by jworr on 2009-10-29
I just upgraded to ubuntu 9.10.  I installed a bunch of different programs, setup my video card driver then restarted.  When it can back up metacity wasn't running.  I was able to add metacity to the "startup applications" to fix it.  Is there someway I can fix the gnome config files to start metacity that way?

---

### Post by jworr on 2009-10-29
my video card is an nvidia 8600 something and I'm using the propriety drivers

---

### Post by MeanEYE on 2009-10-29
> **jworr said:**
> my video card is an nvidia 8600 something and I'm using the propriety drivers

Did you happen to install Emerald? And do you have compiz running :)

---

### Post by jworr on 2009-10-29
No, I didn't install emerald and I'm not using compiz

---

### Post by MeanEYE on 2009-10-29
Before you added metacity to autostart list... what would happen when you log in?

---

### Post by Devport on 2009-10-29
Same here - funnily enough it worked a few times and out of a sudden metacity wasn`t started anymore. Switching to desktop effects enabled ( compiz ) and back didnt reenable metacity. No messages are given up to the gnome desktop - windows are just not decorated anymore.

---

### Post by jworr on 2009-10-29
That's my issue - there is no window decoration.  Thus the windows can't be manipulated at all.  

I created a new user on my box, it didn't have the problem.  It seems like there is some kind of issue with the upgrade of gnome.  However, I would like my original user to work.

---

### Post by MeanEYE on 2009-10-29
Try with: ```
sudo dpkg-reconfigure metacity
```

Let me know how it goes!

---

### Post by jworr on 2009-10-29
unfortunately, that didn't fix it

---

### Post by MeanEYE on 2009-10-30
Can you manually start metacity from console and give post output here? This is like fishing in the dark...

---

### Post by jworr on 2009-10-30
when I start it from the console, I don't get any errors - it just starts

---

### Post by a701440 on 2009-11-02
I have exactly the same problem. After upgrading to 9.10 the window manager just does not start on login. If I run metacity from the command line it works fine. X and gnome desktop seem to work fine. Where is metacity normally started from?

---

### Post by jworr on 2009-11-02
unfortunately, I don't know where metacity normally starts from.  It used to be configured in the file ~/.gnome2/session.  I'm not sure where they moved it to.

---

### Post by MeanEYE on 2009-11-05
> **jworr said:**
> unfortunately, I don't know where metacity normally starts from.  It used to be configured in the file ~/.gnome2/session.  I'm not sure where they moved it to.

Well Metacity is just window decorator, not a window manager... most likely you won't be able to find it in session files. Are you completly sure you are not running Compiz...

What is the result of:
```
ps -A | grep compiz
```

Just a note: If you have desktop effects enabled you are running Compiz...

---

### Post by iRauta on 2009-11-11
Hi! I'm new around here, but I have been Ubuntu / Linux user for a while. I recently upgraded from 8.04 to 9.10.

Looks like I'm having this same problem, when I log in there's no metacity or compiz running. I can open the terminal (panels are visible and working) and run either of them and things are working - until the next login of course. I have Ati Radeon 4870 and use the automatically offered closed drivers if that matters.

Now, to actually contribute at least something: I think I know where the window manager / decorator is specified in settings. Just start gconf-editor (via terminal, you probably won't find it in menus) and browse to /desktop/gnome/session. There is a configuration key required_components_list, which contains a list of values. For me they are [windowmanager,panel,filemanager].

Those values seem to refer to the required_components, which is another "folder" under the session "folder". There are some values, and the important one is windowmanager. Its value is metacity if you have no desktop effects on, and compiz if they are enabled. In my case it doesn't seem to do anything, but checking that value might help figure things out.

Edit: Okay, I took a little chance and added some extra values to those places and the program (firefox to be specific) did run, so I am pretty sure that that place really is the one that is supposed to run metacity or compiz.

---

### Post by jworr on 2009-11-12
for /desktop/gnome/session/required_components/windowmanager I have metacity

---

### Post by iRauta on 2009-11-14
Yesterday, I tried deleting the entire .gconf directory, and the .gnome2 directory too. (Actually, I just renamed them.) Did not help. I think it can be ruled out that the problem lies in those places. The file .xsession-errors contains several error messages, but nothing seems to be related to metacity - or compiz if I try to enable desktop effects.

Now I just created a new user, and for it metacity...sorry, compiz started up fine. So even if the reason for metacity (or compiz) not starting is not in those two obvious-looking directories it still seems to be something in the home directory.

---

### Post by iRauta on 2009-11-14
I think I found out the files that caused this. Took some time to narrow the problem to a specific directory but it's nice to have a desktop that works again!

Go to directory .local/share/applications - .local resides in your home directory. (Ctrl-H shows dot-files and directories in file manager.) I moved these files from there to a backup folder:

**compiz.desktop**
**gnome-wm.desktop** (gnome-wm apparently is a script that runs the actual window manager and seems to be the default value for the windowmanager gconf key)
**metacity.desktop**

I have no idea why those files would cause problems - maybe it is a bad thing to have launchers with some specific names, or maybe the files are in a old format and some update broke compatibility or maybe they are somehow corrupted.

---

### Post by jworr on 2009-11-14
Renaming the files gnome-wm.desktop metacity.desktop in the .local/share/applications directory fixed it!  Good job figuring this out!

---

### Post by Ludwig Weinzierl on 2009-12-22
Moving the files gnome-wm.desktop metacity.desktop in the .local/share/applications directory fixed it for me as well!  
Thanks a lot!

---

### Post by Wiley99 on 2010-01-08
Unfortunately rm-ing the files didn't work for me. I use compiz and suddenly it doesn't start automatically anymore. Another user has no problems, so with me too it's in my home dir. 

I suspect the 'Automatically remember running apps' function: turned it on, didn't like how it worked, turned it off again. Unfortunately, removing everything in ```
 ./config/gnome-session/saved-session/ 
``` doesn't work either.

Any idea's?

---

### Post by Kaminofushicho on 2010-10-17
I was slow to upgrade, but removing the .desktop files from .local/share/applications worked for me.

thanks,

---

