---
title: "Program Startup Manager"
date: 2006-12-14
forum: Desktop Environments
---

### Post by Steve S. on 2006-12-14
Hello all!

Just upgraded to edgy and like it overall, just some things to iron out.

How can I select which items I want to run at startup?  I would like to set wlassistant to run at startup.  In dapper there was a gui thing you could select, then add a launcher to run at startup.

I can't find that in edgy.  Can someone please tell me where that is?

---

### Post by ButteBlues on 2006-12-14
System > Preferences > Sessions

Go to the final tab, labeled 'Startup'. Add the name of any programs you wish to have run at startup.

eg. "gaim" and "/usr/bin/gaim" are both valid entries, but "GAIM" is not

---

### Post by p2cd3 on 2006-12-15
Sorry to jump in - am setting up conky & step 6 is:
6. Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot!

I do not have Preferences under the heading System - I've noticed this in a number of posts

I there a program I did not install?

---

### Post by Steve S. on 2006-12-15
> **a simple façade said:**
> System > Preferences > Sessions

Go to the final tab, labeled 'Startup'. Add the name of any programs you wish to have run at startup.

eg. "gaim" and "/usr/bin/gaim" are both valid entries, but "GAIM" is not

Thanks!  That's it exactly!

---

### Post by Steve S. on 2006-12-16
Well, I'm able to change stuff via the gui, but it isn't changing what is actually starting up.  I still have the same stuff starting and I am not able to add/change things.  Sure, it looks like they are changed, but the same stuff starts.

Can I check this via command or is there another option?:-k

---

### Post by ButteBlues on 2006-12-16
> **Steve S. said:**
> Well, I'm able to change stuff via the gui, but it isn't changing what is actually starting up.  I still have the same stuff starting and I am not able to add/change things.  Sure, it looks like they are changed, but the same stuff starts.

Can I check this via command or is there another option?:-k
You could always look at ~/.gnome2/session

---

### Post by Steve S. on 2006-12-16
> **a simple façade said:**
> You could always look at ~/.gnome2/session

What does that show me?  What is currently running?  Could you tell me how to interpret that?  I've never checked that out.  Can i modify that directly to change what start ups at session start?

---

### Post by ButteBlues on 2006-12-16
> **Steve S. said:**
> What does that show me?  What is currently running?  Could you tell me how to interpret that?  I've never checked that out.  Can i modify that directly to change what start ups at session start?
You _could_ but I'd be careful.

It is what the default session loads.

---

### Post by Steve S. on 2006-12-16
> **a simple façade said:**
> You _could_ but I'd be careful.

It is what the default session loads.

Ok, is there another less risky alternative?

---

### Post by ButteBlues on 2006-12-16
> **Steve S. said:**
> Ok, is there another less risky alternative?
Not particularly. :(

---

### Post by Steve S. on 2006-12-16
No dice...it resets itself and starts with the same stuff every time.  Even changes the list back.

I have gdesklets starting and firestarter starting and I don't want them to.  I want to add wlassistant, but it won't let me, even though I've made all these changes in the gui already.

Any ideas?

Now that edgy doesn't let me have my wireless going right at start up, at least I could have wlassistnat run right at start up, then I can select a connection.  That's the plan anyway.

If I can't do that, I've set a launcher for wlassistant, but I still have gdesklets and firestarter starting at start up and no connection for them to work with.  Very annoying...everytime.

Any ideas?  Anyone?

---

### Post by Steve S. on 2006-12-17
Please someone more knowledgable than me about these things help me out...

Perhaps more info will help.

I tried running the Sessions manager from terminal to see if it would provide any answers:
```
gnome-session-properties
```

Then it said this:
```
** (gnome-session-properties:6016): WARNING **: Could not save /etc/xdg/autostart/gnome-volume-manager.desktop file
```

So I looked in /etc/xdg/autostart/gnome-volume-manager.desktop file and it said this:
```
[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=gnome-volume-manager --sm-disable
X-GNOME-Autostart-enabled=true
```

Is any of this of any significance?

---

### Post by Steve S. on 2006-12-19
bump

Anyone have any advise on this?  I still need to be able to fix there and I'm sure there is a way to adjust that besides the gui....one would suppose.

---

### Post by Steve S. on 2006-12-22
Here I am continuing to answer myself in hopes that I'll find an answer and be able to post it, or someone will have pitty on me and tell me what to do. ;) 

I've had a little more success by opening Preferences>Sessions and deleting the current running programs that I don't want to be starting at start up.

Other than that, I still can't add anything.  Anything I'm missing?

---

### Post by infol on 2006-12-26
edit.

you should be able to edit these without being superuser, so there is probably some messed-up ownerships in your configuration files. try 

```
cd ~/.config/
chown -R *username* autostart

```

---

### Post by Steve S. on 2006-12-26
> **infol said:**
> edit.

you should be able to edit these without being superuser, so there is probably some messed-up ownerships in your configuration files. try 

```
cd ~/.config/
chown -R *username* autostart

```

First of all, THANK YOU SO MUCH FOR THIS RESPONSE. 

Oh, I can edit them just fine.  I can change them like gangbusters in the gui.  And they remain changed.  But the changes just have no effect.

For example, I set the startup so that it runs wireless assistant with ```
gksu wlassistant
```.  I enter that in the startup programs, just as I did with Dapper, and it says I've made the changes.  Every time from then on out, after reboot, whenever I check, those changes are shown.

But wlassistant does not run at startup!

Same goes for firestarter.

And I'd like Beryl to run at startup...nothing.

So what's the deal?  Do I still need to change the configuration file as you suggest?  I don't think that's it, but, of course, I'll try just about anything at this point.

---

### Post by infol on 2006-12-27
for ```
gksu wlassistant
```, do you surround the command with quotes (")??

otherwise, session-manager will only run gksu, and without any further reference, gksu won't know what to do...

furthermore, there seems to be some issues with gksu in ubuntu (both dapper and edgy, at least it has not been workning correctly for me...) so try with good old sudo instead.

---

### Post by 3rdalbum on 2006-12-27
Under the "Session Options" tab, is "Automatically save changes to session" checked? If it is, then uncheck it. And "Ask on logout" should be checked.

---

### Post by Steve S. on 2006-12-27
> **3rdalbum said:**
> Under the "Session Options" tab, is "Automatically save changes to session" checked? If it is, then uncheck it. And "Ask on logout" should be checked.

It is...ok, we'll try that and see what happens.

---

### Post by Steve S. on 2006-12-27
Ok...well, it doesn't ask me when I log off.  I tried to just log off and I used the gui to restart, and at neither time does it ask me.

However, when I am up and rolling in X, the sessions gui is automatically running and presented on the screen.

Does that mean something?

---

### Post by Unreadedpost.com on 2006-12-27
help me! 
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by Steve S. on 2006-12-27
Don't know what that was...

I do need help though.:-?

---

### Post by Steve S. on 2007-01-05
Seriously, am I the only one that has problems with this in edgy?  Price of an upgrade rather than a clean install?  Can anyone please tell me where I can look for this?

---

### Post by Steve S. on 2007-01-05
> **infol said:**
> for ```
gksu wlassistant
```, do you surround the command with quotes (")??

otherwise, session-manager will only run gksu, and without any further reference, gksu won't know what to do...

furthermore, there seems to be some issues with gksu in ubuntu (both dapper and edgy, at least it has not been workning correctly for me...) so try with good old sudo instead.

Thanks, I'll try that tonight...hopefully it will take care of this.

---

### Post by Steve S. on 2007-01-06
All right, I know others are having issues like this with edgy, 'cause I've seen it posted.  The Sessions gui does not get the job done, 'cause nothing has been saved.

This thread gave me the tools to figure it out:
[http://www.ubuntuforums.org/showthread.php?t=297271&highlight=Metacity+removed+from+startup]("http://www.ubuntuforums.org/showthread.php?t=297271&highlight=Metacity+removed+from+startup")

Oddly enough, I have't been able to get it to work with regards to Metacity, as the name of the thread dictates, but I have been able to get it to work with most everything else that I wanted to run at startup.

According to the thread, the startup items are in  ~/.config/autostart, "~" being, in this case, /home/(username).  So I ran this:
 ```
cd ~/.config/autostart 
```then, once I was in the autostart directory, I ran ```
ls 
```just to see what was in there.

Sure enough, the few items that had been running in startup had their files there.  So, copying them, I added a few more files.  For example, I didn't have firestarter running, so, still in the autostart directory, I ran this:
```
sudo gedit firestarter.desktop
```
which effectively created a new file in the autostart directory named firestarter.desktop.  Then, once the file opened, I put this in it, having already looked up my version of firestarter:
```
[Desktop Entry]
Name=Firestarter
Encoding=UTF-8
Version=1.0.3
Exec=gksu firestarter
X-GNOME-Autostart-enabled=true
```

Just like that (including the brackets) as that was what worked in the other files.  Of course, changed the name, version, exec command and the like to suit my needs for whatever item I wanted to run at startup.  Saved it, closed it.

Sure enough, on the next start up, I had firestarter up and running.  This also worked for gdesklets as well, I know for sure.  I think I may have the wrong launcher to start metacity, so if anyone knows that (or gets this to work for metacity window manager) then please post your successes.

Hope this helps.  Please post back if it did.

---

### Post by kuripot on 2007-01-14
I'm having a similar problem to steve s. On startup, I have 3 windows opening on everytime, with all sessions:
1. gnome-terminal
2. nautilus file browser
3. gnome-session manager

Here's what's in ~/.config/autostart/
```
ls ~/.config/autostart/
beryl-manager.desktop          gnome-volume-manager.desktop
gnome-settings-daemon.desktop  xmodmap.desktop
```

I believe this started when I was messing around with sessions manager. I wanted to have a terminal open on startup and thougth that leaving one open on logout would do the trick. Apparantly it did, but with the other 2 windows open as well.

How do I remove these on startup?

---

### Post by Steve S. on 2007-01-14
> **kuripot said:**
> I'm having a similar problem to steve s. On startup, I have 3 windows opening on everytime, with all sessions:
1. gnome-terminal
2. nautilus file browser
3. gnome-session manager

Here's what's in ~/.config/autostart/
```
ls ~/.config/autostart/
beryl-manager.desktop          gnome-volume-manager.desktop
gnome-settings-daemon.desktop  xmodmap.desktop
```

I believe this started when I was messing around with sessions manager. I wanted to have a terminal open on startup and thougth that leaving one open on logout would do the trick. Apparantly it did, but with the other 2 windows open as well.

How do I remove these on startup?

Well, for that, while your session is running, shut down everything.  Then, hit Alt+F2 to open a run dialog.  Then type in ```
gnome-session-save 
```and then close the dialog window and reboot.  See if that takes care of it.

---

### Post by Zymsmith on 2007-01-17
Having the same problem, the entries I make dont KEEP.
exit that editor and return, and my gaim entry is not there.
Guess this has somethings to do with permissions/'passwords.
Endless nonsense.

---

