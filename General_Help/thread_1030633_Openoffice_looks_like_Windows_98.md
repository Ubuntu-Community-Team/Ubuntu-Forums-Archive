---
title: "Openoffice looks like Windows 98"
date: 2009-01-04
forum: General Help
---

### Post by lhamil64 on 2009-01-04
I was reading a tutorial on how to upgrade Openoffice to version 3.0 and that one said to uninstall my old version and install the new version. Well, that tutorial had a link to a file that no longer existed so i had to go to openoffice.org and try to reinstall from that file. That install hung and a few days ago i searched for a different tutorial and i got openoffice 3 installed. But, now the theme looks REALLY bad. It looks like Windows 98. I tried googling for themes but apparently it doesn't support them. How can I make OpenOffice match everything else?

---

### Post by DarKnyht on 2009-01-04
I am by no means an expert, but I will offer what help I can.  

Can you post a link to the instructions you followed so I have an idea where you were told to install this software and where you got the files from?

---

### Post by dragos240 on 2009-01-04
Honestly, try uninstalling 3.0 and reinstalling 2.0, the "windows 98" theme may be the default look, in which you might want to switch back to 2.0. Just a suggestion.

---

### Post by arashiko28 on 2009-01-04
It does look like that, now, most important question, what do you rather to choose: eye-candy over functionality or vice versa?

---

### Post by lhamil64 on 2009-01-04
I found the tutorial i used:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

I will try things again maybe next weekend or something when i have time to get to my other computer.

---

### Post by DarKnyht on 2009-01-04
Thanks for the info.  That is where I got the same instructions for installation.

The problem most likely is that the OpenOffice Theme is set to Classic.  You can change it by going to Tools>Options.  Once there click on View and you can change the theme there.  I personally prefer the default icons over the Human, but to each their own.

I hope this solves your problem.

---

### Post by sandyd on 2009-01-04
hey, are you using kde?
ive had some problems where openoffice from the resipostires + kde looked like junk. its solved if you uninstall all of the the openoffice stuff you have right now (sudo apt-get remove openoffice.org*) then download the debsfrom here([http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)). Then tar xvfz it. then go into the folder from the terminal. run this

cd OOO*
cd DEBS
cd desktop*
mv * ../
cd ../
rmdir desktop-integration
sudo dpkg -i *

---

### Post by lhamil64 on 2009-01-05
I tried changing the theme but only the top row of icons change. I'm using gnome.

---

