---
title: "gnome wont load - wrong screen resolution"
date: 2009-05-22
forum: General Help
---

### Post by blank bank on 2009-05-22
I can't get gnome to load.  

:cry:

I only have one monitor and am using ubuntu 8.10.

I was using ubuntu yesterday and changed the monitor resolution to something my monitor didn't support.  It turned all fuzzy, so I pressed escape.  My mistake!  I guess the escape key means save permanently.

Here's where I am today:  I can boot ubuntu and get to the login screen.  It appears at my monitor's native resolution.  However, when I type in user and password it changes resolution and won't work.  I tried all of the other options and all others fail except I can get the command line working.

If you can help me get this working I promise I won't ever try to change the screen resolution again!

---

### Post by gradysghost on 2009-05-22
Can you tell us what video card you have?  If you don't know, run this command and post the output:

```
lspci | grep vga
```

What is your monitor's native resolution?  What resolution did you try that broke it?  Can you post the file /etc/X11/xorg.conf ?

I could be wrong, but screen resolution is a global setting, is it not?  Does anyone else want to pipe in?

---

### Post by gradysghost on 2009-05-22
I'm sorry.  Turn "vga" into "VGA".  It's case-sensitive.  Like this:

```
lspci | grep VGA
```

If you can't get to a terminal emulator through the standard method in Gnome, you can hit Ctrl+Alt+F2 and log in on the actual terminal.  This should always work despite screen resolution issues.

If you need a command to output directly to a file, you can use the right angle brace (greater than, >) like this:

```
lspci | grep VGA > output.txt
```

I don't know what kind of config you've got running, so I don't know what works best for you.

---

### Post by blank bank on 2009-05-22
The monitor is a wide screen model 16:10 ratio.
Native resolution 1440x900.

---

### Post by blank bank on 2009-05-22
Okay, I'm on a separate computer... What part of the configuration file should I change

---

### Post by blank bank on 2009-05-22
Heres the output of the lspci | grep VGA file:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by blank bank on 2009-05-22
the file
/etc/X11/xorg.conf

is completely blank

---

### Post by oldefoxx on 2009-05-22
I learned something important from my Dad when I was in my young teens.  He was a design electronics engineer with Raytheon out in California, working on a program envoiving missiles.  I was with him in the labs one day, and he was trying to keep me entertained.  So he showed me something and told me something that was so important that I have never forgotten it.

He showed me the uncovered head of a missile and asked me if the displayed circuit boards looked the same.  I said that two did, but not like the third.  He said that all three did exactly the same thing, but the third wad different because it had to fit into a smaller space.  There were some vacuum tubes on each board with spring clips to hold them in place, so this was back before transistors came along.

Anyway, I wanted to know why three if they just all did the same thing.  He said that the missile flew very fast, and had lots of vibration, and the tubes or boards might get damaged.  So to deal with this, they designed three boards instead of just one.  I asked, why not just two?

He said, with just two circuits, if one disagreed with the other, you would not know which one was right.  But with three, you had a majority rule.  As long as two agreed, it would still fly and go where it was aimed.

That has really stuck with me all my life.  I rarely settle for trying something just once, or even twice, but go at it three times.  I even partition my hard drive so that I can do three installs of the same OS and applications, so that if one goes wrong, I have the knowledge and experience of also doing the other two to help me get that one right.

Now yesterday, I was finishing setting up my third install of Ubuntu 9.04 on its own partition, and no matter what I did, I could not lock in the settings for the Nvidia 180 deb file.  Sure, it was in there okay, but I would move it from Auto to a lower setting (aging eyes, you know), and try every method I researched online on how to make it permanent, but on reboot, it kept going back to the auto setting, which makes the text way too small for me to look at.  Nothing would take.

So know what I did today?  I set the sudo -s mode in a terminal consode, then did an gedit /etc/X11/xorg.conf file.  Now the X11 is the graphical tool being used to display just about everything, and this is where the settings have to end up at.  Looked fine as far as it went, so what was wrong?

The trick was to compare these settings with those of a similar file that one of the working partitions had on it.  So I left this open, but went back to the toolbar, and under Places, I mounted the other partition.  Then I went to that partition, went to its version of /etc/X11/xorg.conf, and brought that up in a text editor.  Then I put the two opened views of the files side by side, and began a comparison.  What I found is that the bad version had somehow missed out on recognizing the wide screen monitor I use, so what i did was take the missing or wrong sections, and used a copy-and-paste method to make the two files agree.  I saved the modified version, rebooted, and everything was fine.  In fact, as root (or super user), I could have just taken the right version from one partition and overwritten the wrong version on the root partition, but this way I could see what went wrong and correct it on the fly.

Now you are going to say, "Yeah, that worked for you, but I can't even get my desktop to open up!  So how does that help me?"

Isn't it obvious?  This was only your first attempt.  You need at least one more, maybe two.  They don't have to necessarily be on the same drive, or even the same PC, but once you get one to go right, you are in a position to try and figure out what is wrong with the first one.

Of course you could just start over and try again, but if you end up back at the same point, what have you gained?  Nothing but the realization that you have now failed twice,

Now a second drive or partition is a good idea, but most PCs are so different that succeeding with another one is not a guarantee that you can get back to the first one and then find and fix what is wrong.  In other words, my Dad's bit of wisdom imparted still holds up after all this time.  Even in small groups, majority is one of the best rules out there.  I hope this helps someone.

---

### Post by blank bank on 2009-05-22
This is just too time consuming to continue with...

I'm a C++ programmer and need my computer to just function -- I just want to be a programmer and not a system administrator.  Doestt it seem strange that simply changing the screen resolution will completely break X11?

Here's the steps I used to solve the problem.

Step 1. Backup data
Step 2. Format hard drive 
Step 3. Install Slackware

---

### Post by gasto on 2009-05-22
I must admit that dealing with Ubuntu's drivers is a pain in the **s .

I am still having problems.

---

### Post by oldefoxx on 2009-05-23
I had my own issues to resolve today.  Last night I went to bed, thinking that I had all three partitions function as I intend for them to do.  But then I thought of a few more things.

First, majority rule (2 to 1) can work if the two are doing what you want.  But if not, or if only looking at 1:1 cases (1 seems right, the other then is wrong), you add another factor, which is human judgement and discernment.

You can even have cases where two efforts indicate that something cannot be done, but the other proves that it can be, and there you reject the 2:1 rule outright.  So the majority rule is not an absolute or indication of perfection.

Another thing is that you do have some added options when bringing up the system from a LiveCD.  There is no rescue mode as suggested (an apparent bug in the install process), but you can put the choice on one of the lines, then hit the Esc key.  That gives you the choice of leaving the graphical boot mode amd emteromg tje Text Mode Interface mode inmtead.  Say Yes, and a new black screen with Boot: apprears omstead.

Unless you know what boot images are available to hou, it might be best to enter the word help here, which brings up a new help menu that differs from the one you had through the graphical mode.  There is even mention of a Rescue Broken System, but all you find there is an indication that you won't find out how to do it here.

A couple of the choices relate to possible boot paramters that can be used when continuing, bujt there is no real mention of what the basic boot process calls for.  Online search shows that you should be able to just specify boot, or add the paramter rescue/enable=true.

What might be of most interest to someone with a laptop is that you can specify the display option by using vga=771.  Other suggested options may deal with special machines.

You can't just use these on the boot: line by themselves.  So what can you specify upfront?

Well, obviously "help" was one option.  Further effprt and research showed me two others:  live, and live-install.  Live is just the option to run Ubuntu from the CD.  live-install is how you would initially install Ubuntu.  Other than the memory test, I did not find another option.

But you could enter this:

boot: live-install rescue/enable=true

And it takes off like it will work.  But it is actually just the normal install process.  If you get to the partitioner stage, you are at risk of formatting and overwriting something already installed there.  You can get around this by going on with manual, picking the partition you want to rescue, and electing not to format it.  This might seem to work, but it has already been established that if the partitioner is using an expanded width display, even if you try to keep going forward with Alt+F from page to page, you will fail at the last stage before the install starts.  A bug report has been submitted, both for this problem, and for the fact that there effectively is no documented or enabled way to rescue a broken system.

That said, there is still something that can be done, but this only works as reported here if you have two or more partitions with effectively the same OSes. applications, and data on them.  This is to copy the contents of a good partition over onto one that has become broken.

Several methods for doing this can be found online.  One is to use some backup/restore program to first save the good partition, then restore it to the bad one.

A second method is to become superuser, have both partitions mounted (this can be done via Places in the GUI), and use the tar method, just copying everything from the good partition to the bad one.

A third method is to use the cp method instead of tar, and the two methods work about as well as one another.  But don't just try tar or cp without understaqnding the parameter choices that need or should be made as part of the command line arguments.

I used the third choice myself, and allowed plenty of time for the copy to complete.  Then I apprehensively rebooted into the problem partition.  It came up fine, but I have a few small issues to straighten out regarding reckonizing and mounting the effected partitions and what gets passed to the VirtualBox client as a shared folder.  Really minor problems.

Now being able to work directly from the liveCD means I really only needed two partitions in this case.  Thaqt is a real advantage.  Were I dealling with Windows instead, I would have to have three partitions.  One to boot up with, one to copy from, and a third to copy to.  This is because neither the from or to partitions can be in use as the system boot partition because then many files will not copy or be copied to.  And windows does not offer you a liveCD option.

---

