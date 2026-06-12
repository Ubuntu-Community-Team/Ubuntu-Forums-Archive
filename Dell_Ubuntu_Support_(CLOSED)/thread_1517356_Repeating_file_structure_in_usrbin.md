---
title: "Repeating file structure in /usr/bin?"
date: 2010-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JackieG on 2010-06-24
Ok, so let me first say, I am a Ubuntu newbie so don't expect a lot of "techy" talk out of me.  :-?

I have a Dell Mini with Ubuntu that, in the last 2 weeks, seems to have run out of disk space (80 kb left) .  I can't for the life of me, figure out exactly what is going on.  

I did have a small breakthrough tonight but before I do anything to fix it I thought I should see if someone can explain to me what is going on.

According to Dell my mini only has 4GB of disk space.  I have loaded very little on it since i got it 2 years ago because, to be honest, I don't really know how to.  I use it primarily to access the web when I'm sitting in front of the TV or on a trip.  And when I'm talking not loading much, I'm being honest.  Only Skype (which doesn't work right anyway, and a driver for my wireless printer).   I don't see how I could be out of disk space!

I have looked through my file browser and found that within my usr/bin directory I have a repeating, embedded file named "x11".  (excuse me if I'm using the wrong terms but I think this is close)  Just to make it clear what I mean, within the usr/bin directory, I have my executable files and a file called "x11".  When I enter that x11 file, I have all the executables again along with another x11 file.  When I open that one, same thing... all my executables and another x11 file.  I've gotten through 25 repeats of the x11 file and it's still going (although at this point my mini is locked up so I don't know how far it really goes).  

I don't know how this file got created over and over and over but I assume it each executable file in each layer of the x11 files is taking up space, right?  (As opposed to being just a shortcut as in windows).  If I delete all the layers but the top one will I totally screw up my system?  I don't know what to do and was hoping for a little advice.

And if for some reason these are just pointers (although the do appear have a size to them - like Skype which is 13 MB repeated at least 25 times) where else do I look to figure out where all my disk space went?

Thanks!

---

### Post by gbrainin on 2010-06-25
I can't say where all your disk space went, but you should not worry about the /usr/bin/X11 directory.  That X11 is indeed just a pointer ("symbolic link" in unix-speak) back to /usr/bin.  So there is in fact just one set of files on your hard drive.

---

### Post by JackieG on 2010-06-25
Thanks for the info.  Geez, now I feel stupid.  :P

Still don't know where all my memory went.  Cleared out all my downlaoded files (from e-mail attachments), cookies, history, etc. and I still can't figure out where all my disk space went!  Ugh...

---

### Post by gbrainin on 2010-06-26
Nothing to feel stupid about; it is kind of strange to have something pointing in a loop like that.

As for the size of your files, I'm not sure it's all that unusual.  Now that I look at my own system (which isn't much beyond a standard installation), there's over 4GB used, not counting my data files.  You might want to look into removing some of the packages/programs you don't need, or installing a lighter-weight version of Ubuntu.

---

