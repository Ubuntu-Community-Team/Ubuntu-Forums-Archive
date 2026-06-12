---
title: "Beryl causes blank Java Swing interface"
date: 2007-02-16
forum: Desktop Effects &amp; Customization
---

### Post by LostPavek on 2007-02-16
It should be documented somewhere obvious that Beryl causes Java Swing components to not be displayed.  I spent a couple hours trying to debug my Java application without even realizing the whole time the problem was that it just doesn't work with Beryl.  Unbelievable after spending 3 days getting Beryl to work in Xubuntu Edgy with an ATI card.

---

### Post by WakkiTabakki on 2007-02-16
Put 
```
export AWT_TOOLKIT=MToolkit
```
in your login script or in the script where you start Beryl from. That'll fix it...

BTW, if you go to [http://forum.beryl-project.org]("http://forum.beryl-project.org") and make a search on the word "java" you'll get about 5 pages of hits, most of them concerning this particular problem, and in about 5 different languages. That's fairly obvious if you ask me...

/N

---

### Post by LostPavek on 2007-02-16
Thank you for posting a solution. =)

I wasn't saying finding a solution wasn't obvious, but associating the problem with the cause is not obvious.  To someone installing Beryl, they have no reason to think that as a result of installing it, Java applications won't display Swing components.

---

### Post by theonlyandy on 2007-04-26
Hello there.

I'm using Beryl and some Java-Applications as well, so I came to the same problem...

I put
```
export AWT_TOOLKIT=MToolkit
```
in ~/.bashrc, but that didn't work.

Why is that? Thanks for your help in advance.

Greetings,
 Andy

---

### Post by ernz on 2007-04-29
Same problem. I tried this, and it didn't work for me. However putting the line:

export AWT_TOOLKIT="MToolkit"

...at the very end of these files:

~/.bashrc
~/.bashrc~    (Note: You might now have this one)
/etc/profile

**...seemed to do the trick**. For those of you who don't know, you will need to edit the /etc/profile file with sudo. You can do this by opening the accessories menu, opening a terminal and typing:

sudo gedit /etc/profile

Also, the ~/ prefix is just your home directory i.e. /home/aaron/ 
The '.' prefix of a filename or directory sets that item to a hidden state. You can view hidden items in nautilus by pressing CTRL+H or View > Show Hidden Items in the menus.

Hope this helps,
Ernz

---

### Post by nyvalbanat on 2007-05-01
This totally works! Thanks a lot for posting this workaround.

The bug report to Sun is at [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179). Please go there and vote for it (Sun fixes bugs based on the number of votes, among other things).
-val

---

### Post by theonlyandy on 2007-05-11
Thanks a lot!

Adding the mentioned line in the /etc/profiles did it!

I wanted to vote for the bug, but I didn't find a button to do that.

---

### Post by fbradyirl on 2007-06-11
> **theonlyandy said:**
> Thanks a lot!

Adding the mentioned line in the /etc/profiles did it!

I wanted to vote for the bug, but I didn't find a button to do that.

Hi all,

This has also fixed my Java Swing GUI, but another minor issue still persists (Ubuntu 7.04 with desktop effects enabled):

- when the user moves the window (JFrame) and then hovers the mouse over a component with a tooltip, the tooltip will pop up in the wrong place. It is shown at the original position of the component on screen. This is also the case for combo boxes etc

Any ideas on a fix would be appreciated.

---

### Post by purity control on 2007-08-30
Depending on how you want to launch netbeans you probably dont want to put this command in your .bashrc file. This file is read when you launch a terminal, so it will only help you if you launch netbeans from the command line and not if you click on the desktop icon.

The correct place to put it depends upon whether the fix needs to be for all users on your system or just you.

If you want to make the changes for all users as already stated above  put :
```
export AWT_TOOLKIT="MToolkit"
```
at the end of your /etc/profile  file (sudo needed) 

If you want to make the changes just for you put:
```
export AWT_TOOLKIT="MToolkit"
```
at the end of your .profile file in your home directory (you will need to show hidden files if editing it from the file manager window)

It only needs to be put in one of those files rather than littering all your files with the same code.
You will need to log off and back on again for the changes to take place.

:)

---

### Post by Rancidmaniac13 on 2007-08-31
I have the problem too.

I did what you said, putting that code in the end of the /etc/profiles but now my java application won't run at all.

I get this error when I try to run frostwire:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002adf428b8385, pid=11150, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#

---

### Post by deejross on 2007-09-03
I'm running Gusty and this works for me. The whole Netbeans thing was driving me nuts. All the Swing tutorials are supposed to be done through Netbeans (says their documentation), so I thought I was screwed for a minute.

Although, in Gusty, I had to add it to "/etc/profile", not "/etc/profiles" (notice the lack of an "s" on the end of profile). I should also add that this problem seems to be one of the many things included in the merge to Compiz Fusion. Other than this though, it seems the merge has gone well. I've been running effects for a couple months now and this is the only real unsolved problem I've come across.

---

### Post by Milo82 on 2007-10-03
Thank you for the solution. I had been trying for a week to figure out why an example from my Java class hadn't been working. This fixed it.

---

### Post by MountainX on 2008-04-09
This is still an open bug in Sun Java. Please vote for the bug fix here:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6632124](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6632124)

---

