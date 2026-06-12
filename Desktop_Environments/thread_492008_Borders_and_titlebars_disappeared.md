---
title: "Borders and titlebars disappeared"
date: 2007-07-04
forum: Desktop Environments
---

### Post by kstella on 2007-07-04
Before I made this post, I ran a search to see if anyone else had the same problem. But what happened to them happened while they were using Beryl.

All I was doing was with Preferences > Theme > Customize; I was clicking different options just to see the different combinations. Suddenly, in the middle of trying to render the new settings, my window borders and titlebars disappeared!

Now I can't move, minimize/maximize, or resize windows. And they don't show up on the taskbar (at this moment, I'm posting through Firefox, but there's no Firefox button on the bar).

Can anyone please tell me what happened and how to fix it? Going back to Theme changes nothing, and neither does restarting x.

---

### Post by scannerdarkly on 2007-07-04
using the Beryl Manager, right click on the icon so that you get a drop down.....then hover over "Select Window Manager."  Make sure that Beryl is selected.  Then on the drop down menu click on "Reload Window Manager."  If that doesn't work then on the drop down menu click on Reload Decoration and if that doesn't work then hover on "Select Window Decorator" and make sure that "Standard Beryl Decorator (Emerald)."  And then click on Reload Window Decorator.

This happened to me the first time I messed around with Beryl and I had NO idea how to fix it so I ended up just reinstalling ubuntu.  Then one day i figured it out cause it happened again.

---

### Post by jackmc on 2007-07-04
have you tried restarting the system? This happens to me every now and then (on compiz fusion), and is generally fixed with 

emerald --replace

or

compiz --replace

If you are using fusion you could try that... I would just try restarting to begin with though

---

### Post by kstella on 2007-07-04
Thanks, but the thing is, I'm NOT using Beryl or compiz. I don't even have either of them installed. It happened when I was working with System > Preferences > Theme > Customize.

And even after I restarted, I had the same problem. :( I'd upload the screenshot, but for some reason, the popup that usually comes when I press Print Screen does not come up.

---

### Post by kstella on 2007-07-04
Also, Desktop Effects are disabled. Please, somebody help me. I don't want to reboot into XP...

---

### Post by kstella on 2007-07-04
Hi, guys. I posted this in the wrong forum earlier, so I'm reposting it here.

My window borders and title bars disappeared while I was customizing a Theme. I was not using Beryl or Compiz; I don't even have them installed. I was just using what was available in System > Preferences > Theme > Customize. While clicking to see the different combinations, the window started to flicker, and then suddenly I had no more borders or titlebars.

I restarted, but that did not fix it. I can't move, maximize/minimize, or resize windows. I can only run one application at a time because the buttons do not show up on the taskbar. I'd upload a screenshot, but the popup from pressing Print Screen does not appear. :(

Please, could someone tell me what went wrong, and how I can fix it? Thanks. I searched the forums before posting this, but the threads were all related to Beryl and Compiz.

---

### Post by fjgaude on 2007-07-04
Hopefully you can get to a command line in a terminal. From there, if memory serves, type "gnome-panels" <cr>. That should do it and it is saved for when you re-boot.

frank

---

### Post by kstella on 2007-07-04
Okay. Hehe, what's <cr>? :)

---

### Post by fjgaude on 2007-07-04
It's Carriage Return, but now on keyboards it shows as Enter. <smile>

You may require using sudo also: ~$ sudo gnome-panels

frank

---

### Post by bapoumba on 2007-07-04
@ kstella: merged your previous thread in here.

---

### Post by kstella on 2007-07-04
Thanks to bapoumba and fjgaude.

Tried the gnome-panel command and then restarted. All that happened was that the clock and applications, etc. got reordered on my top panel. Can't figure out how to put them back in order, and still no window borders or titlebars. :( What else could I try?

---

### Post by fjgaude on 2007-07-04
Okay, you can reorder your icons by right clicking on one, unlock and click move. Do that for each one that needs moving.

Again, okay... memory now serves. In your home directory, type <ctrL>-H, to show the hidden files. Delete all the .gnome entries; there should be three of them. Delete .metacity and .mautilus.

Re-boot.

That should do it... of course you are going to have some re-arranging to do with icons and such but you should have all your functions back.

Happy computing.

frank

---

### Post by kstella on 2007-07-04
Okay, thanks. Home directory - do you mean /home/stella or root? In the first, I have four .gnome files, and in the second I have two.

I actually tried your suggestion by deleting them from /home/stella folder, but after restarting, nothing had changed. And the files were still there. Should I have pressed shift+del?

I was going to try root next but decided to ask you first.

---

### Post by fjgaude on 2007-07-04
I meant your home, which is stella... hmmm... I'm at a loss. When you reboot they should be there as they are regenerated.

Can't think of anything else... maybe someone else has an idea what you could next try.

frank

---

### Post by kstella on 2007-07-05
Okay, thanks for responding, anyway. :) I appreciate it.

Please, does anyone else have ideas?

---

### Post by GlennW on 2007-07-05
I've got what appears to be the identical problem to Kstella except that I wasn't messing around with any preferences. In fact, I don't know what happened. I'm an absolute noob. I've followed this thread from the beginning and have followed all the advice given to Kstella. Nothing has changed. When I went to "Windows" at the bottom of the "Preferences" menu, I got this:

[INDENT]Cannot start preferences application for your window manager.
Window manager "unknown" has not registered a configuration tool.[/INDENT]

Did the <sudo gnome-panel> and found out a panel was already running.

How do I get my window manager back? I love Ubuntu but this is like a fly in the ointment!!

Help...

---

### Post by kstella on 2007-07-05
That caught my interest. I also went to Preferences > Windows, and I got the exact same message.

So now there are two of us. Somebody please help. :)

---

### Post by avik on 2007-07-05
Have you tried:

```
metacity --replace
```

That should do the trick, in theory.

---

### Post by kstella on 2007-07-05
avik, it does work! :)  But there's something about the terminal that I don't understand, apparently. When I close it, everything goes back to being border and titlebar-less. What am I missing?

---

### Post by kstella on 2007-07-05
Lots of people having problems with metacity, apparently.

Like I said, closing the terminal takes borders and titlebars away again. I read other threads, and they suggested putting metacity in the startup programs.

Under Startup Programs (Preferences > Sessions), I clicked New. The name I put in is Metacity, and the different commands I've tried are ```
metacity
``` ```
metacity --replace
``` and ```
metacity --reload
```

In all cases, metacity still did not load when I rebooted. :( Anything wrong with what I did?

---

### Post by kstella on 2007-07-05
This was solved. Found the solution somewhere in another thread: sudo metacity then ctrl+c. :) Thanks to everyone for their responses.

---

### Post by GlennW on 2007-07-05
This is great! <metacity --replace> worked just fine. The other issue is whether or not it will survive a restart.

Thanks everybody for the input!!

---

### Post by avik on 2007-07-05
> **kstella said:**
> avik, it does work! :)  But there's something about the terminal that I don't understand, apparently. When I close it, everything goes back to being border and titlebar-less. What am I missing?

Try this.  Append the command with an ampersand like this.

```
metacity --replace &
```

Just wondering, do you have GNOME Settings Daemon in the Startup Programs?  You should have something with the command gnome-settings-daemon.

---

### Post by kstella on 2007-07-08
> Just wondering, do you have GNOME Settings Daemon in the Startup Programs? You should have something with the command gnome-settings-daemon.

Hmm... Well, since I did sudo metacity and then ctrl+c, everything is right even after restarts. I don't see anything with gnome-settings-daemon in the startup programs. Should I worry about it even if metacity seems to be working fine now?

---

### Post by SkylarEC on 2007-11-24
Thanks.

I just ran into this same problem tonight, but it was from trying to mess around with Emerald.  After doing > metacity --replace, I typed > compiz --replace and everything is as it was.

---

