---
title: "Memory Management is awful in Ubuntu"
date: 2005-11-02
forum: Desktop Environments
---

### Post by ngms27 on 2005-11-02
Hi,

I'm regulary getting applications to crash and the apps logs are saying unable to allocate memory or in the case of Firefox segmentation fault.

There is no physical problem with the memory etc as it tests 100%

It seems to be when Ubuntu swops out to swap, i.e a bug of some sort.

Here's my current memory allocation:

             total       used       free     shared    buffers     cached
Mem:        451852     440812      11040          0      31924     185024
-/+ buffers/cache:     223864     227988
Swap:       610428       2760     607668

Any ideas on how to fix this bug?

It seems to affect all types of applications including those running in Sun Java.

JonnyT

---

### Post by 23meg on 2005-11-02
Did you try disabling swap to see if that helps? You can do it by issuing the "swapoff" command followed by the device identifier of your swap partition.

Also, before coming to general conclusions about Ubuntu's or any other system's shortcomings, you should ask around and make sure what you're talking about is a general problem that's not specific to your configuration. Just because you're having severe problems doesn't mean that Ubuntu is responsible for those; saying something is "awful" based on nothing but your negative experience with it won't help solve your problems any faster, it will just spread biased, baseless FUD. If there were critical memory management bugs that would affect any critical number of machines in Breezy they would most likely have been fixed before release because Ubuntu has a very large testing user base. Still, the chance remains that yours has escaped attention; in this case it would be a "showstopper" bug that would get fixed soon after you report it. Please consider resorting to more positive means of expressing your problems.

---

### Post by SickTwist on 2005-11-02
[QUOTE=ngms27]Hi,

I'm regulary getting applications to crash and the apps logs are saying unable to allocate memory or in the case of Firefox segmentation fault.

There is no physical problem with the memory etc as it tests 100%

It seems to be when Ubuntu swops out to swap, i.e a bug of some sort.

Here's my current memory allocation:

             total       used       free     shared    buffers     cached
Mem:        451852     440812      11040          0      31924     185024
-/+ buffers/cache:     223864     227988
Swap:       610428       2760     607668

Any ideas on how to fix this bug?

It seems to affect all types of applications including those running in Sun Java.

JonnyT[/QUOTE]

This could be caused by one or multiple things so I'm going to try to narrow it down by asking for some more information.

1. Are you using any special GTK+/Metacity themes or did you just leave them on the default?

2. Restart the computer, log-in and start the system monitor (Applications --> System Tools --> System Monitor). If you leave Ubuntu running like this for a few hours (don't run any other programs) how much memory is being used?

3. What programs do you use on a day-to-day basis (including any network services like file/print sharing, mail server, etc)? Do you use one program more than the others? Do you leave one (or more) running for long periods of time (if so, how long--hours, days, weeks)?

4. Did you install any software from somewhere other than the Ubuntu respositories?

---

### Post by ngms27 on 2005-11-03
Sorry for the delay in getting back.

1) I'm using default themes

2) On a day to day basis I'm only using Evolution, Firefox, K3B and a couple of Java apps using Suns Java. Occasionally OOO

3) I have only installed Suns Java, Netbeans IDE and Helix player that are not from the Ubuntu repositories.

I'm beginning to think that its something to do with Firefox. OOO has also always been prone to crashing. 

All the above was also true on Hoary.

JonnyT

---

### Post by GeneralZod on 2005-11-03
[QUOTE=ngms27]

2) On a day to day basis I'm only using Evolution, Firefox, K3B and a couple of Java apps using Suns Java. Occasionally OOO
[/QUOTE]

Firefox, Azureus (not sure if you are using this...) and OO.o are huge memory hungry monsters - especially Firefox, which has such bad memory leaks that it will steadily grow in size (dependent on your surfing habits) until your computer slows to a crawl (it once got so bad that I used all 512MB of RAM and all 512MB of swap and on my nice, fast, SATA 7200RPM drive, it took *1 and a half minutes* to close Firefox, measured from clicking "Yes" to the "Close all Tabs" prompt to disappearing from the task-list/ cessation of hard-drive thrashing).  Azureus also appears to have a memory leak which makes X consume huge amounts of memory over time (although I seem to be the only one who's seen this :().

Personally, I just installed the Session Saver Firefox extension and close Firefox down every day or so.

---

### Post by rejser on 2005-11-03
Java-apps uses memory as crazy (including azureus)

---

### Post by ngms27 on 2005-11-03
But thats not the problem with memory being used. The problem is Apps crashing with a no memory error.

i.e. Swop not being used correctly or memory being held incorrectly.

If I do a free after the crash there is always swop available.

JonnyT

---

### Post by yusufk on 2005-11-03
My system crawls to a virtual halt after about 5 minutes of using firefox. Not sure if its the extensions or firefox itself or something else. I also use the novel groupwise client which I think comes with its own Java vm. I'm going to attempt removing firefox extensions, hope its not the ones I really use!

Oh and should firefox be using 40+ % cpu and 126Mb virtual memory? and Xorg 50% and 137Mb ???

---

### Post by az on 2005-11-03
[QUOTE=ngms27]Hi,

There is no physical problem with the memory etc as it tests 100%
[/QUOTE]

Did you test it with memtest86, or just the probe the mb does at boot?  If not, run memtest overnight....

---

### Post by SickTwist on 2005-11-03
[QUOTE=ngms27]Sorry for the delay in getting back.

1) I'm using default themes

2) On a day to day basis I'm only using Evolution, Firefox, K3B and a couple of Java apps using Suns Java. Occasionally OOO

3) I have only installed Suns Java, Netbeans IDE and Helix player that are not from the Ubuntu repositories.

I'm beginning to think that its something to do with Firefox. OOO has also always been prone to crashing. 

All the above was also true on Hoary.

JonnyT[/QUOTE]

1. Do you have any Firefox extensions installed?
2. Have you tried not running any apps (besides GNOME) to see what happens. (This will indicate if there is a problem with something in your GNOME session or the kernel).
3. Have you tried just running these programs one at a time to see if a specific one causes problems?

Like others have said, Firefox, OO.o and Java apps all tend to be memory intensive (but Linux should still be using your swap partition). If the problem is in fact with a specific program, here are some possible solutions:

**Use an alternative program.**
I realize it might not be an optimal solution but there are many alternatives to the programs you mentioned (Epiphany, Abiword, Gnumeric, Thunderbird, Sylpheed, just to name a few). We might be able to suggest alternatives for the Java apps as well if you tell us what you're using.

**Do not use anything else while running the offending program(s)**
This will limit the RAM being gobbled up at a given time and perhaps give you some more stability.

**Use a different desktop or strip down GNOME**
If you would rather not give up the programs that you're using but you are not attached to GNOME, perhaps you should consider trying a more lightweight desktop. This will result in there being more memory available for the apps that you're running. Otherwise, you could minimize the amount of memory that GNOME uses (there are many threads that cover tips how to do this) which will offer similiar benefits.

---

### Post by Hairy_Palms on 2005-11-03
the firefox from the repos is a memory whore, i dont know why, if u install the 1.07 from mozilla.org it uses less memory, and firefox 1.5 uses even less than that, as fore OO.o its just a plain memory whore, i use abiword and gnumeric, if xorg is using that much of your memory you cant have your graphics cards drivers installed try installing them from ati/nvidia

---

