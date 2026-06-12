---
title: "I messed up XIne good!"
date: 2005-12-24
forum: Desktop Environments
---

### Post by crispy_420 on 2005-12-24
MY FIRST POST!!!

In an effort to better my laptop performance with Xine I messed up the graophics settings so when I start Xine it destroys my whole screen.

I installed xine-ui via synaptic. And I tried doing a complete uninstall then reinstall.
Is There a way to start in "safe mode"? Or just return to default setup?

Why I did this: choppy playback of DVD on laptop(DMA already enabled).

Help me get back to atleast default or better yet configure for a laptop.

_Laptop:_

Averatec 5400
Athlon 2800+
512MB DDR
DVD Burner
40GB hard drive
VIA onboard video

The only reason I want xine is DVD menu support. Single chapter DVD's (ripped) play back fine in mplayer. But I would like to watch the extras too.

Thanks.

---

### Post by briancurtin on 2005-12-24
when in synaptic, did you do "mark for removal" or "mark for complete removal"?

the second one will remove all configuration files supposedly. if you did this, then it obviously didnt work, but it is worth a shot if you did not choose that selection. i know you said you did a complete uninstal but im just making sure you meant that you did complete

---

### Post by SavageBeginner on 2005-12-24
I don't think a complete removal deletes the .xine folder in your home folder.  Try a complete removal then delete the .xine folder then install again.

---

### Post by crispy_420 on 2005-12-24
Did a complet removal I think, redoing now....

Just did and restarted....

Waiting....

Now the reinstall....

When I started, the same. Complete messed up screen forcing me to do a hard restart. Again.

---

### Post by SavageBeginner on 2005-12-24
Did you try deleting the .xine folder?

---

### Post by crispy_420 on 2005-12-24
Where is it located?

Will I need "root" to do it?

---

### Post by SavageBeginner on 2005-12-24
Click on Places -> Home Folder 
then press Ctrl+H to view hidden files.  
You should then be able to see the .xine folder.
You don't need to be root since its in your home folder.

---

### Post by briancurtin on 2005-12-24
```
rm -R .xine
```

---

### Post by crispy_420 on 2005-12-24
Trying that now.

Deleted folder and did complete uninstall.

After reinstall IT WORKED.
THANKS!!!

Any tips to configure xine on a laptop? 

I had many dropped frames in xine but not MPlayer. Is there a best graphic setting for xine on a laptop?

---

### Post by SavageBeginner on 2005-12-24
Try setting the video driver to xv.

---

### Post by crispy_420 on 2005-12-24
xv still gave choppy video.

Is this a graphics limitation of my laptop? (I have found no info on model online and planed to add to linux laptops site once working 100%)

Am I screwed for DVDs on this laptop? Or will I have to boot to windows to watch a DVD. Which will suck since I bought the laptop to run linux!

---

### Post by SavageBeginner on 2005-12-24
If DVD's play fine in mplayer it shouldn't be a hardware problem.  Check the settings in mplayer and see if they're different from xine.

---

### Post by briancurtin on 2005-12-24
i dont know how to check this, but is DMA still enabled? when you completely removed Xine and the .xine folder, it may be possible that something was changed with the DMA thing.

i might be way off, since i dont know much about Xine and even less about DMA, but its worth a shot

---

### Post by crispy_420 on 2005-12-24
Thanks for all the help but it is bedtime for me. Will check that out tomarrow.

---

