---
title: "How to completely restore Unity Launcher (all icons are missing)? Ubuntu 14.10"
date: 2014-11-29
forum: Desktop Environments
---

### Post by toma3 on 2014-11-29
[COLOR=#333333][FONT=UbuntuRegular]I was a little too brave in Terminal (manual "**sudo rm -rf name_of_icons/themes**" cleaning) and it seems I broke Unity. At first I did see some icons in left-pane, but after using command **unity --reset-iconsall** the icons are missed. After entering and confirming this command I got a bunch of errors-related reports of "something" missing (I really didn't remember all of it). And if I click on the Launcher upper-left button, Ubuntu freezes.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So, the question is, how to restore Ubuntu Unity? If possible, without using any other settings. Via terminal, maybe with Ubuntu on my DVD?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]/////[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]A few hours later I installed mate-environment-desktop-core via terminal. So I logged in in MATE and saw that there are also some icons missing. There, where they should be, is just a grey square. So maybe a problem is deepest? What do you suggest?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Br.

--------------------------------------

On askubuntu.com one of the people suggested:

[COLOR=#444444]If you do a locate /usr/share/themes | grep --ignore-case .png | wc and a locate /usr/share/unity/themes | grep --ignore-case .png | wc what's the output?[/COLOR][COLOR=#444444] 
[/COLOR]
Any other suggestion?[/FONT][/COLOR]

---

### Post by Frogs Hair on 2014-11-29
You can try the following and log out and in. I've never tried a command of that kind  before and I guess you now know what can happen when using  recursive remove commands . You will find out if the directory is still there when trying the install command.
  ```
sudo apt-get install ubuntu-mono
``` ```
sudo apt-get install ubuntu-mobile-icons
```

---

### Post by toma3 on 2014-11-29
I'll try later at the day, right now it's 04:19 AM here and I have to got to sleep. ;) :)

---

### Post by buzzingrobot on 2014-11-30
What [COLOR=#333333][FONT=UbuntuRegular]"**sudo rm -rf name_of_icons/themes"  **actually did depends on the directory you were in when you executed it.  It's confusing because I don't believe there's any location in the filesystem organized in a "name_of_icons/themes" hierarchy. Icons are in "/usr/share/themes/<name of icon theme>" or in '~/.icons<name of icon theme>' or '~/.local/share/icons<name of icon theme>'.[/FONT][/COLOR]

"sudo rm -rf" would have deleted everything at and after that point in the directory tree that matched whatever the shell resolved "name_of_icons/themes" to be.

Icons are displayed in the Launcher and elsewhere because applications install '.desktop' files in /usr/share/applications that, in effect, point to the correct icon to use for an app.  If that icon has been deleted, you'll get a fallback image.  So, the best bet to get those icons back is to reinstall the appropriate packages.

---

### Post by toma3 on 2014-11-30
Yes, files were deleted from  '~/.local/share/icons' and  '~/.local/share/themes'. I just left those files that are default after the fresh Ubuntu installation. I'll see what I can a few hours later.
On the worst scenario, I'll make a fresh installation of Ubuntu. It won't effect any harm because all important stuff is on the seperated Windows partition and external disk.

---

### Post by toma3 on 2014-11-30
> **Frogs Hair said:**
> You can try the following and log out and in. I've never tried a command of that kind  before and I guess you now know what can happen when using  recursive remove commands . You will find out if the directory is still there when trying the install command.
  ```
sudo apt-get install ubuntu-mono
``` ```
sudo apt-get install ubuntu-mobile-icons
```
Didn't helped; for 'ubuntu-mono' it was said they're already installed.
After that I tried with ```
sudo apt-get upgrade
``` and ```
sudo apt-get dist-upgrade
``` and even received and installed some files, but didn't helped neither.
It will probably be the best to reinstall Ubuntu. ;):KS

If it helps, look on [http://askubuntu.com/questions/554696/how-to-completely-restore-unity-launcher-all-icons-are-missing-ubuntu-14-10](http://askubuntu.com/questions/554696/how-to-completely-restore-unity-launcher-all-icons-are-missing-ubuntu-14-10).
If needed, I can make a photo of my desktop.

---

### Post by krizna on 2014-12-01
Try with unity-tweak-tool 
```

sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity 
```

---

### Post by toma3 on 2014-12-01
Ok, I will. However, now I'm logged as a guest. Theme and icons are ok in this session.

/////


[http://shrani.si/f/p/b5/2mhR5VQ3/20141201141826richtonehd.jpg](http://shrani.si/f/p/b5/2mhR5VQ3/20141201141826richtonehd.jpg)
Even if I type 'Y' (for Yes), nothing happens.

---

### Post by Frogs Hair on 2014-12-01
Without knowing what was removed which isn't clear from the first post it's difficult to make suggestions . Apparently you didn't remove the icons from usr/share/icons and that is why you received the already installed message . You also wrote > ~/.local/share/icons' and  '~/.local/share/themes. I find no icon folder but do find an empty theme folder in ~.local/share. I've never installed themes or icons in that location. Are you testing unity8/mir ?

---

### Post by toma3 on 2014-12-01
Nope, I didn't test Unity 8. But as all the icons and background are available in guest mode, apparently not all was deleted.

---

### Post by buzzingrobot on 2014-12-01
> **toma3 said:**
> Ok, I will. However, now I'm logged as a guest. Theme and icons are ok in this session.

[http://shrani.si/f/p/b5/2mhR5VQ3/20141201141826richtonehd.jpg](http://shrani.si/f/p/b5/2mhR5VQ3/20141201141826richtonehd.jpg)
Even if I type 'Y' (for Yes), nothing happens.

The mention of Mir in that screen capture indicates you aren't running stock Unity.

Is there a '.local' directory in your home directory?

[Edit:  It's not possible to tell what was deleted; the "rm ..." command in your first post is imprecise.]

---

### Post by toma3 on 2014-12-01
> **buzzingrobot said:**
> 
Is there a '.local' directory in your home directory?

[http://shrani.si/f/2q/MX/ViQY2Gu/2014-12-02-020617.jpg](http://shrani.si/f/2q/MX/ViQY2Gu/2014-12-02-020617.jpg)

Here you go.

However, now I did create a new user (via terminal)  and logged in with it. Everything is ok - background, windows, cursor  and icons are in the shape as needed. ----- So obviously something is  wrong just with my primary user account.

---

### Post by Yougo on 2014-12-02
> **toma3 said:**
> Didn't helped; for 'ubuntu-mono' it was said they're already installed.


You can retry the commands with
```

sudo apt-get install --reinstall <package>

```

since you have only damaged files for your user only (guest is OK, and other/new users should be ok as well), 
would it be possible to copy the deleted files and folders over from those users with an USB drive or some other shared location, and paste them where they should be in your session?

---

### Post by buzzingrobot on 2014-12-02
> **toma3 said:**
> [http://shrani.si/f/2q/MX/ViQY2Gu/2014-12-02-020617.jpg](http://shrani.si/f/2q/MX/ViQY2Gu/2014-12-02-020617.jpg)

Here you go.

However, now I did create a new user (via terminal)  and logged in with it. Everything is ok - background, windows, cursor  and icons are in the shape as needed. ----- So obviously something is  wrong just with my primary user account.

Can't tell. If 'tomaz' is your user name, then '/home/tomaz' is your home directory.  You should have a .local directory there.  

A user's .local directory contains configuration files, etc., that affect that particular user.

Creating a new user creates a folder in /home with that username, creates a .local directory within it, and populates it with default files.

Because the file sequence you specified in your first post does not exist, we can only guess what was actually deleted.  Deletion of some of all of the files/folders in .local could have the impact you noticed. If, by chance, you have backups, restore it.

Or, you could continue as the new user you've created.

---

