---
title: "Desktop cube broke my compiz"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Ntgeorge on 2011-04-29
Hello,

I was just experimenting with compiz effects on Natty 11.04, and when I clicked desktop cube (which I'm assuming you're not supposed to do, haha), my compiz broke. The pop up windows are way at the top of the screen, almost out of view, and the windows lack the close, minimize, and maximize buttons. I tried reinstalling all the compiz plugins, and when I rebooted I had the same problem! I am using metacity right now, but I would be very sad if i was stuck with it. Could somebody explain to me how to fix compiz?

Thanks,
Nathan.

---

### Post by RJ12 on 2011-04-30
Ok, try disabling the desktop cube and then running

```
unity --reset
```

---

### Post by manzdagratiano on 2011-04-30
I have enabled desktop cube on mine as well, and the first thing that happened on BOTH my laptops was exactly the same - compiz immediately broke. What I needed to do to fix the scenario was to reopen Compiz Config Settings Manager, only to see that many of the original plugins - Window decorations, etc etc - had been disabled. I enabled them one by one, and I was back in action. I got this working with the desktop cube on both Unity and Ubuntu Classic.

---

### Post by EGamerHDK on 2011-04-30
Hey guys, long time windows user. (Self proclaimed expert) hahahah
First time doing this whole linux thing. Downloaded and installed ubuntu. Worked perfectly. Unity and all. I installed compiz and clicked desktop cube and all my windows borders and everything went away. I rebooted and all I get is a blank desktop and about 2 seconds in I get the little notification of my wireless connecting. No way to "restore" like in windows... huh?
Ugh. I've been trying for over an hour and can't get it to budge. ANy suggestions?

---

### Post by chirag64 on 2011-04-30
Hey guys, u may have to reinstall compiz...
Try these link out...and plz do reply if any of those helped u out..
[http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)

[http://ubuntuforums.org/showthread.php?t=439745](http://ubuntuforums.org/showthread.php?t=439745)

Ohh...and incase you have a blank desktop and don't know how to open terminal, try **Ctrl+Alt+T**

---

### Post by EGamerHDK on 2011-04-30
Sorry, new user question again. Whats the command to restart the computer from the terminal?

**EDIT:** That first link worked!!!!!!!!!!!!

Thank you so much!

---

### Post by Ntgeorge on 2011-04-30
In order to try the first suggestion, I had to log out and change from ubuntu classic to unity. When I logged in, I got a completely blank screen with only my background, as the other posters have said. The shortcut "ctrl+alt+t" doesn't open a terminal window. I can't log out to switch back to ubuntu classic now... what do I do?

---

### Post by Krytarik on 2011-04-30
> **Ntgeorge said:**
> In order to try the first suggestion, I had to log out and change from ubuntu classic to unity. When I logged in, I got a completely blank screen with only my background, as the other posters have said. The shortcut "ctrl+alt+t" doesn't open a terminal window. I can't log out to switch back to ubuntu classic now... what do I do?
Just create a launcher at your desktop for the command "ccsm" (CompizConfig Settings Manger), launch it and re-enable the "Ubuntu Unity Plugin", keep "Desktop Cube" enabled if you want to use it, the same for "Rotate Cube", and check if there are other plugins that have been disabled in the process.

---

### Post by chirag64 on 2011-04-30
> **Ntgeorge said:**
> In order to try the first suggestion, I had to log out and change from ubuntu classic to unity. When I logged in, I got a completely blank screen with only my background, as the other posters have said. The shortcut "ctrl+alt+t" doesn't open a terminal window. I can't log out to switch back to ubuntu classic now... what do I do?

Try pressing **Ctrl+Alt+L** or **Ctrl+Alt+Del**
Press **Ctrl+Alt+F1**, u will get a black-and-white screen. Login to it...
then enter the command
**gnome-session-save --logout**
Then press **Ctrl+Alt+F8**
That sud get u back to the logged out screen

---

### Post by EGamerHDK on 2011-04-30
Okay, so I tried "Wobbly Windows" and the left side bar stayed there but, the one on the top went away. Did the usual unity reset after I disabled it and it worked. Now, I'm just going to stop experimenting and ask if anyone knows how to enable the box and wobbly windows with my system settings staying the same.

I understand that most likely I have to enable these features and then install unity again, but I'm going to just put the question out there for now. Thanks in advance

---

### Post by chirag64 on 2011-04-30
Yeah, the bar on the top seems to go away for me as well whenever I change anything in CCSM, its probably a bug in CCSM.
After u finish setting everything up, just logout and log in again. Everything should be back to normal :)

And btw, please create a new thread if u've a question unrelated to the thread's original question :)

---

### Post by EGamerHDK on 2011-04-30
Alright, thanks!

---

### Post by Ntgeorge on 2011-04-30
> **Krytarik said:**
> Just create a launcher at your desktop for the command "ccsm" (CompizConfig Settings Manger), launch it and re-enable the "Ubuntu Unity Plugin", keep "Desktop Cube" enabled if you want to use it, the same for "Rotate Cube", and check if there are other plugins that have been disabled in the process.

I have been looking through the ccsm settings, and I don't see a ubuntu unity plugin anywhere.

**Edit:** This is getting ridiculous. I get an error when I try to open a terminal window. Probably just going to have to reinstall and go back to 10.10. This is WAY too buggy...

---

### Post by chirag64 on 2011-04-30
> **Ntgeorge said:**
> I have been looking through the ccsm settings, and I don't see a ubuntu unity plugin anywhere.

I think u should be using Unity 3D (the one that comes by default with Ubuntu 11.04) and should be using that desktop environment to see that plugin.
Use search in CCSM to find it. Its under Desktop category.
Also, try updating ur CCSM and Unity if u still don't find it.

---

### Post by Ntgeorge on 2011-04-30
I fixed it! All I had to do was wipe my hard drive and reinstall with Ubuntu 10.10. Worked like a charm!

...Not cool Natty.

---

### Post by Krytarik on 2011-04-30
> **Ntgeorge said:**
> I fixed it! All I had to do was wipe my hard drive and reinstall with Ubuntu 10.10. Worked like a charm!
As if Maverick is *that* more stable, remember the theme bug and numerous other issues, which I don't have in Lucid. If you are to go for long-lasting Gnome 2, and mostly bug-free Ubuntu experience, you should have installed those instead. I don't have to care until the end of April 2013. ;-)

---

### Post by Eversmann on 2011-04-30
Same problem here. I've upgraded from 10.10, and when i disable the desktop wall and click to enable the cube... suddenly all the settings in the compiz manager dissapears, the decorator gets vanished, and the only solution is logging out-in. (all the time in ubuntu classic, not unity).

I returned compiz to default using the commands, and also removed and purged the compiz packages and then reinstall it. It's there a big bug there. Heading to launchpad ;-)

---

### Post by Krytarik on 2011-04-30
> **Eversmann said:**
> Same problem here. I've upgraded from 10.10, and when i disable the desktop wall and click to enable the cube... suddenly all the settings in the compiz manager dissapears, the decorator gets vanished, and the only solution is logging out-in. (all the time in ubuntu classic, not unity).
But after relogin, does Compiz work as expected?

---

### Post by kansas_plainsman on 2011-05-01
> **RJ12 said:**
> Ok, try disabling the desktop cube and then running

```
unity --reset
```

I had the same problem and used the reset trick - and the desktop did get corrected - but I notice that the terminal session in which it is executed never lets go of the command, getting system status messages about various things going on with the desktop manager (some of them notices of failures)

If I ctrl-C out of the session, the desktop reverts to the screwed-up state.

Something else going on here?

---

### Post by Krytarik on 2011-05-01
Try modifying the settings in CCSM directly by following my earlier post #8 in this thread.

---

### Post by wilee-nilee on 2011-05-01
You can have the cube use with caution is all I'm going to say.
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

---

### Post by Krytarik on 2011-05-01
> **wilee-nilee said:**
> You can have the cube use with caution is all I'm going to say.
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)
I have that in my bookmarks, too, but it eventually turned out that there is really no need for doing such a complicated approach.

---

### Post by wilee-nilee on 2011-05-01
> **Krytarik said:**
> I've that in my bookmarks, too, but there is really no need for doing such a complicated approach.

I did the cheat, just turned of the automatic plugin control and moved the desktop to the left then the cube and rotate to the right. As I said use caution.

---

### Post by Krytarik on 2011-05-01
Another approach, that is of interest for users who didn't already screw up their Compiz settings, is 'gconf-editor' based, *mc4man* wrote a post about it at the release day, I noticed it shortly after I bookmarked the other one:
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

But the path to the respective key of the Unity profile is actually "/apps/compizconfig-1/general/screen0/options/active_plugins". And that may even wary if you have a multiple screen setup.

And if you killed your Compiz anyway before, you can just run "ccsm" through a launcher at your desktop, like described, and enable all needed/wanted plugins there, but the "Ubuntu Unity Plugins" as the last.

---

### Post by Mad-Halfling on 2011-05-01
I'm getting hit by this in the release version of Natty.  I had everything working fine in 10.10 and then upgraded. I reverted back to the Classic Ubuntu but as soon as I disabled the Wall it removes all title bars on my windows. If I enable Window Decoration they partially reappear but I can't actually move or resize the windows.  I've tried purging and reinstalling compiz, as well as resetting my GNOME compiz setting and even removing .gconf .gconfd and .gnome2 and restarting to reset them, but as soon as I disable the desktop wall it fracks everything again.  Anyone any ideas how I can revert back and get my compiz cube back (I actually use it a lot functionally so it's not just for the eye-candy aspect of it).

Cheers MH

---

### Post by chirag64 on 2011-05-01
Ever since Ubuntu 11.04 is out, Compiz is getting more infamous than ever before :(
I'm quite sure they will get it fixed by 11.10 though :)
But if u plan to stick to gnome, u're in for a suprise coz from 11.10, Gnome 3 will be out which is similar to Unity (but does not use compiz).
So be ready with more criticism? :P

---

### Post by TrakerJon on 2011-05-01
> **Krytarik said:**
> As if Maverick is *that* more stable, remember the theme bug and numerous other issues, which I don't have in Lucid. If you are to go for long-lasting Gnome 2, and mostly bug-free Ubuntu experience, you should have installed those instead. I don't have to care until the end of April 2013. ;-)

Um Maverick is a lot more stable...Natty is buggy as hell.

Traker

To reset Compiz to default settings...

Open a terminal window (**Ctrl+Alt+T**) and run the following command:

**gconftool-2 --recursive-unset /apps/compiz**

Restart the computer.

---

### Post by Eversmann on 2011-05-01
> **Krytarik said:**
> But after relogin, does Compiz work as expected?

Yes, after relogin, everything is "unity" default.

I've searched for this issue in launchpad and it seems to be a bug in ccsm.

Well, actually, there are two things that make me not switch to unity: the left bar (i prefer Docky), and not having the cube. Believe it or not, for me it was a more productive way: i was able to throw windows to left and right and move around without having to move my left and right hand from the keyboard and mouse. (and, of course, it has more candyness :D )

---

### Post by Sun_Coaster on 2011-05-01
> **chirag64 said:**
> 
But if u plan to stick to gnome, u're in for a suprise coz from 11.10, Gnome 3 will be out which is similar to Unity (but does not use compiz).
So be ready with more criticism? :P

I had the same problem, so installed Gnome 3 on 11.04.
It's stable so far, and is pretty usable with cairo docks. 
It lacks eye candy, but that will come I guess.

I had no patience with unity (looks like a phone OS - totally not cool for uber-cyber-techno-geeks who like to tinker).

.

---

### Post by Krytarik on 2011-05-01
> **Eversmann said:**
> Believe it or not, for me it was a more productive way: i was able to throw windows to left and right and move around without having to move my left and right hand from the keyboard and mouse. (and, of course, it has more candyness :D )
I'm using "Desktop Wall" for exact the same feature, but of course without the effects of "Desktop Cube". I really don't like too much effects, and my machine can't cope with that very well anyway, because it's some 10 years old.

Can you switch to "Desktop Cube" and "Rotate Cube" by following either my posts #8 or #24 in this thread?

---

### Post by Krytarik on 2011-05-01
> **Sun_Coaster said:**
> I had the same problem, so installed Gnome 3 on 11.04.
It's stable so far, and is pretty usable with cairo docks. 
It lacks eye candy, but that will come I guess.
Did you at least install the themes like described in this guide?:
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

---

### Post by Sun_Coaster on 2011-05-02
@ Krytarik
Thanks for the pointer. 
Yes, I'm using the tweaker for themes in Gnome3
I'm looking forward to things like the compiz cube...

So far Gnome 3 is looking like a keeper. (Might try XFCE tomorrow !)
Rob

---

### Post by chirag64 on 2011-05-02
> **Sun_Coaster said:**
> I had the same problem, so installed Gnome 3 on 11.04.
It's stable so far, and is pretty usable with cairo docks. 
It lacks eye candy, but that will come I guess.

I had no patience with unity (looks like a phone OS - totally not cool for uber-cyber-techno-geeks who like to tinker).

.

Yes, thats coz it is kept in mind that the OS may be used in Tablets in near future :)

---

### Post by brad1138 on 2011-05-03
> **Mad-Halfling said:**
> I'm getting hit by this in the release version of Natty.  I had everything working fine in 10.10 and then upgraded. I reverted back to the Classic Ubuntu but as soon as I disabled the Wall it removes all title bars on my windows. If I enable Window Decoration they partially reappear but I can't actually move or resize the windows.  I've tried purging and reinstalling compiz, as well as resetting my GNOME compiz setting and even removing .gconf .gconfd and .gnome2 and restarting to reset them, but as soon as I disable the desktop wall it fracks everything again.  Anyone any ideas how I can revert back and get my compiz cube back (I actually use it a lot functionally so it's not just for the eye-candy aspect of it).

Cheers MH

Same problem verbatim, any solutions yet?

---

### Post by Krytarik on 2011-05-04
> **brad1138 said:**
> Same problem verbatim, any solutions yet?
If you want to use "Desktop Cube" instead of "Desktop Wall", try the approach under the title "Update: An alternative gui way" in this guide:
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

Greetings.

---

### Post by azupan on 2011-05-04
I suspect an insidious bug in CCSM. When you enable/diable Cube or Wall, all settings are reset for a moment, and Compiz goes haywire.
 
Solution: Don't enable/disable wall or cube while Compiz is running. Do it in safe mode. Or, ignore the weird stuff your desktop is doing, and make logoff/logon.
 
Once you've managed to enable the cube & disable Desktop Wall, everything should work fine.

---

### Post by brad1138 on 2011-05-04
> **azupan said:**
> I suspect an insidious bug in CCSM. When you enable/diable Cube or Wall, all settings are reset for a moment, and Compiz goes haywire.
 
Solution: Don't enable/disable wall or cube while Compiz is running. Do it in safe mode. Or, ignore the weird stuff your desktop is doing, and make logoff/logon.
 
Once you've managed to enable the cube & disable Desktop Wall, everything should work fine.

I have 2 logins, 1 Gnome, 1 Unity. I am just going to stick with wall for now. I figure within a month or so they will have Compiz fixed and I wont have to jump through any hoops to activate it.

Thanks,
Brad

---

### Post by pritam_par on 2011-08-10
The very same issue is solved here

[http://ubuntuforums.org/showthread.php?t=1747045](http://ubuntuforums.org/showthread.php?t=1747045)

---

### Post by flobadobbob on 2011-09-15
Hello,
I had the very same problem, activated cube and then unity stopped working.
got it fixed, went into ubuntu classic at the logging page, form there i turned on unity plugin again and turned off cube. logged out then logged into ubuntu, crtl+alt+F2 to get to terminal. there i used the unity --reset command that was mentioned earlier. 
i didn't know how to restart from terminal so i forced a shutdown using the power button(probably not a good idea) when i logged back in unity was flying along like it should.
I am completely new to ubuntu and linux, only got it yesterday. running alongside windows 7.
thank you to everyone that gave help on this thread.

---

### Post by Andrew_nuts on 2012-02-19
> **RJ12 said:**
> Ok, try disabling the desktop cube and then running

```
unity --reset
```

This code works great thanks.:)

---

### Post by jetta on 2012-03-30
> **Krytarik said:**
> Just create a launcher at your desktop for the command "ccsm" (CompizConfig Settings Manger), launch it and re-enable the "Ubuntu Unity Plugin", keep "Desktop Cube" enabled if you want to use it, the same for "Rotate Cube", and check if there are other plugins that have been disabled in the process.

works with me after compiz crash and my dektop menu disappear..

---

