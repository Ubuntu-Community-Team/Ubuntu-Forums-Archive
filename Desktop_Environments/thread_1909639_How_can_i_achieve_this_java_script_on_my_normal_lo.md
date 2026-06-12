---
title: "How can i achieve this java script on my normal login xfce"
date: 2012-01-15
forum: Desktop Environments
---

### Post by geekyhawkes on 2012-01-15
Hey folkes, so i found this script that allows you to welcome people to your website based on time of day;

[http://www.javascriptkit.com/script/cut163.shtml](http://www.javascriptkit.com/script/cut163.shtml)

I want my xubuntu system to do the same to me based on the user name i log in with (if possible, if not i can just fix the name displayed) and the time of dday.  Some form of welcome messgae in text, or selectable .mp3 would be my ideal but ive no idea where to start with this.

Can anyone here help me please?

Thanks;

Andy

---

### Post by Toz on 2012-01-20
How about something like this:
```

#!/bin/bash

AMPM=`date +%P`
SOUND=/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

if [ $AMPM == "am" ]; then
	TEXT="Morning"
else
	TEXT="Afternoon"
fi

canberra-gtk-play -f "$SOUND" &
zenity --info --title "Welcome" --text "Good $TEXT $USER" &

```

Save this code to a file, make the file executable and put it in the user's startup. 

You can change the sound that is played by editing the SOUND line and pointing it to the sound file of your choice (make sure its in an accessible location for all users).

You can change both the title and text of the pop-up box by editing the --title and --text parameters of the zenity command.

Note: you will need the "zenity" and "libcanberra-gtk0" packages installed (if not already present).

---

### Post by geekyhawkes on 2012-01-21
Great, thanks for this almost exactly what i wanted and really neat.  Would there be an easy way I could do morning, afternoon and evening? 

If i moved the SOUND= line to under the if statement then I guess that should trigger a different sound to be played in the morning or afternoon?

```

#!/bin/bash

AMPM=`date +%P`
# SOUND=/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

if [ $AMPM == "am" ]; then
	TEXT=" Morning "
	SOUND=/usr/share/sounds/morning.wav
else
	TEXT=" Afternoon "
	SOUND=/usr/share/sounds/afternoon.wav
fi

canberra-gtk-play -f "$SOUND" &
zenity --info --title "Welcome" --text "Good $TEXT $USER. Have a nice day." &

```

Thanks again for your help so far! Also, the audio fails to play, canberra just reports Failed to play sound: Sound disabled
in a terminal but sound is working on my machine, what am i missing?

---

### Post by Toz on 2012-01-21
Try this one:
```

#!/bin/bash

HOUR=`date +%H`

case $HOUR in
	0[0-9]|1[0-1])
		TEXT="morning, "
		SOUND="/path/to/mp3/file"
		;;
	1[2-7])
		TEXT="afternoon, "
		SOUND="/path/to/mp3/file"
		;;
	1[8-9]|2[0-3])
		TEXT="evening, "
		SOUND="/path/to/mp3/file"
		;;
	*)
	;;
esac

canberra-gtk-play -f "$SOUND" &
zenity --info --title "Welcome" --text "Good $TEXT $USER" &

```

As for the sound not playing in the terminal, try using **aplay** instead. If still nothing, what does the following return?
```
aplay -l
```

---

### Post by geekyhawkes on 2012-01-21
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Ive checked Alsamixer to make sure none of the outputs are muted, but thats all fine. VLC has audio fine within xfce if that helps at all?

Thanks for your help so far.

---

### Post by Toz on 2012-01-21
Try this:
```
aplay -Dplughw:0,1 /usr/share/sounds/morning.wav
```

If it doesn't work, also try with:
 -Dplughw:0,0
 -Dplughw:0,3

---

### Post by geekyhawkes on 2012-01-21
Thanks, so the aplay works, im guessing i could substitute the aplay command into the script above?

---

### Post by Toz on 2012-01-21
Yes, just substitute the command with the parameters that worked.

---

### Post by geekyhawkes on 2012-01-21
Legend, works perfectly now!  Good old AT&T provided my machine a voice:

[http://www2.research.att.com/~ttsweb/tts/demo.php](http://www2.research.att.com/~ttsweb/tts/demo.php)

Thanks again

---

### Post by geekyhawkes on 2012-01-22
Hmm, i psoke too soon, it works perfectly if i run it manually from the terminal but not when i login.  I get the message box but no audio when i login (i just added the script in settings manager - session and startup - application autostart).

What has i missed?

---

### Post by Toz on 2012-01-22
Is there anything in your ~/.xsession-errors log file?

---

### Post by geekyhawkes on 2012-01-23
Yes:

aplay: main:660: audio open error: Device or resource busy

Not sure what is using the audio at login though?

---

### Post by Toz on 2012-01-23
Hmm, maybe the userspace audio isn't initialized yet. Try adding a sleep function to the beginning of the script to delay it a little:
```
sleep 10s
```
...will pause the script for 10 seconds. If that works, try decreasing the value until it works properly.

---

### Post by geekyhawkes on 2012-01-30
9secs is the magic number.  Thanks alot guys works just how i wanted.

---

