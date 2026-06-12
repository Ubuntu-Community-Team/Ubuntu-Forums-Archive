---
title: "Help with &quot;nautilus&quot;"
date: 2005-10-21
forum: Desktop Environments
---

### Post by joplass on 2005-10-21
Everytime I type "sudo nautilus", my desktop background changes from the wallpaper I put there to Ubuntu brown wallpaper and I lose other functionallity like the rigth-click option.  If I can put back my wallpaper the rigth-click option I could not get back.
Anyone know what causes this?
Thanks,

---

### Post by invalid on 2005-10-21
The problem is that you are starting it as the sudo root user.
Your personal settings are not the same as the sudo root user - and since nautilus is more than just the file browser, it covers up other things with the new users settings.

If you are looking to open a root file browser (my guess as to why you need to type sudo nautilus), you should check the UbuntuGuide. It explains how to do this.

Cheers,
Cb

---

### Post by joplass on 2005-10-21
Well maybe I did not explain myself very well.  I just don't want to browse but I also want to modify them and only root does that.  Unfortunatly the guide is more for warty than breezy and a few things are different.

---

### Post by invalid on 2005-10-21
[QUOTE=joplass]Well maybe I did not explain myself very well.  I just don't want to browse but I also want to modify them and only root does that.  Unfortunatly the guide is more for warty than breezy and a few things are different.[/QUOTE]

I'll even save you pain of searching, and tell you that it does work. If you don't believe me, try it yourself.

[http://ubuntuguide.org/#browsefilesfoldersasrootnautilus](http://ubuntuguide.org/#browsefilesfoldersasrootnautilus)
[http://ubuntuguide.org/#openfilesasrootviarightclick](http://ubuntuguide.org/#openfilesasrootviarightclick)

Cb

---

### Post by fimbulvetr on 2005-10-21
invalid is right, it's loading roots preferences. If you run nautilus with --help, you'll see it's got quite a few options that might help you.

Check these out:

```

  --no-desktop                           Do not manage the desktop (ignore the
                                         preference set in the preferences
                                         dialog).
  --browser                              open a browser window.

```

Might try a combination of those, and when you find one that works, make a new shortcut for it. When the shortcut is executed, it will ask you in the gui for a password.

---

### Post by joplass on 2005-10-21
[QUOTE=invalid]I'll even save you pain of searchingCb[/QUOTE] Huh!!!!

---

### Post by invalid on 2005-10-21
[QUOTE=invalid]I'll even save you pain of searching, and tell you that it does work. If you don't believe me, try it yourself.

[http://ubuntuguide.org/#browsefilesfoldersasrootnautilus](http://ubuntuguide.org/#browsefilesfoldersasrootnautilus)
[http://ubuntuguide.org/#openfilesasrootviarightclick](http://ubuntuguide.org/#openfilesasrootviarightclick)

Cb[/QUOTE]

I don't know what you are seeing, this is what I posted.

Cb

---

### Post by joplass on 2005-10-21
Thanks for your help guys but even after following the guide I am still losing my wallpaper to Ubuntu Brown which is my biggest problem.  Maybe something is plain wrong with my box.  I never had this issue with Warty tho.
Thanks anyway.

---

### Post by jasay on 2005-10-21
When you type "sudo nautilus" into a terminal it doesn't just load the file browser with root access but reloads all of nautilus (of which your background is part) with root preferences.  My guess is you haven't set the root background so it uses the default brown.  If you followed the unofficial ubuntu guide correctly there will be a launcher in your Applications>System Tools menu that says File Browser (Root).  Use this launcher to browse files as root, not the terminal.  If you REALLY REALLY want to use the terminal to launch with a root file browser this is the command used by that launcher:
```
gksudo "nautilus --browser %U"
```
Have fun.

---

