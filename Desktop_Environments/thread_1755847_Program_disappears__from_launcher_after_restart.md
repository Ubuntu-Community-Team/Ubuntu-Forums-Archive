---
title: "Program disappears  from launcher after restart"
date: 2011-05-11
forum: Desktop Environments
---

### Post by groundnut on 2011-05-11
I have installed Blender from Blender.org.
I have installed it my home directory.
After launching Blender the icon appears in the unity launcher.
Then I fixed the icon in the launcher via the context menu.
After restart the Blender icon does not reappear?

How can I realize that the Blender icon shows up very time after starting Ubuntu?

---

### Post by mc4man on 2011-05-11
You can only add a .desktop to the launcher, not a binary.

One of several ways - (remove current launcher icon if there
To make path a bit shorter renamed the extracted folder to just blender, placed in home folder,

There are many choices for icon, I picked one
In terminal - 

```
gedit ~/.local/share/applications/blender.desktop
```

used this for a .desktop, note that paths (red) need to match your's, not mine
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=[COLOR="Red"]/home/doug/blender/[/COLOR]blender
Name=Blender
Icon=[COLOR="Red"]/home/doug/blender/icons/48x48/apps/blender.png[/COLOR]
```


Then open your home folder (view > show hidden files) and browse to ./local/share/applications and drag the blender.desktop onto the launcher 
Try a log out/in, it should be good

(if wanting to be avail. to other users then the blender folder should be placed in /usr/local/ and the .desktop created in /usr/local/share/applications/, ect. (one may need to create that applications folder first

---

### Post by groundnut on 2011-05-13
Thank you very much mc4man.

This is to much hassle for me.
I will open the binaries manually instead.

---

### Post by mgmiller on 2011-05-13
Try this...
right click a blank spot on your desktop and select "Create Launcher".
Fill in the fields as appropriate and click the browse button to get to the executable you want for blender.
It will probably give you the correct icon as soon as you select blender, if not, click the icon and browse to an appropriate icon.
Click OK to create the launcher icon on your desktop.
Move this launcher icon to your blender folder.
Finally, drag the icon from your blender folder onto the launcher panel on the left side of the screen and select Keep in Launcher as you did before.

---

### Post by groundnut on 2011-05-16
Thank you mgmiller,

I managed to add a Blender icon to the launcher.

However when I click on the launcher icon a second icon appears in the launcher. This is the "real" icon that launches when you activate the program manually.
I could not find the "real" icon  in the Blender folder. But there are may others.

---

### Post by Z80A on 2011-05-16
Can't help wondering; who concluded that the above procedures for creating a launcher icon for an application was intuitively good and suited for common users? Wouldn't it just seem right if anything (also documents and URL's) could be dragged and dropped to the launcher?

It's a hard job convincing real users that this is a user friendly system in this way. You know what the competition in the market looks like: iOS, OSX, Android... well and Windows 7. These are GUI references potential users will compare Ubuntu and Unity with.

Lastly, don't get me wrong, I [COLOR=Gray]**really**[/COLOR] like Ubuntu - also in this latest incarnation.

---

### Post by mc4man on 2011-05-16
> **Z80A said:**
> Can't help wondering; who concluded that the above procedures for creating a launcher icon for an application was intuitively good and suited for common users? Wouldn't it just seem right if anything (also documents and URL's) could be dragged and dropped to the launcher?

It's a hard job convincing real users that this is a user friendly system in this way. You know what the competition in the market looks like: iOS, OSX, Android... well and Windows 7. These are GUI references potential users will compare Ubuntu and Unity with.

Lastly, don't get me wrong, I [COLOR=Gray]**really**[/COLOR] like Ubuntu - also in this latest incarnation.
This method is only needed if wanting to add an app that doesn't create a .desktop when installed
(and be the start of adding quicklist entries or creating a .desktop just for the quicklist entries, ie. a menu thru an icon

Generally one can just drag an app from the dash or there is an option to add to launcher in Software Center when installing.

---

### Post by wildmanne39 on 2011-05-16
> **groundnut said:**
> I have installed Blender from Blender.org.
I have installed it my home directory.
After launching Blender the icon appears in the unity launcher.
Then I fixed the icon in the launcher via the context menu.
After restart the Blender icon does not reappear?

How can I realize that the Blender icon shows up very time after starting Ubuntu?
Hi, all you have to do is open the program that you want in the launcher, then go to the icon on the launcher and right click on it and check keep in launcher.):P

---

### Post by Z80A on 2011-05-17
Yes, I do get the concept of the basic functionality of the launcher as we have it today. In a future iteration of the launcher, I hope there will be a better support for drag and drop of various items. :-k

Normal end-users are quite familiar with dragging URL's from Firefox's address bar to the desktop or creating desktop icons/shortcuts to documents. A similar support in the Unity launcher (without text file editing and other workarounds) would be valued highly by many end-users; my son for one would like to have a launcher icons for going directly to e.g. YouTube (he used to be able to do this easily in Windows XP's Quick Launch next to the Start button). :roll:

---

### Post by Robbkore on 2011-06-15
> **wildmanne39 said:**
> Hi, all you have to do is open the program that you want in the launcher, then go to the icon on the launcher and right click on it and check keep in launcher.):P

I am running Natty and the issue is as follows (might be the same as the poster):

After opening a program and right-clicking on it's icon in the launcher, it will persist. Once a reboot is necessary, the icons are no longer in the launcher after the OS has reloaded itself. 

I'm not entirely new to Ubuntu but I just started using it again after a hiatus from Linux (was running Ubuntu then Kubuntu on my older laptop until I got rid of it). I have a very limited knowledge of Ubuntu but I am trying to learn.

I've not tried the solutions mentioned above but the original poster said after he did that clicking the icon in the launcher opened another icon in the dock. I'd prefer them to work the way the ones already there work.

---

### Post by mantorpcity on 2011-07-20
> **wildmanne39 said:**
> Hi, all you have to do is open the program that you want in the launcher, then go to the icon on the launcher and right click on it and check keep in launcher.):P I'm using the Unity 2d launcher, and I have done this with a few programs. It's inconsistent in that some of them are there after reboots and some are not. Also, when I launch the programs that had been in there before the reboot it will take that icon from before even if my new shortcut has a different icon.

---

