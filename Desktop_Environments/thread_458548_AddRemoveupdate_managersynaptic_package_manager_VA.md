---
title: "AddRemove/update manager/synaptic package manager VANISHING"
date: 2007-05-29
forum: Desktop Environments
---

### Post by RedGecko on 2007-05-29
Hey I'm fresh in this Ubuntu world, so replies with baby-steps would be most appreciated.

 I think I've managed to screw up my computer. Don't know what's wrong with it. When I try to open Add/Remove Applications, Update Manager or Synaptic Package Manager, the program starts to load up normally then simply vanishes without so much as an error!

The last time I successfully opened Add/Remove Applications was when I added Krita to my applications.  I thought it'd be okay because I was reading up on art programs and the people were saying it's ok to put KDE applications into Gnome. Is that where I messed it up?

When I opened Krita to test it out it worked alright, so I don't know what the problem is.
Just before I added Krita I was researching instructions to make my Wacom tablet work. Could that be the problem? The tablet works both with The Gimp and Krita just fine.

Attached is an image of the program in the process of vanishing.
Other than those three things not opening my system is completely stable (I hope)

I'm so lost :(

---

### Post by aysiu on 2007-05-29
Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo gnome-app-install
``` and then paste back here any error messages you might get?

---

### Post by RedGecko on 2007-05-29
> **aysiu said:**
> Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo gnome-app-install
``` and then paste back here any error messages you might get?

jessica@Pookie:~$ gksudo gnome-app-install
warning: could not initiate dbus
** (gnome-app-install:14994): WARNING **: return value of custom widget handler was not a GtkWidget
jessica@Pookie:~$ 


<-- That is what I get. Thanks for the response!

---

### Post by aysiu on 2007-05-29
Hm. [a Google search on that error turned up a few results](http://www.google.com/search?num=100&hl=en&safe=off&q=%22return+value+of+custom+widget+handler+was+not+a+GtkWidget%22&btnG=Search). I didn't see any definite step by step instructions for fixing the bug, but one bug report seemed to indicate that a patch had been released and updating certain software packages might fix the error.

Can you try this? ```
sudo apt-get update && sudo apt-get dist-upgrade && gksudo gnome-app-install
``` Please post the output of that command. Thanks.

---

### Post by RedGecko on 2007-05-29
My output:
(Yay I figured out how to box it!)
```
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Segmentation fault (core dumped)

```

Thanks!! :D

---

### Post by RedGecko on 2007-05-29
I have some semi-good news! It now takes longer for the program to vanish! It was instantaneous and now it takes a good count to 1.5 second.

---

### Post by aysiu on 2007-05-29
Hm. Found out you're not alone:
[https://answers.launchpad.net/ubuntu/+question/6872](https://answers.launchpad.net/ubuntu/+question/6872)

Can you try pasting these commands into the terminal and then pasting the output back here? ```
sudo rm -f /var/cache/apt/*.bin
sudo apt-get update
sudo apt-get dist-upgrade
gksudo gnome-app-install
``` Each line is a separate command that should have the *Enter* key pressed afterwards.

**Warning**: *paste the commands* in. Do not retype the commands, especially that first one. If you mess up typing that first command, you can accidentally delete your entire installation. **Paste**. Do not retype.

---

### Post by RedGecko on 2007-05-29
Wow... I don't know what happened. 
I did EXACTLY what you told me to. I pasted the commands instead of retyping them. I pressed enter after every one just like you said.
When I put in the first one, it asked for me passcode, so I entered it. I entered the second one, and everything flowed smoothly.
I entered the third one and it went through a whole bunch of rapid text, then my entire system froze. No mouse, no keyboard, no hard disk responce, nothing. I waited to see if the problem would work itself out, but after 15 or so minutes I had to force-reboot the computer.

I came back to give it a second shot, again the first asked for a passcode, and this time the second gave me an error after a bunch of rapid text flow.
My error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
I typed in dpkg to see what it was, and it gave me a few descriptions of commands I could type in.
I decided there that it wasn't worth it to futz around by myself, so I opened firefox to come back to the forum to ask for help. I got to the forum, then tried to log in. Firefox vanished. I opened it again and tried again, it vanished at the log in again. I figured my system might need to reboot or something, so I shut down, and restarted my computer.

When my computer loaded back up it gave me a few options. You see, I have two hard-drives. The master has ubuntu, the slave drive has Win-XP (which is the only reason I am able to type this right now.)

Usually my computer gives me four options at start-up, but this time gave be two new ones also.
Usually I have
an ubuntu option, a recovery ubuntu option, memtest option and windows XP option.
this time I had two different things for ubuntu and two different recoveries!
One was called 
Ubuntu, Kernel 2.6.20-16 generic
the other was
Ubuntu, kernel 2.6.20-15 generic

I selected the one with 15, and it loaded nothing but a black screen with misc text and a place to type (though nothing I typed did anything. It simply showed what key I was pressing.)
I rebooted and selected the 16, and it loaded a screen that looks exactly like the terminal, only that's all. 
I figured since I don't know enough about the terminal I'd come back to that later.
I rebooted and selected the 16 recovery, it went through a whole bunch of sequences and ended up on a red, blue and grey screen with a whole bunch of weird symbols and some readable text...
I could not understand what most of it said, but the parts I could read were talkiong about problems witha  kernel for nvidia (my graphics card) ??????

I'm so incredibly lost now, I am on my XP drive right now because my ubuntu is royally confusing me...
I don't know what I did wrong, but I was able to save all my files off ubuntu and onto XP with a program called explore2fs.

[SIZE="4"]**I know I typed a speech, but my final idea is to just scratch off ubuntu and reinstall it. Do you think that is best?**[/SIZE]

---

### Post by aysiu on 2007-05-29
Hey, I'm as lost as you are. Yeah, I think your best bet is a reinstall. I honestly don't know what happened.

---

### Post by RedGecko on 2007-05-30
Thank you for all your help! I'm going to reinstall ubuntu tomorrow after work. I was wondering what you think started the problem to begin with.
Actually I just realized I failed to mention another thing that was happening when the original three programs wouldn't stay open.
I lot of the time I'd be using firefox and it'd just vanish for no reason also. Like it crashed, but never gave an error. I'd start firefox back up and it'd ask meif I wanna start new or go back to the page I was viewing when it crashed.

It didn't bug me when it didn't hapen a lot but right around the beginning of these posts it was crashing more and more. It didn't bug me TOO much cause every time it crashed I could open it back to where I was anyways, but it was still a pain. Any idea what could of been causing that?

Thank you again for all your help!!

---

### Post by aysiu on 2007-05-30
When I searched for your error, I saw that at least a few other people experienced the same problem, but most of the results were in bug reports with no solution and no explanation of the cause. So it is a real problem, and unknown problem, but a rare problem.

In other words, I have no idea what caused this problem.

---

### Post by evilc on 2007-05-30
> **RedGecko said:**
> My output:
(Yay I figured out how to box it!)

[/code]Thanks!! :D

I had a similar thing no answer why ended up reinstalling missing progs, Looks like a complete reinstall for you.
Slightly off topic could I ask how you managed to box your outputs? I have been trying to remember since v6.10 failed me and reloaded.

---

### Post by aysiu on 2007-05-30
Box it like this (see attached screenshot).

---

### Post by evilc on 2007-05-30
> **aysiu said:**
> Box it like this (see attached screenshot).

Thanks,

---

### Post by hellmet on 2007-05-30
I had a similar problem once , long time ago. Mine happened coz I completely broke my system, trying to learn too many things all at once. IMO, its just the case of a broken system. Sad.

---

