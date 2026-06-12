---
title: "Gnome's &quot;Create Launcher...&quot;"
date: 2006-08-22
forum: Desktop Environments
---

### Post by aweller on 2006-08-22
Hi,

I have downloaded a Java app that I would like to create a desktop launcher for.

In the terminal, the app runs like:

cd /opt/Joone/ && ./RunEditor.sh

So I created a launcher with that command. Unfortunately that doesn't work (it doesn't like 'cd').

So I created an alias in my .bashrc:

alias joone='cd /opt/Joone/ && ./RunEditor.sh'

and put "joone" in the launcher's command box. Unfortunately that doesn't work either.

Does anyone have any ideas how to get Gnome's "Create Launcher..." working in this example?

Thanks, Andy

---

### Post by argie on 2006-08-22
Why not just launch the script directly?
```

bash /opt/Joone/RunEditor.sh

```
And enable the Run in Terminal?

---

### Post by aweller on 2006-08-22
Just tried this to no avail. The Terminal just opens and closes again in a split second. I have had:

cd /opt/Joone/ && ./RunEditor.sh

running from a launcher before, but not now...

---

### Post by aweller on 2006-08-24
Does anyone have any solutions...?

Andy

---

### Post by ToniWiki on 2007-04-03
I suppose that the RunEditor.sh script call the Java App and the jar file is in the same folder. In this case edit the RunEditor.sh script to make something like this:

```

#!/bin/sh
cd /opt/Joone
java -jar Editor.jar

```

Then create a launcher to the script in Desktop or where you want.

It worked for me. :)

---

### Post by pppetter on 2007-04-03
I have done just like ToniWiki, but my script starts counter-strike...
> #!/bin/bash
cd /media/Arkiv/Annat/Wineprogram/Steam
WINEDEBUG="fixme-all" wine Steam.exe -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 128000 &

I put it in /usr/bin, so that it can be run everywhere

---

