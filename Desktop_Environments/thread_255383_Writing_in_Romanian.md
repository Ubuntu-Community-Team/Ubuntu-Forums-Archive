---
title: "Writing in Romanian"
date: 2006-09-11
forum: Desktop Environments
---

### Post by ozPATT on 2006-09-11
Hi all, this may be really easy, but I just can't work it out. 

I would like to be able to type in Romanian. I have gont to keyboard layout, and selected Romanian from the list, and I have been to language support, and selected Romanian, and it installed the necessary language files. 

But how do I switch to the Romanian keyboard and start typing in it? 

Also another question on this subject, I develop websites, and am currently developing a website which has romanian and english on it. I would like to use Romanian characters on the actual website, and so I have set the charset to ISO-8859-2, but I read somewhere that the characters need to be input using a romanian keyboard. is the layout enough does anyone know? or do I actually need to plug in a Romanian keyboard? - which I dont have ;)

thanks

Patrick

---

### Post by BerkeleyDude on 2006-09-11
Are you using KDE? If so, then you should have an icon in the system tray (next to the clock) that allows you to change the language. Also, the default shortcut for it is Alt-Ctrl-K.

If you're using GNOME - it should be similar, I think. There should still be an icon. If you go to keybinding settings, there should be a shortcut for it, too.

You should not need an actual Romanian keyboard - that makes no difference. I can type in Ukrainian using a regular American keyboard :)
Just switch the layout.

As for the charset - I'd strongly recommend using UTF-8. Save the file in UTF-8 format, and specify that as charset in HTML. It's the standard now. And, all other charsets have caused so much trouble that it's just a bad idea.

---

### Post by ozPATT on 2006-09-11
does utf-8 replace all the iso charsets? 

i am using gnome, but i dont see anything near the clock to change layout. :s

---

### Post by sethmahoney on 2006-09-11
You have to add it.  Right click on the panel, click "Add to panel...", and then select "Keyboard Indicator".  After you've got that set up, if you want to add a keyboard shortcut to switch layouts, right click on your new keyboard applet, select "Open keyboard preferences", go to the "Layout Options" tab, open up "Group Shift/Lock Behavior", and select one of the key combinations there.  From then on, either hitting that combination of keys or clicking on the layout applet will change your layout.  Keep in mind that Gnome does this on a per-application basis, so if you're typing in gedit in Romanian and switch to openoffice, it will reset to your default layout.  But then when you switch back to gedit, you'll be typing in Romanian again.

---

### Post by ozPATT on 2006-09-11
perfect! thanks loads for your help, i now have the keyboard and my website working! 

thanks again, 

Patrick

---

### Post by sethmahoney on 2006-09-12
Hurrah!  Glad to help!

---

### Post by dan_m on 2007-07-18
Hi, dear Ubuntu friends,

I had the same problem and I solved it simply reading on the Romanian Ubuntu forum:
[http://forum.ubuntu.ro/viewtopic.php?id=812](http://forum.ubuntu.ro/viewtopic.php?id=812)

So, I try to resume: I use Ubuntu 7.04, and I am a beginner, so I didn't use console commands.

On the Panel: System / Administration / Language support
I selected Romanian and installed it.

The keyboard layout: System / Preferences / Keyboard
Layouts
Add
Romania
Now, please click on the details triangle. You can select Standard or Winkeys.
A couple of days ago I selected Standard, and I didn't notice any difference.
Today I installed Winkeys.
Standard uses Alt+a, Alt+i, Alt+s, Alt+t for RO special letters.
Winkeys is like in Windows: [ ] ; ' \ are remapped.

On the Pannel it appeared a keyboard indicator. You can switch USA/Rou with the mouse.
I learned today to switch it from the keyboard, left-Alt + right-Alt is the default combination.
I changed it to left Alt+Shift and it worked, so I suppose that if you dind't succeed, you probably selected Standard. You should try Romanian Winkeys layout.

I hope it will do.

---

