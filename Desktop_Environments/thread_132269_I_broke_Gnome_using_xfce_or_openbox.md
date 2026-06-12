---
title: "I broke Gnome using xfce or openbox"
date: 2006-02-18
forum: Desktop Environments
---

### Post by garren on 2006-02-18
I'm new at this whole Ubuntu thing, as will soon be obvious, and I think I broke Gnome.  

Ubuntu (Breezy) starts, and lets me log in, but then I just get a blank brownish screen.  I have no panel or taskbar.  

If I hit ctrl-alt-F1 I can get to a terminal.  I have tried reinstalling the kernel.  I have tried reconfiguring X.org.  When I hit ctrl-alt-delete a task list comes up (in a window, mind you, that i am able to move and resize.  And in the task list X.org is listed, which, I assume, is why there is a window).  From there, in one of the menus there is a "help" thing that brought up my browser fully functional, in another window.  I just have no task bar or panel.  

I just discovered one more thing--when I right click a menu comes up allowing me to pull up a terminal or a web browser.  But still no access to apps, and no task bar.  

Ok, now here's how this all came about.  I saw people's desktops configured similarly to Macs and coveted that for myself.  The latest version of xfce seems to be able to do that, so I tried it.  Somewhere along the line I accidentally installed an older version of xfce which wasn't really any different than Gnome (in look, it did have more features I think).  So without even realizing I had installed xfce (the older one), I tried installing expocity.  That didn't seem to work at all, and I gave up.  So then I tried openbox, which seems to be running right now, but not very well.  

I'd be willing to just get back to Medacity (is that what it's called?), if I could just get access to my computer back!  

Also, I should clean out all that stuff I "installed" (I tried installing several differnt ways on the xfce4 and expocity windows managers).  

Any help would be much appreciated!

---

### Post by TheIdiotThatIsMe on 2006-02-18
From the sound of it you are actually in xfce. By default, xfce contains no panels, so all you would get is a desktop. Try going into the terminal, and typing:

```
sudo apt-get install xfce4-panel xfce4-systray xfce-taskbar-plugin
```

And then restart the DE. Alternatively, try clicking on "Session" when you are the login GDM, and click Gnome.

---

### Post by garren on 2006-02-18
I tried downloading those pieces of xfce, and then I logged out and back in (I wasn't sure what you meant by restarting the DE), but I still got nothing.  Also, apt-get said it couldn't find "xfce-taskbar-plugin" but it did find the systray, and panel, and it claims to have installed them.  

Also, I should have said before, the reason I think I'm in openbox is because, at the top of the right click menu it says "Openbox 3."  

Also, this might be like asking for a car for Christmas, but if anyone happens to know what I should be downloading to get the panel that looks like the Mac's, that would be cool.  Otherwise, I'd be happy with a bicycle for Christmas too--how do I get a panel at all?!  

There must be a lot more to customizing the panel and whatnot than I thought.

---

### Post by CompShrink on 2006-02-20
LOL, yeah, I had a similar reaction for about 2 minutes when open box poped up... it was a blank brown screen and I was thinking, "Oh great, not loaded at all..." Then I came to my senses and tried clicking. Left, nothing. Right, hey, here we go...

But really, that's the basics of openbox. It's as lightweight as it possibly can be. I have just started using it myself, so I feel your pain, but unfortunately can only give you a little bit of help, I'm new to this too.

Ok, first of all, you must have set openbox to your default session. You can easily set it back to metacity (Gnome) by logging out (rightlick-the-desktop menu > exit) and then when the GDM (login screen) pops up, click on "sessions" and pick "Gnome." Log in and it should ask you if you want to make it the default. Click yes and you won't have to deal with openbox/xfce. Uninstall them from synaptic if you want (assuming you installed them from there...) or not, doesn't matter.

Or, be like me, tough it out, and build your desktop your own way, more or less from scratch, in openbox. 

Pick a file manager, you can in fact use nautilus, which also gives you a desktop image background, but watch out it removes Openbox's desktop rightclick menu, and it won't come back until you logout. Alt-Ctrl-Backspace.

Pick your own task bar, build the menu yourself, etc etc. Openbox also runs a LOT faster than metacity due to it's simplicity.

As for wanting a Mac OSX style task bar, you can use: [http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210) in either metacity or openbox. I have not tried this, but someone else linked to it as Mac OSX like, so give it a try.

If you want to mess around with openbox, it will take a bit of work and time, but it feels good to have a much more personal and customized, self built GUI. It also runs faster. If you want to tough it out in openbox, start here:
[http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox)

I mapped the "alt-tab that rocks like a ninja" mentioned in that thread to a spare mouse key, and it's so very convient. Openbox is a lot of fun, although a bit of a time sync...

---

