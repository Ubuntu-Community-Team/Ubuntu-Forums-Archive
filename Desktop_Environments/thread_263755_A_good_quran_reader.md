---
title: "A good quran reader"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Ziede on 2006-09-23
Need help installing qtQuran under Ubuntu Dapper Drake,
i followed the directions from [http://ubuntuforums.org/showthread.php?p=1384426](http://ubuntuforums.org/showthread.php?p=1384426)
but no succes. Please help needed to install the libquran on gnome.

---

### Post by Rashid584 on 2006-09-23
Salam alaykum akhi

I hate having to compile stuff manually. Never works for me.

You should check to see if there is a .deb file.

Otherwise, I think there are some pretty good online recitors about? Try [this](http://www.reciter.org/)

Hope that helps.

-Rashid

---

### Post by Ziede on 2006-09-23
WS

Thank you rashid
and
Ramadan moubarak

---

### Post by Rashid584 on 2006-09-23
Ramadhan mubarak akhi :D

Taqaballah wa siyamana wa salata wa salih al alam. Ameen

-Rashid

---

### Post by derakhshani on 2006-12-28
There is an alternative Open Source Quranic Software: [Zekr]("http://siahe.com/zekr/")
An ubuntu installer (deb package) has been built for this project.
You can download it from:
[http://umn.dl.sourceforge.net/sourceforge/zekr/zekr_0.5.0b2-1_i386.deb]("http://umn.dl.sourceforge.net/sourceforge/zekr/zekr_0.5.0b2-1_i386.deb")
After downloading simply do:
```

sudo dpkg -i zekr_0.5.0b2-1_i386.deb

```
Note that zekr depends on sun-java5-jre and does not work with gcj. So; if you do not have sun-java5-jre installed, take a look at:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

I have tested this deb package on both Dapper 6.06 and Edgy 6.10; it works fine.

---

### Post by Rashid584 on 2006-12-28
Assalamu alaikum wa rahmatullah akhi derakhshani :D

Masha'Allah, i just installed zekr and its great :D It has all the functionality you would need from a Qur'an reader...nice artwork, everything :D

BTW the link in your post doesn't work. This [one ](http://sourceforge.net/project/downloading.php?groupname=zekr&filename=zekr_0.5.0b1-0ubuntu1_i386.deb&use_mirror=osdn) should insha'Allah.

I dont know anything about programming...how did they make a Java application use GTK? Are there GTK bindings for java?? I always thought java applications have to look hideous and gray :p EDIT: Don't worry...read the project page, it uses SWT :)

Oh i just thought of something it doesn't have...qirat :( 

Insha'Allah the bruthas who made this and you will be in my duas :) Jazakallah khayran for sharing it

-Rashid

---

### Post by nice view from here on 2006-12-29
Peace, 
nice searchable Quran here that runs well with wine paste the link. Its not open source but its freeware.
[http://www.quranexplained.co.uk/qxp-software.zip](http://www.quranexplained.co.uk/qxp-software.zip)

:-k 
nice day all

---

### Post by meng on 2006-12-29
Echoing my post from earlier today (in a thread about a program to set a reminder for prayer times during the day) someone with a bit of knowhow should seriously remaster Ubuntu: Muslim Edition. Ubuntu ME!

---

### Post by scrooge_74 on 2006-12-29
> **nice view from here said:**
> Peace, 
nice searchable Quran here that runs well with wine paste the link. Its not open source but its freeware.
[http://www.quranexplained.co.uk/qxp-software.zip](http://www.quranexplained.co.uk/qxp-software.zip)

:-k 
nice day all

> **Rashid584 said:**
> Assalamu alaikum wa rahmatullah akhi derakhshani :D

Masha'Allah, i just installed zekr and its great :D It has all the functionality you would need from a Qur'an reader...nice artwork, everything :D

BTW the link in your post doesn't work. This [one ](http://sourceforge.net/project/downloading.php?groupname=zekr&filename=zekr_0.5.0b1-0ubuntu1_i386.deb&use_mirror=osdn) should insha'Allah.

I dont know anything about programming...how did they make a Java application use GTK? Are there GTK bindings for java?? I always thought java applications have to look hideous and gray :p EDIT: Don't worry...read the project page, it uses SWT :)

Oh i just thought of something it doesn't have...qirat :( 

Insha'Allah the bruthas who made this and you will be in my duas :) Jazakallah khayran for sharing it

-Rashid


Hey Guys be carefull, the CIA may be watching LOL   [http://www.ubuntuforums.org/showthread.php?t=326606](http://www.ubuntuforums.org/showthread.php?t=326606)

---

### Post by Rashid584 on 2006-12-30
> **meng said:**
> Echoing my post from earlier today (in a thread about a program to set a reminder for prayer times during the day) someone with a bit of knowhow should seriously remaster Ubuntu: Muslim Edition. Ubuntu ME!

Its been suggested before. I discussed it briefly with some bruthas...only thing is, I have no idea how :p

There's definitely potential...there's Quran software (Zekr) and prayertimes software (SuperKaramba + prayer widgets) etc add in a few nice Islamic wallpapers, tasmiyah at login and logout time, Islamic bookmarks in Firefox/Konqueror and you're sorted (sorta) :D

But how does one go about making a LiveCD and/or distro-based-distro?

EDIT: Alhamdulillah found a good resource: [https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)

I can't try it out at the moment...maybe sometime in the future...do any of you guys wanna try it out? Subhanallah that'd be really awesome...Ubuntu Muslim Edition :D (or maybe a different name...Mubuntu sounds a bit crap imo :p Islamix? Or maybe the Arabic word for Ubuntu...adaab?) I made an IRC channel on freenode but it closes as soon as I logout...how are you supposed to keep a channel open 24/7? :S

> **scrooge_74 said:**
> Hey Guys be carefull, the CIA may be watching LOL   [http://www.ubuntuforums.org/showthread.php?t=326606](http://www.ubuntuforums.org/showthread.php?t=326606)

lol :p

-Rashid

---

### Post by derakhshani on 2007-02-01
> **Rashid584 said:**
> Assalamu alaikum wa rahmatullah akhi derakhshani :D

Masha'Allah, i just installed zekr and its great :D It has all the functionality you would need from a Qur'an reader...nice artwork, everything :D

BTW the link in your post doesn't work. This [one ](http://sourceforge.net/project/downloading.php?groupname=zekr&filename=zekr_0.5.0b1-0ubuntu1_i386.deb&use_mirror=osdn) should insha'Allah.

I dont know anything about programming...how did they make a Java application use GTK? Are there GTK bindings for java?? I always thought java applications have to look hideous and gray :p EDIT: Don't worry...read the project page, it uses SWT :)

Oh i just thought of something it doesn't have...qirat :( 

Insha'Allah the bruthas who made this and you will be in my duas :) Jazakallah khayran for sharing it

-Rashid


Zekr 0.5.0 beta 2 is out:

[http://umn.dl.sourceforge.net/sourceforge/zekr/zekr_0.5.0b2-1_i386.deb]("http://umn.dl.sourceforge.net/sourceforge/zekr/zekr_0.5.0b2-1_i386.deb")

to install zekr simply run:
```
sudo dpkg -i zekr_0.5.0b2-1_i386.deb
```

This package works fine on ubuntu (>= 6.06) and debian.

To find new features out, check:
[http://siahe.com/zekr/]("http://siahe.com/zekr/")

---

### Post by tinkyawoo on 2008-05-01
:confused::confused: Zekr quran can only play if the PC is online. if no internet connection it refuse to play or brows the quran...
any alternative Quran??? Pls

---

### Post by promete on 2008-05-01
> **tinkyawoo said:**
> :confused::confused: Zekr quran can only play if the PC is online. if no internet connection it refuse to play or brows the quran...
any alternative Quran??? Pls


Zekr provides both online and OFFLINE Quran recitation.

If you want to use the offline recitation feature then follow the instructions at [http://zekr.org/wiki/Minshawi_offline_recitation]("http://zekr.org/wiki/Minshawi_offline_recitation").

Right now 3 audio recitation packs for offline use are prepared: [http://zekr.org/quran/recitations]("http://zekr.org/quran/recitations")

---

### Post by abouahmed on 2008-07-16
I have installed ubuntu 8.4, & i need help to install ubuntume. [http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

