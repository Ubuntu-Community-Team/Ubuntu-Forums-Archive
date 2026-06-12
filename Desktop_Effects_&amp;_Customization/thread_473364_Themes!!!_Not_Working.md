---
title: "Themes!!! Not Working"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by ucsblaw on 2007-06-14
I really need some help. I'm running Feisty (gnome) with Beryl + xgl. 

I want to change my windows to other themes but none of them work completely. I can only get the window borders to change but nothing else changes. I can't get the scroll bars, or the face of the window to change. 

I have tried emerald theme manager and the regular gtk theme manager and I get nothing but the border changed. The only other thing that changes is the volume function key (when i press Fn + F4 I can increase my volume and this little volume thing pops up and it is set in the theme that my window borders are set at but thats it...nothing else. Anyone have any suggestions?????

i have looked all over the web, this forum and every wiki i can find and I cant seem to get an answer. 

anyone?

thanks

---

### Post by damaged on 2007-06-14
I've got the same problem but I'm using Edgy + Beryl

I wanted to create a black theme and installed ubuntustudio emerald theme:

[http://gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198](http://gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198)

and then I wanted to add the ubuntustudio theme so that all the controls would be black too but it has no effect on the controls. It only changes the window borders.

I've seen it done in screenshots:

[http://gnome-look.org/content/preview.php?preview=1&id=59198&file1=59198-1.png&file2=59198-2.png&file3=&name=UbuntuStudio+Emerald](http://gnome-look.org/content/preview.php?preview=1&id=59198&file1=59198-1.png&file2=59198-2.png&file3=&name=UbuntuStudio+Emerald)

Can anyone let us know why this isn't working?

Any help much appreciated :)

---

### Post by kpolice on 2007-06-14
First, Emerald will only change your Window borders because it is a **Window** Manager. If you want your controls to change you have to use the Gnome Theme Manager.

If you can change your theme in a normal session, I mean no XGL nor Beryl, but you can't when you run XGL the problem is probably that the gnome-settings-daemon isn't running and this has been asked a million of times.

---

### Post by damaged on 2007-06-14
> **kpolice said:**
> First, Emerald will only change your Window borders because it is a **Window** Manager. If you want your controls to change you have to use the Gnome Theme Manager.

Well, at least for me that's exactly what I'm saying. I'm trying to change the controls with Gnome's theme manager while Beryl is running and they just don't change no matter what theme I pick. If I start a new session with Beryl off, I can change the controls to a black theme, but when I restart with Beryl running the controls revert back to gray again.

> If you can change your theme in a normal session, I mean no XGL nor Beryl, but you can't when you run XGL the problem is probably that the gnome-settings-daemon isn't running and this has been asked a million of times.

Well I guess this makes a million and one.

---

### Post by damaged on 2007-06-14
Just in case anyone who has the same problem reads this post. The "friendly" solution is that you need to run the command:

```
gnome-settings-daemon &
```

That solves the problem temporarily.

However to make it so that this command is run every time you begin a session, you need to add it to your session startup programs by going to System > Preferences > Sessions. Then pick the "Startup Programs" tab and hit the "Add" button. Now, paste the command above into where it says "Startup command:" and hit okay.

Done. That wasn't so hard was it. Of course, I had to know what the problem was before I could find the solution.

---

### Post by ucsblaw on 2007-06-14
I tried what you said and this is what i get...I also added the code to "sessions" and still have problems. When I type in 'gnome-settings-daemon &' my window changes to the desired theme and then changes back to crap after I close terminal. Any suggestions?

thanks again for your help.


> name@ubuntu:~$ gnome-settings-daemon &
[1] 8972
name@ubuntu:~$ xmodmap:  unknown command on line /home/name/.Xmodmap:1
xmodmap:  unknown command on line /home/armen/.Xmodmap:2
xmodmap:  2 errors encountered, aborting.
/home/armen/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/armen/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
armen@ubuntu:~$ /home/armen/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant

** (gnome-screensaver:9020): WARNING **: screensaver already running in this session



---

### Post by ucsblaw on 2007-06-14
also, when i enter the command in 'system'--> Preferences--> 'Sessions' it doesn't save. If i go back to sessions it's not there.

I hate not knowing...someone help me learn.

thanks

---

### Post by kpolice on 2007-06-14
If you run it thorugh the terminal and then you close the terminal then the daemon will also be closed, you can run it by pressing alt+f2 and typing the command there. 

About adding it to your startup programs it should work, I am not using GNOME right now so I can't help you at the moment. Try login in a normal GNOME session and adding it to the startup, then logout and start your XGL/Beryl session.

---

### Post by ucsblaw on 2007-06-14
alt f2 worked like a charm...but i still cant get it to stay in "sessions"...

i guess little by little the pieces are comng together

thanks

---

