---
title: "Sound doesn't work in flash"
date: 2006-07-21
forum: Desktop Environments
---

### Post by GuitarHero on 2006-07-21
Whenever I play videos on video google or You Tube, or whatever, I don't hear any sound with the video.  I also don't have sound in gaim but I'm not sure if that's a related issue or not.  I hear sound in Listen and the startup/shutdown sounds.  I don't hear the little bongo thing on the login prompt screen when you first boot up.  I don't know whats going on.  I used Automatix to install codecs, so now I tried Easy Ubuntu but it said I had to fix broken packages before it could apply changes.  I am using an external USB recording device as my sound device.  As I said, it works for music, and login/logout music.

What's going on?

---

### Post by someguyouknow on 2006-07-21
i have the same issue.....
its seem that you cant listen to music and then have sound on the internet.
usually if i pause Amarok and then restart Firefox the sound works but thats a big hassle....

---

### Post by patrickfromspain on 2006-07-21
Ok, you can try this:

close any aps does uses sound
close firefox
open a terminal and type: killall esd
restart firefox and see if youtube works fine.

If it does, gon unter System -> Preferences -> Sound and uncheck Sound server (ESD)

---

### Post by GuitarHero on 2006-07-21
Ok I'll try it but ive tried it from the start and it still has the same problem, with no sound apps open.  Plus as I said the sound doesnt play for the login.

---

### Post by GuitarHero on 2006-08-08
Well I still dont have this working, I also dont have sound in Wolfenstein.

---

### Post by mankyuhan on 2006-08-08
I am experiencing same problem on my linux machine.  Any solutioN?
Rebooting doesn't help.

---

### Post by Bragador on 2006-08-08
oh well look at that ! I have the same problem.

I installed the flash package for dapper and I have no sound for flash movies or applications.

Cant wait for open flash to be released. Meanwhile If someone knows how to make flash work go for it.

I tested it on this page : [http://www.di.fm/edmguide/edmguide.html](http://www.di.fm/edmguide/edmguide.html)

---

### Post by someguyouknow on 2006-08-08
i use to have the same problem.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

for some, aoss may not work (like for me) so i put auto instead.....
i can watch google video and youtube with no problems now.....
hope this helps someone....
Edit/Delete Message

---

### Post by GuitarHero on 2006-08-09
That didnt do anything.

---

### Post by margni on 2006-08-09
[QUOTE=someguyouknow;1356259]i use to have the same problem.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

Your edit worked for me...  My firefoxrc file looked like:

#ORIGINAL LINE:
#FIREFOX_DSP="none"

I commented out the old line - in case of freak out ;) 
and set up a new line:

#NEW LINE: 8/9/06
FIREFOX_DSP="aoss"

Then I closed and restarted firefox.

Thanks!  Do you know how much longer it will be until there is a newer version of Flash?

Margni

---

### Post by Bragador on 2006-08-09
Flash 9 for linux = early 2007
[http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm](http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm)

---

### Post by GuitarHero on 2006-08-09
It seems sound in firefox does work now, but still no luck in Wolfenstein.  Weird I switched back and forth between sound devices and now it works in wolfenstein, hmm not a complaint here!

---

### Post by margni on 2006-08-10
I found after I had changed the line in the firefoxrc file, I needed to restart FF.

This fixed my problem, is yours resolved?

---

### Post by margni on 2006-08-10
> **Bragador said:**
> Flash 9 for linux = early 2007
[http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm](http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm)

Thanks for the update...!

---

### Post by hard_one on 2006-08-10
I too have the same problem, especially for my daugthers complaining not being able to play on disney channel games.  

I installed the latest version of mozilla and its plugins.  Now I can access youtube and video.google with sound.  But disney channel games still not working.  :-( 

I'll be configuring firefox as mentioned above and comment later if it works for me....a ubuntu noob.

Test sites for me:
[http://www.youtube.com](http://www.youtube.com)
[http://www.disney.go.com/disneychannel](http://www.disney.go.com/disneychannel)
[http://video.google.com](http://video.google.com)

Its comforting to know others are experiencing the same issue.  I thought it was only me ;)

---

### Post by hard_one on 2006-08-10
:p

---

### Post by GuitarHero on 2006-08-11
Well just as randomly as it started working it has stopped again.  Time to go buy a soundcard, hopefully it will work.

---

### Post by swinterry on 2008-05-17
> **someguyouknow said:**
> i use to have the same problem.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

for some, aoss may not work (like for me) so i put auto instead.....
i can watch google video and youtube with no problems now.....
hope this helps someone....
Edit/Delete Message

I tried ```
sudo apt-get install alsa-oss
``` and i got the out put ```
[fedora@localhost ~]$ sudo apt-get install alsa-oss
fedora is not in the sudoers file.  This incident will be reported.
```

---

### Post by lswest on 2008-05-17
in Fedora you have to add yourself to the sudoers file via ```
visudo
``` or add your user to the group "wheel" which is in the sudoers file.  It's a pain to do it every time you install Fedora, and that along with the opening of a new folder in a new window from the filebrowser was reason enough for me to never use Fedora again after installing FC8 a while back.

---

### Post by swinterry on 2008-05-17
Hmm i dont get what i need to type in

---

### Post by swinterry on 2008-05-17
ok i fixed it with  ```
yum -y install libflashsupport
``` thanks

---

### Post by mister_p_1998 on 2008-05-20
> **GuitarHero said:**
> Whenever I play videos on video google or You Tube, or whatever, I don't hear any sound with the video.  I also don't have sound in gaim but I'm not sure if that's a related issue or not.  I hear sound in Listen and the startup/shutdown sounds.  I don't hear the little bongo thing on the login prompt screen when you first boot up.  I don't know whats going on.  I used Automatix to install codecs, so now I tried Easy Ubuntu but it said I had to fix broken packages before it could apply changes.  I am using an external USB recording device as my sound device.  As I said, it works for music, and login/logout music.

What's going on?

Go into preferences and disable system sounds, that often cures it. Pre Hardy Ubuntu's dont multitask sound output well. Hardy does it great.

---

