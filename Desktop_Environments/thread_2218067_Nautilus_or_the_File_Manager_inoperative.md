---
title: "Nautilus or the File Manager inoperative"
date: 2014-04-19
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2014-04-19
As far as I know, I'm using the Unity Desktop. This is Precise Pangolin ver. 12.04 LTS, nautilus 3.4.2 I say this as pressing "Alt" opens the HUD. The file manager, in the left side panel, when clicked, opens for a few seconds and then closes. But: mark@Lexington:~/Desktop$ gnome-shell --version
The program 'gnome-shell' is currently not installed.  You can install it by typing:

Calling for 'Nautilus' from the HUD, returns two items, both folder icons but one has the 'home' icon in the folder and is labeled: "Files", the other folder icon says: "Home Folder". 

Clicking either of these brings up the file manager window. It also restores the missing objects on my [desktop]("http://ubuntuforums.org/showthread.php?t=2217906&p=12992847#post12992847"). But this lasts but 5 to 10 seconds and then the file mgr. window closes of it's own accord and the objects on my desktop disappear as well.

I tried to make a screenprint of my Software Update Manager window, but, while I can call for a screenprint, and name the object, the function of saving isn't working. I opened the terminal and ls-d my /home/mark/Desktop.

I know the files are there, as in a Terminal, I can read:

recipes.txt
The 'Voicemail Access' option - Google Voice Help.pdf
thunderbird.desktop [executable icon]
Trusty Tahr [this is a directory]
TTS Voice Messaging Text to Speech
tv media center [this is a directory]
UTF-8 Special Characters.pdf
UVERSE BILL.pdf
vanBasco's Karaoke Player.desktop [executable icon]
Workman CHINA work

Calling 'nautilus' from the Terminal returns:

```
mark@Lexington:~/Desktop$ nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Segmentation fault (core dumped)
```

I know little of Samba other than it is a server. Has the 'heartbleed' bug or OpenSSL bug something to do with this?

I can use my Google Chrome browser and am posting the request via it. VLC will stream a radio station. Other software applications work, but I cannot save objects.

What has happened to my OS? 

Yes, I am panicking a little.

a few hours and lots of searching later:


```
mark@Lexington:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9500 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.20

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by Mark_in_Hollywood on 2014-04-20
error:: no video mode activated

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

This flaw (or bug) has caused 2 different problems. It has prevented the desktop (/home/mark/Desktop) from being stable. At boot time (cold or warm) the objects on the /Desktop load, but after a few seconds vanish. The file manager behaves much the same way. When called or invoked the "Folder" icon on my left panel opens for a few seconds, then closes without being commanded to do so. At no time during the on-time for the computer can the file manager (Nautilus?) operate properly. Also, trying to fix this and being mislead by those with Unity or Compiz problem, I have reset my left panel and lost a number of application.

A few days later, I saw, at boot time, one icon which had the look or image of the "i'm still loading" the exact moment went by so swiftly I don't know for certain what it is. But, I decided to delete it. It had a filename extension of .jp2. Ubuntu's various apps cannot read a .jp2. After deleting this file and re-booting, I have the formerly lost desktop objects returned to their places on the /Desktop. For example. *.txt, .jpg, .pdf, user created directories "Trusty Tahr",  desktop configuration file (application/x-desktop), .mp3 and such.

---

