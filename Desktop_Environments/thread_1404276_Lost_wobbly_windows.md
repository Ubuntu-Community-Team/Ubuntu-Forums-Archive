---
title: "Lost wobbly windows"
date: 2010-02-11
forum: Desktop Environments
---

### Post by Bartender on 2010-02-11
Yesterday I installed the latest kernel update, then restarted.

This morning I fired up the PC, and it appears that all or most of the compiz settings don't work.  I've only got a few turned on, such as wobbly and opacify.

AFAICT all the settings still look the same in Compiz Settings Manager.

Anyone else do the kernel update and lose compiz eye candy?  Any ideas on how to get it back?

---

### Post by Grenage on 2010-02-11
Have you tried disabling compiz and re-enabling it?

---

### Post by ashwinrao on 2010-02-11
Yes, even I have experienced the same issue. I have lost my emerald settings for the windows. The thing helped me is: System >>> Preferences >>> CompizConfig Settings Manager >>> Effects >>> Window Decoration. Here, please reset the 'Command' by clicking the button in front of it.

The thing I have noticed that it was set to 'emerald --replace' instead of '/usr/bin/compiz-decorator'.

Also, [this thread ]("http://ubuntuforums.org/showthread.php?t=896124")might help you.

---

### Post by Bartender on 2010-02-11
I didn't want to ask how to do it.  Found this link
[http://www.susegeek.com/compizcompiz-fusion/temporarily-disableenable-compiz-fusion-desktop-effects-in-opensuse/](http://www.susegeek.com/compizcompiz-fusion/temporarily-disableenable-compiz-fusion-desktop-effects-in-opensuse/)

and used the two commands shown 

Alt+F2 metacity &#8212; replace

then

Alt+F2 compiz-manager &#8211;replace

Notice the poster wasn't very careful about his dash spacing before the "replace".  That had me worried.  But it worked.  Are these the directions you would have given for disabling/re-enabling?

I guess compiz just does this every once in a while?  Will have to write these directions down.

EDIT:  Found this

Press Alt+F2 and type in
Code:

metacity --replace

Then to turn Compiz back on press Alt+F2 again and enter
Code:

compiz --replace

Looks like there's not just one way to enter the dashes...

---

### Post by ashwinrao on 2010-02-11
> **Bartender said:**
> I didn't want to ask how to do it.  Found this link
[http://www.susegeek.com/compizcompiz-fusion/temporarily-disableenable-compiz-fusion-desktop-effects-in-opensuse/](http://www.susegeek.com/compizcompiz-fusion/temporarily-disableenable-compiz-fusion-desktop-effects-in-opensuse/)

and used the two commands shown 

Alt+F2 metacity — replace

then

Alt+F2 compiz-manager –replace

Notice the poster wasn't very careful about his dash spacing before the "replace".  That had me worried.  But it worked.  Are these the directions you would have given for disabling/re-enabling?

I guess compiz just does this every once in a while?  Will have to write these directions down.

EDIT:  Found this

Press Alt+F2 and type in
Code:

metacity --replace

Then to turn Compiz back on press Alt+F2 again and enter
Code:

compiz --replace

Looks like there's not just one way to enter the dashes...


No, I have posted how I resolved the issue. But, I didn't resolve it completely. When I reboot, all my compiz settings were lost again. Why  this is happening? I didn't had this issue before. Could you please let  me know how it worked for you? Is your compiz settings worked after  reboot? Thanks in advance for your directions.

---

### Post by Bartender on 2010-02-11
Well, you've gone one level past me.  I haven't installed emerald.  Just installed ccsm from the repo's.  

But, yeah, for me this is all I did:

Alt+F2, then ```
metacity - replace
```

I didn't know if I should wait or something?  :D  A few seconds later I did:

Alt+F2, then ```
compiz-manager &#8211;replace
```  and compiz immediately started working again with all settings as they were.

I know that two dashes tells the system something different than one, but forgot what that is.

When something like compiz just stops working every once in a while, it makes me nervous about doing anything to provoke it!  I found most of the effects lost their charm after a few days, so I'm just running a few effects at basic settings.

Oh, dang, I'm on a different PC now in a different place.  So I haven't tested reboot.  Sorry.  I'll post back later with an answer.

EDIT:  OK, I've rebooted a coupla times.  compiz working just like before.

---

### Post by ashwinrao on 2010-02-12
Thanks for your answer! Some thing might be wrong with updates, I'm pretty sure about it. I have resolved the emerald issue by adding the command 'emerald --replace' to start-up applications. After that I got emerald working even after reboot.

---

