---
title: "Can't start Ubuntu!"
date: 2007-02-07
forum: Desktop Environments
---

### Post by daidainius on 2007-02-07
At first: sorry for my english.
I had the fresh Edgy 32bit installed. I decided to install fglrx for my ATi Xpress200 video card. I downloaded latest ati-driver-installer-8.32.5-x86.x86_64.run from ati.
(really latest - ati-driver-installer-8.33.6-x86.x86_64.run)
I used method desribed in:
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati)
No errors appers.
The last step was:
sudo shutdown -r now

Now I can boot in Ubuntu only in recovery mode. :( 
Trying to start normal mode, after system loading progress bar, I have only black screen.
No login message. No messages at all. Ctrl+Alt+Backspace, Ctrl+Alt+F1-F7 not work.
I have't lot experience in Linux.
Please for some instructions. How to fix this problem without reinstalling Ubuntu.
(Finnally I can reinstall fresh Ubuntu copy and waste ~4hours with internet updates) :) 
Please for some instructions.

---

### Post by renzokuken on 2007-02-07
could you post your xorg.conf, when you get the balck screen you should be able to switch to a TTY terminal screen by pressing Ctrl+Alt+F1, then login and type

[code]sudo nano /etc/X11/xorg.conf[/conf]

specifically interested in the Section "Devices" and the resolution section

---

### Post by daidainius on 2007-02-07
Thanks for quick responce.
Now I am in reinstalling step. :)
I will try to install fglrx once more, but I will need some help of course.
If you see the mistake or possible my gap by using reffered method:
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati)
please point it to me.
May I better use precompiled xorg-driver-fglrx_8.28xxx from Ubuntu respositories?
Regarding previous installation:
Now I can't post xorg.conf, but it was "perfectly configured" :) for fglrx driver(I had Suse10.2 prevously installed and new how it must look).
Ctrl+Alt+F1 does not works. I think Xserver can't start at all(or something like this).

---

