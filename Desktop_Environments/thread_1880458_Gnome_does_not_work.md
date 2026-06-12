---
title: "Gnome does not work?"
date: 2011-11-13
forum: Desktop Environments
---

### Post by Cha0sBG on 2011-11-13
I installed gnome with :
```
 sudo apt-get install gnome-shell 
```then loged out , restarted ... what ever and chose GNOME and still the boring new unity interface ... wth ?

using ubuntu 11.10

---

### Post by critin on 2011-11-13
> **Cha0sBG said:**
> I installed gnome with :
```
 sudo apt-get install gnome-shell 
```then loged out , restarted ... what ever and chose GNOME and still the boring new unity interface ... wth ?

using ubuntu 11.10


Did you actually leave out some of the code, or does your example have a typo?  Or am I thinking of something else?  This is what I find.


> sudo apt-get install gnome-session-fallbackAlso, look at this link, there's some tips there.

[http://www.technohunk.com/2011/10/back-to-genome-classic-from-ubuntu-11-10-in-2-step/](http://www.technohunk.com/2011/10/back-to-genome-classic-from-ubuntu-11-10-in-2-step/)

---

### Post by Azyx on 2011-11-13
> **critin said:**
> Did you actually leave out some of the code, or does your example have a typo?  Or am I thinking of something else?  This is what I find.


Also, look at this link, there's some tips there.

[http://www.technohunk.com/2011/10/back-to-genome-classic-from-ubuntu-11-10-in-2-step/](http://www.technohunk.com/2011/10/back-to-genome-classic-from-ubuntu-11-10-in-2-step/)

fallback is not gnome-shell, it should look like gnome 2.

---

### Post by Azyx on 2011-11-13
> **Cha0sBG said:**
> I installed gnome with :
```
 sudo apt-get install gnome-shell 
```then loged out , restarted ... what ever and chose GNOME and still the boring new unity interface ... wth ?

using ubuntu 11.10

You should log out and then click on the wheel in the upper-right-corner in the login-window, and choose session.

---

### Post by critin on 2011-11-13
> **Azyx said:**
> fallback is not gnome-shell, it should look like gnome 2.


Ah, thank you.  It all gets confusing to me, that's why I leave defaults alone and use 11.04.    :(  gnome shell, gnome classic, etc.

---

### Post by Azyx on 2011-11-13
> **critin said:**
> Ah, thank you.  It all gets confusing to me, that's why I leave defaults alone and use 11.04.    :(  gnome shell, gnome classic, etc.

Gnome-shell shall look like unity. Gnome-shell is the main 'desktop' for gnome, but the have the fallback thats look little like gnome 2, with gnome-panels.

---

### Post by Cha0sBG on 2011-11-13
maybe i mis-typed the command here, i'm 100% sure it's correct. Yet it does not work.

---

### Post by Azyx on 2011-11-13
> **Cha0sBG said:**
> maybe i mis-typed the command here, i'm 100% sure it's correct. Yet it does not work.

But what happen when you log-out and login again? Do you try to change session, befor you type you username and login again?

/Cheers

---

### Post by Cha0sBG on 2011-11-14
Yes i change the session to Gnome, Gnome Classic yet nothing happens. Same new unity interface... Btw there is 1 more thing i wanna ask: on what GUI does the shell themes work ? Gnome ? Unity ?

---

### Post by Frogs Hair on 2011-11-14
I have the shell and Unity installed , both of which run on top of Gnome 3 . I don't know why the shell won't start if installed and selected from the session list at login . I would suggest a full restart rather than just logging out if have not already done so.

If you installed the shell via the terminal the you would have had to answer a yes / no question to continue the installation after the package lists were read . 

Up to date GTK 3 themes with shell themes included will work with Unity or the Gnome Shell. The shell theme is simply ignored while using Unity .

---

### Post by Cha0sBG on 2011-11-14
Well, i reinstalled ubuntu ( clean one ) just did my updates and 1 driver for nVidia. If anyone wants to lend me a hand via teamviewer or something gimmie a msg here :} I really want to see what i did wrong. And yet gnome was installed via terminal

---

### Post by Azyx on 2011-11-14
> **Cha0sBG said:**
> maybe i mis-typed the command here, i'm 100% sure it's correct. Yet it does not work.

What command did you maybe mis-typed?

Have you only installed gnome-shell? I have on my 11.10 machine only installed gnome-session-fallback but during that gnome-shell did not being installed. I install gnome-shell now and test...

---

### Post by Cha0sBG on 2011-11-14
Well as i mentioned i was digging around for quite some time and i am sure i installed everything , i went trough a lot of tutorials etc. But if someone would supply the correct steps for a newly installed ubuntu i would be grateful

---

### Post by Frogs Hair on 2011-11-14
Here is a things to do after installation list , which includes Gnome Shell information . [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Cha0sBG on 2011-11-14
Well i've gone trough that tutorial before, will go again tough

EDIT: ok now the classic gnome interface works. But anyone know why i can't chose the shell themes ? I followed the instructions provided by Frogs Hair.

---

### Post by Frogs Hair on 2011-11-14
Shell themes are only applicable while logged into the shell when Gnome is selected at login . The Advanced Settings / Gnome Tweak tool is required to change GTK 3 themes in Classic Gnome , Unity or the Gnome Shell . It is described in Webupd8 link in my other post. 

If you want to install GTK 3_themes or icons from gnome look.org see below.

(Downloaded Themes)

Install the Gnome Tweak Tool / advanced settings for making theme selections  

(Single User) Create a .themes and .icons folder in home / hidden folders . (All Users) Use gksudo nautilus > File System / usr / share / themes or icons .

Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required

---

### Post by Cha0sBG on 2011-11-14
Thanks :), i'm loving the Gnome look. Now i know which look will be the one of choice . And now shell themes etc work aswell.

---

### Post by Frogs Hair on 2011-11-14
Enjoy ,  and mark the thread as solved using the thread tools  if you're good to go . :)

---

