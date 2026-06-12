---
title: "Yakuake not saving bash history"
date: 2011-08-20
forum: Desktop Environments
---

### Post by james_xxx on 2011-08-20
Since upgrading to 11.04 several months ago, Yakuake has seemingly ceased saving to .bash_history. (Konsole, however, saves to .bash_history as normal.)

Has anyone else noticed this?

Would anyone know whether or not this thread is relevant?:

[http://ubuntuforums.org/showthread.php?t=418552](http://ubuntuforums.org/showthread.php?t=418552)

---

### Post by undecidable on 2011-12-03
Yes, it has been an irritating problem for me also,
and I only just realized it was only a Yakuake phenomenon, 
and that Konsole worked correctly.

In any case, the suggestion from that link, ie to add:
```

shopt -s histappend
PROMPT_COMMAND='history -a'

```
to the end of the ~/.bashrc file works.

---

### Post by undecidable on 2011-12-03
An alternative to using 
   ```
 PROMPT_COMMAND='history -a'
```

is instead to put in the .bash-logout file:
    ```
history -a
```

This has the advantage of only appending the history at the end of the session
rather than appending a line to the history file each time there you enter a new command.  This might be important if you have several active yakuake tabs, and you are doing different things on each of them.  

To get the history from a Yakuake tab to the history file, just do 
   ```
 exit
```
and that session will exit, the history will be appended, and an new tab will be opened.

Note that you still need
    ```
shopt -s histappend
```
but that is already in the .bashrc file anyway.

---

### Post by kio_http on 2011-12-04
yakuake should follow Konsole's exact settings. Does history work in Konsole. For me history works in both of them fine. I'm using Kubuntu 11.10 with KDE 4.7.3.

---

### Post by undecidable on 2011-12-04
Yes, agree it should, but doesn't.
Using Kubuntu 11.04.  Was ok in 8.04.  not sure in 10.10.

a.  Yes, history does work in Konsole, but not in Yakuake.

b.  Another parameter that works in Konsole is "Initial Directory",
     which Yakuake ignores.
    My workaround is to put in .bashrc:
```
 cd <my start dir>
```
which works for both.

---

### Post by kio_http on 2011-12-05
Try 
```
sudo apt-get update
sudo apt-get purge yakuake
sudo apt-get install yakuake
```

---

### Post by undecidable on 2011-12-05
I think you are assuming my Yakuake is broken.
But this happens on 3 machines, all clean installs. 

So this is unlikely to be the reason.

---

### Post by kio_http on 2011-12-05
> **undecidable said:**
> I think you are assuming my Yakuake is broken.
But this happens on 3 machines, all clean installs. 

So this is unlikely to be the reason.

I noticed that you say 11.04? On 11.10 everything works fine for me with KDE 4.7.3. I never used yakuake on older KDE releases or Kubuntu releases so maybe its fixed now?

---

### Post by undecidable on 2011-12-05
Yes, could be.
The history bug only appeared in 11.04, was not there in 10.10
(just double checked it).

However I will wait for at least 12.04 before I update.
Too time consuming (and too much trouble finding workarounds for new bugs)
to update too often.

---

### Post by kio_http on 2011-12-05
> **undecidable said:**
> Yes, could be.
The history bug only appeared in 11.04, was not there in 10.10
(just double checked it).

However I will wait for at least 12.04 before I update.
Too time consuming (and too much trouble finding workarounds for new bugs)
to update too often.

Unlike the Ubuntu side of things, on Kubuntu each version (since kde4 was adopted) is a major improvement over the last. Most Kubuntu users upgrade to the latest release. Personally I've never had a problem upgrading a Kubuntu system. I highly recommend that you do upgrade as KDE 4.7 includes a lot of fixes that aren't in 11.04. There are a lot of performance benefits too.

If you chose to upgrade however be aware of [this one issue regarding kmail]("https://wiki.kubuntu.org/OneiricOcelot/Final/Kubuntu/Kmail2").

---

