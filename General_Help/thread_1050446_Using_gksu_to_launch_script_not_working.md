---
title: "Using gksu to launch script not working"
date: 2009-01-25
forum: General Help
---

### Post by bearslumber on 2009-01-25
Hi 

I have a very simple script called > vuzein my ~/bin directory where ~ is /home/bear: 

The script = 
```
#!/bin/bash
cd ~/opt/vuze
./azureus 
```

When I add a new launcher to the main menu using > system/preferences/main menu with the following properties
> type = application;
name = vuze;
command = /home/bear/bin/vuze

the script is launched with no problems.

Now I wish to run the launcher as if I entered ```
sudo /home/bear/bin/vuze
``` on the commend line. The command runs okay on the command line.

But when I change my launcher properties to 
> command = gksu /home/bear/bin/vuze 
nothing seems to happen.

What am I doing wrong? Its driving me bonkers. 

All the help seems to only skim the surface. 

Any help to resolve this issue would be greatly appreciated. Further pointers to more in depth help in this area would be a bonus++++++.

Many thanks in advance.

Bearslumber

---

### Post by bearslumber on 2009-01-27
Thank you for viewing this thread.

The problem was in the script in particular the use of the "~". The line..

```
cd ~/opt/vuze
```

would substitute "~" for ```
/home/bear/opt/vuze
``` when using it directly from the bear login account. 

When invoking the script with gksu or gksudo, the "~" would be substituted to ```
/root/opt/vuze
``` which does not exist.

The lesson I have learned here is always to try invocation on the command line if there is a problem. It immediately revealed the problem.

There is a "user" parameter that is accepted by the gksudo command, and I guess this is what I should have used. Will report this in my next reply when I get on the ubuntu machine tonight.

8-[

One thing I don't understand is why entering ```
sudo /home/bear/bin/vuze
``` on the command line terminal window works fine. Are there some subtle differences between "sudo" and "gksudo"?

Regards

Bearslumber:D

---

### Post by .bitrunner on 2009-11-16
**BUMP**
 
I am trying to launch a would be launcher+script (¨Nautilus_XFCE-root¨) :
 
#!/bin/bash
gksu /usr/bin/nautilus --no-desktop
 
which doesn´t work even from terminal because gksu complains that it doesn´t recognize --no-desktop
 
BUT 
 
#!/bin/bash
sudo /usr/bin/nautilus --no-desktop
 
Works perfectly
 
For anyone wondering why I would want to run such an odd script... I´m running Xubuntu, and have had better luck with Nautilus over Thunar as far as recognizing/mounting second HDD, which gets swapped out frequently. The problem with Nautilus in XFCE is that when launching it, Gnome hijacks your desktop.
Which is where the --no-desktop comes in, and works beautifully. And of course I want to run as root because I´m generally in there to do more than just look at files.
 
I´m trying to get away from sudo launching a GUI program because it leaves a Terminal window hanging open, getting all verbose about things. And that&#347; what GKSU is for anyway, right?
 
also:
 
#!/bin/bash
gksu /usr/bin/nautilus
 
Works as it should, but does not issue the --no-desktop argument, so away goes my X desktop and all my Icons, and I´m back to the Gnome Heron again...no offense to the Heron!
 
To sum things up... why is gksu not able to interpret what follows it the way that sudo does?
and are there any tricks to using gksu in such a way?
 
Thanks in advance for any advice

---

### Post by ysangkok on 2011-04-01
> **.bitrunner said:**
> **BUMP**
To sum things up... why is gksu not able to interpret what follows it the way that sudo does?
and are there any tricks to using gksu in such a way?


Yes. Use the "--" flag to tell i.e. gksudo that you are finished specifying parameters for gksudo.

An example:
```
$ gksudo -- zenity --error
```

Works great.

---

