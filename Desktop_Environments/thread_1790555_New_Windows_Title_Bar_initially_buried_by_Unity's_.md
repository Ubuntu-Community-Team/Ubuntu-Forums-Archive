---
title: "New Windows Title Bar initially buried by Unity's Top Menu"
date: 2011-06-25
forum: Desktop Environments
---

### Post by apollothethird on 2011-06-25
Starting and application or opening new windows on my machine takes two hands.  Once hand with the mouse and one with the alt-key, before I can have normal control over the window.  In normal control, I mean the ability to move, minimize and exit the window.  That's because every time I start a new application or open a new application window it opens to the top left of the screen.

The title bar of the window is buried below Unity's top menu bar.  That means I can't grab the window by the title bar to move it or minimize it.  I have to hold down the alt-key then grab with the mouse to position the window in a location where I can properly view it (closer to the center of the monitor on my right).

I might be missing something if there is an option I can set so the new window locations can remember the position and size from last closed.

This is very annoying, whereas I open and lost lots of windows during the course of working.  Even browsing this forum, I click on the new posts option and right click on topics from the list to read from a new window.  After finishing with that topic I close the window.  Often I might open up two or three windows in that topic to type replies or review references mentioned in that topic.  Then I close all the windows and open up a new window with the next topic of interest.

It's bad enough that the OS doesn't remember the preferred size and position of the window.  But if it were possible to just drive and the window to the position and resist only using the mouse, it would be great, since my hand is already on the mouse.  But because the title menu is buried under Unity's Top Menu, I have to hold down the alt-key with my left hand while dragging the mouse with my right hand.

If no one has a fix or suggestion and this is affecting everyone, I guess it'll be off to the bug/feature forum to inform the developers of the problem.  Maybe they will fix it before the next release.

Thanks in advance for anyone that has any input on this.

By the way, my other computers that are running Unity 2D and Ubuntu classic because they don't have the video power for Unity 3D are not plagued with this bug.  The windows all start at the top left but the title menu bar isn't buried by Unity's Top Menu bar.  That makes it possible to grab the window by the title bar and position it just using the mouse with one hand.

I'm running Ubuntu 11.04, the default Unity 3D.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Alwimo on 2011-06-25
If you click on the button in the launcher to zoom out to show the four workspaces, you should be able to move the windows down a little so that the title bar is clear of the top panel.

I'm sure there would be a better fix, but that should work in the meantime.

---

### Post by apollothethird on 2011-06-25
> **Alwimo said:**
> If you click on the button in the launcher to zoom out to show the four workspaces, you should be able to move the windows down a little so that the title bar is clear of the top panel.

I'm sure there would be a better fix, but that should work in the meantime.

Thanks, Alwimo.  I'll give that a test go as a workaround.  So far lots of work for a new window when you open as many windows as I do in a session.  The first few test causes a little lost of focus on the project at hand.  As you mentioned, I hope someone comes out with something better.

By the way, are you running Unity 3D?  If it's not happening to everybody I might be able to perform more experiments to try to figure out how to make it stop happening to me?

If it's happening to everybody, I'm really surprised the developers allowed such an obvious annoyance to slip by.  I'm sure many of them are using more than one monitor, and often opening a number of windows during the course of their programming.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by nerdy_kid on 2011-06-25
that doesn't happen here, try 

```

unity --reset

```

that will reset all of unity's settings.

---

### Post by Alwimo on 2011-06-25
It doesn't happen for me either (and I use Unity 3D).

I have moved title bars under the panels after changing the panel positions in the past, however, but that's different.

---

### Post by apollothethird on 2011-06-25
> **nerdy_kid said:**
> that doesn't happen here, try 

```

unity --reset

```that will reset all of unity's settings.

Thanks.  I'll probably do that after some more experimentation and possibly input form some of the others.  I used that command lots of times when I first started using Unity.  It seems that, that is the main remedy for just about every Unity issue.  At present I have spent some months with building the environment I have.  I really hate to start over when there is a chance there is some Window behavior option/feature that might be able to check this flaw.

The fact that it's not happening to you gives me hope.  Hopefully someone understanding a bit more about the features will be aware of an option to go into rather than starting over.  If I started over, there's a good chance I'll soon come back to this same spot and get stuck again.  The starting over might turn into a frustrating loop that I hope I can avoid.

I'll eventually start over if no one knows of any windows configuration options to test.  If there isn't any, I might learn from this thread a good way of reporting the bug... or the bug resolution, which will be to ask the developers to look for a way to give the user some control over the size and position of new windows.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by nerdy_kid on 2011-06-25
> **apollothethird said:**
> Thanks.  I'll probably do that after some more experimentation and possibly input form some of the others.  I used that command lots of times when I first started using Unity.  It seems that, that is the main remedy for just about every Unity issue.  At present I have spent some months with building the environment I have.  I really hate to start over when there is a chance there is some Window behavior option/feature that might be able to check this flaw.

The fact that it's not happening to you gives me hope.  Hopefully someone understanding a bit more about the features will be aware of an option to go into rather than starting over.  If I started over, there's a good chance I'll soon come back to this same spot and get stuck again.  The starting over might turn into a frustrating loop that I hope I can avoid.

I'll eventually start over if no one knows of any windows configuration options to test.  If there isn't any, I might learn from this thread a good way of reporting the bug... or the bug resolution, which will be to ask the developers to look for a way to give the user some control over the size and position of new windows.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

you can back up your current settings (most of them at least) by opening ccsm (compiz control), hitting "preferences" and then "export".

---

### Post by apollothethird on 2011-06-25
> **nerdy_kid said:**
> you can back up your current settings (most of them at least) by opening ccsm (compiz control), hitting "preferences" and then "export".

Thanks, Nerdy_kid.  That part is done.  I'm now experimenting with trying to figure out how to affect the reloading of windows.  If I break my current contribution, I can at least get it back.  I haven't reset things back to the default yet.  I'm sure that will make the window menu initiate with the title menu showing since it's that way for everybody else.  If going through the various window configuration options doesn't give relief I'll eventually reset back to the default and try to get my happen environment step by step and see what breaks it.

Also, if I learn how to configure something that gives the user some control over where new windows will appear (the size and position) I'll bring it back to this thread.

The backup feature is a valuable contribution to the thread.  I learned it a while back after having started over so many times.  So far I haven't had to use the restore feature.  So far I've been able to experiment and find the obscure control to fix whatever is broken.  The most common thing that gets broken when I make a chance is the top menu disappearing or becoming unreadable.  Logging out and logging back in or rebooting the computer usually fixes that.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-06-25
The problem with the buried title bar has disappeared.  I was plagued by it for about three weeks.  I'm surprised that it went away on the same day I posted my question.

It's a welcomed site to see the black title bar on new windows without having to hold down the alt-key to drag it into view.

It's an annoyance that most of the applications don't remember the last size and position from the last time it was run.  It's an annoyance to have to reposition the windows every time they open.  I will put in a feature request to have this addressed.  If the developers address this annoyance, the same feature they add to relieve us of this problem will be a resolution for when the Window get stuck with starting too high.

At present a new window is started at the very top left of the monitor on the left.  For a couple of weeks it was miscalculating the top and going too far.

I'll still be surprised if there isn't a unity feature to address that issue.  If someone discovers it at any time, hopefully you'll remember this tread and revisit it with the information.

Thank you to everyone who provided workarounds and gave me hope that it wasn't a flaw in the OS but some temporary mal-function of my setup.  That gave me how to keep exploring, though I don't know anything specific that I did to make the problem go away.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-06-26
I reported the problem fixed too quick.  It appears that it's only partially fixed.  I have four workspaces.  The two top work spaces are working fine as I described in my previous message.  However, the two bottom work spaces still have the flaw described in the original message.

(Unity's Side Bar menu Workspace switcher shows a layout of two to the top and two to the bottom.)

I spent the best part of a day trying to make sure this problem is consistent before posting, so that if I had more information I could give it more consolidated.

Since my ccsm profile is backed up I'll soon use the reset command and report on what happens.  I'll also try to rebuild my environment back to my current preferred configuration (if possible) and reflect on what breaks it if it becomes broken again.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by aksx on 2011-11-07
i had the same problem with the title bar under the unity top bar.Ticking(checking) the Place Windows option under Windows Management in CCSM fixed it..

---

### Post by apollothethird on 2011-11-07
> **aksx said:**
> i had the same problem with the title bar under the unity top bar.Ticking(checking) the Place Windows option under Windows Management in CCSM fixed it..

Aksx.  Thanks for the contribution.  I keep having this problem.  I can't produce it at will.  It just happens at times, then I spend a very long time trying to fix it.  Usually I have to log out and log back on to fix it.  This destroys a large part of the time frame in which I have to work.

I'm trying to find this option you describe.  So far I can't find it.  Where is this "Place Windows option you mention"?

You appear to be describing a default setting which I have never changed and still have.  This is found under:

CCSM -> Window Management -> [Check] Place Windows

If something more or something different from this has to be done, please let me know and I'll test it.  I'll check it the next time I have the problem also and report whether it resolves the issue for me.

Thanks again for your input.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by stinkeye on 2011-11-07
In CCSM -> Window Management -> [Check] Place Windows
try changing the placement mode to ```
centered
```

---

### Post by jamesvjj on 2012-03-07
My Window also randomly, and on it's own moves up under the top title bar. I have struggled with this since I started 11.10. I have not figured out why it randomly does this, but I can move the window by clicking Alt+Button 1 on my mouse or Alt+F7.  The cursor turns into a little hand and I can move the window back down. For the mouse option you have to hold the mouse button 1 down while you move. For the Alt+F7 the little hand remains until after you move the window.

You can change which keys allow you to move the windows by going into CCSM > Windows Management > Move Window > Change Initiate Window Movement keys to your liking.

This is annoying and it seems like a bug.  Did anyone else figure out a solution to avoid this problem in the first place? To me no window should ever be able to go under the title bar and if I try on my own to get a window to go under it's not possible.  It only happens in this random way I've described.

---

