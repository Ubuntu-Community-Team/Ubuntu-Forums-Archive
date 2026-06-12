---
title: "Xubuntu 7.10 desktop problems and more"
date: 2008-01-11
forum: Desktop Environments
---

### Post by phinn on 2008-01-11
---
#1
---
I installed Xubuntu on an old computer (Dell Dimension L433c) at my office hoping it would take the place of Win2k.

There is a Windows 2000 and DOS partion on the same drive and after the installer hung up at 15% 3 times in a row I decided to just tell it to ignore those partitions during install and it worked.  A bug?

Now when I boot the computer into XFCE on a clean install (with safe-upgrade done) there are 2 icons on the desktop: "Volume 5gb" and "Volume 10gb" (DOS and Win2k respectively) and I desperately want to rename those to DOS and Windows so other people in the office that don't know Linux can use the computer easier (because then they'll give the OS more of a chance)

How in the WORLD do I rename these automounted partitions?   I added them manually to /etc/fstab with the following:
/dev/sda4     /media/win2k    ntfs     defaults  1  0
/dev/sda3     /media/dos     vfat      defaults   1  0

And so now they are mounted to those folders however I cannot rename them to Win2k and DOS. They keep their damn automount names.  I can't edit them in XFCE because it says I don't have permission to change the icon names. I even tried starting an XFCE session as root and I couldn't figure out how to change them.

----
#2
----
As a side note, there is a bug with the i810 embedded graphics card on that Dell's motherboard where XFCE completely crashes if I load a simple terminal without going into  /etc/X11/xorg.conf  and change the bit depth to 16 (rather than the default 24).   I heard about this bug in the beta versions but it apparently was never fixed.  At least its an easy workaround.

----
#3
----
One more issue, and its that the X.org is very slow. The redraw speed is awful, especially in Firefox. Also, I couldn't possibly watch a video.  Is this a limitation of the Linux video drivers for the i810 chipset?   It has to be because Windows 2000 is MUCH faster in this respect.  Is there a different (other than the default) video driver I can use. I tried a couple things but nothing helped speed that up.

If I could resolve #1  and maybe #3 it would be huge.

Thanks in advance

---

### Post by TeaSwigger on 2008-01-11
Y'know I actually like Win 2k Pro; it's relatively stable and fast. It's MicroSoft that made me feel obliged to go elsewhere. Oh well it's come out for the better in the end.

re: #1. Understand I only used xfce for a short time, but I also wanted to opt not to show the windows partitions. Seem to recall that there was an option of which icons to show on the desktop; you could elect not to display device icons. Wish I could recall more specifically, sorry. As with the above, I'm not terribly sure about this but you could see if you can "roll your own" desktop entry mapped to /media/win2k etc, if you don't yet know how:

Go into your home folder in Thunar, then into the /Desktop folder. Desktop Icon items go there. Create a new desktop file, iirc like this: create a new file, win2k.desktop with these contents for example:

```
[Desktop Entry]
Name=Win2k
Exec=thunar /media/win2k
Type=Application
Icon=thunar
```

That should launch Thunar right into the win2k partition. Save and see, of course if it doesn't show check that icons are enabled, however one does that in xfce. Won't hurt to try that. Doesn't work just delete that file.

#2 & 3 seem related to me, and xubuntu can't run at 100% until it's sorted. It's not just about the chipset, it's also about the graphics card, so check what it is exactly. Is there a "restricted drivers" utility in Xubuntu? Can't recall. The point is, you want to see if there's a better driver you can use, and then ensure it's being used. 

I know it's frustrating to have these problems but it's none of ubuntu's doing. Getting cooperation from the graphics card makers is one of the many advantages MicroSoft has enjoyed. It's tough on people to try and get their hardware running right using anything else, unless the maker a) releases the code and someone makes a driver and shares it with others out of the goodness of their heart or b) the maker releases a linux-compatible driver, which generally also demands that you enter legal agreements with them (usually in an "accept or deny" option before installing), which in turn is why ubuntu can't preinstall it for you, and in turn that makes you have to take the initiative and some steps involved to install it. We'd have to tell the card maker we, as their customers, don't appreciate their relevant procedures.

ps - if you want faster performance, look into a lighter linux setup. One easy way is ubuntu, using lightweight apps and Fluxbox or IceWM for window manager, for instance. Xubuntu / Xfce is a wonderful, quality desktop environment but it isn't really light and certainly is not as Xubuntu has it. 

Hope all my chatter helps somehow. Luck :)

---

### Post by jken146 on 2008-01-11
You could try changing the labels of these partitions in gparted.

---

### Post by phinn on 2008-01-11
Well guys thanks for the suggestions...  I have finally *fxied* the problem.  None of that kinda stuff worked because it was actually a BUG in the shipped version of XFCE.

I upgraded XFCE to 4.4.2 from these repos:
[http://j1m.net/2008/01/07/get-xfce-442-on-xubuntu-gutsy-gibbon-or-feisty-fawn-2/](http://j1m.net/2008/01/07/get-xfce-442-on-xubuntu-gutsy-gibbon-or-feisty-fawn-2/)

And the icons are gone!  I looked in the changelog and it was actually some kind of bug effecting people in my situation (who let it automount to begin with then added them manually to fstab later)

Not only that but XFCE is using a bit less memory now as they closed some important leaks.

Good game Xubuntu, how about updating your packages next time :)

Problem solved...  Now if only I can get the video drivers to work right.

---

