---
title: "[gnome3]Can't select a sound theme in system properties"
date: 2011-08-04
forum: Desktop Environments
---

### Post by DaTa42 on 2011-08-04
Hello all :)
I've got a problem for two days... I'm running Ubuntu 11.04 and installed gnome 3 on it to replace unity.
In gconf-editor, I see that the sound theme is "ubuntu". So I went to /usr/share/sounds/ubuntu/stereo/ and replaced all the original oog files by new ones I took from Windows 7 (no comment), freshly converted with SoundConverter from wav to ogg.

But now, I haven't any login sound when my desktop appears, same for logout and shut down... The only sound I manage replacing is the "Bark" of gnome 3.

Also, when my computer starts and prompt me the user choice, I have a "*Tunc*" sound that is played instead of one I replaced...

I don't know if it is the cause, but in the system properties > sounds, there are NO dropdown where I could select another sound theme. I've just Alerts volume before Choice a sound alert... No dropdown in the middle.

Please help me :( Google didn't help me to find a solution... :confused:

EDIT :
Maybe this will help you : When I type in the terminal
/usr/bin/canberra-gtk-play --id="desktop-login" 
It says that the file cannot be found, though it is there...

---

### Post by jimmydean886-2 on 2011-12-03
This is not a problem at all, but intentional.

GNOME's mission seems to be to treat all users like they are just plain stupid, and this is a result.

In the old 11.04 ppa version of gnome-shell, the Freedesktop theme is used instead. Just replace that. In Ubuntu 11.10, on the other hand, the Ubuntu sound theme is used. I was able to replace the login and logout sound with those from Windows 2000. (these sounds are awesome)

I also designed a script to allow for a logout sound. See [http://ubuntuforums.org/showthread.php?t=1368649&highlight=logout+sound](http://ubuntuforums.org/showthread.php?t=1368649&highlight=logout+sound) for more information on how to get that working.


Good luck, and I hope this solves your problem.

---

