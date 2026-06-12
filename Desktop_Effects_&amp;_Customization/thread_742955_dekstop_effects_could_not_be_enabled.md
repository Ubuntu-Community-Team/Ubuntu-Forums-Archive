---
title: "dekstop effects could not be enabled"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by zenithlt on 2008-04-02
i have hd 38550 256mb and i cant run desktop effects what to do i`m new in Linux
[[IMG]http://img186.imageshack.us/img186/9306/screenshotzn5.th.png[/IMG]](http://img186.imageshack.us/my.php?image=screenshotzn5.png)

---

### Post by GOROSSI on 2008-04-02
Firstly Do you Mean HP as in Hewlett Packard

secondly is it a laptop or desktop and

is 256MB your total system RAM or the Graphics memory 

thirdly 

how old is the machine?

---

### Post by zenithlt on 2008-04-02
> **GOROSSI said:**
> Firstly Do you Mean HP as in Hewlett Packard

secondly is it a laptop or desktop and

is 256MB your total system RAM or the Graphics memory 

thirdly 

how old is the machine?

u mean my pc ? i bought PC before 2 moth its not a lap top, i have 4gig of ram, radeon hd 3850 256mb vga, dual core athlon  x2 5600+ :guitar:

---

### Post by GOROSSI on 2008-04-02
> **zenithlt said:**
> u mean my pc ? i bought PC before 2 moth its not a lap top, i have 4gig of ram, radeon hd 3850 256mb vga, dual core athlon  x2 5600+ :guitar:

Ok I guessed that you had spelled HP wrong sorry.

It seems to me like a driver Issue 

I have looked on the ATI site[http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html") 

unfortunately it seems that Linux drivers aren't currently available for the card from ATI themselves it Only lists the older 2000 series under the both X86 and X86_64 Linux tabs.

As the card is very new I am sure drivers will come out for it within the next couple of months as Linux is nearly always last unfortunately as there are less users. 

you can try a couple of things though Presuming Your Running Ubuntu not Kubuntu (has a Blue Logo on the Boot screen and Uses KDE instead of GNOME for the desktop.)

one:
Go to System, then Administration and click on "Restricted Drivers Manager" It will tell you if you need any closed source drivers are available for your system which ATI's are not open source I think.

If it says that there are non available for your system do the following:
Go to System, then Administration and click on "Screens And Graphics" the click on the Graphics Card Tab then click on the Driver box closest to the Tab and tell me what it says or give a screenshot and we can go from there If you can't see all the text you can resize the window.

Please note it will definitely say Radeon in the driver list but don't choose unless it's already there as the installed driver as it's probably to old for your card as choosing the wrong driver can corrupt your system as I found myself .
Be sure to click **cancel** and not OK on the dialog box when finish so any mistaken changes that are done are not saved.

I can't promise anything but I might be able to help find a workaround until ATI release the drivers for the card. 

By the way are you dual booting with Windows As you could experiment with different drivers and scrub the install if it goes wrong.

Sorry for the long post but it will save a lot of problems


Hope this helps.

---

### Post by joecool362 on 2008-04-02
Okay what is your OS, Fiesty, Gutsy, our the Beta of Hardy
That Would help alot. Also what desktop enviroment r u using and what is the error message? Also if u r using gutsy just wait for hardy, the desktop effects work much better right out of the box.

---

### Post by zenithlt on 2008-04-02
here is a screen of that drive box... so whats now ? what should i do ? 
[[IMG]http://img516.imageshack.us/img516/6281/screeneu5.th.jpg[/IMG]](http://img516.imageshack.us/my.php?image=screeneu5.jpg)

---

### Post by zenithlt on 2008-04-03
heeeeeeeelp

---

### Post by zenithlt on 2008-04-03
please gimme some help ;x

---

### Post by GOROSSI on 2008-04-03
Just looked at the screen shot I take it your running Ubuntu studio and not just the theme?

right anyway looks like your system is loading a generic driver if you can post the contents of the file **xorg.conf** file I can take a closer look for you It's located here: **/etc/X11/** under your ** file system**  under "Computer" in "Places" which is the Linux equivalent to Windows C:\

It will open with Gedit the GNOME text editor copy and paste the contents on here then I can have further info on what to do about a fix as from the screen shot it doesn't look promising if that's the driver thats loaded sometimes the dialog can be wrong.

sorry for the long wait I'm in the UK I'm guessing your not

---

### Post by zenithlt on 2008-04-03
> **GOROSSI said:**
> Just looked at the screen shot I take it your running Ubuntu studio and not just the theme?

right anyway looks like your system is loading a generic driver if you can post the contents of the file **xorg.conf** file I can take a closer look for you It's located here: **/etc/X11/** under your ** file system**  under "Computer" in "Places" which is the Linux equivalent to Windows C:\

It will open with Gedit the GNOME text editor copy and paste the contents on here then I can have further info on what to do about a fix as from the screen shot it doesn't look promising if that's the driver thats loaded sometimes the dialog can be wrong.

sorry for the long wait I'm in the UK I'm guessing your not

I`m from Lithuania ;x can u explain more cuz i`m new in Linux and i don't understand..
xorg.conf and /etc/X11/  i have put these to Terminal ?  if i have than  

```
kompas@ubuntu:~$ xorg.conf
bash: xorg.conf: command not found
kompas@ubuntu:~$ /etc/X11/
bash: /etc/X11/: is a directory
kompas@ubuntu:~$ 
```

Your`e really trying to help me but please explain more about details, where, what and how... Thnx up. U :guitar:

---

### Post by GOROSSI on 2008-04-03
No sorry my fault :( 

I should have explained it better sorry didn't think about using terminal as I have cerebral Palsy and can't type very well so I avoid the command line like the Plague so I tend to give other's instructions as what I would do.
[B]
Copy and Paste[/B] this command: gedit /etc/X11/xorg.conf

into terminal and you will get the file that you need to copy and paste to this forum

It will open the file in the text editor on your computer

then Choose "Edit", "Select All" then "copy" then paste it into your post

---

### Post by lightchaser on 2008-04-03
I'm having the same problem, if your running Gusty try

Sudo gedit /etc/X11/xorg.conf

---

### Post by GOROSSI on 2008-04-04
> **lightchaser said:**
> I'm having the same problem, if your running Gusty try

Sudo gedit /etc/X11/xorg.conf

You don't need sudo unless your going to edit and save the file which is ill advised unless you know what to put in it

---

