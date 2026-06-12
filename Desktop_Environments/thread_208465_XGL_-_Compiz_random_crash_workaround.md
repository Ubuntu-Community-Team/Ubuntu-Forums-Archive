---
title: "XGL - Compiz random crash workaround"
date: 2006-07-03
forum: Desktop Environments
---

### Post by mkaragia on 2006-07-03
I am having some problems with Compiz crashing at random points.:(  The first solution I came up with was to put a button on the taskbar and push it every time this happens so that Compiz reloads. The script that the button was running was:
```
#!/bin/bash
killall gnome-window-decorator &
wait
gnome-window-decorator &
compiz --replace gconf &
```
Finally, I wrote the following script which runs once at startup and takes care of the reloading of compiz when this is needed. 
```
#!/bin/bash
if [ `ps aux | grep -v grep | grep -c Xgl` -ne 0 ]; then 
	#echo -e "XGL present\n";
	while ([ 1 -eq 1 ]);
	do

		if [ `ps aux | grep -v grep | grep -c compiz.real` -gt 0 ]; then 
				#echo -e "Compiz present\n"
				true;
			else
				#echo -e "Compiz NOT present\n"
				killall gnome-window-decorator &
				wait
				gnome-window-decorator &
				compiz --replace gconf &
		fi

	sleep 5
	done
fi
#echo -e "XGL NOT present\n";
exit 0
```]

All I have to do is wait 5 seconds at the most for compiz to reload \\:D/ (of course you can reduce that even more in the script). It also checks if Xgl is running (and terminates if it doesnt) so that it does not interfere with the normal Ubuntu window manager, should you choose to login using that instead of Xgl.
I though someone might find this useful. If anyone needs further instructions about how to use this script, ask here and I will post full instructions. I hope this helps.:)

---

### Post by mkaragia on 2006-07-03
Btw, just installed the latest CVS (using the excellent guide found [here]("http://ubuntuforums.org/showthread.php?t=148860")) and they REALLY fixed stuff:) Not a single crash so far, and I've used it for a few hours. Flawless!\\:D/ \\:D/  Well done people!
This could effectively render my script above useless, but I so much prefer having no problems than finding ways to briefly patch them;)

---

### Post by snowturtle on 2006-07-06
[QUOTE=mkaragia]Btw, just installed the latest CVS (using the excellent guide found [here]("http://ubuntuforums.org/showthread.php?t=148860")) and they REALLY fixed stuff:) Not a single crash so far, and I've used it for a few hours. Flawless!\\:D/ \\:D/  Well done people!
This could effectively render my script above useless, but I so much prefer having no problems than finding ways to briefly patch them;)[/QUOTE]

Are you familiar with this post:

[http://www.ubuntuforums.org/showthread.php?t=133427]("http://www.ubuntuforums.org/showthread.php?t=133427")

It describes a method toinstall Xgl and compiz.

I installed XGL on AMD64 using this method, and it worked. So now this method is no longer needed, and synaptic will work to install xgl / compiz?

---

### Post by mkaragia on 2006-07-10
> **snowturtle said:**
> Are you familiar with this post:

[http://www.ubuntuforums.org/showthread.php?t=133427]("http://www.ubuntuforums.org/showthread.php?t=133427")

It describes a method toinstall Xgl and compiz.

I installed XGL on AMD64 using this method, and it worked. So now this method is no longer needed, and synaptic will work to install xgl / compiz?

Nope. I used a similar guide to the one you described to install my Xgl and compiz. The script I have given is to restart compiz if it crashes during its usage.

---

### Post by passonno on 2006-07-12
Please post full instructions.  I could definitely use this.

So how stable is compiz for you?

---

### Post by sceptre0 on 2006-07-12
Does it crash when you push Shift+Backspace? I had that problem.  It seemed like it was randomly crashing to me, but I knew of this bug when I installed compiz/xgl.  Here is a link to the fix.

[http://www.compiz.net/viewtopic.php?id=1199](http://www.compiz.net/viewtopic.php?id=1199)

I found the link on this website.  It was very helpful setting up XGL.
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

---

