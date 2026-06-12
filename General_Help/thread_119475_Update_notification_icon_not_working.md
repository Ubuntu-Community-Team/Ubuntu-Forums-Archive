---
title: "Update notification icon not working"
date: 2006-01-19
forum: General Help
---

### Post by pbb on 2006-01-19
I think I've disabled the Update Notification icon somewhere. I used to get very regular update notifications, but I haven't seen anything anymore for the last week or so.
When I do "sudo apt-get upgrade", it does start installing updates.

Does anybody have a clue what I did wrong? I am just a newbie... I would like to have my graphical update notification icon back!

---

### Post by dcstar on 2006-01-19
[QUOTE=pbb]I think I've disabled the Update Notification icon somewhere. I used to get very regular update notifications, but I haven't seen anything anymore for the last week or so.
When I do "sudo apt-get upgrade", it does start installing updates.

Does anybody have a clue what I did wrong? I am just a newbie... I would like to have my graphical update notification icon back![/QUOTE]
System-Administration-Update Manager-Preferences-Settings

---

### Post by pbb on 2006-01-19
[QUOTE=dcstar]System-Administration-Update Manager-Preferences-Settings[/QUOTE]

All options there are checked. The other values:
* Update interval: 1
* Clean interval: 1
* Maximum size: 500
* Maximum age: 30

There are 3 available updates, but still I am not getting any update notifications. Anybody knows what is going wrong here?

---

### Post by dcstar on 2006-01-19
[QUOTE=pbb]All options there are checked. The other values:
* Update interval: 1
* Clean interval: 1
* Maximum size: 500
* Maximum age: 30

There are 3 available updates, but still I am not getting any update notifications. Anybody knows what is going wrong here?[/QUOTE]
Did you install a new Desktop Theme recently?

The other thing would be that you somehow managed to remove the "Notification Area" from your panel.

---

### Post by pbb on 2006-01-20
The notification area is there (I am currently looking at the Firestarter and Gaim icons). And I am using the default Human theme.

Thanks for helping, does anybody have more ideas?

---

### Post by Horndog on 2006-01-20
[QUOTE=pbb]The notification area is there (I am currently looking at the Firestarter and Gaim icons). And I am using the default Human theme.

Thanks for helping,[color=red] does anybody have more ideas?[/color][/QUOTE]
Try right clicking on the panel and choose "Add to Panel" then in the utilities area at the bottom choose "Notification Area".

---

### Post by DaMasta on 2006-01-20
Try running update-notifier from the command line. See if it gives any output. Chances are it'll pop up in the tray. Save your session on exit. If all else fails, add update-notifier to your saved session in preferences.

---

### Post by manicka on 2006-01-20
Go to apps-->update-notifier in the Configuration Editor and check if the 'no_show_notifications' box is checked.

---

### Post by pbb on 2006-01-21
[QUOTE=Horndog]Try right clicking on the panel and choose "Add to Panel" then in the utilities area at the bottom choose "Notification Area".[/QUOTE]

I did that, and it just gives me an empty panel. When I remove the existing Notification Area, all icons in there move to the newer Notification Area. Still no update notification.

---

### Post by pbb on 2006-01-21
[QUOTE=DaMasta]Try running update-notifier from the command line. See if it gives any output. Chances are it'll pop up in the tray. Save your session on exit. If all else fails, add update-notifier to your saved session in preferences.[/QUOTE]

Thanks, I was thinking about that also, but I didn't know what the command for it should be. I ran it, and the reply was:
```
** (update-notifier:11734): WARNING **: already running?
```

---

### Post by pbb on 2006-01-21
[QUOTE=manicka]Go to apps-->update-notifier in the Configuration Editor and check if the 'no_show_notifications' box is checked.[/QUOTE]

Interesting, I went to Applications > System Tools > Configuration Editor > /apps/update-notifier, and the *only* option there is called "default_action", with a value of "1". Would this be the problem?

---

### Post by adam.tropics on 2006-01-21
same here, plus in configuration editor, apps-->update notifier has only 1 key, default action. in the documentation box i get a warning, this key has no schema.

---

### Post by manicka on 2006-01-21
[QUOTE=adam.tropics]same here, plus in configuration editor, apps-->update notifier has only 1 key, default action. in the documentation box i get a warning, this key has no schema.[/QUOTE]

This is what mine looks like
[IMG]http://img296.imageshack.us/img296/5417/screenshotconfigurationeditoru.jpg[/IMG]

I have the notification bubble turned off, but the update icon appears in the notification area.

You can add the missing key by right clicking in the key field and choosing 'New Key...', then add the values like the image below. 'False' will show the notification bubble, 'True' will turn it off.

[IMG]http://img296.imageshack.us/img296/9017/screenshotnewkey2sr.png[/IMG]

---

### Post by astronerd on 2006-01-21
I am having the same problem of the update notifier sometimes(most of the time) not showing up.  But when I went to the config editor I didnt have an update-notifier choice in the list.  It wasnt there, how do I get it to be in the list?

---

### Post by timczer on 2006-01-22
I have the same issue as astronerd, except that since I have installed breezy final, I have not been able to get the update notifier to show up in the notification area.  I have uninstalled and reinstalled the notification area, and the update notifier and it still doesn't work.  I don't find update notifier any where in the configuration editor.

---

### Post by adam.tropics on 2006-01-22
Snap! Manicka has more choices than I have here. Although it has worked all ok in the past I'm not entirely sure when it stopped.

---

### Post by martinbures on 2006-01-23
[QUOTE=Horndog]Try right clicking on the panel and choose "Add to Panel" then in the utilities area at the bottom choose "Notification Area".[/QUOTE]


THANK YOU.  Man.  That made no sense.  My updater was working but GAIM and Amarok would just disappear when I closed them and it was driving me nuts.  I love linux and would never go back, but sometimes there are so many options that you lose the little things - I would have definitely never thought of this on my own.  

Again - cheers.  Later.

---

### Post by pbb on 2006-01-23
Okay, I've added the no_show_notifications item and unchecked it. Two new updates are available now, but I still don't get any notification icon or message.

PS1: Manicka, you have an "update-notifer" item in your tree. Very weird...

PS2: An item named "no_show_notifications" is *bad naming*. It should either be "suppress_notifications" or better yet "show_notifications" and have an inverted value. But that's a remark that should be made to the programmer, and off-topic here.

---

### Post by ardchoille on 2006-01-23
I don't have apps/update-notifier in gconf-editor at all, but my update notification icon works fine, odd.

---

### Post by dcstar on 2006-01-23
[QUOTE=ardchoille]I don't have apps/update-notifier in gconf-editor at all, but my update notification icon works fine, odd.[/QUOTE]
Same here.

---

### Post by pbb on 2006-01-24
Okay, so update-notifier does not seem to be the solution. Does someone have other suggestions?

---

### Post by manicka on 2006-01-24
[QUOTE=pbb]All options there are checked. The other values:
* Update interval: 1
* Clean interval: 1
* Maximum size: 500
* Maximum age: 30
[/QUOTE]

hmm, I'm running out of ideas. You may not being seeing the notfication because you have the updates set to automatically download when available.

My preferences in the update manager look like the screenie at the link below. 
[[IMG]http://img7.imageshack.us/img7/7852/screenshotsettings5ga.th.jpg[/IMG]](http://img7.imageshack.us/my.php?image=screenshotsettings5ga.jpg)

---

### Post by pbb on 2006-01-24
[QUOTE=manicka]hmm, I'm running out of ideas. You may not being seeing the notfication because you have the updates set to automatically download when available.[/QUOTE]

Yeah that also came to my mind, I've disabled automatic downloads but still nothing. I've copied your settings literally now...

---

### Post by pbb on 2006-01-24
I've killed update-notifier, and restarted it from a terminal window, but I got no messages about problems...
Could there be a logfile I should check for problems?

---

### Post by manicka on 2006-01-24
Do you know for certain that there are updates available?

---

### Post by pbb on 2006-01-24
[QUOTE=manicka]Do you know for certain that there are updates available?[/QUOTE]

When I run the Update Manager, I get to see two available updates at the moment. I guess all updates should always trigger the alert? Also after restarting update-manager, or after a reboot, I get to see no alert.

---

### Post by manicka on 2006-01-24
[QUOTE=pbb]When I run the Update Manager, I get to see two available updates at the moment. I guess all updates should always trigger the alert? Also after restarting update-manager, or after a reboot, I get to see no alert.[/QUOTE]

I can only suggest to install those and see what happens when the next lot of updates are available

---

### Post by pbb on 2006-01-24
[QUOTE=manicka]I can only suggest to install those and see what happens when the next lot of updates are available[/QUOTE]

Yeah, I already tried that with the previous set of updates :-| 
Sorry to be so difficult...

---

### Post by manicka on 2006-01-24
[QUOTE=pbb]Yeah, I already tried that with the previous set of updates :-| 
Sorry to be so difficult...[/QUOTE]

That's ok :) , your problem really has me stumped though

---

### Post by pbb on 2006-01-24
Any logfiles I could check?

---

### Post by pbb on 2006-01-24
Anybody online now who has any ideas?

---

### Post by ktogias on 2006-01-28
I also have the same problem. Update notifier doesn't notify me of any updates. I am on Breezy updated from hoary before several months. Update notifier used to work before about three weeks... The only "major" thing I remember doing to my system since then is running ubuntu Automatix script ([http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")).

So, update-notifier is running.

In System -> System management -> Update Manager -> Preferences -> Configuration  the checkbox for "Automatic check for updates" is checked and the interval is 1 days.

In gnome configuration editor i have no apps->update notifier entry.

I have intalled several updates with apt-get update && apt-get upgrade but never seen the notifier icon at the notification area. (The notification area is working)

I killall update-notifier and then run it again from a terminal while having available updates to install, and the only thing i notice happening is other icons in gnome notification area moving some milimeters to the right, but after that no update-notification icon or popup appears. I get no messages from update-notifier on the terminal.

I hope I have described the situation in the most detail I can. I am wondering wether the malfunction of update-notifier is connected in any way to the installation and execution of Automatix script of not...

If anyone has any other suggestions on where to look for the solution please *NOTIFY* me.

---

### Post by ktogias on 2006-01-28
Hey, I think I just solved it!!!

I killed update-notifier and then I did rm -Rf ~/.update-notifier/ . I run update-notifier again and the post-configuration notification icon about some language packages i had just upgraded.

I have no more updates available to test if the notification will popup... If anyone has not installed updates please try this and tell me if the update-notifier works after deleting ~/.update-notifier/ . (I will post again if/when I see it popping up in a couple of days - when more updates will be available - ).

---

### Post by pbb on 2006-01-28
[QUOTE=ktogias]Hey, I think I just solved it!!![/QUOTE]

Hmm... I just killed update-notifier, removed the ~./update-notifier directory, and started update-notifier again. I did not notice anything happening however. :cry:

The ~./update-notifier directory used to have one file in it, it is now re-created with no files in it.

I do have 4 updates waiting to be installed, according to Update Manager.

---

### Post by ktogias on 2006-01-28
Too sad... But the fact that the post-configuration notification icon poped up to  me means that update-notifier realy runs and is able to display icons on the notification area... It seems like for some reason it does not detect that there are available updates...

---

### Post by pbb on 2006-02-01
This is a long shot, but does anybody have anything else that may help?
I've seen there is a newer update-notifier in the Dapper repository, would it help to install that?

---

### Post by fantan on 2006-02-02
Hello!
In conjuction with this topic I have the following problem:
The update-notifier icon in my system is visible at the system tray (notification area) but if I push on it, the update-manager doesn't start at all!
When I type in terminal the command: update-manager, I get the error:

"root@ubuntu:~# update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 31, in ?
    import gnome
ImportError: No module named gnome
root@ubuntu:~#"

And now I have to start the Synaptic ->Update->Select all updates->Apply, to download the updates.

What does it mean and how to resolve this problem to get update-manager to work properly?

Thanks!

Fantan

---

### Post by pbb on 2006-02-05
Bump for the so many'th time... Does anybody have any ideas where I can look for solutions?

Are there any logs I should check? Any other hidden place where error messages might have come up? Any other places/forums where I could find people who know more about it?

I have to say that using Linux is starting to be quite frustrating... Programs not working, huge fontsizes that aren't obeying the settings, a scanner that used to function but now can't be found anymore... Huffff...

---

### Post by dcstar on 2006-02-05
[QUOTE=pbb]
.......
I have to say that using Linux is starting to be quite frustrating... Programs not working, huge fontsizes that aren't obeying the settings, a scanner that used to function but now can't be found anymore... Huffff...[/QUOTE]
Given that you have these other issues, it seems apparent that you have a system that has a fundamental underlying problem, and asking for help to fix one of the symptoms isn't really worth the trouble.

Copy off any important data and reinstall your system on a reformatted partition, then you may find your Linux system as "unfrustrating" as quite a lot of us experience.

---

### Post by timczer on 2006-02-05
I don't think a reinstall is an appropriate answer to this issue.  As represented in this thread, several people have this issue.  Everything else in my system works great, I just have not been able to get the update notifier to work since I installed Breezy.  I can live without the update notifier, it would just be nice to have.  If several people have the issue, there must be an underlying problem that is causing the issue.

---

### Post by Levou on 2006-02-05
Same here.. everything works flawlessly except the update notification icon which worked only a couple of times after installation :-? I run update manager regularly, but I wouldn't mind having the notification icon in the tray as well when new updates are available...

---

### Post by dcstar on 2006-02-06
[QUOTE=timczer]I don't think a reinstall is an appropriate answer to this issue.  As represented in this thread, several people have this issue.  Everything else in my system works great, I just have not been able to get the update notifier to work since I installed Breezy.  I can live without the update notifier, it would just be nice to have.  If several people have the issue, there must be an underlying problem that is causing the issue.[/QUOTE]
There may well be, but now that we (finally) know that the system in question has other significant problems, it is most likely that people have been wasting their time trying to fix one symptom of what is most likely a far more significant issue.

Your issue may be unrelated to the problems and various solutions offered to the OP.

---

### Post by pbb on 2006-02-06
[QUOTE=dcstar]There may well be, but now that we (finally) know that the system in question has other significant problems, it is most likely that people have been wasting their time trying to fix one symptom of what is most likely a far more significant issue.[/QUOTE]

It is not like all these problems all of a sudden appeared at the same time! I've been having the update-notifier problem for at least two weeks now. The scanner problem started a few days ago, it has been working fine even while the update-notifier wasn't working anymore, and the font-problem turned up this weekend. I don't think they are related, but I must add that I am a Linux newbie so I may be totally wrong.

It seems to me there are many more people who have the update-notifier problem, but for most it's just not worth the trouble looking for a solution since there is such an easy work-around.

Reinstalling Linux... My install is a bit older than a month now... I don't think I've ever messed up any operating system so quickly before.

---

### Post by dcstar on 2006-02-06
[QUOTE=pbb]
.....
It seems to me there are many more people who have the update-notifier problem, but for most it's just not worth the trouble looking for a solution since there is such an easy work-around.
.....[/QUOTE]
One thing that might be worth trying is creating a new user (and give it System Admin user privileges).

Then log in and see if the Update Notification appears on the fresh Gnome environment, if it does then that may indicate that your current Gnome user config has got messed up, if not then that is one less thing that could be causing the problem.

---

### Post by pbb on 2006-02-07
[QUOTE=dcstar]One thing that might be worth trying is creating a new user (and give it System Admin user privileges).[/QUOTE]

Thanks for a good suggestion! But nothing seems to happen there either. How long should it take for the updates icon to show up? I still have language-pack-en and language-pack-gnome-en waiting to be updated, but no notification is shown.

---

### Post by hashimoto on 2006-02-07
I'm also with this problem and I have tried to get help earlier. Not available then, but at least you have got more replies than I did. ;-)

Somehow I tend to think that this has something to do with the installation. I did a clean Breezy installatin with the exception of /home. Doesn't work. To my father I did a clean installation (even /home) and update notifier runs fine.

I would be glad to find a solution.

---

### Post by pbb on 2006-02-07
> **hashimoto]I'm also with this problem and I have tried to get help earlier. Not available then, but at least you have got more replies than I did.  said:**
> 

Yeah, I think I've been pestering everybody on the forum quite a bit with this thread...

[QUOTE=hashimoto]Somehow I tend to think that this has something to do with the installation. I did a clean Breezy installatin with the exception of /home. Doesn't work. To my father I did a clean installation (even /home) and update notifier runs fine.

Hmm, mine was a clean installation. In fact, my first try at Linux at all. Did your update-notifier never work? Because mine definetly worked in the beginning, it has stopped notifying me after a few weeks of operation.

[QUOTE=hashimoto]I would be glad to find a solution.[/QUOTE]

Me too! Like I said, the work-around is quite easy. (Just launch Update Manager.) But it is also a thing for me that I *believe* this should be easily fixable, and I think I would learn a lot about using Linux by fixing it. But it seems I do need the assistance of an expert in figuring it out.

---

### Post by dcstar on 2006-02-09
[QUOTE=pbb]
......
Me too! Like I said, the work-around is quite easy. (Just launch Update Manager.) But it is also a thing for me that I *believe* this should be easily fixable, and I think I would learn a lot about using Linux by fixing it. But it seems I do need the assistance of an expert in figuring it out.[/QUOTE]
I just noticed that the Update Notify process is run under Python, so perhaps if there is a problem with Python scripts running it could also affect this.

Perhaps a re-install of the Python stuff might be worth a try?

I also believe it uses the DBUS system, and that can be monitored to see if the messages go through.

I also notice that the /var/lib/update-notifier/dpkg-run-stamp file seems to be updated on a regular basis, this might also be worth checking, along with:

apt-config dump

for info on how your apt is set up.

---

### Post by Horndog on 2006-02-17
I was very surprised when  I got an update notification, first one in at least a month.  I wrote it off as unfixable. Any one else, who had problems, get one today ?

---

### Post by pbb on 2006-02-17
I would love to test, but my PSU died, so I can't access my computer. I'll give you an update when I've received a replacement...

---

### Post by simber on 2006-03-07
What im going to write in not to blame Automatix, i wrote to Arnieboy and he told me that automatix does not do anything to the update-notifier, but after i run it, the icon disappeared.

I repeat im not blaiming anybody, but perhaps automatix and update notifier have a conflict between them.

---

### Post by dunnerz on 2006-03-08
[QUOTE=simber]What im going to write in not to blame Automatix, i wrote to Arnieboy and he told me that automatix does not do anything to the update-notifier, but after i run it, the icon disappeared.

I repeat im not blaiming anybody, but perhaps automatix and update notifier have a conflict between them.[/QUOTE]

both me and my work collegue have installed automatix and the update notifier has dissapeared.

I'm not suggusting it is an issue with automatix, but perhaps one of the items it installs?



I have also recently installed KBUNTU, I wonder if any of its apps conflict (apedt??). 

Also, when I bring up the "system-monitor" update notifier is running as expect, but with the arguments --sm-config-prefix /Update-notifier-fvTukk  --blah, etc. --screen 0

I wonder if this config option is anything to do with it?

---

### Post by sizzam on 2006-03-09
I also started with a fresh install of Ubuntu Breezy, installed some things via Automatix, and now my update-notifier icon is gone.

Curiously, here is a new piece to the puzzle, I'd like to see if anyone else can confirm this behavior:

Kill the update-notifier process

Then, from the terminal issue the 'update-notifier' command and watch your notification area as you click enter.  The separator bar moves ever so slightly, like two or three pixels, as if it is putting an empty icon in place.   If I close the terminal, the separator bar moves one pixel back to where it was.

<Edit>
Here is a list of the things I installed via Automatix:

me@mymachine:~$ more automatix.log
Multimedia codecs|MS TTF Fonts|Archives|Acrobat Reader|gftp|Ctrl-Alt-Del|Numlock ON|AUD-DVD codecs|SUN JAVA 1.5 JRE|Eject CD from Drive|DMA ON|NVIDIA cards|Firefox 1.5.0.1|Gnome Sound fix

---

### Post by arnieboy on 2006-03-10
Here is the solution to this problem:
from terminal do:
```
sudo chmod 644 /etc/apt/sources.list
```
after this update-notifier will work as usual.

---

### Post by dcstar on 2006-03-10
[QUOTE=arnieboy]Here is the solution to this problem:
from terminal do:
```
sudo chmod 644 /etc/apt/sources.list
```
after this update-notifier will work as usual.[/QUOTE]
And from reading this I assume Automatix changes the permissions and "breaks" the notifier, if so what permissions did it set?

---

### Post by arnieboy on 2006-03-10
[QUOTE=dcstar]And from reading this I assume Automatix changes the permissions and "breaks" the notifier, if so what permissions did it set?[/QUOTE]
one of the previous releases of Automatix had a screwed up permission setting (600) for sources.list. This problem has been corrected in the latest version.
update notifier runs as normal user and checks the sources.list which it could not till now because of the faulty permission setting. 
This bug had crept in unnoticed a few weeks back till I noticed it and corrected it.

---

### Post by dunnerz on 2006-03-11
Thanks for the help in fixing the problem.

Brilliant.

Cheers \\:D/

---

### Post by Derspankster on 2007-09-27
> **arnieboy said:**
> Here is the solution to this problem:
from terminal do:
```
sudo chmod 644 /etc/apt/sources.list
```
after this update-notifier will work as usual.

Thank you - makes sense. I'll have to wait and see if it works for me (I'm sure it will) since I earlier ran update manager manually.  Thanks again.

---

### Post by Derspankster on 2007-09-29
Strangely, the sudo chmod 644 /etc/apt/sources.list fix worked on my laptop but not my desktop. The only real difference I can think of is that the desktop runs Beryl and the laptop doesn't.  My laptop has a poor video card and can't run Beryl.

EDIT: I had somehow deleted the notification area from the panel properties. I restored that and the notification icon reappeared. Right click the top panel and "add to panel" for addition of notification area. It's under utilities.

---

