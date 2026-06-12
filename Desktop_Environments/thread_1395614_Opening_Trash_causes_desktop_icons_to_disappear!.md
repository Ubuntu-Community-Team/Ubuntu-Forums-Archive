---
title: "Opening Trash causes desktop icons to disappear!"
date: 2010-02-01
forum: Desktop Environments
---

### Post by Wtwine on 2010-02-01
Hi

My computer (running on Jaunty) has just all-of-a-sudden started behaving strangely when I attempt to open trash, either by clicking the icon in the bottom panel or in Nautilus.  The icons on my desktop disappear and Trash doesn't open.  Nautilus also seems to slow down, e.g. when navigating to files.   If I restart, the desktop icons re-appear, and everything works fine, until I click on trash again....

I have never had problems opening trash before.  Any idea what's going on :confused:

I'm a relative noob, so please keep it simple. 

Thanks

---

### Post by Tamlynmac on 2010-02-01
I have one thought (only one at a time - LOL).

Which icon theme are you using and is it one of the original default themes or did you install a new themes after your original Ubuntu installation? For example, did you customize your icon theme? Or, it may be possible that your system was setup with a customized theme.
(system/preferences/appearance/theme tab/customize/icons tab

You might check which icon theme your using and perhaps even select a different theme to test. Simply left click on "Human" (assuming your not using it) or another one of the default themes then close the customize window and the appearance window. Then try opening trash. If the problem still exists - to return to your theme, simply duplicate the above instructions and left click on your original theme, then close both windows. No harm - no foul.

I've experienced some strange issues using custom icons themes. Especially, with Nautilus and trash.

I just recalled one other problem I've had, it was an update that effected my trash applet in 9.04. I simply deleted my trash icon in the panel and reinstalled. The problem disappeared. It's another simple test that may resolve your issue.

Right click on your trash icon and select "remove from panel" (you may need to uncheck the unlock box first). Then right click on your panel and select "Add to Panel". When the "Add to Panel" window opens select "Trash" from the list and left click on the "ADD" button at bottom of window. It will automatically add the trash icon back in your panel. To move the trash icon back to it's original position, right click on the icon and select "Move". Once the icon is back in it's original position - right click on the icon and check the box next to "lock to panel". It's that easy and if the problem was associated with the trash applet, it will no longer exist. Another no harm - no foul test.

Good Luck and hope this helps.

---

### Post by Wtwine on 2010-02-02
Aha, Tamlynmac, you are onto something!

I did indeed change a few customised icons yesterday!  I went back to standard Human icons, and also removed and then added the trash in the panel.  No more problems!  

Thanks!

---

### Post by Wtwine on 2010-02-02
Hmmmm, not so fast!  It's up to it's old tricks again.  I even deleted launchers  from my Desktop for specific files which I had assigned customized icons.  Still no go.

???

---

### Post by Tamlynmac on 2010-02-02
Glad to hear it worked.
Hope you keep enjoying Ubuntu.

Mac

---

### Post by bonsaiis on 2010-02-03
Hi, I had the same problem. Another tread has a (temporary) solution:

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1[FONT=monospace]

[/FONT]Obviously the update of the libglib packages causes the problems.
Rolling back to the older version fixed it for me (9.04, gnome).

---

### Post by Tamlynmac on 2010-02-03
> bonsaiis
Obviously the update of the libglib packages causes the problems.

Thank you for reminding me of the package. I simply deleted the trash icon and reinstalled and have never experienced the problem again.

I was recently made aware of some issues with a number of customized themes (including icon themes) downloaded from [Gnome - Look]("http://www.gnome-look.org/") and have switched to [Softpedia]("http://linux.softpedia.com/get/Desktop-Environment/"). Since that time, I haven't  had any problems with downloading and installing customized themes.

---

### Post by Wtwine on 2010-02-04
Rolling back to earlier version of libglib, as suggested, seems to have sorted out the problem.  Thanks Bonsaiis!  Thanks also for the tip on Gnome-Look, Tamlynmac.

---

### Post by yanx730 on 2010-02-04
Thanks for your reply~

I also get the same problem, and I also can't open a smb:// directory.

And after your command (down grade the libglib), nautilus can open smb directory again.

Thanks you again~

---

### Post by yanx730 on 2010-02-04
Thanks for your reply~

I also get the same problem, and I also can't open a smb:// directory.

And after your command (down grade the libglib), nautilus can open smb directory again.

Thanks you again~

---

### Post by AlexanderDGreat on 2010-02-11
> Hi, I had the same problem. Another tread has a (temporary) solution:

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

Obviously the update of the libglib packages causes the problems.
Rolling back to the older version fixed it for me (9.04, gnome).

Hi **_bonsaiis_**, thanks for finding the solution for us. I'm experiencing the same problem, however, I'm afraid to take actions I don't understand because it might break other areas of my Ubuntu that I wouldn't be able to explain later.

So what is libglib? What does it do? If I downgrade my version, what will it do in my system? Will it upgrade on the next update of Ubuntu? Will it break my kernel? Why did this happen?

Thank you and hoping for your enlightenment.

---

### Post by AlexanderDGreat on 2010-02-15
Anyone?

---

### Post by Cuco3 on 2010-02-25
You should also post the instructions on how to reverse downgrade...

---

### Post by flam3boy on 2010-03-14
> **bonsaiis said:**
> Hi, I had the same problem. Another tread has a (temporary) solution:

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1[FONT=monospace]

[/FONT]Obviously the update of the libglib packages causes the problems.
Rolling back to the older version fixed it for me (9.04, gnome).

Hi, had the same problem, but this fixed it. Isn't this going to harm my OS in any other way?

Thanks

---

