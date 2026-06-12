---
title: "gnome classic email notifier"
date: 2012-07-09
forum: Desktop Environments
---

### Post by garyzw on 2012-07-09
Is there a gnome classic email notifier I can use that works with gmail?

---

### Post by Frogs Hair on 2012-07-09
Search mail in the software center and some applications will come up . I don't know which might be Classic Gnome compatible.

---

### Post by ajgreeny on 2012-07-09
Try **gmail-notify** from the repos.

---

### Post by dewdrop_world on 2012-07-10
Well, I have to say, I've been having an absolutely terrible time trying to find a Gmail notifier that actually works.

I have been able to find some notifiers that pop up a box for a few seconds. That's fine if I'm at the computer, but if a message comes in while I'm away, the box is already gone and I have no idea. So it's also kind of important to have an icon in the panel. That's where I've had the problem.

- checkgmail: You launch it, configure it, pop-ups appear, nothing in the panel.

- gmail-notify: I don't remember exactly what went wrong here, but I'm pretty sure it was like most of the others. After you configure it, there was no visual feedback that it's working.

- gm-notify: This was the most promising. It hooks into the messaging panel applet and turns the envelope blue when you have unread mail. This worked beautifully for about one day. Then it stopped updating. I first noticed the problem by reading some new messages, and the icon didn't go dark. Then, new mail came in, nothing happened.

So this one is quite good when it works, but I doubt its reliability.

- mail-notification: Good pop-ups, no panel icon.

- gnubiff: Cute, but the applet doesn't live in the panel -- it takes up screen space and hovers over windows.

So I'm just about to reinstall gm-notify, reboot and hope for the best. If it stops working, it stops working.

But, like the original poster, I'm wondering if anybody knows of a Gmail notifier that actually functions correctly in Ubuntu 12.04, gnome classic.

If I had to guess, I would say something might have changed in the panel implementation in gnome for 12.04, and the notifier apps haven't caught up. That's just a guess.

James

---

### Post by dewdrop_world on 2012-07-10
> **dewdrop_world said:**
> Well, I have to say, I've been having an absolutely terrible time trying to find a Gmail notifier that actually works.

- gm-notify: This was the most promising. It hooks into the messaging panel applet and turns the envelope blue when you have unread mail. This worked beautifully for about one day. Then it stopped updating. I first noticed the problem by reading some new messages, and the icon didn't go dark. Then, new mail came in, nothing happened.

So I'm just about to reinstall gm-notify, reboot and hope for the best. If it stops working, it stops working.

It worked great for a few hours. Now, there's an unread message in my gmail box, no notification.

So the question still stands: Is there a notifier that really works?

---

### Post by markbl on 2012-07-10
> **dewdrop_world said:**
> 
So the question still stands: Is there a notifier that really works?
I find that gm-notify works fine. I have used it for ages, including in 12.04. It has a major advantage to all the other notifiers because it uses push (instant) notifications whereas all the others use polling.

However, I mainly use gnome-shell now and unfortunately gm-notify does not display a static panel icon in gnome-shell. So I developed my own gmail notifier that uses push notifications and integrates nicely in both unity and gnome-shell (and unity-2d, gnome-classic, etc). See/get it from [https://github.com/bulletmark/gmail-indicator](https://github.com/bulletmark/gmail-indicator).

---

### Post by garyzw on 2012-07-10
> **markbl said:**
>  I developed my own gmail notifier that uses push notifications and integrates nicely in both unity and gnome-shell (and unity-2d, gnome-classic, etc). See/get it from [https://github.com/bulletmark/gmail-indicator](https://github.com/bulletmark/gmail-indicator).

How would a novice go about installing it?

---

### Post by markbl on 2012-07-10
> **garyzw said:**
> How would a novice go about installing it?
Well you just have to follow the instructions described there, i.e. type a few commands. Generally though, novices should probably keep to standard ubuntu packages installed via ubuntu software center only so perhaps this program is not for you.

---

### Post by garyzw on 2012-07-10
> **markbl said:**
> Well you just have to follow the instructions described there, i.e. type a few commands. Generally though, novices should probably keep to standard ubuntu packages installed via ubuntu software center only so perhaps this program is not for you.


I see if I can get it installed-- I have installed the  Bungie Marathon games which require you to build the game engine. I have my system cloned so if I mess up I can get it back quickly --thanks

---

### Post by black veils on 2012-07-11
the way i have had mail notifications for years, is through my web browser. there are 2 good add-ons, for** firefox: [COLOR=Green]webmail notifier[/COLOR]**, for[B] google chrome: [COLOR=Green]x-notifier[/COLOR]
[/B]

---

### Post by garyzw on 2012-07-11
> **black veils said:**
> the way i have had mail notifications for years, is through my web browser. there are 2 good add-ons, for** firefox: [COLOR=Green]webmail notifier[/COLOR]**, for[B] google chrome: [COLOR=Green]x-notifier[/COLOR]
[/B]

Thanks I will check in to that also.

---

### Post by dewdrop_world on 2012-07-11
> **markbl said:**
> I find that gm-notify works fine. I have used it for ages, including in 12.04. It has a major advantage to all the other notifiers because it uses push (instant) notifications whereas all the others use polling.

However, I mainly use gnome-shell now and unfortunately gm-notify does not display a static panel icon in gnome-shell. So I developed my own gmail notifier that uses push notifications and integrates nicely in both unity and gnome-shell (and unity-2d, gnome-classic, etc). See/get it from [https://github.com/bulletmark/gmail-indicator](https://github.com/bulletmark/gmail-indicator).

Oh, nice, I'm eager to try it, but...

```
sudo pip install imapclient
[sudo] password for xxx: 
sudo: pip: command not found
```

Python 2.7.3 is already installed on my machine. What else do I need?

---

### Post by markbl on 2012-07-11
> **dewdrop_world said:**
> Oh, nice, I'm eager to try it, but...

```
sudo pip install imapclient
```


Read the second half of that same line in the [instructions](https://github.com/bulletmark/gmail-indicator). I.e. you can also use easy_install which is included by so many packages that is likely already on your system.

You can install pip with "apt-get install python-pip" or easy_install with "apt-get install python-setuptools".

You will probably find other prerequisite packages needed on your system. I personally use apt-file to search for packages containing a file (apt-get install apt-file).

---

### Post by dewdrop_world on 2012-07-11
> **markbl said:**
> Read the second half of that same line in the [instructions]("https://github.com/bulletmark/gmail-indicator"). I.e. you can also use easy_install which is included by so many packages that is likely already on your system.

Actually it wasn't, and "pip" actually didn't work. But easy_install did so... I got the test to run successfully! Looks very promising. I'll write back if I run into any problems.

Another note for the README -- it seems to assume that you've installed the unity-style Dash extension. I haven't (don't like it). So I assume that what I should do instead is create an application launcher in one of the menus, or on the panel.

Thanks a lot for doing this! It really has been a pretty dreadful struggle. If this is the answer, I'll be very, very grateful.

James

---

### Post by markbl on 2012-07-11
> **dewdrop_world said:**
> Actually it wasn't, and "pip" actually didn't work.

Do you know what the error was? I may just change the README to use easy_install although in the python world, pip is replacing easy_install.

> 
Another note for the README -- it seems to assume that you've installed the unity-style Dash extension. I haven't (don't like it).

So you are using gnome-shell? What is a "unity-style dash extension"? I could not find anything like that searching "dash" at extensions.gnome.org. I hardly use any extensions, certainly nothing like that. I believe the out-of-the box gnome-shell is minimalist but has everything you really need.

> 
So I assume that what I should do instead is create an application launcher in one of the menus, or on the panel.


No, the launcher was created for you and installed in the auto-startup when you typed "make install". Look for gmail-indicator in your apps under the dash. Run "gnome-session-properties" from a terminal and you will see the session startup launcher. You don't need to do anything, it should just work from now on provided you have configured your gmail account + password in ~/.gmail-indicator-rc. Go to the source dir and type "make uninstall" to remove everything if you decide you don't want it.

---

### Post by kansasnoob on 2012-07-12
I don't use gmail but I recalled a conversation during Precise development so I dug it up, sorry so many posts to read through, but look here beginning post #313:

[http://ubuntuforums.org/showthread.php?t=1873765&page=32](http://ubuntuforums.org/showthread.php?t=1873765&page=32)

Then follow the conversation between josephellengar and mc4man up thru post #327 where Joseph said be included a "patched checkgmail":

[http://ubuntuforums.org/showpost.php?p=11582716&postcount=327](http://ubuntuforums.org/showpost.php?p=11582716&postcount=327)

No promises just thought I'd share the conversation I remembered :)

---

### Post by markbl on 2012-07-12
> **kansasnoob said:**
> .. checkgmail ..
Like all notifiers other than gm-notify and my gmail-indicator, checkgmail just polls for new mail periodically. AFAIK, only gm-notify and gmail-indicator use push notification from the gmail server, i.e. you get new-mail indication within seconds.

---

### Post by dewdrop_world on 2012-07-12
> **markbl said:**
> Do you know what the error was? I may just change the README to use easy_install although in the python world, pip is replacing easy_install.

It was something about not being able to install the right version of one of the dependencies, and the error message said to use easy_install. Sorry, I don't have the text now.

> So you are using gnome-shell? What is a "unity-style dash extension"?

Beats me. I only recently switched to 12.04, and I never heard anything about a "dash" in Ubuntu 10.04 with gnome. That's why I found that instruction perplexing -- I have no idea what you mean by "dash" in that context. "Go to the dash and search for..."? So I was guessing it would be something like unity's dash (where you do go search for apps etc.).

> No, the launcher was created for you and installed in the auto-startup when you typed "make install".

Right, I eventually figured that out. BTW, so far the applet is working great! It's working better for me than anything I could find in the Ubuntu repositories. Kind of amazing -- it lets me know when mail comes in, and it goes dark after I read all of those messages. Like it should be.

Thanks for sharing that!
James

---

### Post by markbl on 2012-07-12
> **dewdrop_world said:**
> I have no idea what you mean by "dash" in that context. "Go to the dash and search for..."? So I was guessing it would be something like unity's dash (where you do go search for apps etc.).
I am referring to the gnome-shell activities overview application search as a "dash", analogous to Unity's dash for searching for apps. Although the gnome-shell official documentation is confusing on this, e.g. see [https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet) which calls the gnome-shell launcher bar the "dash".

---

### Post by dewdrop_world on 2012-07-12
> **markbl said:**
> I am referring to the gnome-shell activities overview application search as a "dash", analogous to Unity's dash for searching for apps. Although the gnome-shell official documentation is confusing on this, e.g. see [https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet) which calls the gnome-shell launcher bar the "dash".

Oh, OK, you're using a totally different gnome then. The screenshots on that webpage look nothing like what I'm seeing -- I mean, no resemblance at all. Since there are other gnomes out there, maybe the readme shouldn't assume that specific one.

Anyway, I just had my first problem with it. After waking from sleep, it didn't update for a long time. On other occasions, after waking from a suspended session, it would update for new messages within seconds.

I'm not sure if that's anything you can address in the code. Logging out and logging back in makes it start working again, although that's a bit disruptive to workflow.

Still enjoying the tool, though --
James

---

### Post by markbl on 2012-07-13
> **dewdrop_world said:**
> 
Anyway, I just had my first problem with it. After waking from sleep, it didn't update for a long time. On other occasions, after waking from a suspended session, it would update for new messages within seconds.

gmail-indicator is designed to be very robust and even though it uses push (event) notifications, it will always recover sync within 5 minutes at the worst case after abnormal system or network problems cause notifications to be lost (such as your system suspending). You probably suspended your PC, then immediately resumed it, so at the worst case it may take gmail-indicator a few minutes after this to resync. If your laptop had been suspended longer (i.e. the usual case) it will notify immediately. I'll look to see if I can improve this.

---

### Post by dewdrop_world on 2012-07-13
Okay. My latest observation is, after the computer was suspended overnight, it didn't sync right away. I had finished reading my new e-mail with no activity from the indicator. But a couple of minutes after that, the indicator did pop up with a new message (which arrived after I'd read the other ones).

So it didn't die -- it just took longer than I expected.

Minor quibble -- other than that, it's working perfectly. (It just popped up again! :) )

James

---

### Post by dewdrop_world on 2012-07-13
Hm, no, it seems this time it really has stopped working.

After my first morning session, I suspended it again for about half an hour (took a shower), then came back. Through the gmail web interface, I could see a new message, but no notification. I waited probably about 20-30 minutes, nothing.

So I thought, maybe it needs to get a new push notification to reactivate. So I read the message, and then sent myself a test message. The test message was about 7 minutes ago, as I'm writing this. No notification.

If I logout and login again, I'm sure it will work.

So it seems sporadic. When I woke the machine up first thing this morning, it did start picking up indications after a few minutes. This time, no.

As a workaround, is there a way to restart or reset the process from the command line? That would be better than logout/login.

James

PS I'm familiar with git, so just advise of any updates, I'll know how to get them.

---

### Post by markbl on 2012-07-13
> **dewdrop_world said:**
> Hm, no, it seems this time it really has stopped working.

dewdrop, I guess this thread is not really the place for discussions about issues pertaining to gmail-indicator. Please raise an issue with your description above at [https://github.com/bulletmark/gmail-indicator](https://github.com/bulletmark/gmail-indicator). If you don't want to create a (free) github account to do this then I will create an issue on your behalf. All further dialog about this should be entered there.

PS later edit: I added this (and described how to restart gmail-indicator) as [issue 3 at github](https://github.com/bulletmark/gmail-indicator/issues/3).

---

### Post by dewdrop_world on 2012-07-13
> **markbl said:**
> PS later edit: I added this (and described how to restart gmail-indicator) as [issue 3 at github](https://github.com/bulletmark/gmail-indicator/issues/3).

Good point- future observations will go into the issue tracker.

I already have a github account, but you beat me to it- I'll add your repository to my watch list.

Thanks for the tip on restarting. Will try it tomorrow if it occurs again.

Really appreciate your work on this.

James

---

### Post by dewdrop_world on 2012-07-17
Closing the book on this, for the benefit of other readers -- it turns out that the failures on my machine are because of a bug in the notification daemon, which affects some (but apparently not all) installations. The bug limits the size of the notification queue to 20, and at the same time, doesn't remove notifications from the queue unless the user actively clicks the X button. If you have a lot of e-mail coming in and you're not quick with the mouse, of course you'll reach that limit quickly.

Mark added a configuration option to ~./gmail-indicator.rc:

```
notify = false
```

Now the indicator will change the color of the envelope icon and show the right number of unread messages, but not pop up a notification and not run into the limit.

Thanks again to Mark!
James

---

### Post by ammofreak on 2012-07-17
As an aside from the classic email notifiers: I finally ended up with Popper. Been using it for over 2 years now & it's great. Good for IMAP & POP. Go to _[https://launchpad.net/~ralf.hersel/+archive/rhersel-ppa](https://launchpad.net/~ralf.hersel/+archive/rhersel-ppa)_ if you are interested. Cheers!:D

---

### Post by lapega on 2012-10-25
Not working with 12.10. :(

---

