---
title: "Nautilus always running?"
date: 2009-01-17
forum: General Help
---

### Post by gm__ on 2009-01-17
Nautilus is the file browser, right?

Then why would it run all the time using 220 memory?

---

### Post by DeMus on 2009-01-17
> **gm__ said:**
> Nautilus is the file browser, right?

Then why would it run all the time using 220 memory?

Probably for the same reason in Windows the explorer is running all the time as well: to show you the desktop which is nothing more than a folder in your home folder.

DeMus

---

### Post by ajcham on 2009-01-17
220MB is a lot of memory for Nautilus to be using.  Do you have a lot of image or video files saved to your desktop? Are they showing image previews?  That is the only way I am able to get Nautilus's memory usage to increase, but even so it's not by much.

Does Nautilus always consume this much memory for you?  What happens if you log out? Is the memory usage still high when you return?

---

### Post by MaxIBoy on 2009-01-17
Run the key combo "alt+f2" and type in "gksudo killall nautilus." See what happens.;)

---

### Post by exploder on 2009-01-17
DeMus provided a good explanation. You can probably get the memory use down by turning off Tracker in Sessions. Tracker is notorious for memory use and does not provide any real functionality.

---

### Post by hikaricore on 2009-01-17
> **MaxIBoy said:**
> Run the key combo "alt+f2" and type in "gksudo killall nautilus." See what happens.;)

don't do this :p

---

### Post by ajcham on 2009-01-17
[QUOTE=Me]Do you have a lot of image or video files saved to your desktop? Are they showing image previews? That is the only way I am able to get Nautilus's memory usage to increase, but even so it's not by much.[/QUOTE]

Actually, after checking it out a bit more:

I logged out and back in again. Nautilus is consuming about 8MB immediately after logging in - I navigated to an image folder, and usage went up to about 45MB and stayed there even after I closed the Nautilus window.  I take it from that that Nautilus must cache image previews into RAM, so it doesn't have to generate them again next time. Logging out will clear that cache (there's probably a command to clear without logging out).  Also you can disable the image previews.

It shouldn't matter really - I would assume that Nautilus will automatically relinquish the RAM it is using, in the event that another program needs it.

---

### Post by theozzlives on 2009-01-17
> **gm__ said:**
> Nautilus is the file browser, right?

Then why would it run all the time using 220 memory?

If it was using that much that wouldn't leave much for   other apps  on my 2 256 machines. Something's wrong somewhere.

---

### Post by exploder on 2009-01-17
> It shouldn't matter really - I would assume that Nautilus will automatically relinquish the RAM it is using, in the event that another program needs it.

Absolutely right!

---

### Post by DeMus on 2009-01-17
> **exploder said:**
> Absolutely right!

I know it is easy for me to say this, having 4GB of ram, but let the pc use the ram, that's what it is there for. If it stays empty you have bought too much ram and wasted money. The more ram is used the faster the pc will be when changing to applications which are running in the background already since they will be in the ram. Don't worry about ram usage, let the pc play with it.

DeMus

---

### Post by ajcham on 2009-01-17
> **theozzlives said:**
> If it was using that much that wouldn't leave much for   other apps  on my 2 256 machines. Something's wrong somewhere.

A little more testing, and I think now that Nautilus must limit the size of its image cache, depending on how much RAM is installed.  In my case I have 1GB of RAM, and I cannot make Nautilus exceed 45.2MB usage.  I suspect the OP has more RAM than I do, which is why Nautilus allows itself 220MB.

---

### Post by gm__ on 2009-01-17
"220MB is a lot of memory for Nautilus to be using. Do you have a lot of image or video files saved to your desktop? "

No, nothing fancy everything's normal.

"You can probably get the memory use down by turning off Tracker in Sessions."
"Also you can disable the image previews."   How can i do these?

Thanks for the help everybody!

---

### Post by gm__ on 2009-01-17
DeMus 

Yes that sounds kinda logical.
I just had this idea that the less ram used is the better.
I have enough, 2GB. But still its kinda strange what nautilus uses comparing it to all of you.

Ajcham

Yes i have 2GB. Do you think that makes Nautilus faster for me?

Would like to hear others mem usage too to compare it to mine.

---

### Post by DeMus on 2009-01-17
> **gm__ said:**
> DeMus 

Yes that sounds kinda logical.
I just had this idea that the less ram used is the better.
I have enough, 2GB. But still its kinda strange what nautilus uses comparing it to all of you.

Ajcham

Yes i have 2GB. Do you think that makes Nautilus faster for me?

Would like to hear others mem usage too to compare it to mine.


My Nautilus uses 60.0MB at the moment.
What is on your desktop aprat of the usual launchers? You keep .jpg files there, movies perhaps? Do you have a large photo as background image by any chance?


DeMus

---

### Post by gm__ on 2009-01-17
No no everything is in folders so no image or anything on my desktop.
And only the default desktop image.

Ok my bad. It only uses 22 MB. But i thought it meant 220 MB because there are a
lot of apps using 5-10 MB and all in all i have almost 400 MB running.

Which is pretty unusal comparing to windows only used for me a 100 and something.

I probably should start to desactivate services i dont use like in windows.

Is there a msconfig-like stuff like in windows to determinate what programs to start on start up?

---

### Post by johnjohn2 on 2009-02-14
> **gm__ said:**
> DeMus 

Yes that sounds kinda logical.
I just had this idea that the less ram used is the better.
I have enough, 2GB. But still its kinda strange what nautilus uses comparing it to all of you.

Ajcham

Yes i have 2GB. Do you think that makes Nautilus faster for me?

Would like to hear others mem usage too to compare it to mine.

If you have clam av and clam scan installed this may cause it to use so much.

---

### Post by Protocol84 on 2010-08-27
I know this is a +1 year old thread but there was an unanswered question by [gm__]("http://ubuntu-ky.ubuntuforums.org/member.php?u=73724")

In 10.04 I use Bootchart and it gives me a visualization of what is happening during boot. (It automatically runs after the next boot once installed, Check /var/log/bootchart for the results)

Then I use Bootup-manager AKA bum 2.5.2 and System> Preferences> Startup applications to remove all the applications and services I do not need. Helped my boot time greatly, from ~40 seconds to ~20-25 seconds depending on it's mood.

---

