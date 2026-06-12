---
title: "Firefox crash, getting really annoying"
date: 2008-04-02
forum: Desktop Environments
---

### Post by Xamindar on 2008-04-02
Firefox will work fine for a while then it will all of a sudden crash and once it crashes it wil refuse to work any more.  I will try to open it again from the icon in the gnome menu, firefox will appear and then die imediately.  It will keep doing this, even if I reboot.  But it eventually works again if I give up and shut the computer down for the day, next day it will work again.

Now here is the weird part (as if all that wasn`t weird enough):

When it starts crashing and refusing to start up, I just figured out that if I open a terminal and just launch "firefox" it comes up just fine.

Any ideas why this is happening?  Nothing like this has ever happened on my gentoo box or in any other linux I have used.

---

### Post by fela on 2008-04-02
right click the menu bar and select 'edit menus'. in the dialog that comes up look for firefox, right click and select 'properties'. tell me what's in the 'command' text box.

---

### Post by kellemes on 2008-04-02
> **Xamindar said:**
> When it starts crashing and refusing to start up, I just figured out that if I open a terminal and just launch "firefox" it comes up just fine.


Just do this for a while and wait for crashes.. the terminal will often be showing some informative messages about this issue.

---

### Post by erginemr on 2008-04-02
Sometimes, it is the extensions (addons) that bring Firefox to its knees. You can also try disabling Firefox addons selectively, to see if they are responsible for these crashes.

---

### Post by Xamindar on 2008-04-03
> **fela said:**
> right click the menu bar and select 'edit menus'. in the dialog that comes up look for firefox, right click and select 'properties'. tell me what's in the 'command' text box.

"firefox %u"
I just took off the "%u" part to see if it makes any difference, can't imagine why it would though.

> **erginemr said:**
> Sometimes, it is the extensions (addons) that bring Firefox to its knees. You can also try disabling Firefox addons selectively, to see if they are responsible for these crashes.

well, only extensions I have installed are google browser sync and adblock plus and that is the same as my gentoo box that has never had this issue.

---

### Post by strongsad on 2008-04-04
I am having the same problem.  I haven't been able to get firefox to load since I finished the setup.  It immediately closes on start up sometimes I can get around it by opening another file with firefox but it closes as soon as I visit another website.  Sometimes I get an input/output error but most of the time nothing happens.  I haven't added any pug-ins or extensions yet.  I check the 'command' box and it just has 'firefox' in there.

---

### Post by erginemr on 2008-04-05
A faint hope and is unlikely for a new install but something in your Firefox user settings may be causing it to crash. So, having no other clue, I suggest you to rename the hidden directory ".mozilla/" in your home folder to something else and try to restart Firefox. From a terminal:
```
mv ~/.mozilla ~/.mozilla.mybackup
```

---

### Post by strongsad on 2008-04-05
I went into the packet manager and reinstalled it. I tried to do it throught the add/remove but it did not work either.  Now I'm having a problem of making a launcher for it every time I start my computer.  For some reason my settings aren't being saved and I have to mount my hard drive every time as well. And I can't delete anything from the desktop, not even files i saved to it.  Also my "shutdown" and "restart" buttons are gone.

---

### Post by erginemr on 2008-04-05
As Firefox is an essential part of the Ubuntu desktop, I believe during reinstallation process, you may have deleted some more packages unintentionally. I am sorry, but the best way in such a case is to do a clean reinstall of Ubuntu.

---

### Post by strongsad on 2008-04-05
I am almost positive it was the update in automatic updates that messed it up.  I did a fresh install, this time I didn't have to do an OEM install, and i didn't update firefox and it works fine as of now.  However I can't get ubuntu to update all the way. Every time I run the update manager it gets an error with one of the updates and then freezes.  Well just kidding, i just tried to reboot and the system doesn't come back on.  great.......

---

### Post by erginemr on 2008-04-05
:shock: This is me stupefied!

> ...Well just kidding, i just tried to reboot and the system doesn't come back on. great...

I cannot quite get you. Did you just do a new install? If so, did you try to update and couldn't succeed? If so, can't you boot your system any more? Or was all this just a joke? Who am I? ;)

---

### Post by strongsad on 2008-04-05
Sorry i was in the middle of writing that post while waiting for the update manager to finish installing all the updates. I fixed the [COLOR="Red"]firefox[/COLOR] issue by doing a clean install and before I ran the update manager I opened firefox to test it and it worked fine.  I figured it must be the update so in the update manager I deselected the update and started installing all the other updates.  I got an error on one of the updates, but i can't remember which one, and the update manager said it installed all but that one.  I open the the update manager again and suddenly there were another 73 updates so i went to install them again most of them appeared to be the same as the ones i just installed and at the end I got the same error.  I closed the error window and then the update manager froze in a loop of refreshing its self.  I went to the shut it down through the ubuntu version of the task manager and that wouldn't open.  too frustrated to go to the terminal and kill the process I just went and restarted the system safely.  Well it froze on the restart so I had to shut it down hard and when i tired to reboot the system it never loaded.  On start up the Dell screen appeared but then the hard disk stopped spinning and it just sat there with a black screen.  So that is the story of that problem.  I am doing another fresh install because the system won't come up at all.  So unless anyone has any other advise I am going to install each update one at a time and see what happens.  

For other people with the [COLOR="Red"]firefox[/COLOR] problem just go to the symantic manager and reinstall firefox and that seems to do the trick, and if you have to install again just don't do the update for firefox and you should be fine.  Hopefully you won't have the same error as me with the update manager.

---

### Post by erginemr on 2008-04-05
Now that you are deep down to your throat with Ubuntu installation over and over, and are having serious problems with Firefox, why not just download and install Hardy Heron beta? I have read in another thead of the forum that it will update itself to the official version (to be released 20 days from now) via Update Manager. 

I have tried booting into the Hardy Live CD and everything seemed to work right. I have read other people's posts, who had satisfactory performance with acceptable stability, too. So, I suggest you to install Hardy Beta which packs Firefox 3 Beta instead, and upgrade it to the final version 20 days later.

---

### Post by Xamindar on 2008-04-17
I don't know what you guys are talking about with this reinstalling but you shouldn't have to reinstall the whole operating system to get firefox to work properly.  

Even though I took out that "%u" it still crashes every once and a while.  Maybe I should just compile it from scratch sense no one knows why it does this.  But just like the original problem it still launches just fine from the console.  Why the heck does the gnome menu make it crash?  I have never heard of such a thing before.

---

