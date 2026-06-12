---
title: "Please Help With Wow On Ubuntu"
date: 2007-02-26
forum: Gaming &amp; Leisure
---

### Post by thrash_em_all on 2007-02-26
Im new to ubuntu and i still dont know how to use it properly, im used to the spoon feeding of windows and i dont understant terminal use lol. but heres my problem. i have installed WoW on the computer. it seems to work fire sometimes, i can log in, choose realm and log in. but as soon as im logged in. the game freezes and completely closes. VERY ANNOYING. 

Sometimes, though it manages to run fine and i can get some gaming done. the only problem is none of the spell icons appear and i have to hover the mouse to see what they are. whenever i open my bag it seems to crash and close. whenever i try to open the abilities menu wow closes.

This must seriously be the most annoying thing that has ever happened to me in my whole life. haha it really is a pain in the @$$. i wish i knew how to fix it but the only way i can see WoW running to its full potential is if i install Windows again and go back to simple yet effective running of the program.

If anyone has any hints or can guide me through installing WoW or wine properly could you PLEASE help me.

---

### Post by willskills on 2007-02-26
There are a few guides written for this, try starting here; [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (or Sammi might get you!)

If you still don't have any joy; try getting in touch with me in IRC - I'll see if I can give you a hand!

willskills @ irc.freenode.net (#ubuntu-uk,#cisco,#wowwiki) or just send me a PM :)

---

### Post by matthew on 2007-02-26
I removed the poll. We don't like it when people call each other "noobs," even when the person the name is directed toward is you. :)

---

### Post by Sammi on 2007-02-26
> **willskills said:**
> There are a few guides written for this, try starting here; [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (or Sammi might get you!)Boogie-man says BUH :twisted: hehehe



@thrash_em_all
Your two problems(crash and distorted icons) are covered in the troubleshooting section of the howto. Please post back if you are having problems implementing the fixes.

---

### Post by thrash_em_all on 2007-02-26
ok i dont think you understand how much of a linux idiot i am. i dont know how to find any programs that i have installed to c_drive. i simply cant find c_drive :| can anyone tell me where i should save the contents of the WoW cd's? and how to access them later? thankyou

---

### Post by Sammi on 2007-02-26
On the top left of your desktop you'll see three options. One is "places". Left click on that and then left click the first menu item, called "Home Folder", in that drop down menu. A new window should appear. This is the application named Nautilus. It is the program that lets you view/copy/move/delete or just do pretty much everything to the files and folders on your computer.
Right now you should be viewing the directory with the address /home/*<username>*/ in your hierarchical directory three, where *<username>* is your computer login name.  For example if it is "mike", then it would be /home/mike/. If you're used to windows, then you should be feeling nicely at home right about now.

Use Nautilus to copy all the files from all the WoW cd's to a directory on your computer. This could be /home/mike/wow/ for example. Just select "overwrite" if Nautilus says that a particular file already exists.

You find Wine's artificial C: drive at /home/*<username>*/.wine/drive_c/

Please note that a punctuation in front of a folder name, like ".wine", means that it is a hidden folder. You can view hidden files in Nautilus by pressing the Ctrl and H key at the same time while in a Nautilus window.

---

### Post by Sammi on 2007-02-26
Just found some very basic instructions on how you use your Ubuntu Desktop for you: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

Particularly these two are relevant to a complete noob: :p
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/root-and-sudo.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/root-and-sudo.html)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/terminals.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/terminals.html)

---

### Post by thrash_em_all on 2007-02-27
thanks soooooo mcuh lol the main thing that helped me was the ctrl H part haha i could not figure out why i couldnt find any folders. my WoW problem still persists though. i followed every instruction in the HOWTO for worldof warcraft. but as soon as i log in wow crashes and i cant quit the program until i restart the computer or log out. i tried to end process but it still didnt disappear. :( i wish i could get WoW to work as it is the only game i play. :(

---

### Post by Sammi on 2007-02-27
Have you added those lines to xorg.conf, as suggested in the troubleshooting section of your howto?

Use this command to edit xorg.conf:
```
gksu gedit /etc/X11/xorg.conf
```
gksu is a graphical sudo and gedit is a text editor, so that line opens xorg.conf in a text editor in superuser mode.

This post might be useful:
[http://www.ubuntuforums.org/showpost.php?p=2183925&postcount=185](http://www.ubuntuforums.org/showpost.php?p=2183925&postcount=185)

---

### Post by willskills on 2007-02-27
Remember the Regedit fix :D

---

