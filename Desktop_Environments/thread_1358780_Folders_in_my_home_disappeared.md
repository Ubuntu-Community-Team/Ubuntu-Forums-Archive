---
title: "Folders in my home disappeared"
date: 2009-12-18
forum: Desktop Environments
---

### Post by Elokin6 on 2009-12-18
Hello everyone,

I'm experiencing a major issue and am about to ditch Ubuntu altogether.  I really hope you can help me out here.

I'm running the 32 bit version of Karmic and have been using Ubuntu for about two years.  It has been my primary operating system for over a year, so I'm not a complete newb, although I am far from an expert, I kind of know what I am doing. 

Here's my issue:  I had a folder open at the bottom of the hierarchy of several folders and I attempted to drag a folder from my desktop into that nautilus window and got an error saying something to the effect of "that folder does not exist".  I tried to go up a level in the hierarchy using the nautilus button, and that file did not exist.  So I closed that nautilus window entirely and opened up my home in a new window and that entire hierarchy was gone.  So I checked it in the terminal, still no folder.  WTF????????

I know that this just screams "user error" but I swear upon my grandmother's grave that it is not.  I've had similar issues with Jaunty and possibly Ibex (I can't remember each time this has happened) but it was while moving files and only the files disappeared.  While I believed that those instances couldn't be user error, I wrote them off as moments of idiocy.  Now that I've had this issue happen several times this week and an entire file hierarchy has disappeared, I know something is jacked up.

I installed Karmic 3 days ago.  It was a completely fresh install (formatted my home and root) because I was having the disappearing file problem in Jaunty.  I'm using the ext3 file system.  I checked my file system using e2fsck and it found 0 bad sectors.

The files I lost are not a crisis because they can be reinstalled by reinstalling the program that created them (Sims 3).  I just need to know how to stop this from ever happening again.  If I were to lose a project for school, I would freak directly out.  

I'm sorry this is long winded, but I'm freaking out.

Thank you for your help.

---

### Post by spiderbatdad on 2009-12-18
Is it possible you are running multiple instances of nautilus, as in clicking too many times? Check the system monitor. Does a restart restore your files? After using Ubuntu for nearly five years and hanging around these forums as long, I have very rarely heard of this problem, and invariably did involve some user error or hardware problem.

---

### Post by Elokin6 on 2009-12-18
Thanks for your reply,  I appreciate it. 

I did have another nautilus window open then, as well as a couple of firefox windows.  The other nautilus window was open to another folder in my home.  I've restarted my computer to boot of the live cd and then again to boot ubuntu, and my files did not return.

I know this is really strange.

---

### Post by holiday on 2009-12-18
Try finding the missing folders through the console. 


Applications->Accesories>Terminal

$ ls | grep drwx

Are the folders listed?


I have issues with nautilus. If I launch it from the console, nautilus clutters the screen with a stream of messages. It freaks, it gets lost, it doesn't refresh! Ay yi yi! It hangs! This is supposed to be a mature app!

It's probable that nautilus is just too mature. It's been improved into oblivion. 

I've switched to thunar.

# apt-get install thunar

---

### Post by Elokin6 on 2009-12-18
That grep command isn't working for some reason, but ls -la doesn't show the folder.

I'm not familiar with Thunar.  Is it much trouble to integrate?

---

### Post by holiday on 2009-12-18
> **Elokin6 said:**
> That grep command isn't working for some reason, but ls -la doesn't show the folder.

I'm not familiar with Thunar.  Is it much trouble to integrate?

No sorry. I have a toothache I'm treating with whisky. 

Yes of course it's ls -la. And if that is not finding your missing folders then they are not there. 

I use that grep all the time. I don't know why it's not working for you. 

I found Thunar while playing with the XUbuntu distro. The installation to Ubuntu is pretty clean. I think. My system needs a deep refresh. I'm not disciplined.

But try it out. If it pulls in a lot of stuff you don't want then cancel. I doubt it will find your missing ones, but I like it way better than nautilus.

I mean the name itself suggests -oh well - 1980-something.

---

