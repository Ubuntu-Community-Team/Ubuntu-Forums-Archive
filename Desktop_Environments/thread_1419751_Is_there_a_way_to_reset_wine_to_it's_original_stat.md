---
title: "Is there a way to reset wine to it's original state?"
date: 2010-03-02
forum: Desktop Environments
---

### Post by ki4jgt on 2010-03-02
Got a Windows virus

---

### Post by Cabs21 on 2010-03-02
uninstall it
reintsall it
stop installing unknown .exe files from porn sites.... I mean be careful what you install into wine

---

### Post by shihkster1015 on 2010-03-02
After you uninstall, go to home folder and show hidden files. Make sure the file ".wine" is not there anymore. And make sure that every instance of wine has been uninstalled. The best way would be to go to terminal and type
```
 sudo apt-get autoremove *wine*
```Just make sure that the things listed after you press enter is not a vital system file or anything important you need.

---

### Post by Cabs21 on 2010-03-02
> **shihkster1015 said:**
> After you uninstall, go to home folder and show hidden files. Make sure the file ".wine" is not there anymore. And make sure that every instance of wine has been uninstalled. The best way would be to go to terminal and type
```
 sudo apt-get automreove *wine*
```Just make sure that the things listed after you press enter is not a vital system file or anything important you need.

as a note automreove command is spelled autoremove

---

### Post by shihkster1015 on 2010-03-02
sorry 'bout that
typed a bit too fast

---

### Post by 3Miro on 2010-03-02
Don't do that. First try moving the .wine directory

```
mv .wine .wine_mybackup
```

Then run the wine configuration utility

```
winecfg
```

This will create a new and clean .wine folder. You can start all over again without losing anything in the backed up .wine_mybackup folder.

You can actually still run programs from the old folder by using the WINEPREFIX variable:

```

WINEPREFIX=$HOME/.wine_mybackup wine "something.exe"

```

This will run the something.exe file, but use the old settings in .wine_mybackup.

---

### Post by shihkster1015 on 2010-03-02
i still think it will be better to wipe out .wine cuz if you move it, the virus will probably be moved along with it. And if you try to run that file, you never know if the virus will strike again

---

### Post by d3v1150m471c on 2010-03-02
Yep, delete .wine then
```

sudo apt-get remove wine
sudo apt-get autoremove
sudo apt-get install wine

```

---

### Post by shihkster1015 on 2010-03-02
> **d3v1150m471c said:**
> Yep, delete .wine then
```

sudo apt-get remove wine
sudo apt-get autoremove
sudo apt-get install wine

```

just go ahead an autoremove. It's much cleaner

---

### Post by 3Miro on 2010-03-02
> **shihkster1015 said:**
> i still think it will be better to wipe out .wine cuz if you move it, the virus will probably be moved along with it. And if you try to run that file, you never know if the virus will strike again

In any case remove will not remove the .wine folder. If you want to zap it completely use either purge or just
```
rm -fr .wine
```

@ki4jgt: btw, how did you find out about the virus, AV software usually doesn't work under wine and most windows viruses cannot harm wine dues to compatibility issues (wine is an API layer on top of the Linux kernel and not an emulation of the windows kernel, where most problems are). Also, you might want to notify people in winehq about this.

---

### Post by AndersAA on 2010-03-02
ignore everyone telling you to uninstall the wine package, it will do nothing.

Wine exists on a system level, your virus is running on a user level. And uninstalling wine won't remove the .wine directory in your home directory.

---

### Post by Paddy Landau on 2010-03-02
After you've reinstalled Wine (or, rather, deleted your .wine directory), before you install any Windows programs, install [PlayOnLinux]("http://www.playonlinux.com/"). This lets you install every Windows program in a separate "prefix".

Then, if one prefix gets a virus, just tell PlayOnLinux to delete that one and reinstall the program that was there. All your other Windows programs -- and the main Wine program -- will remain unaffected.

---

### Post by ki4jgt on 2010-03-05
First, I deleted the .wine folder, yet all my stuff is still the same after I reinstall. Second, My half witt, full brained cousin wrote the virus specifically for WINE, and we were playing around. It doesn't spread, like normal viruses, but it does cause one big headache

---

### Post by ki4jgt on 2010-03-05
And I can't get rid of it

---

### Post by Paddy Landau on 2010-03-05
> **ki4jgt said:**
> My half witt, full brained cousin wrote the virus specifically for WINE, and we were playing around. It doesn't spread, like normal viruses, but it does cause one big headache
That's where PlayOnLinux should help. Unless your cousin got access to root (the Administrator), he can't have damaged Wine (and unfortunately it sounds as though he might have done).

But, generally, a Windows virus can damage only the Windows folder; in PlayOnLinux, each application has its own Windows folder, making it much safer (and hugely easier to uninstall).

> **ki4jgt said:**
> And I can't get rid of it
Did you delete the .wine folder, *and* uninstall with autoremove, *and* reinstall as per the previous instructions?

Do this:

[LIST=1]
[*]Uninstall with [FONT=Courier New]sudo apt-get purge wine[/FONT]
[*]Remove old packages (in case your cousin got these files) with [FONT=Courier New]sudo apt-get autoremove[/FONT]
[*]Clean up further with [FONT=Courier New]sudo apt-get clean[/FONT]
[*]Now delete your Wine folder from your home directory with [FONT=Courier New]rm -rf ~/.wine [/FONT](please type that carefully! or do it from Nautilus)[FONT=Courier New]
[/FONT]
[*]Reinstall Wine with [FONT=Courier New]sudo apt-get install wine[/FONT]
[*]Finally, install [PlayOnLinux]("http://www.playonlinux.com/") (follow the installation instructions on the website). Use PlayOnLinux to install and uninstall Windows programs.
[/LIST]
If that still doesn't work, then find out what else he might have changed. Did he change your file [FONT=Courier New].bash_profile[/FONT] in your home directory? Did he change your menu's Wine entries?

---

### Post by nikhilbhardwaj on 2010-05-23
> **Cabs21 said:**
> 
stop installing unknown .exe files from porn sites.... I mean be careful what you install into wine

damn
i get all my viruses like this

---

### Post by 3Miro on 2010-05-23
> **nikhilbhardwaj said:**
> damn
i get all my viruses like this

I always enjoy a good piece of Necromancy!

---

### Post by texaswriter on 2010-05-23
> **shihkster1015 said:**
> i still think it will be better to wipe out .wine cuz if you move it, the virus will probably be moved along with it. And if you try to run that file, you never know if the virus will strike again

The Windows virus can't affect Linux, so moving the folder would suffice. Viruses aren't magical, they actually have to be memory resident to do anything.

Shouldn't need to un/re install Wine either. 

If you really feel like it, you may certain do all the above things.

---

