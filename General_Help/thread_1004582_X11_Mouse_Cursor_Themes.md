---
title: "X11 Mouse Cursor Themes"
date: 2008-12-07
forum: General Help
---

### Post by f37u5g0d on 2008-12-07
So I just tried to install a new mouse cursor theme on ubuntu 8.10 and I ran into a few problems but after browsing the forums for about 30 minutes I figured everything out from 3 or 4 different threads and I thought I should compile some of the things that I found so it is easier for others.

1.  To install a theme download a *.tar.gz file from the Internet.  Open a nautilus window of the location where the file is and drag the uncompressed .tar.gz file onto the theme changer window found under System -> Preferences -> Appearance Preferences (theme tab).

2.  If you have compiz enabled in order to change your mouse cursor you need to go to System -> Preferences -> Compiz Effects Settings Manager (if it isn't there then run "sudo apt-get install compizconfig-settings-manager" ) Once you have that open go to General Options and blank the line that says "Cursor Theme."

3.  When you install a new theme restarting X11 (ctrl + alt + backspace)  to take care of some bugs like a different cursor appearing in some windows.

4.  You will get an error that says "Directory cannot be moved over directory"  If you try to install a mouse theme more than once.  Sometimes though (this was happening to me randomly) even though the theme is in the ~/.icons folder (technically installed) it doesn't show up in the menu you get when you go to System -> Preferences -> Appearance, click customize go to the pointer tab.  This is very confusing.

5.  Last, going to the menu described in #4 and clicking on a different cursor will work a lot better if compiz is turned off.  I suggest turning compiz off to work on your mouse cursor and then turning it back on when you're finished.

---

### Post by souldure on 2009-02-03
bro i have had some similar problens and i found that is you havent modified the default theme index in your /usr/share/icons/default folder you cant do this with nautilus in ibex i dont think you have to open it and change the default theme name i found it easyer to just get the theme index out of the theme itself add it to the usr/share/icons directory using sudo nautilus and copying it into the directory / though when you replace the theme index be sure to right click go to properties and make it executable and then right click on your desktop click change desktop background click the theme folder and drag the cursor gz into it and install it  then select it from cursors in system preferences cursors after that go to compiz and click general and type in the cursor name restart x and it should be complete root windows and all. im new to ubuntu so if i am wrong please let me know or if there is a cleaner more simple way please let me know thanks. 
                                                            souldure

---

### Post by souldure on 2009-02-03
i feel rather like a dunce now this was the wrong window i was trying to post into though i didnt notice anyone mentioning anything about making the cursor executable in usr/share/themes/default after replaceing it that turned out to be my main problem. sorry for the confusion . souldure

---

### Post by f37u5g0d on 2009-02-04
lol, ok thanks for explaining :)

---

