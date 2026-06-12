---
title: "Applications menu contents is gone, menu opens empty..."
date: 2010-04-12
forum: Desktop Environments
---

### Post by Morales2k on 2010-04-12
Hello guys n gals!

All other threads I checked about this happening were more about the meny not opening up entirely, but to me, what happens is that the menu contents is missing.

Here is a screenshot (i was told that some might not see it due to htaccess restrictions on the host):
[IMG]http://www.tucms.com/images/applications.png[/IMG]

That little white area is the whole applications menu. Removing it and adding it again did nothing. Doing a command on terminal such as: *killall gnome-panel* yields no visible improvement. It takes the panel away, and after a while it comes back, but the applications menu stays the same...

Another thing that is happening, probably related to this thing is this:
[IMG]http://www.tucms.com/images/system.png[/IMG]

System>Preferences>Main Menu is not working from the panel launcher. I open a terminal (I understand that the name of the package is *alacarte)*, and I execute using *gksu alacarte*.

The program launches, from terminal, I see all the Application Menu launchers as they should be... nothing outta the ordinary... however, the launcher from the prefs menu doesn't work... 

Will I need to reinstall gnome-panel?

I've been considering reinstalling ubuntu jaunty... ive had flash issues since i upgraded to karmic... and upgrading in its own light is a buggy process (bad aftertaste) compared to a fresh installation (less programs left over from previous version, etc).

I hope there is an easy solution for this, if reinstalling gnome-panel is in order, then that would be easy i think... reinstalling ubuntu carries another streak of things to-do before one goes that far... but Ive been using this for a while now and the disk is kinda full... 

Anyhow... thanks in advance for any help provided here!

---

### Post by dannyboy79 on 2010-04-12
you could try to reinstall the GNOME Menu and libgnome-menu within synaptic. 

check this, login as a guest and see if the menu is fine.

if so, rename your user's .gnome2 folder temporarily, and restart your whole machine, not just log out. then if all is ok when you come back, then just copy and paste items from the .gnome2old to the new .gnome2 folder created. I had to do when I screwed up my top panel. it worked. maybe it'll work for you. good luck

---

### Post by Morales2k on 2010-04-12
Thanks for your prompt reply! :D

I tried your first suggestion, and it didn't work. Moving on to the second one...

---

### Post by trig on 2010-04-12
how did the second turn out?

---

### Post by Morales2k on 2010-04-12
This didn't go as you explained it dannyboy79... 

I followed your steps... I only had one user and a root system login... (i am somewhat green in this area of ubuntu), so I made a new user, named it guest, and assigned a password... logged out, logged on that user, the menu populated correctly and it all worked normally. 

So I log out and back into my user, renamed the .gnome2 folder to .gnome2_old, restarted the machine, but when logging back in, the menu still acted the same... Whats more, i had a program (pidgin) run automatically on startup, and it starts with its window open on desktop... the panels and that window (could be the window manager?) did not work, it only showed desktop icons, and nothing more... 

after a while i noticed i had some other window open in there... the cursor would turn into the resize icons... so i searched for the normal position of the close button on upper right corner, and closed an unknown invisible window... after that the gnome-panel loaded and the pidgin window displayed... it freaked me the hell out to no end... but after a quick zip of 7oz. of wine im somewhat ok again.... So... back to the drawing board then!?

I'm going to restart again and see if i replicate the invisible window issue... *shrug*

---

### Post by dannyboy79 on 2010-04-12
well the renaming of .gnome2 folder was a fix for a missing volume indicator applet. i thought i would at least mention it hoping it may fix it. you can always just delete the new .gnome2 folder and rename the .gnome2old back to .gnome2. i wish I could help. i am sure it's something in your home directory as far as a config file that got fubared.

---

### Post by dannyboy79 on 2010-04-12
have you tried to re-add the main menu? by right clicking on the top panel, and click, add to panel. then look "main menu". good luck

---

### Post by Morales2k on 2010-04-12
Thanks for your sugestions dannyboy, but nothing seems to bring the stuff back... I' ve been googling but nothing more turns up on this exact error, most of what comes up is the normal misshaps of hasty clicks messing up the panels... tuts on how to customize and stuff like that... but my applications pane has flat out quit on me... lol ugh... guess these things are bound to happen especially just after i recovered the machine from a nasty ext3 fs error... >_<  

Oh well... that might be a reason for the problem on its own light... its only been like this after the recovery ... I used the live cd (gparted) and i brought it back to life... maybe i could have mentioned this in the beginning... lol (my bad)

---

### Post by Morales2k on 2010-04-12
BINGO!

[Finally came across something that helped me fix it!]("http://hatherly.com/blog/?p=17")

That blogpost indicates the exact same problem I had. The solution is somewhat odd though... but it made my Applications menu come back to life again (Thank God! I was annoyed to no end with having to run everything with alt+f2).

The thing to do (in case the blogger goes offline someday), is to search for the folder called menu inside ~/.config/ (if you don't see it, or don't know where it is... press ctrl+h inside your home folder to see that folder... and many more.)

Once in there, there should be a file called applications.menu, and like in the blog post, mine also had 0kb filesize, so I deleted it (also as suggested by the blogger).

After that, my Applications menu INSTANTLY worked again. Now I wag my tail like the happy dog I am. 

:D

:popcorn:

---

### Post by dannyboy79 on 2010-04-13
glad you got it sorted! mark the thread solved so others can find the fix easily.

---

