---
title: "pcgen"
date: 2008-06-03
forum: Gaming &amp; Leisure
---

### Post by the2ndgenesis on 2008-06-03
Hey everyone, just wanted to stop in to ask about some problems I've had with the F/OSS RPG campaign manager, pcgen ([http://pcgen.sourceforge.net/01_overview.php](http://pcgen.sourceforge.net/01_overview.php)).

Frankly, I'm at my wit's end as far as the installation/configuration goes. What I thought would be an easy new roll for a friend's DND campaign turned out to be an hours-long tribulation of trying to figure out how to load the source materials, totally in vain. I still have no idea what to do... what file to configure to load the 3.5 SRD, whatever. No matter what I did it refused to work... and the on-site documentation was no help either.

To be honest, I'm kind of disappointed that the primary open source campaign manager isn't straightforward enough for a novice such as myself to use. Does anyone have any advice from experience on how to get the program running satisfactorily?

If it helps, I unzipped the installation files to my home directory, where .pcgen was also created when I ran the program. Attached is a screencap of what the GUI looks like when I run pcgen from the terminal... perhaps there's just something really obvious that I'm missing here.

Any help is greatly appreciated. Thanks everyone!
/rant

---

### Post by Thpbltblt on 2008-06-13
Bump.

I've got the same problem.  Everything appears to have installed fine, and the source files are there, but they don't show up in the gui.

---

### Post by craigchambers on 2008-07-09
Same problem here... Did either of you solve this?

---

### Post by craigchambers on 2008-07-09
OK, I got this to work eventually!

Here's how I got it to work...

1) Make sure that the only version of Java installed is Sun's (JRE 6 worked for me).  I uninstalled Open Java (installed by default in Hardy) and then reinstalled Sun's Java in Synaptic.

2) Extract PCGen into ~/.pcgen/ (where ~ means the user home folder)
To do this I opened the zip file, browsed into the pcgen5140 folder, did a select all (Ctrl + A) then selected extract.  I selected to extract to .pcgen

3) Make pcgen.sh executable (either via the gui from properties > permissions > execute, or via command line: chmod 755 pcgen.sh)

4) Run pcgen.sh - all the sources are now available.

Hope that it works for you guys!
I got a lot of my info from the PCGen Yahoo groups: [http://games.groups.yahoo.com/group/pcgen/message/97531](http://games.groups.yahoo.com/group/pcgen/message/97531)

/Craig

---

### Post by Thpbltblt on 2008-07-09
That solved my problem.  Thanks Craig!

---

### Post by _march_ on 2008-08-01
> **craigchambers said:**
> 
1) Make sure that the only version of Java installed is Sun's (JRE 6 worked for me).  I uninstalled Open Java (installed by default in Hardy) and then reinstalled Sun's Java in Synaptic.

You can also start it by using the absolute path: 
*/usr/lib/jvm/java-VERSION-sun/jre/bin/java -jar pcgen.jar*

This will do it:
**pcgen.sh**
```
#!/bin/bash
cd ~/.pcgen/
/usr/lib/jvm/java-6-sun/jre/bin/java -jar pcgen.jar
```

---

### Post by KrasniyRus on 2010-02-06
> **craigchambers said:**
> 
1) Make sure that the only version of Java installed is Sun's (JRE 6 worked for me).  I uninstalled Open Java (installed by default in Hardy) and then reinstalled Sun's Java in Synaptic.
/Craig

Thank you a lot! It worked for me too

---

