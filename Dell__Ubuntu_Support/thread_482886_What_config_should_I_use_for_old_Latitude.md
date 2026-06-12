---
title: "What config should I use for old Latitude?"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by JimGvo on 2007-06-24
I have an old D300XT Dell Latitude laptop that is currently running SuSE 9.3.  I'm not happy with Novell so I'm going to upgrade it to another distro.  Ubuntu seems like a likely choice.  It only has 128Mb of memory.  I think that's all it can hold unless you want to purchase memory from Dell, which costs more than I paid for the laptop 5 years ago.

So what configuration would be best for this limited memory, slow laptop?  It's a general purpose system and isn't used for games or video or even playing audio.  I may compile a program or two or browse or edit files/openoffice etc.

Thanks,
Jim.

---

### Post by apel_2804 on 2007-06-24
With 128mb ram you should use xubuntu!

---

### Post by kmangwing on 2007-06-24
I've got a Latitude C600.  It didn't come with an OS, so I used Ubuntu for a while, but that was extremely slow, and when I did an install form a 7.04 disk, it would take a long time and have screen resolution errors.  I had to download, burn, and install 6.10 in order to have it be problem free.  I was then able to upgrade to 7.04.  But the only thing is, it was still extremely slow.  So, I tried Xubuntu, and it worked extremely well.  It boots up really fast, it looks really nice, and I can run every GNOME program I've tried.  There are only a couple of problems.  The first is that Ubuntu doesn't fully support my graphics card (which may not affect you), so whenever I try to run anything that takes over the screen (like most games), I get duplicate sections of the screen, parts that still display the desktop, etc.  The second problem is that Xubuntu doesn't have a very good wireless network manager by default, unlike Ubuntu.  This is easily solved by installing GNOME's Network Manager applet.  If you want to do that, you need to go [here]("http://ubuntuforums.org/showthread.php?t=448952"), and read Belathor's post.  It tells you how to fix startup problems with the applet.  But other than those two problems, everything has been fine.  Since you have such low ram, I think you need to use the alternate install cd.  I think you'll like Xubuntu.  I know I'm sticking with it. 
Something ironic, in order to get the Ubuntu 6.10 cd to install, I had to install windows xp.

I hop this helps.

---

### Post by caro on 2007-06-24
> **apel_2804 said:**
> With 128mb ram you should use xubuntu!

Agreed!

---

### Post by Tethtibis on 2007-06-26
I agree on the agree! lol :p

---

### Post by JimGvo on 2007-06-29
Thanks to all the agreers, if there is such a word.  Xubuntu went in fine.  Ubuntu didn't want to install.  

However I have two issues.  The first is that it never offered an option to tell it I my hardware clock was on local time.  Also I searched all over for a method of telling it that after the fact and the only things I found referenced were not applicable.  For instance a number of sites suggest changing a value in /etc/sysconfig/clock but that doesn't exist.  Another suggested right clicking the clock and selecting "adjust ..." but there is no such option.  

Whats a fellow to do since I run this on Win98 also.

Second, it didn't seem to sense my laptop screen size, hence I have this 1 - 1.5 inch border around the screen.  That's a lot of real estate on a screen this small to lose.  How can I get it to use the rest of the screen?

Thanks,
Jim.

---

### Post by mysticrider92 on 2007-06-29
For your first question, I think that you need to go into the settings manager to change your time settings. I don't use XFCE, so I couldn't tell you how to do this.

For the second question, I would go into Windows, right click the desktop and choose "display". On the settings tab, it should show the screen resolution. Write down the numbers displayed there. Boot into XUbuntu. Type "sudo mousepad /etc/X11/xorg.conf" in a teminal (in the applications menu). Scroll down almost to the bottom and look for a line that says: Section "Screen". On this section you will see something like this (don't copy it, it is probably not right for your screen:
> 	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1024x768"	"640x480"
	EndSubSection
The "Modes" tag is what you want to edit. Add a resolution in front of the first listed (in my case, 1440x900) and put the resolution numbers you got from Windows there, in the same format as the others in the file. For example, to add 1280 by 800 as a resolution, you would put "1280x800" in front of "1024x768" (most likely what is listed on yours if you have the gap).

I am fairly sure that is the problem, since you have a laptop with an lcd.

---

### Post by terry98 on 2007-07-07
Well i currently own a HP Omnibook XE3 Original Specs: 10GB, 64mb ram, Win98SE. i upgraded to 128mb and tried xubuntu either way it was pretty slow.. and added another 25mb dimm no w i use ubuntu feisty with 80gb and 384mb ram and i dont have any complains at all, if u can upgrade that ram of yours u should do it..

---

