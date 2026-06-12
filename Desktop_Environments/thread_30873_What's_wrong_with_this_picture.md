---
title: "What's wrong with this picture?"
date: 2005-04-30
forum: Desktop Environments
---

### Post by telmo on 2005-04-30
Ok, Nautilus, just took 20 secs to open up!!!
What's wrong with this picture?

I've seen some threads about Ubuntu being slower than windows. I've made one myself, but this is ridiculous!
Twenty seconds it's a long time! I've tried everything, (DMA; Prelink; HDparm,etc) This is NOT good for my mental health! :)

(HP Pavilion ZX5000; 768 Mb RAM; HD 80Gb 5400RPM; ATI M10 9600 64Mb w/3D accel.; P4 3.06 Ghz)

---

### Post by Professor X on 2005-04-30
That is odd.  Nautilus opens almost instantly on my Athlon XP 2500 with 512 MB RAM.  Start nautilus from the command line and see if you get any error messages.

---

### Post by vaskark on 2005-04-30
For me Nautilus is freezing a lot lately. Sigh.

---

### Post by Shadow Skill on 2005-05-01
[QUOTE=telmo]Ok, Nautilus, just took 20 secs to open up!!!
What's wrong with this picture?

I've seen some threads about Ubuntu being slower than windows. I've made one myself, but this is ridiculous!
Twenty seconds it's a long time! I've tried everything, (DMA; Prelink; HDparm,etc) This is NOT good for my mental health! :)

(HP Pavilion ZX5000; 768 Mb RAM; HD 80Gb 5400RPM; ATI M10 9600 64Mb w/3D accel.; P4 3.06 Ghz)[/QUOTE]
 Well judging from your specs it shouldn't be taking more than ten seconds [granting the lag from initial startup.] for nautilus to start coming up.  What version of Gnome are you running?

---

### Post by Tobias Pistohl on 2005-05-01
It's really no secret, that the nautilus file-browser isn't the fastest one around. But while startup time is OK if the directory to open doesn't contain too many files (it takes 2-3 seconds to start up and open my home directory on my old PIII-800 notebook), it's getting horribly slow, if you're opening a directory with hundreds or thousends of files in it. There it could really do better. Personally, I just try to avoid opening such bloated directories with nautilus.

Cheers

---

### Post by Nob on 2005-05-01
verry odd... :S
my nautilus is starting for 3 secs...

---

### Post by ritger on 2005-05-01
I've noticed nautilus slowing down on occasion as well. One thing to do is to check if any other processes make extensive use of the harddrive (add the system monitor applet to gnome-panel and define the colors so you can make out I/O wait operations when running it). Or, alternatively, run top in a terminal and look for the `wa' in the status view. If that is a high number some other process is eating disk performance.

Also, look how much memory nautilus is consuming, it can get rather heavy on mem usage. Whenever nautilus gets sluggish try to kill it with killall -9 nautilus. It'll come back on it's own. This usually works for me.

---

### Post by telmo on 2005-05-01
I'm using Hoary, with XFCE4. It's a little faster than Gnome and i don't like ROX, so i'm using Nautilus. But sometimes takes so long to open... :(

---

### Post by tread on 2005-05-01
I think there is an option about creating thumbnails .. maybe that's what is slowing down nautilus? Mine works fine though, but I dont have a situation where I have thousands of files in one folder. 

Try switching the thumbnail option off ..

---

### Post by ernestoongaro on 2005-05-01
Perhaps its your icon set....sometimes when I have a fancy icon set my computer goes slower...thats all I can think of..because nautilus opens up instantly on a PIII 500mhz for me. :neutral:

---

### Post by Nob on 2005-05-01
well...step by step... i'm barely using any file manager :)
terminal is all wee need - like good ol' days... ;)

---

### Post by telmo on 2005-05-01
[QUOTE=Nob]well...step by step... i'm barely using any file manager :)
terminal is all wee need - like good ol' days... ;)[/QUOTE]

Yes, i think i'll just use the terminal...  :roll:

---

### Post by Nob on 2005-05-01
[QUOTE=telmo]Yes, i think i'll just use the terminal...  :roll:[/QUOTE]
 why so ironic?
terminal rules... :D

---

### Post by nocturn on 2005-05-02
[QUOTE=Nob]why so ironic?
terminal rules... :D[/QUOTE]


While the terminal is a good option for many (including myself), many people feel more comfortable witht a GUI solution.

Apart from that discussion, Nautilus should not take so much time to start up on that machine, so the poster has a real problem.

---

### Post by nocturn on 2005-05-02
[QUOTE=telmo]Ok, Nautilus, just took 20 secs to open up!!!
What's wrong with this picture?

I've seen some threads about Ubuntu being slower than windows. I've made one myself, but this is ridiculous!
Twenty seconds it's a long time! I've tried everything, (DMA; Prelink; HDparm,etc) This is NOT good for my mental health! :)

(HP Pavilion ZX5000; 768 Mb RAM; HD 80Gb 5400RPM; ATI M10 9600 64Mb w/3D accel.; P4 3.06 Ghz)[/QUOTE]

Is it only Nautilus?  Do other apps (like FireFox, OO, ...) perform better?
Can you try it under a new userID?

---

### Post by bvc on 2005-05-02
[QUOTE=telmo]I'm using Hoary, with XFCE4. It's a little faster than Gnome and i don't like ROX, so i'm using Nautilus. But sometimes takes so long to open... :([/QUOTE]Maybe xfce4 isn't as fast as you think since you want to use gnome apps. I haven't ran it since its early days but consider that in gnome nautilus is mostly already loaded into memory so it doesn't take as long to 'start' initially. Not the case with xfce4, or at least it didn't used to be the case. That's the common misconception in using wm's or a small de in this case. Give a short time, if you use the same apps as you would in gnome, xfce4, fluxbox, whatever will end up using the same, or very very close, resources. Same apps, same libs, and linux loves ram. The alternative is to use only all stand alone apps that do not depend so much on gnome libs etc... like rox that you don't like.

BUT, that is still a long time IMO. It 'maybe' takes that long on my old box that's a 600Celeron 192MB 66fsb

---

### Post by Nob on 2005-05-02
oh yeah, check option in xfce to load gnome services on startup... ;)

---

### Post by Jet2k5 on 2005-05-02
I seem to have the same problem.  But it I think it's that initial lag.  Nautilis open in like 3 seconds for me, not even maybe 2.  But yet again my computer has been running for almost 3 months.  When ever I restart the computer, and I log on etc... and try to open firefox I get the same exact problem you do.  It takes up to like 20 seconds for firefox to open.  So I let the computer run for about 1 minute and then open up firefox ( and it's fast ) so that I don't get disappointed.

From a technical point of view I think they call that caching.  After the program is one cache ( which means it's ready to launch again * i think * ) then it's completely fine ( speed wise ) I've come to accept that fact.  Anyhow good look, but  I don't think it's going to be fixed :(

At least you have a good video card :) I'm stuck with an M6 :X

---

### Post by telmo on 2005-05-02
[QUOTE=Nob]oh yeah, check option in xfce to load gnome services on startup... ;)[/QUOTE]

I did! But, nevermind. Really! I just customized my transparent terminal and i'm loving it, so i'll just put it to good use. :)

And i can also run Rox from time to time, to see if i can adapt.

BTW, are there any services i can disable that run on boot, to make my system run a little faster? Maybe that's what is all about...

Thank you very much, all of you!

---

### Post by sgornick on 2006-11-05
With Edgy Eft on my HP Pavilion zx5000 (zx5078cl) I find that Nautilus is hanging ... at the exact point that it tries to play the login startup sound.  If I then go into the console (Alt-F1) and % killall esd, Nautilus will resume loading instaneously.  

This was occuring on Dapper as well.  As a workaround I disabled startup sound, and that let me get by as I was hoping it would go away in Edgy.  I did a clean install of Edgy and am getting the same thing -- gnome/nautilus hang on startup.

Here was my original post on it:
[http://www.ubuntuforums.org/showthread.php?t=248166&highlight=sound+power+startup](http://www.ubuntuforums.org/showthread.php?t=248166&highlight=sound+power+startup)

I believe it is similar to this bug reported:
[https://launchpad.net/bugs/40176](https://launchpad.net/bugs/40176)

---

### Post by Engnome on 2006-11-05
Maybe try thunar?

---

### Post by d3v1ant_0n3 on 2006-11-05
I have same processor and memory as the OP, and for me, starting nautilus by Menu>Places>home takes just under a second.
Using the starter bar Gdesklet thing, it takes just over 2.
Starting from terminal takes a similar time to starting from the menu.

---

