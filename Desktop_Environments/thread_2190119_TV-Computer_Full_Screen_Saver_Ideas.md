---
title: "TV-Computer Full Screen Saver Ideas?"
date: 2013-11-25
forum: Desktop Environments
---

### Post by The Immortal on 2013-11-25
I have my computer screen mirrored on my big screen TV.
I play CLEMENTINE and use my phone as the remote (cool!).
I must keep the computer screen running while  it is connected to the TV or else the TV quits.
I want a screen saver that runs THE WHOLE TV not just "most" of it.
Since the TV is a plasma I'm afraid of screen burn in.  This TV doesn't have a feature that allows the TV to run while the screen is shut off.  And I can't find A PLEASANT screen saver in Ubuntu.

Any ideas??

Thanks in advance.

---

### Post by papibe on 2013-11-25
Hi The Immortal. Welcome to the forum ):P

I'd start by checking the power settings on 'Power', so that the computer is being suspend when inactivity.

Then I'd go to 'Brightness and Lock', and set to never turn off the screen when inactivity. Also I'd set not to lock your computer.

By default, there's no screensavers anymore. Take a look at this [tutorial]("http://askubuntu.com/questions/292995/configure-screensaver-in-13-04") in order to install a set of them.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by stinkeye on 2013-11-26
You could use xautolock  to play a slideshow or video after a set period of idle time.

eg ...plays a fullscreen picture sideshow using image viewer after 3 mins idle time.
```
xautolock  -notify 10 -notifier 'notify-send "Slideshow will start in 10 seconds"' -time 3 -locker "eog --fullscreen --slide-show [COLOR="#FF0000"]/path/to/picture/folder[/COLOR]"
```

or play a video
```
xautolock  -notify 10 -notifier 'notify-send "Video will start in 10 seconds"' -time 3 -locker "totem --fullscreen [COLOR="#FF0000"]/path/to/vid[/COLOR]"
```
Specify [COLOR="#FF0000"]your path[/COLOR]

Install via terminal...
```
sudo apt-get install xautolock
```
See manual in terminal....```
man xautolock
```

---

