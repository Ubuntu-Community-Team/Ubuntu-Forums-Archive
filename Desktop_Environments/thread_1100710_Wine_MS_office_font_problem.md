---
title: "Wine MS office font problem"
date: 2009-03-19
forum: Desktop Environments
---

### Post by O-pos on 2009-03-19
Hello,

I have Microsoft office 2003 on wine, which works perfectly fine, but there is a problem with the font Arial, which is always italic and can't be made regular non-italic. 

When I start word and go to Meu > Format > Font and choose Arial under "Latin text font", it only has two options: narrow and bold italic. Other fonts work perfectly fine. Any suggestions how to deal with that? Maybe the system confuses Arial with Arial narrow?

---

### Post by metapaso on 2009-06-04
> **O-pos said:**
> Hello,

I have Microsoft office 2003 on wine, which works perfectly fine, but there is a problem with the font Arial, which is always italic and can't be made regular non-italic. 

When I start word and go to Meu > Format > Font and choose Arial under "Latin text font", it only has two options: narrow and bold italic. Other fonts work perfectly fine. Any suggestions how to deal with that? Maybe the system confuses Arial with Arial narrow?

I found an answer to this problem on [http://ubuntuforums.org/archive/index.php/t-1036323.html](http://ubuntuforums.org/archive/index.php/t-1036323.html)

In my case, there was something wrong with having multiple copies of the same font installed in various locations (i.e. the ~/.wine/c_drive/windows/Fonts folder AND your regular X fonts that ubuntu uses.)  As a quick fix, I used nautilus to navigate to my /home/myname/.wine/c_drive/windows folder and re-named the Fonts folder to old.Fonts.  Then I created a new, empty Fonts folder.  When I next launched MS Word, the Arial italic problem was gone.

I did not check to see if other fonts were missing or invalidated because of this action, but Arial and Helvetica work fine now.

Just a side note, I tried the winetricks script installation of mscorefonts and this did not help the problem at all.

---

### Post by scorp123 on 2009-11-22
I was just in the same boat ...

I have to use a commercial Windows application and I have to do that under WINE (... long story ...).

The fonts looked as if somebody had wiped their hand over wet ink, absolutely nothing was readable. None of the workarounds helped.

What finally did help is to upgrade to "wine1.2" from this PPA:
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by HeadHunter00 on 2009-11-22
[U]@[FONT=Arial Black]metapaso, thanks
[/FONT][/U]

---

### Post by HeadHunter00 on 2009-11-22
Never mind, scorp's solution is better:popcorn:

---

### Post by O-pos on 2009-11-23
In my case it heplped to just delete the content of ~/.wine/drive_c/windows/Fonts
Now everything works fine.

By the way, where would be the fonts be located I am using now?

---

### Post by max4 on 2009-12-09
> **O-pos said:**
> In my case it heplped to just delete the content of ~/.wine/drive_c/windows/Fonts
Now everything works fine.

By the way, where would be the fonts be located I am using now?


^^^^ Worked for me, Thanks. I am running word 2007 in wine 1.1.31 on karmic, btw.

---

### Post by Ender985 on 2011-01-25
Shameless bump to say that it also worked for me with Wine 1.3.11 and Office 2007. Having installed all-fonts via winetricks I was still having problems with some fonts like Calibri or Arial Narrow, renaming the C_folder/Windows/Fonts to Fonts.bckp solved the issue. Probably because winetricks installs the fonts someplace else which creates a conflict.

Thanks!

---

### Post by herrkeuner on 2011-03-17
Hi guys,

 I also tried to rename the /windows/fonts folder to /fonts.old but when i do that the font seems to be fine but now i the bold letters are normal.
When i change it back, als my letters are bold and i cant do anything against it :/
so it gets vice versa when i change the folder name

halp :)

---

