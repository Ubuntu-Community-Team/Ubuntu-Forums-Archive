---
title: "I need help! Can't get back into Ubuntu after booting into XP"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Wandering Wombat on 2005-10-17
Hi,
I run dual boot with winXP and really only use windows for about 2 things, while I learn how to use the equivalents in breezy. Anyway I logged into windows today and did what I had to do, then went to log into my beloved Breezy,  guess what I can't, I have been doing all updates and ubuntu has been running better than ever. I can't even paste in what the problem was, can't even remember really what it was. It won't let me log in with failsafe, it said something about you my be out of disk space and that is not the case.

As I can't really give any hints for getting advice I guess what I want to know is what are my alternatives is there any eg. rolling back, although I don't think I have installed anything that may have caused problems. In windows if I ever had a similar problem I would just run the install disk again and choose the appropriate option and generally I could always get back in to fix what was needed. Is there any thing similar with Breezy. This is really starting to get me down, I just get ubuntu the way that i want and this is the second time this kind of thing has happened first was with Hoary which led me to just clean install Breezy. I am getting to the stage where everytime I log into ubuntu I don't know whether things will be fine or I have to spend half the day finding a solution. I really love Ubuntu and everything about it, I enjoy configuring things and really don't want to use Windows anymore. Any help would be much appreciated. If this isn't the right forum to post in I apologize and please let me know where I should post this or move it thanx.

Cheers.

---

### Post by drummer on 2005-10-17
Is it possible to write down what the error is when you try to log in? It sounds like a similar problem I had where I could get to the login screen, but logging into gnome failed, saying the login lasted less than 10 seconds.....etc. not sure exactly. There was also a toggleable text area at the bottom of the error message with extra info. The problem was with a file called .ICEauthority or something similar (I'll check later when I'm at my Linux box).. its permissions were mucked up.

Post the error if you can, it might be the same problem.

---

### Post by aysiu on 2005-10-17
Is it possible that your /home partition is full, even if your entire Ubuntu installation isn't full? A live CD may help you diagnose the problem. But, yeah, if you give the exact error, people are more likely able to help.

---

### Post by Wandering Wombat on 2005-10-17
Thanx for replying so quick.

It is exactly the same as drummer mentioned:-

your session only lasted 10 seconds.If you have not logged out yourself,this could mean that there is some installation problem or that you may be out of disk space.Try logging in with one of the failsafe sessions (can only bring up Command line)to see if you can fix this problem.

Let me know if anyone can make something out of that eg. same as drummer said he had.

Otherwise I will write the rest down then type it in, oh how I hate typing actually I dislike writing on paper these days lol.

Thanx
Cheers.

---

### Post by Wandering Wombat on 2005-10-17
Oh I vaguely remember my disk space root had about 5 Gig free and home has about 20 Gig free short of being hacked and someone filling up my harddrives I don't think its that. Although of course anything can happen.

Cheers.

---

### Post by drummer on 2005-10-17
Try this, switch to a virtual console with Control+Alt+F1 and login, then do:```
sudo chown user:user /home/user/.ICEauthority
```where user is your username you log in with. With any luck it's what happened to me, if not then no harm done but you may have to write down the error and post it to let others with some knowhow debug the problem. The more information the better.

---

### Post by Wandering Wombat on 2005-10-17
Woo Hoo your a lifesaver (in the finest Aussie tradition) Drummer it worked no problems, I appreciate your help. I was hoping I didn't have to write the errors on paper then type them in, don't want people to think I am a slack arse, I have Multiple Sclerosis and can't write very well these days in fact can hardly understand my own handwriting lol. So your help really was appreciated. This is part of the reason I love Ubuntu it has the best forum of helpful people I have ever come across.

Cheers and thanx again. 

Oh by the way was the problem caused by me or another reason any ideas for future reference.

---

### Post by drummer on 2005-10-17
I've been told that the problem can occur if there's a process running through the sudo of gksudo command and it doesn't terminate properly, or doesn't leave the file as it should once it's finished with it. I don't think it's anything you can do your self, just something that happens if one of those processes crashes or something.

I'm glad I could help.

---

### Post by TLE on 2005-10-18
Hey
I just had the exact same problem and maneged to solve it, though it did really scare me. I'm no Linux guru so I'm not that strong in "terminal debugging".

Anyway I did a lot of installs in my last login, (which was the one that messed it up), but it was all install from the Starter Guide, so I would think it was unlikely that it was the problem. But anyway, I though we could try to track the problem, perhaps by comparing an apt log, if there is such a thing, (probably is, this is Linux after all).

But first I did a search in the Ubuntu bugzilla (No need to do the same work twice), and it turned out that this bug has been reported [http://bugzilla.ubuntu.com/show_bug.cgi?id=2053]("http://bugzilla.ubuntu.com/show_bug.cgi?id=2053"), and it seems as if it i actively being worked on. The general though there seem to be that it has somthing to do with the K3b setup program. Though I don't think I ran that last time. 

I'm going to follow it for a while, and se what they come up with, but I'm not going to post there yet, (don't know all the bugtracking "dos and don'ts" yet).

Happy Ubunting

---

### Post by Wandering Wombat on 2005-10-18
I do have k3b installed, don't have a need to use it much, be interesting to see what the problem is, hope they sort it out, only has happened once to me. The fix from drummer above worked no probs, but yes it was quite weird, I didn't think I had done anything stupid to cause it myself, though I aint no Linux expert lol.
Cheers.

---

