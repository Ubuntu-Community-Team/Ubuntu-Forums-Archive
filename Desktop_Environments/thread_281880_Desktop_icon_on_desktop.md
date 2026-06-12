---
title: "Desktop icon on desktop?"
date: 2006-10-21
forum: Desktop Environments
---

### Post by dannyboy79 on 2006-10-21
I am using Xubuntu Dapper.I noticed one day that my Desktop foler was gone from my username directory?  I would like to point out that I have 1 icon on my desktop which is of a screenshot I took. I did a find using sudo find / -name Desktop and found it in the wastebasket. I did a copy and paste into my users home directory and all of a sudden an icon named Desktop showed up on my desktop? WHy would there be an icon to my desktop folder on my desktop? How can I fix this? I want a desktop folder but I don't want the icon or quick link to the folder on my desktop?

---

### Post by dannyboy79 on 2006-10-22
can someone please help me. I have helped so many people and all i ask is some help once in awhile. i have posted over a dozen requests for help and have only been helped once. why is what seems like an easy problem to solve not one person can even attempt to help me?? I mean whats the point of posting questions if no admin or moderators attempt to help me?? I'll keep posting and bumping until I get help because out of the 438 posts, 12 are for help and the rest are HELPING people so I would really appreciate it if someone could help me. Thank you fellow Ubuntu users.

---

### Post by DaveBorealis on 2006-10-22
> **dannyboy79 said:**
> I am using Xubuntu Dapper.I noticed one day that my Desktop foler was gone from my username directory?

It sounds like you copied the Desktop into itself.  Without seeing your setup, I can only guess.  But as long as you don't have anything of value in it--or if you do, move it out for the time being--just delete the Desktop folder and logout.  When you log back in it will have regenerated a fresh new Desktop folder.

Best regards,
Dave

---

### Post by dannyboy79 on 2006-10-23
i'll try that, thank you. i don't think that'll work since I had originally realized that my Desktop folder was gone? which I had logged in and out plenty of times before reaslizing this. i just want a Desktop folder that I can place stuff in and in which they'll then show up on my actual desktop but I just don't want a folder on my desktop that states desktop? it's creating a link to a link, which is pointless. HA, i'll try that and see if I need more help. I want to tell you I really appreciate the suggestion as I never get help from people! I have major sounds weirdness going on as well. if you'd want to try and help me with that?

---

### Post by DaveBorealis on 2006-10-23
> **dannyboy79 said:**
> i just want a Desktop folder that I can place stuff in and in which they'll then show up on my actual desktop but I just don't want a folder on my desktop that states desktop?

Where are you looking for the desktop folder?  If you have a desktop, then there should be one in your home directory, which you should see when you open nautilus or open a terminal and type ls -l.

(Point me to your sound thread and I will take a look, but sound problems are usually quite hardware specific, and hence usually challenging to resolve.)

Dave

---

### Post by dannyboy79 on 2006-10-23
I got the Desktop folder fixed. I did what you suggested and all is well now. The sound issue can be found in a few places, check out this one that I started [http://www.ubuntuforums.org/showthread.php?t=250140](http://www.ubuntuforums.org/showthread.php?t=250140) or this one that another person started [http://www.ubuntuforums.org/showthread.php?t=242123&highlight=si7012](http://www.ubuntuforums.org/showthread.php?t=242123&highlight=si7012) but they both have the problem with the SIS si7012 onboard sound only working out of 1 speaker yet in windows both speakers work?

---

### Post by DaveBorealis on 2006-10-23
With regards to sound, try this.  Open a terminal, maximize it to fill your screen, type alsamixer, and use the right arrow to move from selection to selection.  The up arrow increases amounts, down arrow decreases.  And experiment.  Start first with PCM to see what that does.  This is a shot in the dark, but just might fix things for you.

NOTE, write down your origial settings before making changes, so that if you screw things up you can go back to where you began.

Worth a try!

Dave

---

### Post by dannyboy79 on 2006-10-25
i have already played around with everything in alsamixer to no avail! thanks for the suggestion though. what's so weird is that it used to work prior to me playing xmms. is there anyway, xmms settings took over alsa somehow and I have to change settings in xmms? please help me more if you can.

---

### Post by DaveBorealis on 2006-10-25
> **dannyboy79 said:**
> it used to work prior to me playing xmms. is there anyway, xmms settings took over alsa somehow and I have to change settings in xmms? please help me more if you can.

I've seen that on my machine.  Either quitting xmms and restarting the browser or whatever, or logging out and back in brought the sound back.

Sound support on Linux isn't ready for primetime yet.  Close, maybe, but not there.

---

