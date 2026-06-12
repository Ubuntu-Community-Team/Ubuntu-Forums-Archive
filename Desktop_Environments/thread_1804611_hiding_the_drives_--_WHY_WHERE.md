---
title: "hiding the drives -- WHY? WHERE?"
date: 2011-07-14
forum: Desktop Environments
---

### Post by AndyH-uf on 2011-07-14
I had a plan for the dual boot install. I prepared hard drive space. I made the Ubuntu install CD.

In Windows, I also read the install instructions for the modem and its drivers. There is even  step by step manufacturer provided instructions under the heading "Installing on Ubuntu." What could be easier?

The Linux install went ok. The desktop is there. I hunted around awhile and identified the Window's disk partitions, my many project files, the Linux whatever-they-are-called sections, and  various Linux applications.

By and by I accessed the modem CD, opened the instructions so I could follow along easily, started the install. Next: open Terminal and reply to a few questions. That seems to be all that is necessary. Immediately after the modem install instructions are step by step instructions for setting up an internet connection.

Only Terminal is well hidden. Ubuntu help knows nothing about it and nothing about command entry under any label I can think up. I spent more than a hour trying everything I could think, or stumble across, probably each at least three times, with no results.

Isn't Linux basically a command line system? Why is there such a strong effort to make it hard to find out about that part? Sure, once one knows how, and uses it a few times, one will probably remember, but the functionally is so basic one should be able to find [COLOR=Red]*something *[/COLOR]with Search or Help.

It was necessary to shut down, start Windows, get on-line, and use more reasonable search engines to find out how to find Terminal. Then I went back to Ubuntu.

Now Ubuntu does not show anything except the exceptionally uninteresting Home folder. No hard drives, no other file systems, no optical drives, no way I can get the system to tell me anything about them.

I can find Terminal but I can't find how to get to the CD so I can recommence the modem install. I don't know if I will care about Home as I begin to (hopefully) use Linux, but I am certain I will always want access to everywhere Windows Explorer reveals. So, back to Windows again.

Any useful hints?

---

### Post by mcduck on 2011-07-15
Linux doesn't show different drives as separate entities, everything is inside the one and the same directory hierarchy.

(So unlike Windows where you have C: drive and a D drive etc, in Linux you only have the one directory tree, and all drives are mounted into it. With automatic mounting, any removable drives and media will appear inside the /media directory.)

Anyway, simply inserting the CD should make it appear on the desktop and also in the side bar of the file manager.


What comes to yur problems finding the terminal, that's quite amazing, considering it's not hidden in any way, it's listed in exactly the same place (and way) as any other programs on the system. And also simply tying "terminal" in the Dash or the Applications menu will find the terminal for you. (Or if you installed older version than 11.04, it's under Applications/Accessories)

---

### Post by AndyH-uf on 2011-07-15
Yes, there are no drive letters. There were icons along the left hand side of the desktop for each partition. One (or maybe more than one) icon opened a directory tree, different from what I'm used to with Windows, but still easy to use. Giving the system a CD made that CD appear as a left hand icon and (immediately or after it was accessed, I don't recall) as an icon further right on the desktop.

These were there every previous time I booted into Ubuntu from a flash drive, and were there after the system was installed onto the hard drive. Now there is nothing having to do with any directory hierarchy. No hard drives or optical drives are anywhere to be found; there is no directory tree. Putting the CD into the drive produces nothing visible, nothing functional.

The hard drives and their partitions did not go away physically. Windows finds everything to be normal.

There is an icon that displays Home. The few things put there by default during the installation are displayed if I use that icon, but there is nothing else I would identify with the data storage system. Maybe "mounting," or lack thereof, is the problem, but what is necessary to accomplish that?

Terminal was not among any of the lists of applications, in any of the different categories I could find available from the desktop. I looked at all the lists of applications I could find. I experimented with many of these applications, to be sure I wasn't just not recognizing Terminal  because of a label I did not expect. I tried everything a number of times. Then, after reading about it on line, I got to it by doing something I did not know as possible to do. However, that is not at all the point. My comment was about a glaring deficiency.

The Terminal is quite important. There is Help across the top of the desktop and within various windows that can be opened, including those showing the applications. Search is also available most places. Neither Help or Search could find "Terminal" (as related to this function) or "command line" or a few other things I tried repeatedly. Terminal is an item that should be there. It isn't a minor bit of fluff that almost no one will ever care about.

---

### Post by coffeecat on 2011-07-15
> **AndyH-uf said:**
> My comment was about a glaring deficiency.

There is no glaring deficiency. The terminal can be found in exactly the place mcduck described. What version of Ubuntu are you running?

---

### Post by AndyH-uf on 2011-07-15
I eventually found a way to see the disks and optical drives. It isn't what I was using before but it allowed me to access the CD and proceed with the modem driver install. sort of, maybe, partly

I double clicked on the install file, located on the CD, then opened Terminal to follow the installation, and respond as required. Only nothing at all displayed in the Terminal window. The modem driver may have installed without any intervention, although that's mostly a guess, since nothing said anything about it.

Then I spent a long while trying to find the things I had to use, according to the instructions, to set up an internet connection. I couldn't fine anything in/on the system that was like what the instructions described, so I never managed to get started. No doubt there are other instructions somewhere. A thing for another day.

---

