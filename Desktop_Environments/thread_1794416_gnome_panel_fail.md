---
title: "gnome panel fail"
date: 2011-07-01
forum: Desktop Environments
---

### Post by jp351 on 2011-07-01
hi all.

i am using the gnome desktop in 9.10

where to start... let's see. i have the lower panel basically set to only display the "show desktop" button, the window display *area*, and a temperature applet. within my temp applet is the temp for both HDD's, my gpu, and cpu. 

my problem started when trying to set up a second lower panel (third in total) to display the temp of the HDD's to clear up a little space with the window display *area*.. well, when i did so, i had set it to the bottom so it would be a small panel that just displayed those 2 temps just above the gpu / cpu temps. all was fine until i hit OK on the panel pref's... i had accidentally checked "auto hide".

the problem is that after boot / log in, the panel app entirely stops responding (including the upper, lower, and the third "problem" panels). if i open the system monitor and try to kill/end the gnome-panel app, the system becomes mostly unresponsive and i can't do much of anything.. including opening folders... nothing. 
if i select the gnone-panel in the system monitor, stop the process, then kill it, it will restart, usually loading a couple more apps than previously (which would be nothing but the panel itself). upon killing it, as i said, it would restart the panel app, this time loading "settings", "places", "applications", and as i have my top panel set, a few of my 7 or so shortcuts... but never makes it to the clock. after saying that much, the bottom panel (during the second launch of the panel app) will display the "show desktop" button, and the system monitor........... it ALSO shows PART of the sensors app... and the lower left corner, about the height of 2-4 pixels, flashes fairly quickly between black and white (which is due to the third "problem" panel and the black theme i'm using). 

i've tried killing the panel app, right clicking it and selecting properties, but it's too fast of a process stop for me to click properties. i CAN right click and open the properties for the sensors applet running within the third panel, though it does take about 1-2 minutes before the properties window opens. if anyone uses said app, they'll know that the properties for it are limited and we all know that changing those won't fix my issue :/

anyway, long story short....... how can i remove that dam third panel and get on with things? lol.

sorry if it takes me a little bit to get back, i have to use my roommate's laptop, which doesn't like my wireless router all that much, so i can only connect with it every so once in a while for a few short minutes. 

oh, also, i should probably mention that i can only "kill" the panel app 2-3 times before the system becomes entirely unresponsive and all i can do is move the mouse before i have to do a hard restart (hitting the reset button on the case) which i really don't like doing.

any and all help and advice is much appreciated.
thanks all
:)

---

### Post by jp351 on 2011-07-01
hi all.
i return with a minor update, hoping this may help anyone with helping me with this little problem of mine.

last night i started up my computer with the idea of playing with the terminal and system monitor to see if i could stop the third panel from auto hiding, but instead what i did was after log in, i left the system idle. when i woke up this morning, i opened system monitor (since nothing had changed with panel itself). when i checked the status of the panel app, i noticed that it was drawing about 120% cpu (i have dual cpu's) and about 1.1 gb of ram.

i also noticed that i'm limited on what programs/software i'm able to run as well as i cannot mount/access either my slave drive OR the windows partition on my primary. 
my primary is a 500gb drive with a 20gb partition for windows which i will run in a virtual machine from time to time as necessary. when i open "my computer" (from desktop) i can see both my slave drive and my windows partition, however, when i double click OR right click and click "mount", i'm given an error that says it can't be accessed, or i need authentication, or authentication failed.. or something similar. when i want to find something (via the search tool) i have to open my documents (from desktop) and click the search button, then below after the search has started, i have to click "my documents" and select "filesystem" in order for the search to search for what i'm looking for specifically. 
in other words, i had to search for both "system monitor" and "gnome terminal" with this method, and create a copy of both of these on my desktop. 

essentially, if i want to launch something, it has to be on my desktop, or i have to look for it manually in my hard drive.

as i've said, i can't access either my slave drive OR my windows partition, and can't really launch much of anything.

---

### Post by jp351 on 2011-07-08
nothing?
ok... so i've got nautilus working and such, i can mount my slave drives and all..

so that begs the question, is there any way to restore the gnome-panel to it's default settings? 
OR
is there an equivalent "system restore" i can do to before this problem?

i can't seriously be having such a trivial problem and no one be able to help.. can i? :(

---

### Post by koleoptero on 2011-07-09
Go to the directory ~/.gconf/apps and delete the folder named panel. That should reset the panel to its default configuration. Restart and it should be OK.

---

### Post by jp351 on 2011-07-09
omg omg ty, finally some help lol :) :)

soon as i have a chance to get on my home pc, i'll give it a whirl.
even if it restores it to default settings, i don't care. i can add my shortcuts and apps back to the panel in probably 10-15 minutes.

i'll post back later and let you know the verdict.
thanks again :)

---

### Post by jp351 on 2011-07-10
so like i didn't know that folder was there. when i opened it, i saw 3 folders there, top panel screen0, bottom panel screen0, and panel0.. or something similar to those. i deleted panel-0 and restarted and it worked!! :)
thank you so much!!! :D

---

### Post by koleoptero on 2011-07-10
Glad I could help :) Remeber to mark the thread as solved from the menu above :)

---

