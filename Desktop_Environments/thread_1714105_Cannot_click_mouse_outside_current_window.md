---
title: "Cannot click mouse outside current window"
date: 2011-03-24
forum: Desktop Environments
---

### Post by Inphernal on 2011-03-24
Hi all,
I've just recently begun to have a problem with my mouse. I can use it normally in one window, but it will not click outside of this window. I cannot use the title bar buttons either. It seems like right clicking "frees" the mouse, but then it just gets stuck in the next window I open.

What could this be? It is very annoying.

Ubunutu 10.10 Maverick
Toshiba Satellite C655-S5049

---

### Post by cipherboy_loc on 2011-03-24
Does Alt+Tabbing work? Are you using stock Maverick (with GNOME), or do you run a different desktop environment?


Cipherboy

---

### Post by Krytarik on 2011-03-24
It seems to be Compiz (desktop effects), are you using it?

Try upgrading your video driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos, maybe it helps:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

---

### Post by Inphernal on 2011-03-25
I am using stock Maverick, with GNOME.
I was using Compiz and this suddenly happened. I tried reinstalling it and that did nothing.
I tried "metacity --replace" and that works temporarily but freezes the terminal window in which I perform the command. If I try to close this terminal window it says it must kill the process.
I now have no title bar or window border at all, so I can't move windows even. However, I can now at least use the task bar, but only when running a terminal with "metacity --replace", otherwise the current window's menu bar lays over it, and I cannot get to it without closing the current window.

I upgraded my drivers per your advice, reinstalled Compiz, and restarted but that did not help.

---

### Post by Krytarik on 2011-03-25
Please try the following, to reset all Compiz settings:
- logout
- press Ctrl+Alt+F1 to switch to a console
- login there
- rename both directories, "~/.compiz" and "~/.gconf/apps/compiz"
- switch back to GDM with Ctrl+Alt+F7/F8
- login again

If that doesn't help, check "~/.xsession-errors" for error messages.

Also, if you need to replace Compiz with Metacity, you can either set "Appearance -> Visual Effects" to "None" or run "metacity --replace" via the Alt+F2 dialog.

---

### Post by thewildbill on 2011-03-25
I have also been experiencing this problem intermittently, but also something else that sort of complicates the issue. If an app. presents a window that requires a response, sometimes it is above the other windows with focus as it should be, but other times it's behind other windows and still demanding a response before I can do anything else.  Combined with the original issue here it's not always obvious what's going on, and it becomes more of a problem. I am doing what's recommended here re the window manager. Any other settings I could check? Thanks.

---

### Post by Krytarik on 2011-03-25
@thewildbill: Like you said, your matter is indeed different. But if you like to set that windows with the "demandsattention" state are always above other windows, you can set that in Compiz' "Window Rules" plugin. Enter in the field "Above":
```
state=demandsattention
```
I have it that way, it's much more usable for me than the default setup.

---

### Post by Inphernal on 2011-03-25
> **Krytarik said:**
> 
- rename both directories, "~/.compiz" and "~/.gconf/apps/compiz"

If that doesn't help, check "~/.xsession-errors" for error messages.


How do I do that? Sorry, iIdon't know the commands too well. Are those the directories, i don't see that on my drive.
And the alt-f2 console isn't coming up.

---

### Post by Krytarik on 2011-03-25
> **Inphernal said:**
> How do I do that? Sorry, iIdon't know the commands too well. Are those the directories, i don't see that on my drive.
And the alt-f2 console isn't coming up.
I assumed a certain level of knowledge, since you didn't post in the ABF.

- Alt+F2 is meant to be used when you are logged in

- the mentioned directories are hidden, the preceding dot indicates that

- you should familiarize yourself with the command line:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

In the meanwhile, just switch "Appearance -> Visual Effects" to "None", like I mentioned.

---

### Post by cipherboy_loc on 2011-03-25
If you are using compiz, make sure you have GNOME Compatibility enabled for the Alt+F2 to work.



Cipherboy

---

### Post by Inphernal on 2011-03-26
Ok, renaming those directories didn't seem to help, but I deleted them and anything related to Compiz altogether, and the reinstalled and the problem is gone.

Thank you for your help!

---

### Post by Krytarik on 2011-03-26
> **Inphernal said:**
> Ok, renaming those directories didn't seem to help, but I deleted them and anything related to Compiz altogether, and the reinstalled and the problem is gone.
Ah, re-installed the compiz packages. We should try that more often! ;)

Great that it worked!

---

