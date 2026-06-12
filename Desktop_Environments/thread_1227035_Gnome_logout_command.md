---
title: "Gnome logout command"
date: 2009-07-30
forum: Desktop Environments
---

### Post by vaibhav on 2009-07-30
What is the command to log out from gnome?
I don't want to do System -> Quit... -> Logout, but type a command from terminal to log out of gnome, and possibly even make a launcher.

---

### Post by m4lte on 2009-10-09
bump. this is quite a good question!

---

### Post by wojox on 2009-10-09
Ctrl+Alt+Delete

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
create a launcher. Name it what you wish. your command line is thus: "gnome-session-save --logout-dialog". copy and paste, or at very least mind the <space> in the middle (I say this b/c I beat my brains out trying to figure out why my launcher worked in one account and not another).
If you want to change your icon the path is /usr/shared/icons

---

### Post by drajkuma on 2009-10-09
> **ST3ALTHPSYCH0 said:**
> create a launcher. Name it what you wish. your command line is thus: "gnome-session-save --logout-dialog". copy and paste, or at very least mind the <space> in the middle (I say this b/c I beat my brains out trying to figure out why my launcher worked in one account and not another).
If you want to change your icon the path is /usr/shared/icons

Now, can I make it show up on top of all windows always?  Sometimes, it comes in the foreground and sometimes its hidden in the background.

Thanks
Dan

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
How do you have your desktop setup? why not just put either a logout applet or a quick switcher applet on your panel? Just out of curiousity. I had to learn the command b/c I've set mine up as an OSX clone, so I needed a logout launcher on my AWN panel. I guess what I'm asking is what do you mean always on top?

---

### Post by drajkuma on 2009-10-09
> **ST3ALTHPSYCH0 said:**
> How do you have your desktop setup? why not just put either a logout applet or a quick switcher applet on your panel? Just out of curiousity. I had to learn the command b/c I've set mine up as an OSX clone, so I needed a logout launcher on my AWN panel. I guess what I'm asking is what do you mean always on top?

Well, since you're absolutely, wickedly, twisting my hand, I admit that I had to make the Desktop run like Windows.  It didn't matter that I had a secure OS (viruses be damned, that's what spouses are for).  

I have the aero-clone theme, and I have customized the Main menu to be pretty much like Windows, albeit more like win 2K.  Basically, I'm okay, but I'm trying to get my circle of friends to convert to Linux.  

Oh, and did I say that my wife complained that the internet was missing because she couldn't see the "e" icon?  I had to replace the firefox icons with downloaded internet explorer pngs to satisfy her.  I even had to replace the OpenOffice icons to MS icons and they didn't bat an eyelid as the splash screen said OpenOffice 3.0 while loading

Thanks
Dan

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
Hey, I'll admit to even greater heresy.... My Jaunty install is actually a Wubi install, and I'm currently running win 7 instead of Ubuntu in any flavor. Nonetheless, I'm still a little lost as to what you're asking. For the little while that I ran with a basically gnome theme (my panel was setup reminiscent of windows as well) I don't ever recall a maximized window covering it. Now, keep in mind that I just installed Ubuntu on Monday (yes, as in 4 days ago) and I've spent more time in windows than in Ubuntu since. Have you tried toggling the auto hide feature? That should continue to lend a windows-esque feel to things.
And as to your wife "requiring" the M$ icons.... when I make the final move to Ubuntu, I'll probably continue using Office '07 through Wine b/c my former experiences with OO left me wanting a few features.

BTW, post a screenshot, I'd like to see how close you've gotten with your emulation.




WHAT A MINUTE!!! I just reread your question, and it clicked. You're saying that the logout dialog sometimes opens in the foreground and sometimes on the desktop behind everything else!!! Now, to answer that.... I'd like to know too. LOL I've had the problem a lot, and I always just minimize whatever's on top. Also, that dialog looks nothing like a windows shutdown/logout dialog. There's probably a way to edit it (I don't think there's anything you can't do in a linux distro if you can simply find the coding) to make it look the same, but that's beyond me. I have a grand total of 4 days working with linux distros including a couple of hours with Ubuntu on a live CD 2 years ago, and a day with redhat Fedora back in 2000. I'll do some googleing!

---

### Post by jimmydean886-2 on 2011-12-03
In Gnome 3, the command is gnome-session-quit

---

