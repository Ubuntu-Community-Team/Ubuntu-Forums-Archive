---
title: "Cedega"
date: 2006-06-18
forum: Gaming &amp; Leisure
---

### Post by blazer666 on 2006-06-18
I have just installed ubuntu AMd64 6.06 (my very first linux setup!) I want to run cedega and have joined transgaming so I can dowload cedega. I can not for the life of me see the AM64 version there is a i386 version which doesnt work! so how do i get this running on my system.

TIA

Del

---

### Post by handy on 2006-06-18
[QUOTE=blazer666]I have just installed ubuntu AMd64 6.06 (my very first linux setup!) I want to run cedega and have joined transgaming so I can dowload cedega. I can not for the life of me see the AM64 version there is a i386 version which doesnt work! so how do i get this running on my system.

TIA
Del[/QUOTE]

There is no 64bit version.  You need to **force** the install or run in 32bit mode, or install the 32bit version of Ubuntu.

If you do a search of the forums you will find all the details, if someone doesn't post them here first!

By the way, I swapped to 32bit after using 64bit Ubuntu, & could detect no speed difference!

---

### Post by Jason_25 on 2006-06-18
Just grab the tar.gz version from the website and extract it anywhere.  No need to force it.  Then you can upgrade to the latest version from within the GUI.

---

### Post by handy on 2006-06-19
Have a look in [**this thread**]("http://ubuntuforums.org/showthread.php?t=82676&highlight=cedega+64bit"), you may find some useful Cedega on 64bit info'.

---

### Post by blazer666 on 2006-06-19
[QUOTE=handy]Have a look in [**this thread**]("http://ubuntuforums.org/showthread.php?t=82676&highlight=cedega+64bit"), you may find some useful Cedega on 64bit info'.[/QUOTE]


Now I am totally confused.

I cant install cadega as it say the following.

Cannot open cadega_timedemo_installer.htm

please I do not have a clue how to install Linux programmes. to me the above file looks like a html file! so what am I doing wrong? I have looked at that URL you game me  and I cant make head or tail of what I am supposed to download. Bin usr - WHAT IS IT! ](*,) 

I cant even get the NVIDIA graphics drivers to install.

---

### Post by blazer666 on 2006-06-19
[QUOTE=Jason_25]Just grab the tar.gz version from the website and extract it anywhere.  No need to force it.  Then you can upgrade to the latest version from within the GUI.[/QUOTE]


Where can I get this from?? the only files that look like the one you mentioned on the website is: cedega-small-5.2.tgz

is that it?

if so I have downloaded it there are 3 dirs in it called: usr opt and etc, now what?? 

please help.

---

### Post by eqisow on 2006-06-19
I'm, umm, not particularly sure why you've been advized to install the .tar.gz file. It seems to me the easiest way to go about this would be to make sure the cedega package is in your home folder, open up the terminal in 'Applicatons --> Accessories --> Terminal', then copy/paste the following:

```
sudo dpkg -i --force-architecture cedega-small_5.2_i386.deb
```

Then you sould be able to run it from the terminal with 'cedega'. It should also create a menu entry. If you don't see one right away, copy/paste

```
sudo killall gnome-panel
```

into the terminal. This will kill your menu bar and restart it, hopefuly with the new Cedega entry.

Edit: For future reference, the .tar.gz file they are talking about is a compressed archive, similiar to .zip in Windows. With a .tgz file you can usually eithe rinstall it to it's 'proper' location, or just run it from the directory you extracted it to. To install the Cedega .tgz file in particular, you would do the following:

```
cd / && tar xvzf ~/Desktop/cedega-small-5.2.tgz
```

Edit again: Also for future reference, there were [install instructions]("http://downloads.transgaming.com/files/cedega_quick_start_5.2.html") at the Cedega site. (You may need to be logged in to view that)

---

### Post by handy on 2006-06-19
Hi Blazer666,

Hang in there, the learning curve that you are currently on loops the loop, it is that steep!!

Don't neglect the online help, it's not like windoze help, it actually does help!

***Menu: System / Help / System Documentation / Ubuntu Desktop Guide***  

All the basics are there.  Then you have the forums for the specifics, or to clarify anything that you don't understand.

Know that if you choose to stick with it, in a month you will be starting to feel comfortable, in 3 you will be at home, in 12 months you will know so much you will surprise your self!! :KS

---

