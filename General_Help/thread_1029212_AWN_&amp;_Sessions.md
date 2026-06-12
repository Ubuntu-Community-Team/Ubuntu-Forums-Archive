---
title: "AWN &amp; Sessions"
date: 2009-01-03
forum: General Help
---

### Post by detroit/zero on 2009-01-03
I have AWN added to my sessions to start automatically whenever I reboot/log into my computer. The problem is that when everything in the startups is being loaded, AWN loads before compiz and I get a little popup telling me that "AWN requires a compositing manager....", then compiz loads, and AWN starts normally.

I've tried adding sleep to the AWN launch command, but when a sleep is preset there, AWN fails to load at all until I do it manually, whether it's 10 seconds or 60. (The sleep command doesn't fail to load conky, though, which starts with a 30-second delay.)

In Sessions, I've seen the "current session" tab that lists all the startup items and their order/launch priority. I've been hunting around online, but I've not been able to find a definitive manual/how-to on how this tab in Sessions operates. As it stands, I have two items with an order of 40 (gnome-panel & nautilus) and then about a dozen or so things with an order of 50 - Conky & AWN are two of them, but so is Firefox (which doesn't load at startup), fusion-icon, update-manager, nm-applet.. so on & so forth.

I'm thinking if I change this order number for AWN & Conky I can do away with the sleep commands, and still have both not start until after compiz has had time to load and take over compositing my screen? 

Am I thinking right or not? Also, can anyone point me towards a more thorough explanation of how sessions works and is structured?

---

### Post by detroit/zero on 2009-01-10
One week bump.

---

### Post by kaivalagi on 2009-01-10
I have a generic session start script I run, it loads awn amongst other things....works fine (just change the bold "login" to your login name):

```
#!/bin/sh

	# Wait for gnome-session to load before starting anything else
	echo "waiting for gnome-session to be present before starting applications..."

	while true; do

	    if [ $(pgrep -u,**login** gnome-session) > 0 ]; then

			pidgin &
			pid=$!
			echo $pid > /tmp/pidgin.pid
			
			avant-window-navigator &
			pid=$!
			echo $pid > /tmp/avant-window-navigator.pid
			
			deluge &
			pid=$!
			echo $pid > /tmp/deluge.pid
			
			rhythmbox &
			pid=$!
			echo $pid > /tmp/rhythmbox.pid
			
			tomboy &
			pid=$!
			echo $pid > /tmp/tomboy.pid
		
			break;
		else

			sleep 1;

	    fi

	done 

fi
```

---

### Post by detroit/zero on 2009-01-10
> **kaivalagi said:**
> I have a generic session start script I run, it loads awn amongst other things....works fine (just change the bold "login" to your login name):
Looks handy. Am I correct to assume that I just remove the sessions-startup entries for whatever items are in this script, and let the script handle their launching? (In your examples, pidgin, awn, rhythmbox, etc..)

---

### Post by kaivalagi on 2009-01-10
> **detroit/zero said:**
> Looks handy. Am I correct to assume that I just remove the sessions-startup entries for whatever items are in this script, and let the script handle their launching? (In your examples, pidgin, awn, rhythmbox, etc..)

Yep, thats right. you may need an additional sleep inside the main if statement if you still have issues...especially if you are using conky

I also have a stop script, hence the pid file create...so I can turn all on and off as I see fit by using the 2 files...stop script below:

```
#!/bin/sh
	
	if [ -s  /tmp/pidgin.pid ] ;then	
		until ! read pid
			do
			kill "${pid}"
			done < /tmp/pidgin.pid
			rm -f /tmp/pidgin.pid			
	fi

	if [ -s  /tmp/avant-window-navigator.pid ] ;then	
		until ! read pid
			do
			kill "${pid}"
			done < /tmp/avant-window-navigator.pid
			rm -f /tmp/avant-window-navigator.pid			
	fi
	
	if [ -s  /tmp/deluge.pid ] ;then	
		until ! read pid
			do
			kill "${pid}"
			done < /tmp/deluge.pid
			rm -f /tmp/deluge.pid			
	fi
	
	if [ -s  /tmp/rhythmbox.pid ] ;then	
		until ! read pid
			do
			kill "${pid}"
			done < /tmp/rhythmbox.pid
			rm -f /tmp/rhythmbox.pid			
	fi
	
	if [ -s  /tmp/tomboy.pid ] ;then	
		until ! read pid
			do
			kill "${pid}"
			done < /tmp/tomboy.pid
			rm -f /tmp/tomboy.pid			
	fi

```

For some reason I had bash as the shell, not sh, so if things are not working properly change the line:

#!/bin/sh
to:
#!/bin/bash

Have fun

---

