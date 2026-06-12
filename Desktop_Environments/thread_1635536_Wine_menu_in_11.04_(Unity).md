---
title: "Wine menu in 11.04 (Unity)"
date: 2010-12-01
forum: Desktop Environments
---

### Post by carltonh on 2010-12-01
I just upgraded one installation to 11.04, and this is my 1st experience with Unity.  In 10.10 I had a "Wine" sub-menu in the Application Menu, just like the Internet, Office, Sound & Video sub-menus.

Now in 11.04 I click on the file manager and it pulls up Nautilus with /usr/share/applications. I'm pretty sure my Wine applications aren't there since the executables are not kept in that directory in previous releases.  It may matter that I was using the ubuntu-wine PPA (Scott Ritchie's) before the upgrade.

How is (or will) Wine menus be organized in Unity 11.04?

---

### Post by garvinrick4 on 2010-12-01
It is going to be a bit 11.04 is not even in Alpha 1 yet. It is very unstable and everyday
is going to be a new set of problems. It is not meant for daily use just for testing.

---

### Post by davebb on 2011-03-20
I had a similar experience, though I just upgraded my netbook from 10.04 to 10.10 in preparation to the 11.04 release, and it has Unity as the desktop manager already.  I thought that was coming out in 11.04.  Anyways, I first noticed the All Applications only shows the first 100, which I looked up and that will get released properly with Natty according tot he bug tracker, but I don't see my WinE menu either.  Heck I can't even find WinE as an app in any of the menus.  SO Unity is production in 10.10 at least for the netbook it seems as I've gone with just stable release packages for my configuration.  
Anyone else have any ideas?  Thanks in advance.

---

### Post by roger_1960 on 2011-04-16
Hi

I am trying beta2 of 11.04 and all of the OPs comments still seem to apply.

I have installed wine from the Software centre and the only way to run MS software installed under wine is by browsing to them using the "browse C drive" application to find the .exe and double clicking it.  Is there a way of creating an icon for Wine or for the MS app under wine within the launcher?  Am I missing something?

So far, Unity seems really good!

---

### Post by marin123 on 2011-04-16
right-click -> Keep in launcher?

---

### Post by roger_1960 on 2011-04-16
Mmm........

Most app icons can be dragged to the launcher (right clicking does nothing), but there is no icon for WINE in applications and the icon for the .exe cannot be dropped in the launcher.  Wine is working (by navigating to and double clicking the .exe icon), its just an issue of getting it into a menu somewhere.

---

### Post by oren tal on 2011-04-30
well now I can find the wine application, but there is still no wine submenu.


Are they going to fix it?

---

### Post by N_L on 2011-05-07
Just spent a while trying to figure this out, any word on it?

---

### Post by N_L on 2011-05-07
Anyone knows what to do? I made launcher that leads me to wine's c but now all my folder's are grouped under that icon when I open them instead of home, plus it's still pain to find right .exe file :|

---

### Post by mc4man on 2011-05-08
> **N_L said:**
> Anyone knows what to do? I made launcher that leads me to wine's c but now all my folder's are grouped under that icon when I open them instead of home, plus it's still pain to find right .exe file :|
You might find it better to use the Home Folder and create some quicklist entries (r. click on icon) to open nautilus at the locations of your .exe's
This link gives the basic's how  to do
[http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity](http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity)

So as an example I use Imgburn in wine. If I wanted to add it's folder location to the Home Folder the quicklist entry in nautilus-home.desktop would look like this (using '.....' to account for space in path

```
[ImgBurn Shortcut Group]
Name=Imgburn
Exec=nautilus --no-desktop '.wine/drive_c/Program Files/ImgBurn'
TargetEnvironment=Unity 
```
Atm I only have 2 wine progs and being curious about have added as standalone icons to the launcher (probably won't keep, just curious..
The big thing was to have the added icon control the prog, not just open it then have a 'Wine Windows Program Loader' icon open and control the prog.

Have managed to do so though on one install had to edit mimeinfo.cache and or bamf.index, not sure which
screen shows both open and under their icon's control

To add to the launcher the prog needs a .desktop, in both cases I put the .desktop in ~/.local/share/applications, ran once by d. clicking on to ck. and then added to launcher

Ex. of the 2 .desktops

```
[Desktop Entry]
Name=ImgBurn
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\ImgBurn\\\\ImgBurn.exe 
Type=Application
StartupNotify=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/ImgBurn
Icon=/home/doug/.local/share/icons/b06c_imgburn.0.png
```

```
[Desktop Entry]
Name=vobblanker
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\VobBlanker\\\\VobBlanker.exe 
Type=Application
StartupNotify=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/VobBlanker
Icon=/usr/share/icons/Humanity/mimes/32/video-x-generic.svg
```

---

### Post by vduke on 2011-05-13
Find myself in the same boat folks. I did however goto system settings and look into the main menu option.  I see my wine folder listed and it's sub menus. Even if there was a plugin for the launcher specifically to give us our wine menu back (Or if you remember the launcher button we had the ability to add to our panels *the one with the ubuntu logo on it* that specifically gave us the main menu!) that would be great. Otherwise I am still stumped for the moment.

---

### Post by mc4man on 2011-05-13
> **vduke said:**
> Find myself in the same boat folks. I did however goto system settings and look into the main menu option.....
If you really wish to access the old gnome menu in unity _one way_ is shown here in posts 10,11
You can add it to your launcher and it'll pop up the complete gnome menu in a standalone window

[http://ubuntuforums.org/showthread.php?p=10805842#post10805842](http://ubuntuforums.org/showthread.php?p=10805842#post10805842)

---

### Post by wildmanne39 on 2011-05-14
> **vduke said:**
> Find myself in the same boat folks. I did however goto system settings and look into the main menu option.  I see my wine folder listed and it's sub menus. Even if there was a plugin for the launcher specifically to give us our wine menu back (Or if you remember the launcher button we had the ability to add to our panels *the one with the ubuntu logo on it* that specifically gave us the main menu!) that would be great. Otherwise I am still stumped for the moment.

Hi, I am running awn dock and I have an applet at the bottom of the page on my launcher that has the exact gnome menu, all you have to do is click on the icon and you can choose what ever program you want to open from the menu.If anyone wants it I will look up the instructions and give you the link to how to set it up.:D

---

### Post by surnj1 on 2011-05-14
wildmanne39, i am interested.

---

### Post by wildmanne39 on 2011-05-15
> **surnj1 said:**
> wildmanne39, i am interested.

Hi, it took me a little while to find it but here it is you will have to read the whole post most likely and I asked some questions that he replied to that you may also have to read. [http://ubuntuforums.org/showthread.php?t=1747676&highlight=awn+launcher](http://ubuntuforums.org/showthread.php?t=1747676&highlight=awn+launcher)  .I hope this helps I enjoy the awn launcher very much.):P

---

### Post by dankegel on 2011-05-15
This is being tracked at
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/753276](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/753276)

Please go mark "this bug affects me" there if this problem affects you.

---

### Post by wildmanne39 on 2011-05-16
> **vduke said:**
> Find myself in the same boat folks. I did however goto system settings and look into the main menu option.  I see my wine folder listed and it's sub menus. Even if there was a plugin for the launcher specifically to give us our wine menu back (Or if you remember the launcher button we had the ability to add to our panels *the one with the ubuntu logo on it* that specifically gave us the main menu!) that would be great. Otherwise I am still stumped for the moment.

Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

### Post by JHansonJr on 2011-08-03
This is what I did, and it seems to work. Right click on the empty desktop, and create launcher. If you don't know what to put in the blanks, you can copy&paste from whatever the same spaces contain under the application's entry in the Main Menu application. Then, drag and drop THAT icon onto the Unity sidebar. Worked for me. Unity 2d.

---

