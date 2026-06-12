---
title: "Still having minecraft problems"
date: 2012-04-30
forum: Gaming &amp; Leisure
---

### Post by plexx92 on 2012-04-30
I downloaded minecraft but there was problems with the graphics. The graphics were buggy and transparentish. So I deleted minecraft from my comp. Then I tried allocates minecraft forum post. It worked up until I ran his text file in the terminal. I didn't get a response from my computer. Any suggestions?

Attached is a screenshot of the graphics.

---

### Post by regor210 on 2012-04-30
[B]Updated
[/B]
To install Mincraft goto
[http://dl.dropbox.com/u/54213557/MIFU/mifu.sh](http://dl.dropbox.com/u/54213557/MIFU/mifu.sh)

 download mifu.sh

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.

$ cd ~/Downloads/ && chmod -x mifu.sh

$ cd ~/Downloads/ && bash mifu.sh

press 1 to install minecraft.

After the installation there will be a launcher in your games menu.

Note. if you are using **Ubuntu** **12.04** you have to update LWJGL by hand or you will get a black screen when loading the game.

post 16#  here

[http://ubuntuforums.org/showthread.php?t=1812767&page=2](http://ubuntuforums.org/showthread.php?t=1812767&page=2)

---

### Post by plexx92 on 2012-05-01
That link is broken to mifu.sh

---

### Post by regor210 on 2012-05-01
Sorry, fix it, try again.


Your &#65279;transparentish issue my be from Ubuntu 3d desktop effects. You could try logging out and selecting the Ubuntu 2D desktop then log back in.

---

### Post by plexx92 on 2012-05-01
Error on line 90: syntax error 
Something about token and 'done"

---

### Post by regor210 on 2012-05-01
Hum I just used that bash script 4 hours ago. 
**Update** LOL, He edited it in the last 4 hours, its now installer v0.2a

Try installing minecraft by hand.

Download minecraft.jar from here.
[http://www.minecraft.net/download](http://www.minecraft.net/download)

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

If your using Ubuntu 12.04 go here

Post #16

[http://ubuntuforums.org/showthread.php?t=1812767&page=2](http://ubuntuforums.org/showthread.php?t=1812767&page=2)

---

### Post by emma157 on 2012-05-01
there should be a problem with your graphic card.

---

