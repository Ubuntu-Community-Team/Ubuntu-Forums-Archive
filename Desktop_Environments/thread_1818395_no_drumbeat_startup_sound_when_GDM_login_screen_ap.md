---
title: "no drumbeat startup sound when GDM login screen appears in Ubuntu 10.10"
date: 2011-08-04
forum: Desktop Environments
---

### Post by Beef Eater on 2011-08-04
My new Ubuntu 10.10 installation does not play the drum beat sound just before the login screen appears. After login, the Gnome login sound plays just fine and all sound events appear to play just fine.

Why the drum beat sound does not play is a mystery to me! I find the sound quite helpful, especially when I work with a few computer system and reboot them from time to time, as it prompts me to go back to the system that has completed the reboot cycle. I would really like to get the sound back! Extensive search at ubuntuforums.org and googling the Net provided me with a few clues as to what may be causing the problem, but none of them has worked to solve the issue. Specifically,

1. In gconf-editor,
/apps/gdm/simple-greeter/settings-manager-plugins/sound
"active" key is set to true (ticked); "priority" is set to 3 (default value).

2. In gconf-editor,
/desktop/gnome/sound
"enable_esd" key is set to true; "event_sounds" is set to true; "theme_name" is set to "ubuntu".

3. In Sound Preferences, sound effects volume is set to about 80% and is NOT muted. The output volume is about 70% and is NOT muted. Again, the sound events work fine as soon as I am logged in.

4. system-ready.ogg in /usr/share/sounds/ubuntu/stereo links to dialog-question.ogg in the same directory. I can play system-ready.ogg and hear the usual Ubuntu drum beat sound without any problem!

5. Running
/usr/bin/canberra-gtk-play --id="system-ready"
from command line produces the startup drum beat sound just fine.

6. I have found nothing suspicious in /var/log that would indicate some kind of sound problem.

7. There has been no additional customization of my Ubuntu 10.10 installation. It is still pretty much a plain vanilla installation.

When I log out and GDM restarts to show the login screen, I should hear the drum beat "system-ready" sound, but I hear nothing. My Ubuntu is silent.

At this point, I have no other ideas as to what may be causing the problem. Any ideas will be much appreciated!

---

### Post by Beef Eater on 2011-08-17
Bump.

Does anyone here know if there are additional logging capabilities in the sound module that would capture what libraries are loaded, what programs are run, etc during GDM initialization?

---

### Post by tedrogers on 2011-11-03
Not much help to you, but I have this exact problem but with 11.10 instead. In all over versions it has been stable and working.

---

### Post by Beef Eater on 2011-11-03
> **tedrogers said:**
> Not much help to you, but I have this exact problem but with 11.10 instead. In all over versions it has been stable and working.

Oddly, and certainly not of help to you, but the fact that you are experiencing the exact same problem is good in the sense that it increases the likelihood that someone in charge takes note of this problem and does something.

Personally, I would be happy if someone pointed me to some tracing or logging facility that would allow me to investigate what is going on. I am beginning to believe that GDE may be attempting to sound the drumbeat before all necessary GDE initializations are complete. But it's just a guess...

---

### Post by tedrogers on 2011-11-04
There are usually boot logs, but they might as well be in Swahili as far as I'm concerned.

I do not know where these would be located though.

I've heard of a graphical boot logger as well, which generates an image of boot processes. Again I don't know what this utility is called, but a little research may reveal it to you.

---

### Post by tedrogers on 2011-11-04
Maybe Plymouth will help:

 [https://launchpad.net/ubuntu/+source/plymouth](https://launchpad.net/ubuntu/+source/plymouth)

---

### Post by tedrogers on 2011-11-04
Found it, it's called bootchart:

[http://m.lifehacker.com/278002/graphically-analyze-your-boot-sequence](http://m.lifehacker.com/278002/graphically-analyze-your-boot-sequence)

---

### Post by tedrogers on 2011-11-04
I just ran bootchart, and I don't know if this is significant, but the pulseaudio process doesn't appear to be initialised before the login prompt (which appears as a blank point in time with no activity before login is successful).

See my bootchart attached - what do you make of it?

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/t500-oneiric-20111104-1.png[/IMG]

Bottchart howto is here:

[http://ubuntuforums.org/showthread.php?t=868189](http://ubuntuforums.org/showthread.php?t=868189)

---

### Post by tedrogers on 2011-11-04
Another thing I've noticed is that running 11.10 on an Intel Mac has the same problem.

Usually I run it on my Lenovo T500, but at work I run it on an Intel Mac...no conga drum bonks here either! :(

---

### Post by Beef Eater on 2011-11-04
Thank you tedrogers for the hint! I installed 'bootchart' and ran a few experiments with it today. The log files it writes are not much helpful as it seems impossible to figure out their internal format without spending undue time on deciphering their fields or looking at the source code. There is no description of the file formats at Sourceforce or at the project's website, [www.bootchart.org]("http://www.bootchart.org/"). The graphical visualization tool is not of much help either.

However, I did notice that in my particular bootchart log, 'canberra-gtk-play' runs earlier than pulseaudio. The screen capture of the graph is attached. This seems suspicious. Why would the sound player run before pulseaudio? Unfortunately, I lack the knowledge of GDE initialization process and at this point, I am stuck with what I have. My only hope is that someone who does have such knowledge sees this thread and gives advice.


[IMG]http://vkulkov.dyndns.org/files/2011-11-04_172351.png[/IMG]

---

### Post by tedrogers on 2011-11-05
Yes, this does seem suspicious...but having looked about it would seem that 'canberra-gtk-pl' is responsible for login/out sounds, but maybe not system ready sound.

The search continues...

---

### Post by Beef Eater on 2011-11-05
'canberra-gtk-play' is used both for playing login/out sounds and the system ready sound:

/usr/bin/canberra-gtk-play --id="system-ready"

However, bootchart truncates the command line and it's impossible to see the command line arguments. For this reason, it is not possible to tell precisely what is played, but it appears to me that it has to be the system-ready sound. I cannot think of any other candidate. The login sound appears later - if you look at the right edge of the graph, you can see a number of processes usually associated with the login event.

So I think it is the system-ready sound that is played before pulseaudio process is started.

---

### Post by tedrogers on 2011-11-05
Okay that makes sense to me now. Good reasoning!

---

### Post by mahoutsukai on 2011-12-01
Still nothing with this problem? Because I have it also and couldn't find anything.

---

### Post by Beef Eater on 2011-12-01
Nothing! ;-(

---

### Post by tedrogers on 2011-12-02
No nothing from me either. Seems there are a few of us though so that at least confirms the problem is a real one.

---

### Post by Beef Eater on 2011-12-03
Okay, now I can confirm that the problem is likely pervasive to the newer Ubuntu releases. My new Acer laptop with Ubuntu 11.10 Oneiric Ocelot does not produce the drumbeat sound upon GDM initialization - it's exactly the same problem as on my desktop unit.

---

### Post by dcstar on 2012-01-27
> **Beef Eater said:**
> My new Ubuntu 10.10 installation does not play the drum beat sound just before the login screen appears. After login, the Gnome login sound plays just fine and all sound events appear to play just fine.
..........
At this point, I have no other ideas as to what may be causing the problem. Any ideas will be much appreciated!

I had this exact same issue on my system until I discovered that I had my speakers plugged into the wrong audio port on the back of my PC (the "Subwoofer" output, I must have mistakenly plugged it in there when moving some cables).

When plugged into the correct default "Line Out" port (the Green connector) the drum sounds then played when the login screen came up (and all other sounds played ok too, as they had on the other port).

It seems that the mechanism that plays the "Drum" sound before user login defaults to a fixed motherboard audio port before the proper sound system is started as part of the login process.

---

### Post by Beef Eater on 2012-01-31
> **dcstar said:**
> When plugged into the correct default "Line Out" port (the Green connector) the drum sounds then played when the login screen came up (and all other sounds played ok too, as they had on the other port).

I wish I could solve the problem by using a different audio out port! I only have one audio port - it is the general "Line Out" port.

Also notably, my Ubuntu 11.10 notebook computer has the exact same problem with the drum sound. The drum sound does not play regardless of whether the built-in speakers are used or external speakers are connected to "Line Out". It looks to me that something is wrong with the sound system initialization since v10.10.

---

### Post by LinuxFan999 on 2012-01-31
> **Beef Eater said:**
> I wish I could solve the problem by using a different audio out port! I only have one audio port - it is the general "Line Out" port.

Also notably, my Ubuntu 11.10 notebook computer has the exact same problem with the drum sound. The drum sound does not play regardless of whether the built-in speakers are used or external speakers are connected to "Line Out". It looks to me that something is wrong with the sound system initialization since v10.10.
My computer doesn't play that sound at the login screen either. I think the Ubuntu developers may have removed the ability to play the login sound entirely when they worked on 11.10.

---

### Post by Beef Eater on 2012-05-08
An update:

The drumbeat startup sound is back in 12.04 Precise Pangolin, working right out of the box!

Oddly, the login sound is no longer enabled by default. To enable the login sound, the following command has to be added to the Startup Applications:

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

---

### Post by tedrogers on 2012-05-09
Yeah bongo is back ;)

---

### Post by sunilendril on 2012-05-24
I installed Ubuntu 12.04 but the drum-beat during the login is still not there. I noticed that the Volume applet on the top remains on mute when I boot. The drum-beat does appear if I just log out from a session. I fixed the Ubuntu login sound by the above method but havent found solution to the drum-beat as of yet.

---

### Post by cavejug on 2012-05-27
Hi there friends,
 exchange between few of you on this tread  was very useful in resolving my predicament. I wanted to get rid of this, for my liking, very annoying sound at the boot up. And the only way to get rid of it at the start-up (boot-up) was to shutdown WITH THE SOUND MUTED.  If I happen to shutdown with sound enabled it is there at next start-up. But since I dislike it so much, I make my choice before shutdown. Hope this make sense and can be helpful to those of you who want the opposite effect. Cheers:-\"

---

