---
title: "QGIS: Install on Jaunty?"
date: 2009-09-23
forum: Education &amp; Science
---

### Post by christianshearer on 2009-09-23
Can someone help me to install QGIS on jaunty.  I have tried a few pathways that are shown around the web, but I am not sure that they were meant for jaunty.  For whatever reason, it is still not installed on my computer.

I am totally a novice in dealing with the terminal, (recent windows convert), so please be very explicit in your instructions.  Thank you very much. 

Christian

---

### Post by christianshearer on 2009-09-23
Hey!  I did it, only with the help of Ubuntu forums and the awesome people helping here. Thanks so much to badaveil, ajgreeny, and technophobia.

 I'll try to tell you what I did.

First Go to **System -> Administration -> Software Sources**

(enter your password)

"**Third Party Software**" Tab

Click "**+Add**"

When it prompts you for a APT Line, enter:

deb [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/) jaunty main

click on "**Add Source**"
Then click "**Reload**" to update

At this point I got a "NO PUBKEY" error, but not to worry, because we have added the source.

Now, open your terminal type the following:

```

~$ gksudo gedit /etc/apt/sources.list
```

(A window should open, and you should see your newly added source, [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/))

close that window with the x in the corner

then type into the terminal:
```

~$ sudo apt-get install qgis
```

(it should install)

[COLOR="Purple"]if it doesn't then try this:
```

~$ sudo apt-get update
```

that will do some stuff then try this again:
```
~$ sudo apt-get install qgis
```[/COLOR]


then:
```

~$ qgis
```

And walla! It should open. Or you can find it automatically added to programs:
[B]
Applications -> Education -> Quantum GIS[/B]


This whole community of open-sources is awesome. I feel like I just kicked microsoft in the balls, and it feels good.

---

### Post by christianshearer on 2009-09-29
I have an amendment to that previous post.

After having QGIS for a week, I realized I had the unstable version.

So, in that first step, when loading a APT line, load this instead (stable):

deb [http://ppa.launchpad.net/qgis/stable/ubuntu/](http://ppa.launchpad.net/qgis/stable/ubuntu/) jaunty main


otherwise follow the directions, and you should have it.

Peace
C

---

