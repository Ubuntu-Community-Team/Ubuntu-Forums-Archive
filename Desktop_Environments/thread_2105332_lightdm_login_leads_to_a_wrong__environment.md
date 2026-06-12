---
title: "lightdm login leads to a wrong  environment"
date: 2013-01-15
forum: Desktop Environments
---

### Post by Seagul on 2013-01-15
This login problem appeared this morning.

My favorite environment is gnome-classic (with effects). I can't use it any longer !
When I choose the environment on the login screen, here is what happens:

When I choose===================>                                                   it logs 
--------------......................................................                                                       ---------------
Ubuntu======================>                                                         Unity 2D ou 3D (depends on ?)
Ubuntu 2D===================> Unity 2D
Gnome Classic (without effects)          => OK. Gnome Classic (without effects) 
Gnome Classic================> Unity 2D

weird !

I then created another user and I can log in normally for this user, but it is impossible to do it for my main user. 

Here are the results of commands:

**ls /usr/share/xsessions**
-----------------------
gnome-classic.desktop  gnome-fallback.desktop  ubuntu-2d.desktop
gnome.desktop          gnome-shell.desktop     ubuntu.desktop

**cat /etc/lightdm/lightdm.conf**
-----------------------------
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
autologin-user=

**cat ~/.dmrc**
------
[Desktop]
Session=gnome-fallback

**cat  OtherUser/.dmrc**
---------------
[Desktop]
Session=gnome-classic

**cat '/var/lib/AccountsService/users/boss'**
-----------------------------------------
[User]
XSession=gnome-fallback
XKeyboardLayouts=
Background=/usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg

I tried to replace "gnome-fallback" by "gnome-classic" in   ~/.dmrc and   '/var/lib/AccountsService/users/boss', but it returns to gnome-fallback.

What can I do ?

---

### Post by VanillaMozilla on 2013-01-18
I have an almost identical problem, except that everything ends in Gnome Classic (without effects).  This happens in versions 12.4 and 12.10.

lightdm.conf settings seem to make no difference.

One clue, though.  I select a desktop, but the setting doesn't stick.  If I go back and check the selection before entering a password, it defaults to Ubuntu, no matter what I have selected.  The only exception is if I am already logged on, in which case it defaults to Gnome Classic (without effects), which is what I am already logged on to.

---

### Post by VanillaMozilla on 2013-01-18
This is [bug 1052453,](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1052453) which is supposed to be fixed but evidently is not.

---

### Post by ibjsb4 on 2013-01-18
@Seagul

Sure sounds like you been hit with the bug, but I notice that  /etc/lightdm/lightdm.conf is set to user-session=ubuntu.

Won't make any difference if its the bug.

I would think you could install "gdm" and use it as a work-a-round untill this bug in lightdm gets fixed.

```
sudo apt-get install gdm
```

It should ask you during or after the install if you want gdm or lightdm as default.

---

### Post by VanillaMozilla on 2013-01-18
(Slightly off-topic post--can be ignored)
Note to self on changing the background image:  If you do happen to have a working version of unity-greeter, it's controlled by something like unity-greeter.conf.  There are lots of nicer pictures you can use in /usr/share/backgrounds.  Of course, you can use your own too.

EDIT:
But it turns out that that's not the file.  It's not lightdm-gtk-greeter-ubuntu.conf either.

The default ugly background is 'warty-final-ubuntu.png'.  Searching the disc for the text 'warty-final-ubuntu' shows 14 files that refer to that file or 'warty-final-ubuntu.jpg', so it's probably one of those.  Some seem more likely than others.  It may be hard-coded.  I'd sure like to replace that image, but....


EDIT again:
OK, here's what works.

If the background file is specified as 'warty-final-ubuntu.jpg', some of the software (which may or may not be running) redirects it to 'warty-final-ubuntu.png' file, as a workaround.  So it's a little complicated to get this correct.  But there's a simple way to trick it.  Why fight it?

There's only one warty-final-ubuntu.png, and it's in /usr/share/backgrounds.  Just replace the file with a file of your choice.  Make sure it's a .png file.  It's not necessary that the image size match the monitor size.

---

### Post by VanillaMozilla on 2013-01-20
Let us know if the gdm works.  :)

---

### Post by VanillaMozilla on 2013-01-21
**Here's how you can get gdm (warning:  here be dragons):**
If you already have gdm installed, as you likely do, just
sudo dpkg-reconfigure lightdm
(or is that gksudo?) to choose which one to use.

Choosing gdm left me with a nice logon screen with a background but no way to log on.  You know, those nice little graphical tools are so easy to use, but it's so difficult to undo the damage if you can't log in to an xwindows system.


**Recovery (what I did, anyway):**
1. <Ctrl><Alt><F2> or something to get a bare terminal session.
2. startx gets you a blank xwindows session
3. <ctrl><alt>t to get a terminal (or whatever key combination you hope will work)
4. <alt><tab> to *find* the terminal
5. *Now* you can
sudo dpgk-reconfigure gdm
again to undo the mess (set it back to lightdm.
6. Terminate the session however you can manage to do it, and reboot.

Good luck.

---

### Post by ibjsb4 on 2013-01-21
@[VanillaMozilla]("http://ubuntuforums.org/member.php?u=463177")

The OP of this thread has not replied for six days.

Why do you rant on ??

If you can't figure out how to use gdm maybe you need to start your own :o

---

### Post by VanillaMozilla on 2013-01-22
This is not a rant.  I have the same problem, and I would be remiss if I did not document my experience with it and how to avoid the pitfalls and repair the damage.

I was fully expecting a follow-up from the OP, reporting the results, but so far we have heard nothing.  Meanwhile, I still have the same problem, and I see no reason to fragment the discussion with another thread.

As for not being able to "figure out" how to "use" gdm, according to your directions there's not supposed to be anything to figure out.  You didn't say anything about how to configure it.  A lot of people will already have gdm installed.  That's where I started from.

If you know of documentation that is sufficiently detailed to prevent disaster, please feel free to add that information.

---

### Post by ibjsb4 on 2013-01-22
OP = 1 post

[VanillaMozilla]("http://ubuntuforums.org/member.php?u=463177") = 6 post

  > I see no reason to fragment the discussion

You haven't, you hijacked it  :)

---

### Post by VanillaMozilla on 2013-01-22
OK, sorry if you're offended by a second user, but on some forums it is considered a good idea to keep discussions of the same problem together.  (EDIT:  That's [Section II, rule #1](http://ubuntuforums.org/index.php?page=policy) of this forum also.)  Note that I (1) found the bug report; (2) reported that it is supposed to be fixed but doesn't seem to be; and (3) actually *tried* the proposed solution, found it incomplete, and explained why.  Where I come from that's considered a substantive contribution to the discussion.

Meanwhile, if by some chance the OP does post back, his posts won't get lost.  And don't worry, this isn't a filibuster.

Perhaps you were offended by the remark about gdm being someone's little joke (I have removed it).  That was a joke, not a barb thrown at you.  Keep in mind how you would feel about your OS almost being bricked.  And please, I'm trying to keep this on a friendly and helpful basis.

---

### Post by ibjsb4 on 2013-01-22
I see you edited all your post, good show :)  Im moving on now.

---

### Post by VanillaMozilla on 2013-01-22
Edited for clarity and brevity.  Also, didn't want to offend you.  If you have more info on this, it's very welcome, but don't feel obligated, as it's just a computer for testing.  Thanks for your help.

---

### Post by VanillaMozilla on 2013-01-22
**This works for me.**

Edit /etc/lightdm/lightdm.conf.  Change the greeter from unity-greeter to lightdm-gtk-greeter.

There's no need to use gdm instead of lightdm; you just need to change the greeter.

But be prepared with an escape if it doesn't work.

---

### Post by Seagul on 2013-01-23
):P
Hello,
Sorry for not giving news for the past days. I have been very busy trying out to restore a fully operational user session. While I was trying it blew all my menus and I was having a hard time.
As my contribution, here is a summary of what I did.
I understood that when it deals with 2D (whether unity session or gnome-classic session ), it is handled through metacity) whereas when it comes to 3D it is compiz. I realized that the problem came from compiz, and i remembered  that I had changed one parameter in ccsm, which resulted in a question "some plugins may be uncompatible, do you want to go on" (the idea, not the exact words !). As a lesson to other users: DON'T ANSWER YES IF YOU ARE RUNNING GNOME CLASSIC. It ruins the environment. Despite all my efforts, I was not able to restore it. From a user standpoint, everything acts as if there were conflicts between options used by compiz in the 2 environments.
From all the posts I read, the best I found that gave me hints to solve the problem was: [HTML]http://ubuntuforums.org/showthread.php?t=1860615[/HTML]I followed the tips but none of them gave me the solution.
I did not switched to GDM because it did not seem to me it would solve the problem. What I did instead what to rely on the observation I made in my  first post:
[HTML]  I then created another user and I can log in normally for this user, but it is impossible to do it for my main user. 
[/HTML]I created a new user from scratch and copied patiently from one user to the user, trying not to copy what seemed to be in connection with compiz.
After five days of hard labour, it works now.: 3D and everything restored
There may be much simpler solutions, but I failed to find them.
Thank you both for your help.

---

### Post by ibjsb4 on 2013-01-23
Very nice job, glad you got it all sorted out.  And your thread was, shall we say, very entertaining  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

