---
title: "Missing panel"
date: 2010-02-21
forum: Desktop Environments
---

### Post by redcrystalmoon on 2010-02-21
I'm missing my top (and only) panel, I can't access anything on my computer now except firefox and movieplayer since they are what comes up when I restart, I guess that's because I opted to save my running applications during my last session. I also did some updates... I've read a couple other posts about the same thing but they were in xubuntu and none of the fixes are valid for me... 

I'm running ubuntu 9.10 just installed it last week, on my acer one netbook. everything was dandy until tonight when I rebooted and found that my panel is gone... Right click on the desktop shows no way to get it back, no route to applications or add panel. I didn't do anything to get rid of it it's just gone... Is this a known issue with the updates or kernel does anyone know?

---

### Post by MooPi on 2010-02-21
Check this thread for a solution, Look for howefields post
[http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel](http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel)

---

### Post by redcrystalmoon on 2010-02-22
Thanks,
It says to open a terminal though and I'm not sure how to do that without my panel... there's no option when I right click on the desktop... is there a way to open a terminal with the keyboard?

---

### Post by kemsiro on 2010-02-22
alt + f2
type in gnome-terminal

there you go

---

### Post by redcrystalmoon on 2010-02-22
thanks but I tried that and nothing happened...

---

### Post by gadolinio on 2010-02-22
Press ALT and the F2 key (while still holding ALT pressed).
In the window that appears, type: gnome-panel
Then press enter.

---

### Post by redcrystalmoon on 2010-02-22
Edit, just for anyone else who might have this issue, here's what worked for me:
 
 				 				[gadolinio]("http://ubuntuforums.org/member.php?u=910735") 				 				 			
    			
"ALT F2 should give you a little window where you can type an application's name to make it run. 
If that doesn't work and you have no panels, try this: double click your user's icon on the desktop. When the file browser opens, go to filesystem (list on the left), then from the folders you see on your right enter "usr", then "bin". You'll see a lot of files there. There's one called "gnome-panel"; double click it."


Just FYI, ALT F2 still did nothing for me.... but thanks for your help, it's much appreciated ;o)

---

### Post by gadolinio on 2010-02-22
> **redcrystalmoon said:**
> Edit, just for anyone else who might have this issue, here's what worked for me:
 
                                  [gadolinio]("http://ubuntuforums.org/member.php?u=910735")                                               
                
"ALT F2 should give you a little window where you can type an application's name to make it run. 
If that doesn't work and you have no panels, try this: double click your user's icon on the desktop. When the file browser opens, go to filesystem (list on the left), then from the folders you see on your right enter "usr", then "bin". You'll see a lot of files there. There's one called "gnome-panel"; double click it."


Just FYI, ALT F2 still did nothing for me.... but thanks for your help, it's much appreciated ;o)

HAHAHA!  I'm actually the one who wrote that answer, but the idea came to my mind after having posted in this thread :P
Sorry i didn't remember to suggest the same here...

---

### Post by gadolinio on 2010-02-22
Now that i'm aware of both threads needing the same, i repeat the same suggestion i added in the other thread:
"Just in case this happens again, you can create a link to that file and keep it in your user's folder. So next time you just double click your folder in the desktop, and then the link to gnome-panel."

---

### Post by redcrystalmoon on 2010-02-23
Lol yeah I knew it was you who posted in the other thread that's why I included your name :o) 
I thought it would be good to post it here too in case others needed it. Also I'll repeat the post from [koleoptero]("http://ubuntuforums.org/member.php?u=381026") 
"The alt+f2 run dialog in gnome is handled by the gnome-panel so when it's not running the run dialog doesn't appear."

Thanks all for the help and the info ;o)

---

### Post by bgflounder on 2010-04-04
I opened usr, then bin, and looked for gnome-panel, but nothing. I installed 9.10 about 2 weeks ago and know little to nothing about the OS, but i didn't think i needed to install anything else. I realized i couldn't find gnome-panel after i tried rightclick, open terminal, gnome-panel and the Alt-F2 method. can anyone help me out with this? frustrated...

---

### Post by YnotStrebor on 2010-05-01
I'm having the same problem since upgrading from 9.10 to 10.04, the gnome-panel is running but nothing is displayed in the spaces where the panels should be.

Howefield's suggestion of:

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

works, until a reboot. Everytime I boot I have to restore the panels. Alt+F2 works, and in case newcomers are wondering, you can also type firefox into the Run Application box that pops up in order to start firefox.

---

