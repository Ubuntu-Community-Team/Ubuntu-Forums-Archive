---
title: "Weird Problem ?!?!?"
date: 2009-01-07
forum: Desktop Environments
---

### Post by hmgp on 2009-01-07
Hello everyone!

I have been struggling with a problem for some time now. It doesn't affect my daily work but it's annoying.

Since I made an upgrade to Ubuntu 8.10 from Ubuntu 8.04 every time I try to open a folder on the Places menu, for example: Documents or Video or Home, Ubuntu opens the default media player instead of the Nautilus within the selected folder !?!?!?
If I ask to open the Places->Computer or Places->Network they open OK within Nautilus, only the default Gnome Folders (Documents, Videos, Home, etc.) have this problem.

So now I will tell you what I already tried:

- So I tried looking at the .gconf with gconf-editor but nothing.

- I have a separate home partition so I already made a clean install and ... nothing happened. Problem persisted.

- Next I went radical, deleted .gconf, .gnome2 but nothing again.

Anyone has a clue on this?

Thank you!

---

### Post by hmgp on 2009-01-08
bump!

still no solution...

---

### Post by zhocchao on 2009-01-08
hi
in nautilus any folder right click...
open with other aplication...
open folder...

maybe that will help

g
z

---

### Post by hmgp on 2009-01-09
Hi there. Thank you but I don't quite understand your idea or you didn't quite get the problem.

I can't do a right clink in a menu entry under the "Places" menu...

---

### Post by keithld on 2009-01-09
Try going to Places > Computer then Edit> Preferences then click on the "Media Tab" and see what the different devices are set too...

You can change some of them there...

I had a similar problem after installing VLC, but I uninstalled it and the problem seemed to go away...

---

### Post by zhocchao on 2009-01-09
I could be wrong, but as long as you don't open nautilus and try what I wrote above I wont believe it. (someone I know had the same Problem(at least I think so) and that was the solution). 
...
...
...
I'd try to create a folder on desktop and then try what I wrote above (I am starting to get an idea what you mean. Slow but there will be light)
z

---

### Post by hmgp on 2009-01-14
> **zhocchao said:**
> I could be wrong, but as long as you don't open nautilus and try what I wrote above I wont believe it. (someone I know had the same Problem(at least I think so) and that was the solution). 
...
...
...
I'd try to create a folder on desktop and then try what I wrote above (I am starting to get an idea what you mean. Slow but there will be light)
z

Nope! Did what you said but nothing changed. Still the same problem...

---

### Post by hmgp on 2009-01-14
> **keithld said:**
> Try going to Places > Computer then Edit> Preferences then click on the "Media Tab" and see what the different devices are set too...

You can change some of them there...

I had a similar problem after installing VLC, but I uninstalled it and the problem seemed to go away...

I can change, but there is none linked to the folders. It's only Audio,CD,DVD,etc...

I really don't remember more things to do. Maybe opening a bug?

---

### Post by zhocchao on 2009-01-14
ok
i am wrong!
If you click the folder on the desktop nautilus opens the way it should?

i found this in .GnoMenuSettings.xml:


<Command Action="Home" Exec="xdg-open [Home]"/>
<Command Action="Documents" Exec="xdg-open [Documents]"/>
<Command Action="Pictures" Exec="xdg-open [Pictures]"/>
<Command Action="Music" Exec="xdg-open [Music]"/>
<Command Action="Games" Exec="xdg-open [Videos]"/>

Maybe yours is different?

---

### Post by wirespot on 2009-01-14
Bump. Any luck?*I got the same problem, except for me it opens directories in a MC (Midnight Commander) running in an xterm. Only some stuff under the Places menu does this (Home, Desktop and a folder right next to them). The rest of folders everywhere use Nautilus.

---

### Post by zhocchao on 2009-01-14
are the same lines in your .GnoMenuSettings.xml ?

---

### Post by hmgp on 2009-01-15
> **zhocchao said:**
> ok
i am wrong!
If you click the folder on the desktop nautilus opens the way it should?

i found this in .GnoMenuSettings.xml:


<Command Action="Home" Exec="xdg-open [Home]"/>
<Command Action="Documents" Exec="xdg-open [Documents]"/>
<Command Action="Pictures" Exec="xdg-open [Pictures]"/>
<Command Action="Music" Exec="xdg-open [Music]"/>
<Command Action="Games" Exec="xdg-open [Videos]"/>

Maybe yours is different?

Wooooowwww! Here is that file in your system? I cant find a file named like that in my system... Neither any with settings with xml extension, and neither with Menu and xml extension.

---

### Post by zhocchao on 2009-01-15
(Here=Where?) It's in Home. If you don't have this file, maybe it could help if I send you mine, or you could create another user and look if he has this file.

---

### Post by hmgp on 2009-01-15
I tried that. In a new user home I don't get the file named .GnoMenuSettings.xml.

Strange, but in a new user everithing works fine in the places menu ...

I'm getting tired. Maybe I get radical an copy all .(dirs) from the new user home to my home...

---

### Post by zhocchao on 2009-01-15
[http://ubuntuforums.org/archive/index.php/t-967467.html](http://ubuntuforums.org/archive/index.php/t-967467.html)

This sounds like your problem (and like my solution). Maybe the command line thing is a help.

(the xml file could be a dead config file of another software)

---

### Post by hmgp on 2009-01-19
Thank you.

That did it.

It's kind of weird since it only took one action on Documents folder to get all the other (Videos, Music, etc.) to work...???

Thanks again for you help!

---

