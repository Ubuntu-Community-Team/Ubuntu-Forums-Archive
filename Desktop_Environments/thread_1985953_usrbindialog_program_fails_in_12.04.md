---
title: "/usr/bin/dialog program fails in 12.04"
date: 2012-05-24
forum: Desktop Environments
---

### Post by rhdinah on 2012-05-24
I've this shell ...

```
#!/bin/bash
DELAY=90
TIME=$(echo "scale=0; `date +%H`*60+`date +%M`+$DELAY" | bc -l)
HOUR=`printf "%02d" $(echo "scale=0; $TIME/60" | bc -l)`
MINUTE=`printf "%02d" $(echo "scale=0; $TIME%60" | bc -l)`
HOUR=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE/100" | bc -l)`
MINUTE=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE%100" | bc -l)`
HH=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE/100" | bc -l)`
MM=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE%100" | bc -l)`
TIME=`dialog --stdout --title "Shutdown" --timebox "\nShutdown time:" 0 0 $HH $MM 00`
if [ $? -eq 0 ]; then
	sudo -b shutdown -P ${TIME:0:5}
fi
```

Which works reliably and as expected in 10.04 and 10.10. With 12.04 the dialog fails by returning a return code of -1 ... sometimes and not reliably ... some days it works ... some time of the day it works ... strange. The man page indicates that -1 is returned if the ESC key is pressed ... which it isn't ... or that an error has happened within **dialog** itself.

Has anyone any clue whether this is really a failure or not? Thank you!

---

### Post by rhdinah on 2012-05-24
Never mind ... (embarrassing) ... because I didn't modulus 24 for hours ... so I delivered **dialog** improper input parameters is why it failed. Turns out that 10.04 and 10.10's **dialog** was more tolerant of bad parameters. Corrected below is a handy and inexpensive shutdown script. Make yourself a password-free shutdown user and away you go. Great for shutting down your system by a certain time if you're watching a video in bed and fall asleep. :-)

```
#!/bin/bash
DELAY=90
TIME=$(echo "scale=0; (`date +%H`*60+`date +%M`+$DELAY)%1440" | bc -l)
HOUR=`printf "%02d" $(echo "scale=0; $TIME/60" | bc -l)`
MINUTE=`printf "%02d" $(echo "scale=0; $TIME%60" | bc -l)`
HOUR=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE/100" | bc -l)`
MINUTE=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE%100" | bc -l)`
HH=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE/100" | bc -l)`
MM=`printf "%02d" $(echo "scale=0; $HOUR$MINUTE%100" | bc -l)`
TIME=`dialog --stdout --title "Shutdown" --timebox "\nShutdown time:" 0 0 $HH $MM 00`
if [ $? -eq 0 ]; then
	sudo -b shutdown -P ${TIME:0:5}
fi
```

---

