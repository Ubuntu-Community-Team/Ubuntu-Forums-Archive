---
title: "Newbie with 2 questions to start"
date: 2006-09-11
forum: Desktop Environments
---

### Post by eggy1962 on 2006-09-11
Hello there. 
I have just installed ubuntu recently and have managed to do certain things  like setting up my spare printer,installing digikam to use my canon camera, sorted my email thru  evolution, but i have a couple of  questions i could do with some help with:-
1.is there a program that allows me to listen to shoutcast radio network
2. is there  any program that will allow me to use my creative zen vision m mp3 player. i have plugged it in but no response.
Thanks
Mark

---

### Post by luckyaba on 2006-09-11
1. StreamTuner is what i use to listen to radio streams. Nice program and already has alot of stations listed with a feature of adding more.

2. The MP3 player should auto mount itself or at least both of mine do. If your asking about a program to make playlists and such i believe amarok would work quite well.

---

### Post by eggy1962 on 2006-09-12
Hi again
1. streamtuner  was just the job
2. no luck in getting my creative zen to be  recognised 
is there a program that can be used to make my mp3 player  work?
3. new question ...how to i get pictures/graphics to open with my emails in evolution?

---

### Post by Fully216 on 2006-09-12
gnomad2 will do the job for your creative zen.  I have a zen-xtra that works fantastic.

FYI, other multimedia (players, formats, etc) questions, info can be found here.  I would recommend a quick read through for newbies.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bulldog on 2006-09-12
For your pictures go to view and tic show pictures or use <CTRL> l.

---

### Post by eggy1962 on 2006-09-12
Hi again
pics in email  working but 
no luck with my mp3 player..gnomad2 doesn't  find my  zen vision m... can't seem to find it on the usb bus message...so is that the  end re my particular player?

---

### Post by eggy1962 on 2006-09-12
i just tried this=
mark@mark-desktop:~$ lsusb
Bus 004 Device 002: ID 041e:413e Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04b8:0001 Seiko Epson Corp. Stylus Color 740 / Photo 750
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
mark@mark-desktop:~$

when i plugged the player in it had power to charge up,it appears to be recognised in lsusb yet  gnomad2 says it can't find it

---

### Post by Fully216 on 2006-09-12
Do you have libusb and hotplug installed as well?  See [http://gnomad2.sourceforge.net/?section=supplement](http://gnomad2.sourceforge.net/?section=supplement) for more information.

It is documented that they player works with gnomad2, so we just have to figure out why yours isn't working.  In some cases, a cvs version of libnjb is required.

There is also a guide here that I found useful.  [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article)

---

### Post by eggy1962 on 2006-09-12
hmmm this is where i come unstuck... no i don't have libusb or hotplug install as far as i know  and it seems they are not available via ubuntus add/remove so i assume it means finding a  source and downloading them then having to do work via  command line...i have  done very little with this (in linspire) and had to be taken step by step..if you have the patience to try and guide me step by step i'll have a go

---

### Post by Fully216 on 2006-09-12
No problem.  I don't mind walking you through it.  Did you install gnomad2 through the synapic package manager?  If so, it should have taken care of the dependencies issue.  The nice thing is that you can easily search for packages you need and even reinstall broken packages (as is the case with your installation).  

System > Administration > Synaptic Package Manager

Then enter your password.

Click search in the upper right hand corner.  Type in gnomad2 and click search.  This should bring up only one package.  The lastest version in the repos (which I have) should be 2.8.1-1.  right click on the source box and click mark for installation/reinstallation (which ever the case maybe depending on your previous install).

Notice this will tell you which package dependencies you don't have and install them as well, which is nice.  You can also look at the dependencies by right clicking and selecting properties.

If this does not work, let me know and we can do a manual install.  I would recommend SPM because it keeps track of what software you have installed on your system, which is very nice.

If you have questions, you can also see this comprehensive website ... 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by eggy1962 on 2006-09-13
sorry i haven't had a moment to try your instructions as yet, i will try when i get home from work tomorrow

---

### Post by Fully216 on 2006-09-14
Just let me know how it goes, otherwise I will give you the command line instructions.  Good luck!

---

### Post by omegamike on 2006-09-14
i had a similar problem recognizing my dell dj which uses the same drivers as the creative labs mp3 players. i found that when i ran gnomad2 as sudo, i could get it to recognize the device. Try hitting Alt+F2 and typing in "sudo gnomad2" to run the program.

---

### Post by slibuntu on 2006-09-14
If you still cant get Gnomad working, go to my blog and theres a link to a brilliant howto for creative players, by msak002. Its under "Essential Apps: Gnomad2" in the "Essential Apps" section

---

### Post by eggy1962 on 2006-09-14
right did as  was told....only gnomad2 file showed after the search so i went ahead and asked it to re install... try it after this re install still no luck  says  "no jukeboxes found on usb bus"
so as far as i can tell it installed ok but just not being recognised

---

### Post by eggy1962 on 2006-09-14
magic!!! followed slibuntus link and then did the install via mkir's instructions/download..(didn't go the full command line way...too much of a newb) and lo and behold  i can now see whats on my  zen...one slight hiccup is that i dont have a program header/icon to start it up...i had to do alt f2 and type in gnomad2 and  run... is there a  simple way i can get it to set up a quickstart header/icon?

---

### Post by Fully216 on 2006-09-15
I am assuming you want to add it to the applications menu.  To do that, just go to Applications > Accessories > Alacarte Menu Editor and add your program to the menu. Go the the part of the menu you want to add it to, then click file/new menu entry, and type the command that starts the program.  Usually all installed programs are located in your PATH (probably /usr/bin), so you dont have to know where exactly it is installed.  

Hope this helps and glad you got it working.  :-)

---

### Post by eggy1962 on 2006-09-15
sorted the listing...... a big thanks to all that helped me....i'm on holiday(vacation) for 2 weeks now so you will all have a bit of peace n quiet while i'm  away:D  i am pretty sure i will  find  some other problems along the  way as i get used to ubuntu

---

### Post by lfvsouza on 2007-07-28
Tanx fully for the answer, and eggy for the question ! lol.
I have a zen vision m and i just made it work using your step by step guide.
Important detail, eggy: remember to connect your zen BEFORE opening the gnomad2 software, and it will recognize it imediately.
Sucess !

---

### Post by jamieh on 2007-07-29
> **eggy1962 said:**
> Hello there. 
I have just installed ubuntu recently and have managed to do certain things  like setting up my spare printer,installing digikam to use my canon camera, sorted my email thru  evolution, but i have a couple of  questions i could do with some help with:-
1.is there a program that allows me to listen to shoutcast radio network
2. is there  any program that will allow me to use my creative zen vision m mp3 player. i have plugged it in but no response.
Thanks
Mark
For the MP3 player, I would recommend either Rythembox, Amarok, or Banshee. Banshee is most like iTunes, and the other two have alot more features.

---

### Post by eggy1962 on 2007-07-29
i am now able to use either g nomad or amorak.....preferring gnomad at the moment

---

