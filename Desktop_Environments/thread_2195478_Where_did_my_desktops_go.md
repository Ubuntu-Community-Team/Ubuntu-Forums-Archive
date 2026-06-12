---
title: "Where did my desktops go?"
date: 2013-12-24
forum: Desktop Environments
---

### Post by dijxtra on 2013-12-24
Hello,

I have Kubuntu 13.10. I type quite fast and reckless, so I managed to press something and now a my whole desktop is empty, as if I switched virtual desktop. That means: not only are my open windows gone, my widgets and wallpapers are also gone. I haven't simply switched a virtual desktop. I used to have two virtual desktops, both with custom wallpapers, one with widgets one without widgets. Now I have two virtual desktops, both have default kubuntu wallpaper and no widgets (not even a default folder view which comes on freshly installed systems). My windows still exist (I can see their processes with ps), but I cannot access them.

I now rebooted, and nothing changed (except the processes are gone, obviously). I still have 2 virtual desktops with default wallpapers and no widgets.

So, how do I get my virtual desktops back? And what did I press anyway? :-D

Thanks in advance!

---

### Post by deadflowr on 2013-12-24
Do you see anything in the top right corner?
I think it should say desktop.
If you press that it should give a dropdown.
Look for something that says activities.
I don't which type of layout you had, but it should be one of the ones listed.
There are usually several different layouts.
They would be names like newspaper, files and folders, search and launch.
Unfortunately, I'm not on Kubuntu right now, so I'm trying to remember this as best I can.
But sometimes when you switch the layout, it reset all the desktops to the defaults.
I have seen that if I switch back, all my stuff is as I set it.

---

### Post by marco-parillo on 2013-12-24
Deadflowr has a good memory. If that does not work, in desperation, you can also try to rename your .kde directory. When you re-boot, it should get re-created with defaults. Note, I have never tried this myself, but I have seen this advice:
[http://ubuntuforums.org/showthread.php?t=1798971&p=11021762#post11021762](http://ubuntuforums.org/showthread.php?t=1798971&p=11021762#post11021762)
[http://askubuntu.com/questions/31378/how-to-reset-kubuntu-to-initial-state](http://askubuntu.com/questions/31378/how-to-reset-kubuntu-to-initial-state)

---

### Post by SeijiSensei on 2013-12-24
As the author of one of those posts, I now realize there is a step missing.

When you boot into recovery mode, the root filesystem is marked read-only, so you cannot move the .kde directory.  Here's a corrected sequence of steps.  Boot into recovery mode, then type:

```

mount -o remount,rw /
cd /home/username
mv .kde .kde.bad
reboot

```

The first command remounts the filesystem with write permissions.  Note there is no space after the comma.

I've used this method on a few occasions when my KDE configuration was broken for some reason.

---

### Post by dijxtra on 2013-12-24
> **deadflowr said:**
> Do you see anything in the top right corner?
I think it should say desktop.
If you press that it should give a dropdown.
Look for something that says activities.
I don't which type of layout you had, but it should be one of the ones listed.

Wow, what do you know. Never knew those activities existed.

That fixed it, thanks!

---

### Post by deadflowr on 2013-12-24
Yeah, a lot of people complain about the bloat of KDE, this being such an example.
But I actually enjoy it!:P

It's nice to run a desktop with extra features(and tons of them to boot), and not one where the extra features are really just replacing the existing ones.

---

