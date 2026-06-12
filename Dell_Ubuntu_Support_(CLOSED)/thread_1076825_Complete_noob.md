---
title: "Complete noob"
date: 2009-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sidlexic on 2009-02-21
Last night i decided i couldn't put up with Vista anymore and installed Ubuntu on my Dell XPS M1210.  I have no idea what i'm doing...
Few questions;
Is windows completely gone? i backed up all my files on to an external but not sure if i can retrieve them as i'm sure there are compatibility issues.  I see a "lost and found" folder and i'm assuming thats my windows junk?  How can i get things like my music out of there?
Why is my fan running all the time?
And I'm sure you guys are going to ask what version I'm running so where do i find that?
Thanks for your patience.
One more thing, is there anything like a task manager to show me my CPU usage?

---

### Post by phndrummer on 2009-02-21
///////////////////////////////////////////
Last night i decided i couldn't put up with Vista anymore and installed Ubuntu on my Dell XPS M1210. I have no idea what i'm doing...
Few questions;
Is windows completely gone? i backed up all my files on to an external but not sure if i can retrieve them as i'm sure there are compatibility issues. I see a "lost and found" folder and i'm assuming thats my windows junk? How can i get things like my music out of there?
Why is my fan running all the time?
And I'm sure you guys are going to ask what version I'm running so where do i find that?
Thanks for your patience.
One more thing, is there anything like a task manager to show me my CPU usage?
//////////////////////////////////////////////////////////

Yes it would be helpful to know what version you installed. 
Now, depending on how you installed Ubuntu will tell you if Windows is completely gone or not. I don't remember off the top of my head, but I think that if you went with all the default settings then Windows is still there. If you told the installer to use the entire hard drive then it's gone. 

when you have ubuntu up and running, plug in your external and an icon may pop up on your desktop. If it doesn't then click on the 'places' menu at the top of the screen and click on the name of your external. If it's not there or there is an error when you click on it then the filesystem on the external hard drive is probably an ntfs filesystem (the filesystem windows uses. linux uses a fat32 filesystem). If that is the case then look here: [http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/](http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/) this will tell you all need to know about getting your data.

And finally about your CPU usage. right click on the panel at the top of the screen and select 'add to panel'. scroll through the list and click on the cpu frequency scaling monitor and select add. This little app didn't work on my dell desktop so, I'm not sure if it'll work on yours. If it doesn't work, then return to that menu and scroll down to the system monitor. That one seems to work for me.

good luck

---

### Post by cybergalvez on 2009-02-21
> **Sidlexic said:**
> Last night i decided i couldn't put up with Vista anymore and installed Ubuntu on my Dell XPS M1210.  I have no idea what i'm doing...
Few questions;
Is windows completely gone? 

[COLOR="SeaGreen"]Most likely, it depends on if you installed ubuntu on just the freespace left on your drive or if you used the entire HD for ubuntu[/COLOR]

i backed up all my files on to an external but not sure if i can retrieve them as i'm sure there are compatibility issues.  

[COLOR="SeaGreen"]Actually if you backed up your files to an external HD then I am sure thats where they will be, just plug in the drive and it should mount without any trouble.  If it does not mount its most likely because windows did not dismount it properly (XP does that all the time) and a window will pop up telling you what to do to fix that.
[/COLOR]
I see a "lost and found" folder and i'm assuming thats my windows junk? 

[COLOR="SeaGreen"]Nope thats for the OS to use[/COLOR]

 How can i get things like my music out of there?

[COLOR="SeaGreen"]They are not there, use your external drive[/COLOR]

Why is my fan running all the time?

[COLOR="SeaGreen"]don't know, mine doesn't that sounds like a BIOS issue, check there first[/COLOR]

And I'm sure you guys are going to ask what version I'm running so where do i find that?

[COLOR="SeaGreen"]What did you download? [/COLOR]


Thanks for your patience.
One more thing, is there anything like a task manager to show me my CPU usage?

[COLOR="SeaGreen"]System>Admistration>System Monitor

I also like htop which can be installed from synaptic (System>Administration>Snynaptic[/COLOR]



Hope this helps

---

### Post by Sidlexic on 2009-02-22
Thanks guys! I was looking at the "about Ubuntu" under "system" it says there;
Thank you for your interest in Ubuntu 8.04 - the Hardy Heron - released in April 2008.
Guess thats my version?

---

### Post by cybergalvez on 2009-02-22
> **Sidlexic said:**
> Thanks guys! I was looking at the "about Ubuntu" under "system" it says there;
Thank you for your interest in Ubuntu 8.04 - the Hardy Heron - released in April 2008.
Guess thats my version?

sounds good, hardy is pretty stable, I have it installed on two of my computers, and intrepid on two of them.  In any event did you find your data? Did the external HD work?

---

### Post by gnoob on 2009-02-25
> **Sidlexic said:**
> 
Is windows completely gone? 

When you installed Hardy, it asked you whether to use the whole drive for ubuntu or to split the hard drive into partitions, one with vista and the other with Ubuntu.  If you do not see an option (in black and white text) to select windows when you boot up (before you see the Ubuntu logo) then you probably do not have vista installed anymore.

---

### Post by Sidlexic on 2009-02-25
> **cybergalvez said:**
> sounds good, hardy is pretty stable, I have it installed on two of my computers, and intrepid on two of them.  In any event did you find your data? Did the external HD work?

Yes the HD worked thanks.

---

### Post by Therion on 2009-02-25
You might want to check out **[Linux 101](http://linux.about.com/od/linux101/Linux_101.htm)**.  

It should Kinda give you a little jump start/intro into your new distro of choice.

Welcome aboard, by the way.

---

### Post by armandh on 2009-02-25
as long as you have your data I would not cry over the lost vista.
my wife's laptop is rarely booted to vista.
she is happy with 8.04

---

### Post by Talon2 on 2009-02-25
> **Sidlexic said:**
> 
One more thing, is there anything like a task manager to show me my CPU usage?

Sure.

Go down to the bottom desktop panel and right click to bring up "Add to Panel".  Once in "Add to Panel" select "System Monitor."

I use it all the time.

---

### Post by Sidlexic on 2009-02-25
> **armandh said:**
> as long as you have your data I would not cry over the lost vista.
my wife's laptop is rarely booted to vista.
she is happy with 8.04

Rejoice rejoice! Its gone forever!

---

