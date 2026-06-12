---
title: "Applet to open favorite directories"
date: 2010-06-26
forum: Desktop Environments
---

### Post by finny388 on 2010-06-26
I'm using Ubuntu 10.04.

I'm looking for a panel applet that will act much like the Application/Places menu but only includes my few favorite directories preferably with submenu ability and icon settings.

any suggestions?

I found this very difficult to word in google or elsewhere.

---

### Post by Dr_Willis on 2010-06-26
Check out Hawkscope  - it puts a applet icon in the panel that lets you quickly access various locations.

It is a java app and also works on other operating systems. So you may like so much you will want it on  the 'other' os's  out there.  :p

[http://code.google.com/p/hawkscope/](http://code.google.com/p/hawkscope/)

---

### Post by ajgreeny on 2010-06-26
Forgive me, but why is this any better or different from using Bookmarks which are already on the gnome menu?  I have never seen or heard of Hawkscope before, but can not see that it really adds anything to what is already there in Bookmarks.

---

### Post by finny388 on 2010-06-26
Compared to Bookmarks:

[LIST]
[*]I want to have categories for them (submenus).

[*]I don't need to see every place on the computer, I just want 2 categories, 3 locations within each - that's it.

[*]Finally, I'm using the Main Menu applet (main GNOME menu) so it is click, mouse over, click instead of a simple click to get to "Places".
[/LIST]

Re: Hawkscope

Looks like EXACTLY what I'm looking for:
> [LIST]
[*]Configurable favourite locations for quick access
[*]Hide unwanted drives, folders or files by adding them to blacklist
[/LIST]
Thanks Dr Willis, so I downloaded the deb file from the link - the 5th one down "hawkscope_0.6.1-1_i386.deb   	 Debian Package for i386 GTK Linux (Ubuntu)" - I'm using 32bit Ubuntu 10.04.

I ran the installer without any problems, took about 4 minutes, it is now in my menu under Accessories. But when I launch it, there a  lightning quick flash in my panel and then nothing. Checking System Monitor, there is no hawkscope process running. I rebooted, no change.

Have you used this yourself? On what OS? Any idea what is wrong? I don't have compiz enabled though I doubt that's an issue.

---

### Post by finny388 on 2010-06-27
^

---

### Post by finny388 on 2010-06-27
If I type hawkscope in terminal and hit enter, I get error:
"Error occurred during initialization of VM
Too small initial heap for new size specified"

---

### Post by kerry_s on 2010-06-27
you can do exactly what you want with the menu editor.
then you can add the menu to the panel.

you just create the sections & launchers
then add to panel-> application launcher
drag the whole menu instead of opening it

hope that makes since?
pics

---

### Post by finny388 on 2010-06-28
thanks kerry_s

As a matter of fact I had done exactly that before.

I just wanted something dedicated (not part of the ubuntu menu) and easy to customize (Menu editor is pretty clunky).

I received a fix for Hawkscope:
> 1. Edit /usr/bin/hawkscope (or locate the file with command "which hawkscope" if it's not available there)
2. In line: 

java -Xms4m -Xmx32m -jar /usr/share/hawkscope/hawkscope.jar $1 $2 $3 $4 $5 $6 

increase -Xms4m -Xmx32m values to something bigger, i.e. -Xms16m -Xmx64m

So if anyone else has trouble using it, this worked for me.

Unfortunately, it is no cleaner than ubuntu menu, (but it is highly customizable and offers plugins)

I think I'll go the way of the drawers applet.

---

