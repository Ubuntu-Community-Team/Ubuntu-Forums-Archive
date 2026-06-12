---
title: "Need help with getting an .mp3 file to play in Rhythmbox when Ubuntu boots up"
date: 2009-04-09
forum: General Help
---

### Post by kristv on 2009-04-09
Hello,

New user here....to both Ubuntu and Linux.  I need assistance with something I'm trying to set up, but am struggling to resolve.  Here's the scenario:

I've installed Ubuntu on a spare PC at my desk and am trying to figure out everything and make sure all of our needs are going to be met with this OS.  So far, so good.  I've figured out how to get the PC on our network, online and how to file share so that we can push files to the PC remotely.  

The company I work for uses PC's to play our music-on-hold recordings (in mp3 format) for when customers call in and are waiting on hold for a call center rep. to answer.  We currently use Windows XP but are looking to migrate to Ubuntu on these PC's for better stability and easier admin.

I've done some researching online and have figured out how to add programs to the boot sequence in the Sessions Preferences, but I think I'm doing something wrong.  I thought that if I added the mp3 file to the startup list, it would just fire up in Rhythmbox once Ubuntu finished booting but this doesn't happen.  Do I need to do something different here to acheive this?  I'm trying to keep it simple, so I don't want to get too crazy with editing boot files, etc.  

Basically, this is needed in the event that if one of our locations (we have 60+) was to lose power, when the PC powers up again it would just start playing the mp3 automatically once it booted up.  We don't attach monitors/keyboards/mice to these PC's, as there isn't really a need since we admin them remotely, so having someone on the site start up the mp3 file again manually isn't really an option.

Thanks in advance for pointing me in the right direction!  :)

---

### Post by wylfing on 2009-04-09
You can control Rhythmbox from the command line with the rhythmbox-client program. So quite likely what you need is a tiny bash script.
[LIST=1]
[*]Choose Applications > Accessories > Terminal.
[*]Type ```
gedit startsound.sh
```
[*]Paste this into the editor:```

#!/bin/sh

rhythmbox-client --play-uri="mysound.mp3"
```
Substitute the filename of your mp3 file where it says mysound.mp3. You'll have to specify the entire path, for example /home/pheebor/mysound.mp3.
[*]Save the file, and quit the editor.
[*]Type ```
chmod +x startsound.sh
```
[*]Add startsound.sh to your session startup programs.
[/LIST]

---

### Post by PreviousN on 2009-04-09
I'm a little confused as to what you're doing here. 

> The company I work for uses PC's to play our music-on-hold recordings (in mp3 format) for **when customers call in and are waiting on hold** (emphasis mine) for a call center rep. to answer. We currently use Windows XP but are looking to migrate to Ubuntu on these PC's for better stability and easier admin.

Sounds like you have a really specialized situation. What program did you use on windows? There *may* not be a program like that for ubuntu. From what I understand, you're using a specialized program to START a music file playing when someone calls in. I don't know of much about asterisk but that may be where you want to start looking. [http://www.asterisk.org/](http://www.asterisk.org/)

Since I don't have experience with your setup, but I'm intrigued, I'm gona take a wait and see approach. If no one with more experience with that type of setup comes forward I'll see what I can do for you. Its possible (and easy) to get a computer to run an mp3 on boot (as evidenced by the above post). But that would be the same song repeated over and over. Why not try internet radio instead? (though this is further down the line, after seeing if ubuntu can do what you need). 

Anyways, despite the fact that I'm not able to answer your question, I'm sure someone will, and Welcome to the ubuntu community! :-).

---

### Post by kristv on 2009-04-09
Hey, thanks a ton, guys!

Wylfing: that seems to have (mostly) worked.  Rhythmbox now loads when I reboot the PC or pull the power and plug it back in.  Unfortunately, the mp3 file doesn't start playing automatically though.  I have to start playback manually still, which is what we are trying to avoid.  Is it possibly a bug with Rhythmbox?  Should I maybe use some other music playback program?

PreviousN: We aren't using anything special really with Windows XP.  In Windows, you add the mp3 file's shortcut to the "Startup" folder, and the OS knows to play the file with the default player upon bootup.  It's a very simple procedure and I was hoping Ubuntu had something similar in place.

What Wylfing suggested does work to a certain extent, but I need the file to actually play once the player has loaded.  Rhythmbox appears to be keeping the "repeat" setting intact, but it's just not firing up the mp3 once it has loaded during bootup.  I did use the right path for the file and named it correctly, so I'm a bit baffled as to why it's not playing?

---

### Post by kristv on 2009-04-09
AHA!  I figured out what was wrong....I put a space between  --play-uri= and the mp3 file name.  Doh!  Once I removed the space and rebooted....music file is now playing upon boot up!

Thanks again, guys.  I'm one more step closer to getting this PC set up the way we want it.  Now I just have to figure out if the Nortel reporting software will work on it or not....  :D

---

### Post by sekinto on 2009-04-09
I recommend downloading VLC using the Synaptic Package Manager. It can play many types of video/audio file and is really lightweight (it also has an easy command line interface).

After installing just put this in your startup:
vlc --repeat <file>
where <file> is the full path to your file.

If you don't want to see a gui interface and just want the music to play in the background you can use:
cvlc --repeat <file>
but then to stop the music you would have to run:
killall vlc
since you won't have an interface (meaning to close button!).

Edit:
VLC can also handle streams and playlists if you want to play multiple files in a loop or randomly.

---

### Post by kristv on 2009-04-09
> **sekinto said:**
> I recommend downloading VLC using the Synaptic Package Manager. It can play many types of video/audio file and is really lightweight (it also has an easy command line interface).

After installing just put this in your startup:
vlc --repeat <file>
where <file> is the full path to your file.

If you don't want to see a gui interface and just want the music to play in the background you can use:
cvlc --repeat <file>
but then to stop the music you would have to run:
killall vlc
since you won't have an interface (meaning to close button!).

Edit:
VLC can also handle streams and playlists if you want to play multiple files in a loop or randomly.


Thanks for the recommendations!  I would probably want to see the gui because there would be no question for the person accessing the PC remotely as to whether the file was playing or not.  Also, it allows quicker control of the program if we need it.  The fact that it's lightweight might be handy in our situation, since the Nortel reporting software definitely isn't!

---

