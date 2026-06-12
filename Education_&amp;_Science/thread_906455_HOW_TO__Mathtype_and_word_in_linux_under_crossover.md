---
title: "HOW TO : Mathtype and word in linux under crossover / wine, hellenic fonts"
date: 2008-08-31
forum: Education &amp; Science
---

### Post by Claus7 on 2008-08-31
Hello,

I was having problems displaying the equations that were written in mathtype in word (installed in linux under crossover office or wine).
In addition, I had mainly problems displaying the **hellenic** (greek) **fonts and letters** via mathtype.
The how to I'm writting is based on other posts in this forum. I have gathered the information and I have added steps, that I think that they are helpful, so as someone to make it work.

So, we take into account that we have a dual boot with windows xp on one hand and Ubuntu Dapper Drake 6.06 on the other. The version of Mathtype I'm using is 6.0 and the version of office is 2003. The installation of office and mathtype is done both in ubuntu and windows. 
In ubuntu the installation of office is via crossover, whereas the installation of mathtype via wine. I do not think that installing mathtype via crossover will have any difference. Do it from both. Also, in word it would have been better to disable the macros before installing mathtype. Either way you can insert an equation in word by going to :
Insert -> Object -> Mathtype 6.0

After you have finished with the installation you propably might face problems with the fonts. The best thing you have to do is to go to : Places -> Search for files, and select the windows partition as your destination. The string you have to put is :
**symbol.ttf**
Now the result you will get should be :
*name_of_windows_partition/WINDOWS/Fonts*
Just drag it to your Desktop

Next open a terminal and copy that file as root to :
*/opt/cxoffice/share/wine/fonts*

Open word, open mathtype and go to :
Preferences -> Equation Preferences and choose **Load from Factory Settings ...**

Normaly you will be able to choose and see nicely the hellenic letters.

References:
[http://ubuntuforums.org/showthread.php?t=771564&highlight=mathtype](http://ubuntuforums.org/showthread.php?t=771564&highlight=mathtype)
[http://ubuntuforums.org/showthread.php?t=820760&highlight=mathtype](http://ubuntuforums.org/showthread.php?t=820760&highlight=mathtype)

Hope this helped,
Regards!

---

### Post by midden on 2008-11-10
I realize this is an old post, but thanks -- your howto got my equations displaying correctly.

---

### Post by webbsd on 2009-01-08
Worked perfectly. Thank a lot :)

---

### Post by Claus7 on 2009-04-07
Hello,

you are welcome! 

Just to add that the destination of copying one's fonts might be different depending on where the installation of cxoffice took place. Another place according to a default installation might be:
~/cxoffice/share/wine/fonts/

If someone does not have a dual boot someone can find and download the fonts from here:
[http://www.dll-files-download.com/S/2008-01-13/15553.html](http://www.dll-files-download.com/S/2008-01-13/15553.html)
edit:also this site has the fonts:
[http://hawaii.hawaii.edu/math/Courses/Math100/Chapter0/FAQ/WinFont.htm](http://hawaii.hawaii.edu/math/Courses/Math100/Chapter0/FAQ/WinFont.htm)
edit2:you have to restart mathtype for the changes to take effect. If the above procedure does not work, then you have to set manually the path to where the fonts where downloaded. If you restart, the fonts should be displayed correctly.

because the name of the file is in capital letters, a renaming to small ones might not be a bad idea.

Regards!

---

