---
title: "Some programs don't follow my selected theme."
date: 2010-11-08
forum: Desktop Environments
---

### Post by blur xc on 2010-11-08
This one is a bit weird, because I don't recall this being a problem in the past, but a few of my applications don't follow my selected them.  They look like the update manager, which I think follows the root users theme.  I read a fix a long while back how to fix that, when I was running 9.04, but I never re-fixed it after upgrading to 10.04, and I can't find that article again...  

So far the programs acting goofy that I've found is Acroread, Google Earth, and Bibble 5 Pro...  Dunno if there's more.  I just did a quick check of a few closed source programs I had installed.

See screenshots:

Thanks,
BM

---

### Post by 3Miro on 2010-11-08
If you installed a theme by dragging it into the Appearance menu, then it is placed in /home/your_username/.themes and is thus accessible to your user only. The update manager runs as root, which is a different user and doesn't know how to find the theme. You can open a terminal and type:

```
 gksudo nautilus 
```

this will open the file manager with the ability to do any changes to your system. Be very careful, you can accidentally delete important files. From your home folder, hit Ctr + H to show hidden files and go into .themes. Copy the folder with the name "Your theme" and then place it in /usr/share/themes/. This should fix the Update Manager issue. Make sure to close this fila manager windows after you are done.

I don't know if it will fix all of your other programs.

---

### Post by atera on 2010-11-08
this worked perfect to make update manager use my theme, but I wonder if there's a way to make nautilus itself use it when you run it with sudo..?

---

### Post by 3Miro on 2010-11-09
> **atera said:**
> this worked perfect to make update manager use my theme, but I wonder if there's a way to make nautilus itself use it when you run it with sudo..?

This should have fixed nautilus too. (btw you should use it with gksudo not sudo) I don't know about other programs like Adobe Reader.

---

### Post by SantaFe on 2010-11-09
What I do is make a copy of the theme folder on the sesktop, then open a terminal & paste this in: sudo cp -r $HOME/Desktop/Overglossed /usr/share/themes

Just put your theme folders name in place of Overglossed  & press enter.  After you enter your password it will copy it there.  BTW: if there are any spaces in the folder name, use " marks around it or it won't work.

I know, Po-tay-to/Potato, but it seems easier to me, course I made a text file so I can copy/paste a little faster. ;)

---

### Post by 0N3 on 2010-11-09
Try ubuntu-tweak

---

### Post by blur xc on 2010-11-12
Ok, so I've done some testing, and have at least figured out what caused the problem.  All my installed applications used to run properly, following whatever theme I had selected (except the update manager, but that's a different story), UNTIL I installed the "Divergence - A New Hope" theme package.  

To reproduce the problem, I switched over to my wife's user account, and verified that the same programs that aren't working right for me, worked right for her, and they did.  I tired a couple of different themes, and everything was fine.  Then I changed her theme to the "A New Hope" theme, and BAM- all those same programs switched to a default gnome theme (Win 95 blocky, gray and blue color, like in my screen-shots), but when I switched back to her original theme, all of those programs stayed like that.  So, it's like now they permanently go by the root user's theme or some crap like that.  It's weird, and frustrating.

[http://www.webupd8.org/2010/11/divergence-iv-new-hope-updated-to-v077.html](http://www.webupd8.org/2010/11/divergence-iv-new-hope-updated-to-v077.html)

Thanks,
BM

---

