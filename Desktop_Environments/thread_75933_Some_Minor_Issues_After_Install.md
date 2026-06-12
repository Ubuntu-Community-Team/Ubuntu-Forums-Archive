---
title: "Some Minor Issues After Install"
date: 2005-10-14
forum: Desktop Environments
---

### Post by SteveF on 2005-10-14
I just installed Kubuntu (Breezy Badger) and ran into a couple of issues:

1) Kate will not work except when using kdesu.  When I run it as a user from the menu or when clicking on a text file, it starts to run and then dies.  When I run it from a console, I get the follow error:
kate: ERROR: Communication problem with kate, it probably crashed.

2) Konqueror will not work with Netscape email.  I don't know if this is a distribution issue or just a limiation of Konqueror.  I login to the webmail and eventually it hits an error page with the message:
The service you are trying to reach is temporarily unavailable - please try your request again..

I don't get this error with Firefox.  Firefox also gets a different login screen which leads me to believe Konqueror is just not supported correctly (I have tried changing the browser identification but it doesn't work)

3) I can run the menu editor from a terminal window, but is there a way to run it from the menus.

4) Automount of USB memory cards does not work correctly.  I get an error from Konqueror about the folder not existing.  From a terminal window I see the device is mounted and I can access it.  I thought I read somewhere that this might be a bug in KDE, but wanted to check anyway.

5) I download Numlockx in order to start with my numlock set.  The instructions I saw (for Ubuntu Hoary) stated that I needed to modify /etc/X11/gdm/Init/Default, that does not exist in this distribution.  I was expecting to see a kdm folder, but I don't see it.  If I install using Adept, do I need to do anything else?

Thanks for any pointers,

Steve

---

### Post by SteveF on 2005-10-14
Sorry to reply to my own post, but I forgot one other item.

I installed Firefox.  It's default home page is:
file:///usr/share/ubuntu-artwork/home/index.html

That does not exist in this install, so I think it might be a bug in the package or the default install for Kubuntu.

---

### Post by Estariel on 2005-10-14
>  4) Automount of USB memory cards does not work correctly. I get an error from Konqueror about the folder not existing. From a terminal window I see the device is mounted and I can access it. I thought I read somewhere that this might be a bug in KDE, but wanted to check anyway.  That's because they somehow forgot (?!) to compile HAL support into media://. I hope this will get fixed soon, because I use lots of external harddrives, and this error annoys me :/ Also, does anyone know, if I can have a ivman config file in my home directory that overrides the default one (I don't want to change the default one...) I'd like to switch the default behavior of opening a konqueror window off. I just want it to get automounted, no need of stopping my workflow by opening a window...

---

### Post by Freddy on 2005-10-14
> 1) Kate will not work except when using kdesu. When I run it as a user from the menu or when clicking on a text file, it starts to run and then dies. When I run it from a console, I get the follow error: kate: ERROR: Communication problem with kate, it probably crashed. BigKate is unfortunetly buggy, this is solved for me ( Breezy Badger) but appearantly not for you :(. You could add kdesu before the run command in the menu editor, otherwise I haven't heard of any solution for this bug. You could use kwrite instead (already on your system) or install the great Kedit through apt-get.> 2) Konqueror will not work with Netscape email. I don't know if this is a distribution issue or just a limiation of Konqueror. I login to the webmail and eventually it hits an error page with the message: The service you are trying to reach is temporarily unavailable - please try your request again.. There is a solution but I'll have to get back to on this cause I don't remember how. > 3) I can run the menu editor from a terminal window, but is there a way to run it from the menus. Just rightclick on the kmenu button and choose menueditor. > 4) Automount of USB memory cards does not work correctly. I get an error from Konqueror about the folder not existing. From a terminal window I see the device is mounted and I can access it. I thought I read somewhere that this might be a bug in KDE, but wanted to check anyway. Yeah this is a known bug with the implementation of KDE 3.4.3 in Breezy Badger, hopefully a fix in on the way. > 5) I download Numlockx in order to start with my numlock set. The instructions I saw (for Ubuntu Hoary) stated that I needed to modify /etc/X11/gdm/Init/Default, that does not exist in this distribution. I was expecting to see a kdm folder, but I don't see it. If I install using Adept, do I need to do anything else? You won't have to use that in KDE, just open up your kcontrol/systemsettings and there's a tab called periphial/keyboard or something (don't use english) there you can enable numlock from start. > I installed Firefox. It's default home page is: file:///usr/share/ubuntu-artwork/home/index.html This is because firefox is looking for a pagefile installed in ubuntu, just alter your default homepage within firefox settings and that message will disapear. /// Freddan

---

### Post by manubreizh on 2005-10-14
hi,
for 4), just look at [http://ubuntuforums.org/showthread.php?t=75771]("http://ubuntuforums.org/showthread.php?t=75771")
upgrade to 3.5beta1 solved the problem for me.

---

### Post by Freddy on 2005-10-14
[QUOTE=manubreizh]hi,
for 4), just look at [http://ubuntuforums.org/showthread.php?t=75771]("http://ubuntuforums.org/showthread.php?t=75771")
upgrade to 3.5beta1 solved the problem for me.[/QUOTE]
Yeah maybe :), if you are a daredevil. I tried the beta version of KDE 3.5 a while back and it totally messed up my system with alot of graphical bugs. To those who gonna try this solution beware that this could very well destroy parts of your KDE with no real satisfactory way to downgrade back.   /// Freddan

---

### Post by SteveF on 2005-10-14
For those having trouble, Kate now works.  I restarted the computer and installed Kedit.  One of those two caused Kate to now work.  No idea which though.

---

### Post by Freddy on 2005-10-14
> For those having trouble, Kate now works. I restarted the computer and installed Kedit. One of those two caused Kate to now work. No idea which though.
Weird solution but good to know :)   /// Freddan

---

### Post by kLy on 2005-10-21
[QUOTE=Estariel]That's because they somehow forgot (?!) to compile HAL support into media://. I hope this will get fixed soon, because I use lots of external harddrives, and this error annoys me :/ Also, does anyone know, if I can have a ivman config file in my home directory that overrides the default one (I don't want to change the default one...) I'd like to switch the default behavior of opening a konqueror window off. I just want it to get automounted, no need of stopping my workflow by opening a window...[/QUOTE]

Hey. Does anyone know the bug number for this bug? I tried searching bugzilla for ages but didn't come up with anything. thx.

---

