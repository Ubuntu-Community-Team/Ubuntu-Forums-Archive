---
title: "Suspend and Hibernate 100% working.....for me at least."
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by RangerDanger on 2007-07-18
I have been working with Feisty since Saturday and have never used any form of linux before.  I have to say I love it.  I am finding it very easy to work with and for some reason it is coming very easy to me.  For some reason anything I want to set up just come so easy to me, the figuring out why will take some time.  I am sure I will have problems it seems everyone does at some time.  So far I have found that most fixes are to complicated and a simpler approach is what works best.  That being said, I am using a Dell e1505 with an ati x1400 graphics card and only needed to delete one word in one file to get suspend and hibernate working 100% all the time including wakeup.  I will not take credit for this fix as it really is not mine, but it is part of at least 5 that I have seen.

go into /etc/default/acpi-support
change the line POST_VIDEO=true to read POST_VIDEO=.

To make this as easy as possible open the terminal and type, sudo gedit when gedit opens hit open and navigate to /etc/default/acpi-support .  The file will open, delete the word true from the line POST_VIDEO=true and put a period in its place.  Save the file and exit gedit, then exit the terminal.  Now suspend and hibernate should work, well at least it does for me.

---

### Post by strabes on 2007-07-18
Your keyboard and mouse might sometimes freeze upon wakeup. If that starts happening, check out [this page](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14).

---

### Post by RangerDanger on 2007-07-18
> **strabes said:**
> Your keyboard and mouse might sometimes freeze upon wakeup. If that starts happening, check out [this page](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14).

Actually haven't had any problems at all with this issue.

---

### Post by angryfirelord on 2007-07-18
RangerDanger, you are my hero! :KS I've been trying to get this to work for months.

Thank you very much! I can't believe how simple a fix that was.

---

### Post by RangerDanger on 2007-07-19
> **angryfirelord said:**
> RangerDanger, you are my hero! :KS I've been trying to get this to work for months.

Thank you very much! I can't believe how simple a fix that was.

You are very welcome, it is very simple.  In this case I think less is more is a good thing.  This is all I had to do and it works 100% all the time and brings up no other problems.  I can't believe how many threads on this issue are in the Dell forum and beginners forum.

---

### Post by Kallahorn on 2007-07-25
This seems to fix the suspend function, but when I try to hibernate, it fails and displays the following message: Hal failed to hibernate.

So anyone else seeing that?

Running Feisty on Dell e1505 with x1400, compiz-fusion & proprietary ati drivers.

---

### Post by strabes on 2007-07-25
That's not a video issue, it's a HAL one. This fix won't work.

---

### Post by angryfirelord on 2007-07-25
> **Kallahorn said:**
> This seems to fix the suspend function, but when I try to hibernate, it fails and displays the following message: Hal failed to hibernate.

So anyone else seeing that?

Running Feisty on Dell e1505 with x1400, compiz-fusion & proprietary ati drivers.
Some possible threads: [http://ubuntuforums.org/showthread.php?t=437115]("http://ubuntuforums.org/showthread.php?t=437115")
[http://ubuntuforums.org/showthread.php?t=197062]("http://ubuntuforums.org/showthread.php?t=197062")

---

### Post by benx009 on 2007-07-30
i have been having problems w/ hibernate/suspend for a long time!!!! i am so happy i found this thread!

---

### Post by CarVac on 2007-07-30
wait. Does this only work with ati or does it work with most cards?

---

### Post by ndinadis on 2007-07-30
I have tried many of the fixes for suspend, I have the same laptop as you. 
Can some one post the contents of the whole file for me so I can revert everything else back to original and only change the one value.
Thanks, Nick

---

### Post by T0MA on 2007-07-31
that didnt do the trick on my laptop.. after suspend i still get a blank screen and the wireless logo doesnt turn on either.. 
resuming from hibernate froze on me.. hmhm

---

### Post by apswartz on 2007-07-31
> **strabes said:**
> Your keyboard and mouse might sometimes freeze upon wakeup. If that starts happening, check out [this page](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14).

You know, I didn't have any problems for the first couple of days, then they started without having made any changes to the config files.

---

### Post by drumour on 2007-08-15
This is only a thank you,  but Thank You. I have been using ubuntu for nearly a year now and have tried everything short of a kernel compile to get this essential feature to work. This fix got it working on both my systems - both nvidia 7900 graphics but one a dual core intel extreme and the other an amd64x2. Fingers and everything else crossed that this is not lost when Gutsy comes on stream

---

### Post by notwen on 2007-08-15
I have the new Inspiron 1420n and suspend works w/o a hitch, but hibernate fails miserably, generally resulting in a total system shutdown. , anyone w/ another 1420n that is having better luck w/ hibernate?

---

### Post by kallistra on 2007-08-17
I was having the same issue too. Suspend worked perfectly but hibernate... good luck. My resolution was screwed up every time I resumed. I have 915resolution because I've the 17" wide screen Dell E1705. I couldn't find any resources that 'spelled' it out, so this is why I'm posting this. I'm hoping this will help others. I do not know if this will work on other systems with 915resolution, but this fixed both my hibernate and video issue in one shot. 

Here is what I did, my resources are here: 
[https://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T60.html#Hibernation](https://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T60.html#Hibernation)
and 
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Just in case my way doesn't go, you have a few more ideas.

Here are my steps.

```

sudo apt-get install hibernate uswsusp

sudo dpkg-reconfigure uswsusp

```

Stick to all the defaults when running the reconfigure, however I did set mine with checksum, early writeout, and compression. 

```

sudo cp /etc/uswsusp.conf /etc/uswsusp.conf.old
sudo gedit /etc/uswsusp.conf

```

Here's mine:

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda7
compress = y
early writeout = y
image size = 483503718
RSA key file = /etc/uswsusp.key
shutdown method = platform
compute checksum = y

```

What you're looking for above is that the resume device is the short path and not some long one. 

Next comes hibernate's part.

```

sudo cp /etc/hibernate/common.conf /etc/hibernate/common.conf.old
sudo gedit /etc/hibernate/common.conf

```

This is a fairly big file with several options. You want to find this location:

```

### hardware_tweaks
# IbmAcpi yes
# Runi915resolution yes
# FullSpeedCPU yes

```

Modify it like so...

```

### hardware_tweaks
Runi915resolution yes
IbmAcpi yes
# FullSpeedCPU yes

```

Why moving the Runi915resolution worked for me, I wish I was better at this to say. I'm just another newb trying to get along. All I know, is that it worked. I did a lot of other things up to this point, so it could be a superstition.

Continuing...

Since my only issue was with hibernate and not suspend. I'm going to modify my hibernate script so that I can use it with my power options and power down, and etc.

```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux-old
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

```

Locate the following line in the script:
```

#Other distros just need to have *any* tools installed

```

We're going to change the order of the if statements so hibernate is first. 

Old:
```

#Other distros just need to have *any* tools installed
else
	if [ -x "/usr/bin/powersave" ] ; then
	        $POWERSAVED_SUSPEND2DISK
		RET=$?
	elif [ -x "/usr/sbin/pmi" ] ; then
		/usr/sbin/pmi action hibernate force
		RET=$?
	elif [ -x "/usr/sbin/pm-hibernate" ] ; then
		/usr/sbin/pm-hibernate
		RET=$?
	elif [ -x "/usr/sbin/hibernate" ] ; then
		# Suspend2 tools installed
		/usr/sbin/hibernate --force
		RET=$?
	elif [ -x "/sbin/s2disk" ] ; then
		# uswsusp tools installed
		/sbin/s2disk
		RET=$?

```


New:
```

#Other distros just need to have *any* tools installed
else
	if [ -x "/usr/sbin/hibernate" ] ; then
		# Suspend2 tools installed
		/usr/sbin/hibernate --force
		RET=$?
	elif [ -x "/etc/acpi/hibernate.sh" ] ; then
		# acpi-support installed
		/etc/acpi/hibernate.sh force
		RET=$?
	elif [ -x "/sbin/s2disk" ] ; then
		# uswsusp tools installed
		/sbin/s2disk
		RET=$?
	elif [ -x "/usr/sbin/pmi" ] ; then
		/usr/sbin/pmi action hibernate force
		RET=$?
	elif [ -x "/usr/bin/powersave" ] ; then
	        $POWERSAVED_SUSPEND2DISK
		RET=$?

```

I purposely didn't remove anything. I only reorganized it. Anyways, that's my fix and my first one ever. :) 

If it works for anyone else as welll, feel free to let me know. :KS

Kallistra

---

### Post by rzrgenesys187 on 2007-09-12
Awesome, i've been working on this problem for a while now.  Thanks a million, now vista has nothing on ubuntu

---

### Post by angryfirelord on 2007-09-12
> **rzrgenesys187 said:**
> now vista has nothing on ubuntu
I know! Ubuntu suspends fine, but Vista can't do it. :p Seems the tables have turned...

---

### Post by kiloecho7 on 2007-09-15
You folks are awesome.  Editing the POST_VIDEO feature worked for me.  Running Gutsy on a Thinkpad x61s.

---

### Post by angryfirelord on 2007-09-15
This should be a sticky somewhere.

---

### Post by manzuk on 2007-09-16
Kallahorn Try this [http://ubuntuforums.org/showthread.php?t=471855&highlight=powersave](http://ubuntuforums.org/showthread.php?t=471855&highlight=powersave)

---

### Post by riven0 on 2007-09-18
Just wanted to say that RangerDanger is a genius. This worked perfectly for me. 

Lappy:

IBM Thinkpad R60 with an Intel Mobile 945GM integrated graphics card.

---

### Post by odelay on 2007-10-21
This fix does not work in Gutsy with the ATI x1400 (Dell e1505).

I can't really use my laptop much until this is fixed.

---

### Post by Kallahorn on 2007-10-21
Yeah, can't get it to work in Gutsy either (Dell e1505, ATI x1400) ...

Was working so nicely in Feisty though.  : /

---

### Post by Antman on 2007-10-23
> **RangerDanger said:**
> 
go into /etc/default/acpi-support
change the line POST_VIDEO=true to read POST_VIDEO=.


Doesn't work 
Laptop Specs:
IBM Lenovo T60 w/ATI X1300 video card

---

### Post by odelay on 2007-10-23
> **Antman said:**
> Laptop Specs:
IBM Lenovo T60 w/ATI X1300 video card

Interesting that it worked for an X1300 but not an X1400 in Gutsy...

---

### Post by Antman on 2007-10-23
> **odelay said:**
> Interesting that it worked for an X1300 but not an X1400 in Gutsy...

Oh wait... I just remembered that I just installed Ubuntu 7.10 again as a test and didn't get a chance to load the Restricted ATI drivers....:(
I'll load them and try again and see if it works.:-k

---

### Post by Antman on 2007-10-23
Ok, just loaded the restricted drivers and it doesn't work. Jeez... the ATI drivers stink. My next laptops will only be Nvidia cards.

---

### Post by odelay on 2007-10-23
I don't know whether to be happy because I wasn't doing something wrong all this time or to be sad that no one's got it working.

Oh.  Right.  

It's the latter.

---

### Post by aaaantoine on 2007-11-09
Suspend to RAM *mostly* works, both with Ubuntu's built-in suspend action and with uswsusp.  However, I cannot resume from either, so they're both useless to me.

Ubuntu's built in suspend shuts everything down and the screen goes black, but the green power light remains on.  uswsusp shuts a few things down, and the power light even changes to a flashing yellow.  But, a blinking cursor remains on the screen, and the system still responds to the Caps Lock key and USB activity.

Ubuntu 7.10 AMD64, Acer Aspire 5050-5554, Radeon Xpress 1100.

---

### Post by pwn on 2007-11-10
Works on Gutsy + nVidia card

But there're a few problems.

1. Upon resume, there is no audio
2. It works only once. I cannot hibernate again until I reboot.

---

### Post by wonder76 on 2007-11-10
works ok on gutsy (also sound)

dell 9300, nvidia 6800go

suspend works also many times (not only once) without reboot

---

### Post by Portable_Jim on 2007-12-18
> **RangerDanger said:**
> I have been working with Feisty since Saturday and have never used any form of linux before. I have to say I love it. I am finding it very easy to work with and for some reason it is coming very easy to me. For some reason anything I want to set up just come so easy to me, the figuring out why will take some time. I am sure I will have problems it seems everyone does at some time. So far I have found that most fixes are to complicated and a simpler approach is what works best. That being said, I am using a Dell e1505 with an ati x1400 graphics card and only needed to delete one word in one file to get suspend and hibernate working 100% all the time including wakeup. I will not take credit for this fix as it really is not mine, but it is part of at least 5 that I have seen.

go into /etc/default/acpi-support
change the line POST_VIDEO=true to read POST_VIDEO=.

To make this as easy as possible open the terminal and type, sudo gedit when gedit opens hit open and navigate to /etc/default/acpi-support . The file will open, delete the word true from the line POST_VIDEO=true and put a period in its place. Save the file and exit gedit, then exit the terminal. Now suspend and hibernate should work, well at least it does for me.

I had given up hope for getting suspend to work on my computer. This looked like hope, however resume did not work.

If i suspend when I resume it gives me the following message:
```
 RADEON 9000 113-dh-84911p02334 CH-A BIOS 250/200
```which is the exact text found [here.]("http://www.techpowerup.com/vgabios/226/ATI.9000.128.Hynix.030323.html") I know that this is some sort of bios problem, but do not know how to fix it.

So there will be no suspend for me.:sad:

---

### Post by OlyPerson on 2007-12-18
Ok, big noob question here...
So I go into the acpi-support file in gedit and then change it and save.  However, when I try to save it says I don't have permission.  How do I get permission outside of the CLI?

EDIT: Never mind!  I got it, I just had to open it by using the terminal using sudo gedit acpi-support

EDIT2: Ok, so it can now come back from suspend, but then the internet doesn't work.  Anyone have a fix?

---

