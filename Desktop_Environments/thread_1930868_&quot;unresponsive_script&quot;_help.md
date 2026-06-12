---
title: "&quot;unresponsive script&quot; help??"
date: 2012-02-24
forum: Desktop Environments
---

### Post by chitowner2 on 2012-02-24
I am using kubuntu 11.10 and regularly experiencing "unresponsive script" errors. My system is up-to-date for all applications. 

I want to state right here that this is NOT an issue dependent on a /specific/ application but occurs across a range of GUI applications that use HTML. 

The general problem is that when the unresponsive script error occurs, if no user is present to respond, the entire system eventually becomes unresponsive and a reboot is required.

I have experienced this problem with Thunderbird, Firefox and Chrome. I know that it also occurs in IceWeasel and probably other applications as well. 

I am appealing to the deeper thinkers and more experienced folks out there to consider this problem. My hope is that something at the system level can be identified that is common to this problem irrespective of application, and that some command can be written (bash file or such) that would intercept the error and stop the script without user action at the GUI level.

Let's have some discussion on this please.

CT
:popcorn:

---

### Post by ohadcn on 2012-02-24
try to run them from terminal and tell us the terminal output when you get this message
 
 as far as i know that chromium & firefox do not have a lot in common  and uses their html engine so i guess the problem is in the network  connection or the gui
 how do you connect to the internet? is the connection stable? have you tried to browse using rekonq?

---

### Post by chitowner2 on 2012-03-08
I don't actually ever see the scripts that cause problems, so I wouldn't know how to run them in a terminal. Also, re-thinking, chrome/chromium does not have the same problem, but comparing chrome/FF/konqueror, very often konq uses more system resources (cpu and memory) than either chrome or FF. 

My internet connection is not normally a problem. For example I never have problems with instant messaging when the script problems occur. They are clearly not related to basic connection status. 

As for re-konq, as distinct from konq, I am not sure since I don't normally use re-konq, but I am aware it is available.



> **ohadcn said:**
> try to run them from terminal and tell us the terminal output when you get this message
 
 as far as i know that chromium & firefox do not have a lot in common  and uses their html engine so i guess the problem is in the network  connection or the gui
 how do you connect to the internet? is the connection stable? have you tried to browse using rekonq?

---

### Post by Zorael on 2012-03-10
Difficult to say.

As suggested you may want to start your browsers from a terminal and see if they output anything of interest.

If it eventually bogs your whole machine down, it may be that the "unresponsive script" starts infinitely looping and hogging more and more memory, until the point where you run out of RAM and it has to start hitting the disk for swap.

What you could try at this point to save yourself a reboot is to force an out-of-memory kill; this will forcedly terminate the process that's consuming the most memory. To do this, hit **Alt+SysRq+F** and wait a few seconds. If it doesn't seem to react, hit **Alt+SysRq+R** first and then the first command again. Entering '**dmesg**' in a terminal after regaining control should list what process was killed and give an inkling to what's happening.

The only thing HTML-y that I know is shared between Firefox/Thunderbird and Chromium are the normal plugins, like Flash and Java. There may be more; I'm hardly an expert on this.

There are probably ways to audit and internally debug scripts/plugins from inside both those browsers. You could try exploring the Chromium inspector, for instance. Googling around may help.

---

### Post by chitowner2 on 2012-03-10
Zorael,

Thanks for the detailed response. I will indeed jot those commands down on my cheat-sheet for handy reference. Like the sock puppet BTW.

CT

---

### Post by matt_symes on 2012-03-10
Hi

> but occurs across a range of GUI applications that use HTML. 

I think it's more lightly to be Javascript.

Do you still see if it you disable Javascript in your browsers (etc) ? It may be painful to browse certain sites for a while but it would implicate/eliminate it.

I see the same error (by the looks of it) occasionally in Firefox but i have not bothered to look into it.

I have seen this in Ubuntu 12.04.

EDIT: Can you list some of the sites where you see this error.

Kind regards

---

