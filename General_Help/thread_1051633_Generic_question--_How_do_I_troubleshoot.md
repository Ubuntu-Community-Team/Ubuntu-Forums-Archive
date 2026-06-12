---
title: "Generic question-- How do I troubleshoot?"
date: 2009-01-26
forum: General Help
---

### Post by Squish42 on 2009-01-26
I know this this very generic and a little vague but here it goes...

I had a a little hiccup in my Hardy Heron install a few days ago - after rebooting to apply some patches I got a "OAFIID:GNOME_FastUserSwitchApplet" error, and the remainder of the boot took forever to complete.  I did a little searching and found a fix here: [http://ubuntuforums.org/showthread.php?t=619767](http://ubuntuforums.org/showthread.php?t=619767).  I did the "sudo aptitude install gnome-applets" as suggested and now I can reboot with *almost* no issues.  

I say "almost" because my system doesn't "feel" the same.  A little sluggish and a couple other things I can't put my finger on.  Two symptoms I can identify are:
[LIST=1]
[*]my login name, sound control and printer control do not appear in the panel any more and,
[*]Update manager did not run last week
[/LIST]

If you have solutions for the identifiable problems, great.  But I'm actually just looking for a guide on where to look for clues as to what is failing at start-up that causes these things to not work.  And, in looking, I may figure out what else is wrong.

Thanks,
Evan

---

### Post by adamlau on 2009-01-27
```
dmesg > ~/Desktop/dmesg
```

Review the dmesg file on your desktop for clues.

---

### Post by mb_webguy on 2009-01-27
Your applet issue is likely because that "OAFIID:GNOME_FastUserSwitchApplet" error (which means that the User Switcher applet, which is the one with your name on it, did not load successfully for some reason) gave you the option to ignore or delete, and you clicked delete.

All you need to is right-click on the panel, select "Add to panel", and select User Switcher.  You can probably do the same for the other applets you're missing, though I'm not sure why they would be missing unless you've also accidentally removed them.

And I don't know why Update Manager didn't run for you last week unless you were having internet connectivity issues...

---

### Post by Squish42 on 2009-01-27
> **adamlau said:**
> ```
dmesg > ~/Desktop/dmesg
```

Review the dmesg file on your desktop for clues.

Thanks for the reply.  I've run the command and reviewed the file bt nothing is obviously wrong.  Is there something I should look for, maybe a keyword, that will tell me where to look?

---

### Post by Squish42 on 2009-01-27
> **mb_webguy said:**
> Your applet issue is likely because that "OAFIID:GNOME_FastUserSwitchApplet" error (which means that the User Switcher applet, which is the one with your name on it, did not load successfully for some reason) gave you the option to ignore or delete, and you clicked delete.

I do have a vague recollection of selecting a 'negative' response.  I'm suprised I would pick delete though.

> All you need to is right-click on the panel, select "Add to panel", and select User Switcher.  You can probably do the same for the other applets you're missing, though I'm not sure why they would be missing unless you've also accidentally removed them.

Hey, cool.  I never knew that existed.  Now everything is back and I have a couple new applets.  

As far as the notification. network and sound applets, there was another error message after the FastUserSwitchApplet error that I must have selected the wrong response.

> And I don't know why Update Manager didn't run for you last week unless you were having internet connectivity issues...

This one is still a mystery.  I just forced a check for updates and the notification is back. Maybe I'm back in business.

Thanks!!!

---

### Post by Squish42 on 2009-01-29
I was just notified of a few updates.  Everything is back to normal.  Thanks for the quick help on the specific problems.

Back to the heart of the question though... How do I troubleshoot?  Is there a log I can review that would have told me about a conflict or a failed application?  adamlau pointed me to dmesg but after looking at the results, I'm not sure what I'm looking at.  Is that the only boot log?  Is there something else that records the boot and/or login process?

---

