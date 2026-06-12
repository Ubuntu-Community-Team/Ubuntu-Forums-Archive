---
title: "desktop background"
date: 2007-09-07
forum: Desktop Environments
---

### Post by monoufo on 2007-09-07
I have a nice mac desktop background, and a mac gdm login screen.  the problem is that it is ubuntu brown in between.  how can i get my background image loaded as soon as the login process starts instead of at the end, or at least make it a solid blue instead of ubuntu brown.

---

### Post by Beggar on 2007-09-07
You can change the color by right clicking on your desktop and then selecting "Change Desktop Background". At the bottom of this dialog you should see an option for "Desktop Colors". You really cant change when the desktop image is loaded, theres alot that needs to happen at logon and the background image is not a priority.

---

### Post by AnRa on 2007-09-07
Just use the dialog for changing backgrounds! ;)

---

### Post by mcduck on 2007-09-08
> **monoufo said:**
> I have a nice mac desktop background, and a mac gdm login screen.  the problem is that it is ubuntu brown in between.  how can i get my background image loaded as soon as the login process starts instead of at the end, or at least make it a solid blue instead of ubuntu brown.
Nautilus (the file manager in Gnome) draws your background image, and Ubuntu needs to start Gnome before it can start Nautilus. So you can't get a background image before that.

But you can change the color that is shown while loading Gnome: Go to System/Administration/Login Window, and on the Local-tab, just under the GDM theme selection, is the selection for GDM background color.

---

### Post by monoufo on 2007-09-08
Thank you mcduck for having reading comprehension skills and showing me that screen.  However it didn't work.  I did get my login screen to show up properly though.  Now it shows up my login screen, then flashes to the color i put there, then goes back to brown, then goes to my background image.  That color brown has got to be set somewhere, and I'm determined to find it.

---

### Post by mcduck on 2007-09-08
> **monoufo said:**
> Thank you mcduck for having reading comprehension skills and showing me that screen.  However it didn't work.  I did get my login screen to show up properly though.  Now it shows up my login screen, then flashes to the color i put there, then goes back to brown, then goes to my background image.  That color brown has got to be set somewhere, and I'm determined to find it.
Ok, try also changing the background color in the same window where you select your background image (System/Preferences/Desktop Background). Nautilus might show that color while loading the actual background image.

---

### Post by Beggar on 2007-09-08
> **monoufo said:**
> Thank you mcduck for having reading comprehension skills and showing me that screen.  However it didn't work.  I did get my login screen to show up properly though.  Now it shows up my login screen, then flashes to the color i put there, then goes back to brown, then goes to my background image.  That color brown has got to be set somewhere, and I'm determined to find it.

Hope you weren't trying to insult me as my suggestion was most reasonable, as you can tell by the man with great reading comprehension skills making it for the third time in this thread. :)

---

### Post by rainwalker on 2007-09-08
So which method didn't work?

I was going to say the same mcduck said
System -> Administration -> Login Window
Under the "Local" tab, below the list of choices for login screens, there's a place to choose the background color.

---

### Post by monoufo on 2007-09-09
i had already changed the background color on that spot too.  The background color is set to some shade of blue in both locations but the brown is still persistent.  It's only a few seconds, but kinda distracting.

---

### Post by justask on 2007-09-12
monoufo:

You need to modify:

   feisty /etc/X11/gdm/PreSession/Default
   gutsy /etc/gdm/PreSession/Default

Comment out all the lines in the Set Background Color section in that file.

---

### Post by monoufo on 2007-09-12
hmm interesting.  I wish i could understand that language and especially the variables, then i could do some really cool stuff.

---

### Post by sstusick on 2007-09-12
Where exactly are the background wallpapers stored? In which directory?

---

### Post by monoufo on 2007-09-14
I have no idea.  They probably put it somewhere in your home directory.  I didn't need to change my background wallpaper, i needed to change the color of Xorg's background.  Ubuntu stupidly hard codes this color in that config file mentioned above.  I changed the default color, once i figured out the hex code for it.  They should let this be changed in one of their many GUIs.  if people wanted to configure everything by hand like that, they'd use gentoo or something.

I hope they fix it be the final release. It'd probably only take one developer a couple hours or something.

---

### Post by mcduck on 2007-09-14
> **sstusick said:**
> Where exactly are the background wallpapers stored? In which directory?

The ones installed system-wide are in /usr/share/backgrounds, but you can of course keep your own backgrounds where ever you like..

---

### Post by TrAvELAr on 2007-11-09
> **justask said:**
> monoufo:

You need to modify:

   feisty /etc/X11/gdm/PreSession/Default
   gutsy /etc/gdm/PreSession/Default

Comment out all the lines in the Set Background Color section in that file.

Great info, but you could just go to the end of the file and find the line that says "BACKCOLOR=dab082" and replace dab082 with the color that you would like to see.

---

### Post by monoufo on 2007-11-11
better would be to set the color to x.

---

### Post by Arthur Archnix on 2007-11-22
I think setting color to x is best too. More info here.
[http://ubuntuforums.org/showthread.php?p=3820180#post3820180](http://ubuntuforums.org/showthread.php?p=3820180#post3820180)

---

### Post by PeterJS on 2007-11-22
> **justask said:**
> monoufo:

You need to modify:

   feisty /etc/X11/gdm/PreSession/Default
   gutsy /etc/gdm/PreSession/Default

Comment out all the lines in the Set Background Color section in that file.

Thank you much good sir, that has been aggravating me for a while. I also just edited the line down at the bottom that sets the color like TrAvELAr did.

---

