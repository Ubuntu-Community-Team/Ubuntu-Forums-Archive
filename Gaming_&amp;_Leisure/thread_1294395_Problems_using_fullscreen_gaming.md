---
title: "Problems using fullscreen gaming"
date: 2009-10-18
forum: Gaming &amp; Leisure
---

### Post by Maramros on 2009-10-18
I have found this problem in Tremulous, Sauerbraten, Urban Terror, and Glest. I will be playing the game for about fifteen minutes, and then, randomly, the screen will go black, and then, when it comes on again, the game will be a small window, I'll be able to see my normal desktop behind it, and the computer is unresponsive. At that point, the only thing I can do is force-quit the computer by holding down the power button, which is not a good thing to do.
Is this a driver problem? If so, what driver am I missing?

---

### Post by hikaricore on 2009-10-18
Have you tried disabling the screensaver?

---

### Post by myromance123 on 2009-10-18
I had this exact same problem!
 No joke, read [here]("http://ubuntuforums.org/showthread.php?t=1283352") to see how I got help from AI to solve it.

 Let me know if that helped you fix it!
The problem you have truly is the exact same problem I had... It might start to become a phenomena for Ubuntu 9.04...or not.


EDIT: To make things easier for you (if you know you're way around Ubuntu), switch off/disable screensaver and Untick "Unredirect Fullscreen" from General Options in ccsm. Else just head to the last post in the thread in the provided link.

---

### Post by Maramros on 2009-10-19
Well, I thought that fixed it, but apparently it didn;t. I was playing Urban Terror, and this time it lasted almost an hour, but then it minimized the screen *and* put the computer to sleep. I woke the computer up again, and the screen went dark for a second, and I thought it was going to re-fullscreen. However, when the screen resumed, Urban Terror was still windowed, the Urban Terror window was black, and one note of the ambient music was playing over and over, and the computer was unresponsive. I had to restart the computer.

---

### Post by hikaricore on 2009-10-19
So wait you minimized a fullscreen game and put your computer in suspend mode?
That's a recipie for disaster right there.

---

### Post by Maramros on 2009-10-19
No, I didn't do it, the computer minimized the game and put itself to sleep.:(

---

### Post by hikaricore on 2009-10-19
Then you need to disable power saving options (such as sleep mode) as well.

---

### Post by Maramros on 2009-10-19
playing a fullscreen game counts as being inactive? Strange. I'll see if that works, though. Thanks.

---

### Post by hikaricore on 2009-10-19
For some reason gnome isn't detecting input while the game is running.
This can be caused by a number of things, but I am certain it is the problem.

---

### Post by Maramros on 2009-10-19
Strange. Anyway, thanks!

---

### Post by hikaricore on 2009-10-20
Ignore the post by Chiku1, they're a spammer.
The post should be removed shortly.

---

### Post by jrrader on 2009-10-31
Found this while looking for a problem I'm having with sauerbraten but didn't see this suggested so decided to add it.  

Why play games in gnome?  There are so many things that can go wrong, screen saver, messenger, notifier... anything that pops up can force you out of full screen in a bad way.  To get out of it you can switch to a tty (ctrl alt f1 to f6), type the command "ps -U [username]" and then kill games process.

Better solution - don't play games in gnome.  If you are going to play a game, choose xterm or awesome wm under session at login.  With awesome (have to install first: "sudo apt-get install awesome")you can still run GUIs but it barely uses up any of your system resources  - and no game ending popups.

---

