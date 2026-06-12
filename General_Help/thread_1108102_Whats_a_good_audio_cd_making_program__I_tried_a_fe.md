---
title: "Whats a good audio cd making program?  I tried a few, and they all failed."
date: 2009-03-27
forum: General Help
---

### Post by Mashuteichou on 2009-03-27
Just curious because I downloaded a few, some failed, some failed to see the cd drive, some failed to convert the music before it burned.   I have used windows since windows 3.1 all the way to windows 7, and I am still stuck in that mode: Load the music in a playlist, hit burn, the program does all the work.  Windows Media Player, Itunes, Ashampoo, Cheetah Burner, etc.  

Here is what I used in Linux: 
K3B
GnomeBaker CD/DVD writer
Brasero Disc Burning
Amarok

Here is what I used in WINE:
Ashampoo CD burning studio
Cheetah Burner


The Linux programs didn't convert the files and failed, then said to convert them manually.  Even though they are already MP3 or WMA files.  Or, they burned all the way then at the last second, it failed.  Which was the Gnome one.

The Windows programs didn't recognize the CD drive, or just shutdown when I hit the burn button.  

So, how do I make a simple audio CD, with a drag and drop to playlist/burn, like in Windows Media Player?  I burn both MP3 CD's, and simple Audio CD's.  But, a simple Audio CD is all I need currently.  (Burning a couple CD's for a CD player that doesn't support MP3)

---

### Post by Stenrad on 2009-03-27
Hi there!

I have always used Serpentine Audio Cd Creator without any problems. Very fast and simple to use. Never let me down yet. :-)

Hope that helps!

Stenrad.

---

### Post by logos34 on 2009-03-27
> **Mashuteichou said:**
> 
Here is what I used in Linux: 
K3B
GnomeBaker CD/DVD writer
Brasero Disc Burning
Amarok

Actually, Amarok is only a media player.  For burning option it calls k3b.

The problem in k3b at least seems to be you lack the mp3 (mad) decoder and ffmpeg lib plugin.  Elsewhere you appear to need the gstreamer-bad and -ugly pkgs, and w32codecs for .wma files.  Try installing the following and then attempt to burn audio cd in any of the apps:

> sudo apt-get install libxine1-ffmpeg libk3b2-extracodecs ubuntu-restricted-extras w32codecs

(for the last you'll need to enable the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos)

hope that helps

---

### Post by Chemical Imbalance on 2009-03-27
EDIT: (Ignore this post)

Sound-juicer works great for me.


sudo apt-get install sound-juicer


EDIT: (Ignore this post)

---

### Post by logos34 on 2009-03-27
> **Chemical Imbalance said:**
> Sound-juicer works great for me.

yes but that's a cd ripper, not burner app

---

### Post by Chemical Imbalance on 2009-03-27
> **logos34 said:**
> yes but that's a cd ripper, not burner app

Woops I didn't pay close attention.
:oops:

---

### Post by irregardlessly on 2009-03-27
I like GnomeBaker, but if you can't get any of those programs to burn then I would say there is something generally wrong with your setup and no app will work.

---

### Post by Chemical Imbalance on 2009-03-27
Sounds like either you have a hardware issue or Ubuntu isn't correctly identifying your drive.  Just a thought...
Do you have Windows installed?  If you do, try booting into it and burn something.  If it doesn't work there, you have a hardware problem.

---

### Post by Mashuteichou on 2009-03-27
Tried Serpentine, got to 100% then failed and said put the speed slower.  
But its on default.

--------------------------------------------------------------
You're right, I noticed when I hit burn CD in Amarok, it was K3b.  

Ill download the codecs as soon as I post this.

---------------------------------------------------------------
Not sure if I should try sound juicer or not.  >_>  Not sure if thats a real post or not.  

---------------------------------------------------------------
I understand now.  Sound Juicer isn't a burner app.   xD

---------------------------------------------------------------
I do have Windows XP Installed and I switch back and forth to use a couple things Linux doesn't support yet.  And to test things if they don't work right in Linux, like burning CD's.

Windows XP burns the CD's fine.  Kinda.  Windows Media Player never works, but Ashampoo Burner and Cheetah Burner work.  Might be because I have WMP all but killed in Zonealarm.  I don't trust it, so it doesn't work right.  

I have a Toshiba X205-sli1, which is a HD-DVD player/burner.  There are random updates and patches for the Vista that came with it.  I had to tweek XP to make it work.  Originally, I couldn't even find the hard drives to load XP on.  Afterwards, with beta drivers and stuff, XP works 10 times better then Vista.  But, Ubuntu works 10 times better then XP.  ^_^

I'm still learning it though.  Hence the noobish question.  

I am going to try the slowest speed on one of the burning programs.  I have x52 cds and the burner works that fast, but it says to slow the burn speed down when I tried Serpentine.  So thats where I am going to start after I get the codecs.

---

### Post by Mashuteichou on 2009-03-27
This didn't work correctly, I had to delete the w32codecs part to work.  Does this make a difference?  (It seems to be downloading things normally.)  

sudo apt-get install libxine1-ffmpeg libk3b2-extracodecs ubuntu-restricted-extras w32codecs

---

### Post by logos34 on 2009-03-27
from all that you've said it appears this may a be a codecs *and* hardware issue.  I won't even venture any suggestions on the hardware side since I have my own problems burning dvd+r in any app

w32codecs: as I pointed out you have to enable the Medibuntu repo *first* (link underlined)

---

### Post by Mashuteichou on 2009-03-28
After I downloaded the codecs, K3b works perfect.  Even at full write speed.  Thanks for the help.  ^_^

---

### Post by logos34 on 2009-03-28
ok, good to hear the codecs fixed k3b.  So now you can rule out the hardware.  As for the other burning apps, not sure, but it doesn't really matter since k3b is hands down the best/most fully featured burner. So use that frm now on.

For my part I wish I could rule out my drive as the issue, but it appears to be having trouble tracking on dvd+r -- makes data dvd+rw and -r just fine.  And I just bought a pkg of 50 dvd+r...Arg!!!

---

