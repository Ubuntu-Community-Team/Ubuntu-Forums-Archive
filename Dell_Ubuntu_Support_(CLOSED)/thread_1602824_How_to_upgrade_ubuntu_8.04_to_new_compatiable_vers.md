---
title: "How to upgrade ubuntu 8.04 to new compatiable version"
date: 2010-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chitragurung on 2010-10-21
I have been using Dell Inspiron Mini 10 with Ubuntu 8.04 Hardy Heron released in April 2008. This is with me since last year, brand new and nothing made change in operating system. Now I am really want to upgrade ( if possible automatically and without loosing data ). How can I upgrade it to next compatiable version from above ?
 
For the fresh installation, very few people use linux and no people available to do so.
 
Your recommendation is highly appreciated.

---

### Post by RedSingularity on 2010-10-21
You can do so from a terminal or a nice interface.  I assume you would like the interface.  Go to System>Admin>Update Manager.  See if it gives you an option to upgrade to another distribution.  In your case probably 8.10

---

### Post by chitragurung on 2010-10-21
**I found the following from Ubuntu website. When I try to go Software properties, I could not find instead there is Software sources**
 
**Upgrade from 8.04 LTS to 10.04 LTS**
 
 
**Network Upgrade for Ubuntu Desktops (Recommended)**
 
 
 

You can easily upgrade over the network with the following procedure.[LIST=1]
[*]Start System/Administration/Software Properties
[*]On the **Updates** tab, set **Show new distribution releases:** to **Long term support releases only**, then press **Close**.
[*]Press Alt-F2 and type update-manager
[*]Click the **Check** button to check for new updates.
[*]If there are any updates to install, use the **Install Updates** button to install them, and press **Check** again after that is complete.
[*]A message will appear informing you of the availability of the new release.
[*]Click **Upgrade**.
[*]Follow the on-screen instructions.
[/LIST][https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by RedSingularity on 2010-10-21
Those instructions are fine.  Thats exactly the procedure.  Software sources is Software properties by the way.  Go to software sources and follow from there.

---

### Post by chitragurung on 2010-10-21
I went to software sources, there is three tabs, Update, 3rd party software, authentication.
 
In the Updates 
Automatic updates
check for updates- then there are options like daily, weekly etc
Also has click options 
download all updates in the background
only notify abourt available updates
 
After saving those option, and gone to update manager, it says system is uptodate.

---

### Post by RedSingularity on 2010-10-21
Under all that there should be RELEASE UPGRADE.  You sure there is nothing there?  Cant scroll down?

---

### Post by chitragurung on 2010-10-21
Scroll down has only those options
 
Daily
Every two days
Weekly
Every two weeks

---

### Post by RedSingularity on 2010-10-21
What does this command give you?

sudo do-release-upgrade

---

### Post by chitragurung on 2010-10-21
it says no new release found

---

### Post by RedSingularity on 2010-10-21
Try this in terminal and see if you get the RELEASE UPGRADE option in the bottom of the window.

gksudo software-properties-gtk

---

### Post by chitragurung on 2010-10-21
It does like this and open software source properties window and there is no changes. Shall I restart  my system ?


chitra@chitra:~$ gksudo software-properties-gtk

(software-properties-gtk:5646): libglade-WARNING **: unknown property `orientation' for class `GtkVBox'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(software-properties-gtk:5646): libglade-WARNING **: unknown property `orientation' for class `GtkVBox'

(software-properties-gtk:5646): libglade-WARNING **: unknown property `orientation' for class `GtkVBox'
chitra@chitra:~$ 
chitra@chitra:~$

---

### Post by RedSingularity on 2010-10-22
You can restart if you like.....I am posting a picture of what the window should look like.

[IMAGE HERE]("http://postimage.org/image/7ttcrpg/")

See if you are missing an option there.[IMG]http://postimage.org/image/7ttcrpg/[/IMG]

---

### Post by chitragurung on 2010-10-22
[IMG]http://egtours.com/images/Screenshot-3.png[/IMG]no like that same as before nothing changed.

---

### Post by RedSingularity on 2010-10-22
Very interesting.  Did you buy the netbook with Ubuntu installed?

---

### Post by chitragurung on 2010-10-22
Yes. I was using Dell Inspiron 6400 before with windows. Last year I bought new one and came with ubuntu.

---

### Post by RedSingularity on 2010-10-22
I see.  Seems like Dell disabled that feature.  Probably for warranty reasons.  They sold you a netbook with _***Hardy Heron ***_and they want it to stay that way in case you ever call for support.

---

### Post by chitragurung on 2010-10-22
So, How can I solve this problem ?

---

### Post by RedSingularity on 2010-10-22
I would suggest a fresh install of the newest distribution.  Of course using a flash drive to install since there is no CD drive.  And above all, with a install you did yourself, you know there is nothing "taken out" that you will not be able to use!  Whenever I get a new computer I wipe it and do my own fresh install of an OS.  Of course this voids their warranty.

---

### Post by chitragurung on 2010-10-22
How to restore my current data ? Fresh means, I override in the current or remove all, and install new one ?

---

### Post by RedSingularity on 2010-10-22
Fresh means you install a brand new ubuntu.  You can save your home directory though.  Pictures, music, movies, Documents, etc.... will be saved.  Even things like firefox bookmarks will save.  What will not save are programs you have installed.  You will need to reinstall those programs.

---

### Post by chitragurung on 2010-10-22
SO it means first I save all my files in the external drive and install new ubuntu ie 10.04 or Just override on current setting ?

---

### Post by RedSingularity on 2010-10-22
You save all wanted files to external Hard Drive and then install new 10.04 which will erase ALL data currently on the disk.  (Note:  You will also need a USB pen drive to install 10.04)

PS:  If you are uncomfortable with this please know that it is not necessary yet.  You system will be supported until April of 2011.

---

### Post by chitragurung on 2010-10-22
Thank you very much for your support. I will work out accordingly. But after April will it upgrade automatically ?

---

### Post by RedSingularity on 2010-10-22
That is a good question.  I am not sure how dell set it up but it may work that way.  They may have locked it until the due date.  I really honestly dont think so but you never know.  If you choose to do the fresh install of 10.04 there is an excellent guide [here](https://help.ubuntu.com/community/Installation/FromUSBStick) explaining how to do it.  And of course feel free to come back with any questions.  :)

---

### Post by chitragurung on 2010-10-22
I surfed around Dell site and has same problem with others

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19349601.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19349601.aspx)

I will follow your guidance. 

Thank you so much for your prompt responses for my inquiries.

---

### Post by RedSingularity on 2010-10-22
Happy to help :)

---

### Post by chitragurung on 2010-10-22
One more question, when I install fresh which one should I install 10.04 or 10.10 ?

---

### Post by RedSingularity on 2010-10-22
10.04 has support till 2013 since it is a long term support version.
10.10 has support until 2012.

I would go with 10.04  Thats what I will be using for the next 3 years and there is not much difference in 10.10 in terms of applications anyway :)

---

### Post by ugm6hr on 2010-10-23
As you've discovered, the Dell 8.04 cannot, and will likely never, be allow upgrades, since it is a lpia (not i386) version.

I have a Mini 9, and would suggest 10.10 if you use Suspend. 10.04 would not suspend correctly if you had an SD card mounted at the time of suspending.

Other than a minor nuisance with the initial wifi driver installation - [http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html) - which is easily fixed (and also affects 10.04) - it appears to work flawlessly.

I am using the Desktop version (i386), and have removed 1 panel, and enabled the "Show Hide Buttons" options on the remaining 21 pixel panel, to allow full use of the screen.

Compiz also works fine with the basic settings, which allow the "Expose"-like showing of all open windows (Super+A shortcut).

---

### Post by TheNewKid on 2010-11-23
I've had the same issues as chitragurung - I have the same pre-installed Hardy Heron release - and so have found this thread really useful except for the fact that I can't create a bootable usb.  I've followed the instructions and run the command in the terminal, but can't find where the program has gone.  How can I run it / find it?  It doesn't appear in 'System' or 'Applications'.

Help greatly appreciated...

---

### Post by ugm6hr on 2010-11-23
You cannot easily create a bootable USB from the pre-installed 8.04 from Dell.
I would suggest trying to create it on another computer - any Windows or other Ubuntu computer will work.

---

### Post by fjgaude on 2010-11-23
Has anyone tried using the ubuntu-10.04-dell_A00.iso to upgrade a mini 10 or 10n that has 8.04 on them?

---

