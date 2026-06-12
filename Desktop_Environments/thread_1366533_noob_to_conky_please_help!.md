---
title: "noob to conky please help!"
date: 2009-12-28
forum: Desktop Environments
---

### Post by phillychease on 2009-12-28
i just installed conky and i found a conky file i really like. where do i put it and what do i name it as?

---

### Post by stinkeye on 2009-12-28
Name it whatever you like
eg conkymain
Best to create a folder in you home directory called conky and place all your conky stuff there.
To load type in terminal
```
conky -c ~/conky/[COLOR="Purple"]conkymain[/COLOR]
```
[COLOR="#800080"]or whatever you named it[/COLOR].

[_[COLOR="DarkRed"]**HOW TO: A Beginners Guide to Setting up Conky**[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")

---

### Post by mike998 on 2009-12-28
The above is good if you are running either multiple conky instances or want to quickly swap between them.

If you rename the file .conkyrc and put it in your home directory, just launching conky will pick up this config file.

I can also advise taking a look at the documentation, as config files do need tweaking from time to time.  I did the same to my conky config, and I got it JUST how I want it.  Sorta.

---

### Post by mick222 on 2010-01-14
newbie question how do i restart conky.I just installed and ran conky created  a new .conky rc in home folder and added script but can't get it to restart so that i can try the script.Ok found that
>  pkill conky
Now the script I put in my home folder isn't working it still loads the script from /etc/conky/conky/.conf
Got it had saved in home but not put it in a folder called conky.I'm probably a bit of a pain but trying to learn and to lazy to look through the long thread.

---

