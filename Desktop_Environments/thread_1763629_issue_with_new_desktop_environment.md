---
title: "issue with new desktop environment"
date: 2011-05-20
forum: Desktop Environments
---

### Post by jammeramd64 on 2011-05-20
First Hi, All,
I haven't posted in a while so please forgive any fopa's, ha ha ha..
I hope I'm in the right place, I have been using Ubuntu since like 9.04? I think, loving every minute of it!..
I just upgraded from 10.10 to 11.04 on my compaq laptop,
My Issue is this, the upgrade went well for being over the internet, rebooted, got to the kewl new desktop environment, then tried to enable compiz fusion desktop cube, and darn it if I didnt lose the desktop environment. The pic I installed as desktop background is still there, and the desktop icons are as well, but no sidebar or taskbar/menubar at the top,I dont know if this is a resolution issue, or if unity is the desktop environment then it maybe' isn't enabled?,... while trying to fix this issue(in recovery mode) I got an error message saying that my hardware doesn't support unity, I do not know if that is the problem or not, everything worked fine until I tried to run compiz fusion, now all I have is a desktop background and icons?? I am still learning the Linux environment and how to do things with the command line so please be patient with me and I will give you all the kudo's!!
Please, if you can help me with this issue,I would greatly appreciate it, and thanks in advance!.....jammeramd64:popcorn:

---

### Post by jammeramd64 on 2011-05-20
My laptop is a compaq cq60-615dx notebook, with intel graphics.it is 64-bit, but I am using the 32-bit, 10.10 when I upgraded (online) to the new 11.04, I went online to upgrade because I didn't want to mess up my previous install(lots of packages) to reinstall.... 
 
p.s. while in recovery mode' it said couldn't determine graphics hardware, you'll have to configure it yourself? I think that is what led to the unity issue from above maybe??

Anyway once again thanks in advance... jammeramd64:guitar:

---

### Post by Mr. Shannon on 2011-05-20
This is happening a lot lately.  Compiz aperently does not work right with Unity, at least the cube does not.  See this link: [http://ubuntuforums.org/showthread.php?t=1763005]("http://ubuntuforums.org/showthread.php?t=1763005")

If you realy want to use the Compiz cube and unity then you can look at this:[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html")

Got this link second hand so I have no idea how well it works.

---

### Post by jammeramd64 on 2011-05-20
thank you so much...

---

### Post by jammeramd64 on 2011-05-20
Thank You, Mr Shannon, for your Advice, and expert tutelage, I was able to reset unity by opening terminal via ctrl+alt+f1, then typing [unity --reset], without the brackets.from this link you gave me.

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html) 

I guess I could have logged into classic and loaded compiz (ccsm), and changed the desktop cube back to wall and fixed this issue that way.

[http://ubuntuforums.org/showthread.php?t=1763005](http://ubuntuforums.org/showthread.php?t=1763005)

But all is well in my world now so thanks again for all your help, and to everyone who's ever helped me in this Linux/Ubuntu Community!! 

Thank You Again...Jammeramd64:D

---

### Post by Copper Bezel on 2011-05-20
> I guess I could have logged into classic and loaded compiz (ccsm), and changed the desktop cube back to wall and fixed this issue that way.

Actually, you really couldn't. By default, Classic Gnome and Unity store their Compiz settings in two separate places in gconf, so changing CompizConfig in one won't affect the other. You *can* change the backend to a flat file that's used system-wide, but there's usually no reason to do so. 

Just so you'll know for the future. = )

---

### Post by Krytarik on 2011-05-20
Actually, you *can* change the Compiz settings for Unity from within classic Gnome, therefore just select the profile "Unity" first, in "CompizConfig Settings Manager -> Preferences (lower left) -> Profile".

And switch it back to "Default" before you leave the classic Gnome session again. Of course, that would enable the Unity Launcher/Panel in that session during the process.

Also, if you do that approach, make sure to re-enable any plugin, besides the "Ubuntu Unity Plugin", that may have been disabled as well, as a matter of cascade effect.

Greetings.

---

### Post by Copper Bezel on 2011-05-20
Good point - I hadn't considered that. If your Classic Gnome settings are already configured the way you want them, that would be the better option (assuming that your Default profile doesn't have any Unity-breaking settings applied, although I guess the Classic desktop would be the best place to diagnose that, too.)

---

### Post by jammeramd64 on 2011-05-22
Thanks to all!, for all your help in this matter, got my Unity desktop with cube enabled after about 10 mins via this link;
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

P.S. don't worry so much about losing menu's, sidebars, and title bars , just make sure you have bookmarked this link in your browser of choice, and put it on the desktop along with the ccsm shortcut, now just follow the link's advice to the letter and you'll be golden.... I even had to reboot
after disabling the plug-in's, (booted to the classic desktop) and resumed the task at; enable plug-in's 
  MAKE SURE NO Other PLUG-IN"S get disabled in the process, (VERY IMPORTANT!!)1. Window Decorations 2. Place Windows
3. Move Window 4. Resize Window 5. Scale :guitar:

---

