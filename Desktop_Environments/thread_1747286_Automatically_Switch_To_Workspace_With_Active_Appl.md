---
title: "Automatically Switch To Workspace With Active Application (with Compiz?)"
date: 2011-05-02
forum: Desktop Environments
---

### Post by pistachepastis on 2011-05-02
Hi all,

I wondered whether there is a way in Compiz (or some other way) of not just assigning particular applications to default workspaces, but also, when an application is opened, to switch to the designated workspace automatically. (That is, "follow" the active application)

So suppose:
Firefox is assigned to workspace 2.
I am currently in workspace 1, where I launch Firefox.
Firefox opens in workspace 2, but I myself am still in workspace 1.

What I wonder then is: Is there a way of following Firefox, so to speak? That is, in my example, that I switch automatically to workspace 2

I am using Ubuntu 10.10.

Hope this is clear.
Thanks in advance!

---

### Post by Bonster on 2011-05-03
Enable the plugin called 'Extra WM Actions' in ccsm

Theres a option for 'Activate Demanding Attention Windows'

---

### Post by pistachepastis on 2011-05-04
Great! That did it!

---

### Post by pistachepastis on 2011-05-04
Mmm, I noticed that this works only for applications that actually can demand my attention (for instance an instant message pop-up, or a reminder pop-up), not for, e.g. firefox.

So when I open firefox in workspace 1, it moves to workspace 2, without having a demanding attention button in workspace 1. 

Moreover, what the Extra WM plugin still asks is to hit a keystroke. Is there no way of automatically following the window (without keystroke)?

(something what looks similar to Xfce option to "focus on window's own workspace")

---

### Post by pistachepastis on 2011-05-08
I found another (perhaps not so elegant) way.

I wrote a shell script, with a set of wmctrl commands (wmctrl can be obtained through synaptic).

Whenever I click my Firefox button, it runs the script, rather than simply Firefox. The script does the following:
1. it opens firefox
2. sends the window to workspace 2
3. switches to workspace 2
4. brings the window into focus.

Here is the script:
```

#!/bin/bash
firefox &
sleep 1

wmctrl -r firefox -t 2
wmctrl -s 2
wmctrl -a firefox

```

I saved the script in my home directory, (named .firefoxredirect.sh)

I made it executable in terminal through:

```

sudo chmod a+x ~/.firefoxredirect.sh

```

And then made a "Custom Application Launcher", which executes the command

```

bash .firefoxredirect.sh

```

One problem remains. If I launch Firefox from within a different application, the script is not executed. So Firefox moves to the desired workspace only through the Custom Application Launcher.

I tried to solve this using Devil's Pie, but Devil's Pie scripts don't seem to allow the inclusion of bash commands.

Help would be much appreciated.

---

### Post by ibnishak on 2012-08-13
Did anyone make any progress in this matter?

---

### Post by wildmanne39 on 2012-08-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

