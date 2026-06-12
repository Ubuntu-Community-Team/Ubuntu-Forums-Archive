---
title: "Sid Meier's Alpha Centauri &quot;serial&quot; Crash"
date: 2010-10-11
forum: Gaming &amp; Leisure
---

### Post by mega_muda on 2010-10-11
Greetings, 
 
This is my first post so please be gentle. 

I managed to run Sid Meier's Alpha Centauri on Ubuntu 10.04. The game runs, I watch the fancy intro make all the selections and things and then I see my colony pod landing on the planet. Next thing, the game asks me how I want to name my first city. So I make my choice and then the game suddenly crashes giving me this:

X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #563
  Current Serial #566

I have already searched the forums and the only thing I found were 4 year old threads references to a non-existent "X" file I should modify.

Any help would be greatly appreciated. This is a gem of a game and I would love to make it run.

---

### Post by rettichschnidi on 2010-10-11
Problem: This games needs a X-Server without the Composite-Feature enabled

Solution: Disable Composite

How to do:

Either

a) add to your /etc/X11/xorg.conf:
	  		Section "Extensions"
			Option "Composite" "Disable"
			EndSection

b) create a new xorg.conf and start a 2nd server (google helps)
c) Use Xephyr and disable the compisite feature (sudo apt-get install xserver-xephyr, "Xephyr :1 -ac -br -fullscreen -reset -extension Composite")

---

### Post by mega_muda on 2011-01-20
Las time I gave up on trying at some point. Now I am back and more determined than ever.
This time there seems to be a whole new problem. The game won't run at all.
After "sudo smacpack" all I get in response is this:

X Error:  BadValue
  Request Major code 129 (XFree86-VidModeExtension)
  Request Minor code 10 ()
  Value 0x13c
  Error Serial #84
  Current Serial #86

I have added a xorg.conf file to the X11 folder and even added the suggested lines to the xorg.conf.failsafe file.

Does anyone have any suggestions on how to solve this?

(Now running on Ubuntu 10.10)

---

### Post by tryten on 2011-03-18
Hi!
Do u still have problems with the game? I have xubuntu 10.10 and following rettichschnidi's suggestion helped me. First install Xephyr 
```
sudo apt-get install xserver-xephyr
``` I did a script to make the game easier to run, but u have to add your username:
```
#!/bin/bash
if [ `id -u` -ne 0 ]
then
        echo You have to run this script as root
        exit 1
fi

# Put in your username below
me=YOUR_USERNAME

Xephyr :1 -ac -br -fullscreen -reset -extension Composite &
DISPLAY=:1

echo Starting the game...
sudo -u $me -s smacpack
echo `killall -v Xephyr`
DISPLAY=:0
echo Bye $me 

```
You have to run it as superuser because of Xephyr, but the scrip will run the game as "YOUR_USERNAME".
I'm actually a bit proud. I'm trying to learn bash scripting and this script is my best so far.

Save it to /somewhere/some_name.sh and:
```
cd /somewhere/
chmod +x some_name.sh
sudo sh some_name.sh
```

If u want to start the game by hand, type the following in a terminal:
```
sudo Xephyr :1 -ac -br -fullscreen -reset -extension Composite &
#The screen goes black, use Alt+TAB to find the terminal again
DISPLAY=:1
smacpack
```

---

### Post by DuckHook on 2011-03-29
Just a Linux n00b myself, but is it really a good idea to run any game as superuser? I'd rather go for option (b) and start a new Xserver.

---

### Post by rettichschnidi on 2011-03-30
Hi

Could you please try the new LIFLG installer?

Link: [http://liflg.org/?catid=7&gameid=90](http://liflg.org/?catid=7&gameid=90)
Feedback: [http://liflg.org/forum/viewtopic.php?t=949](http://liflg.org/forum/viewtopic.php?t=949)

You can start either:
- smac.sh for the original Alpha Centauri
- smacx.sh for the extension
- smacpack.sh for the "launcher" (thought this will require xephyr if you have composite enabled)

I'd like appreciate if you could report back if this installer works out of the box for you or if there are any errors.

---

