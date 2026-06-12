---
title: "quake 3 no sound in breezy"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by defl on 2005-10-16
Hi!
I got some major problems with quake 3 in breezy. Simply running "quake3" results in a starting game without sound and in  the starting msg:
...
------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
....

Starting quake 3 with "artsdsp -m quake3" results in a non starting quake and the following console output:

...
------- sound initialization -------
Received signal 11, exiting...

anyone got an idea how to run quake3 with sound? :)

ps: i'm using asus p4p800e-deluxe's onboard sound with an ac97 2.3 compatible alc850 codec.

---

### Post by seethru on 2005-10-20
you could try installing alsa-oss, and then running quake3 with aoss quake3. Arts generally isn't used for anything besides system sounds.
Aside from that, it doesn't look like quake3 was able to access /dev/dsp so it may be a permissions issue.

---

### Post by sinbad782 on 2005-11-22
I'm having exactly the same issue here. The output that Quake3 gives is as aboe:

------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------   

Has anyone else had this problem, and what are the correct permissions for /dev/dsp ?

---

### Post by sinbad782 on 2005-11-22
Have tried the aoss quake3 trick and I already have the alsa-oss package installed. The former gives some crackling noises from the sound card but no real sound. Have tried setting the default sound system to ALSA under System Settings -> Sound & Multimedia -> Hardware but that doesn't do anything either.

---

### Post by sinbad782 on 2005-11-23
I'm having the same issue with Enemy Territory which is also an ID game. I downloaded this morning and am getting the error:

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------


I have set the permissions on /dev/dsp to 666, but this hasn't changed anything as far as I can see. Anyone else have any idea how to fix it?

---

### Post by sinbad782 on 2005-11-24
Note to others: have managed to fix this. I took two steps:


1.) Use dedicated Quake 3 binaries for Ubuntu:

For Quake 3, use the binaries provided at: [http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/)    - just extract the files into the matching folders, usually located under /usr/local/games/quake3


2.) Fix sound by adding settings to startup scripts:

To fix the sound problems, add the following three lines to your /etc/init.d/bootmisc.sh file:

#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------



Finally, reboot and you're done. Don't forget to adjust the shortcuts in your menus to point to the new Quake 3 binary (usually at /usr/local/games/quake3/linuxquake3 )

---

### Post by pmjdebruijn on 2005-12-04
Hi,

You could also try my icculus.org binaries which are compiled natively for Breezy:

[http://www.xs4all.nl/~bruijn9/quake3/breezy/](http://www.xs4all.nl/~bruijn9/quake3/breezy/)

Regards,
Pascal de Bruijn

---

### Post by noigeaR on 2005-12-05
I've had troubles getting sound to work with the Quake 4 demo and Enemy Territory.
An easy solution that works for me is to open a terminal (Konsole) and use the command ```
killall artsd
``` before starting Quake.

---

### Post by veehell on 2005-12-06
Hi i had several / general problems with my SBAWE64.
* isapnptools
* alsa
help me to fix to xmms, totem, xine have sound 

But Quake3Arena had still no sound :(, So i search the web and found this
**/usr/local/games/quake3/quake3 +set_initsound 1**
Which force to quake run on 1st Alsa defined card and force inicialization.
I don't why but this only command makes my Quake run with sound.
So maybe it help you too.
Q3A pointrelease 1.32beta , installed from official package, own data from purchased original game + some modes, so cpma, corkscrew and some other modes run aswell. Matrox card with DRI accelaration. Quite ok.;)

---

### Post by braynyac on 2005-12-07
veehell,

That worked flawlessly!  Instant sound, thank you very much!  =)

~braynyac

---

### Post by jmooney on 2005-12-17
I'm running Ubuntu, but maybe this will apply.  I have the regular version of quake III and it works just fine when I go into Gnome.  However, I recently installed Xubuntu-desktop to evaluate it as an interface for my kids.  Hearing that it used less resources than Gnome, I tried launching Quake III from XFCE to see if there were any noticable performance improvements (just for the record, I also tested OpenOffice 2.0 and Adobe Acrobat reader).  Anyway, no sound in Quake III.  Went back to Gnome and still no sound in Quake III.  Rebooted computer, logged into Gnome - and quake III works, sound and all.  Went back to the login screen and started an XFCE session and, once again, no sound in quake III.  Logged out of XFCE then logged back into Gnome and again, no sound in quake III.

Reboot, log into Gnome, sound is back in Quake III.

As long as I only log into Gnome, sound works in quake III....or so it would seem.

any thoughts?

---

### Post by jmooney on 2005-12-18
[QUOTE=jmooney]I'm running Ubuntu, but maybe this will apply.  I have the regular version of quake III and it works just fine when I go into Gnome.  However, I recently installed Xubuntu-desktop to evaluate it as an interface for my kids.  Hearing that it used less resources than Gnome, I tried launching Quake III from XFCE to see if there were any noticable performance improvements (just for the record, I also tested OpenOffice 2.0 and Adobe Acrobat reader).  Anyway, no sound in Quake III.  Went back to Gnome and still no sound in Quake III.  Rebooted computer, logged into Gnome - and quake III works, sound and all.  Went back to the login screen and started an XFCE session and, once again, no sound in quake III.  Logged out of XFCE then logged back into Gnome and again, no sound in quake III.

Reboot, log into Gnome, sound is back in Quake III.

As long as I only log into Gnome, sound works in quake III....or so it would seem.

any thoughts?[/QUOTE]


Ok, did some more troubleshooting.  Tried loading XFCE with GNOME services but it had no effect.  Also, I was getting a "/dev/dsp resource busy" message so I tried this:

sudo killall esd

Then ran quake3 and it worked with sound.

Need a better solution though.

Joe

---

### Post by f1d094 on 2005-12-19
Pascal...have you made any patches for the x86_64 version to work with punkbuster?

Right now, I can either have sound (compiled x86_64) or play on pb enabled servers 32 bit chroot)...but not both.

Or if you could point me in the right direction on how to patch the source myself.


Thanks!

---

### Post by veehell on 2005-12-20
a this does not help ?
[post#9 from this thread ]("http://www.ubuntuforums.org/showpost.php?p=549739&postcount=9")

Gnome usually use ESD to serve sound to Gnome and to programs. I dont know much about Xfce, but you have to check if using ESD too or if it use any other sound server or if it direct to /dev/dsp. Killing ESD is way ;) of workaround :) 
Also group.google.com has fine forums threads too, many times it save my "ass" because the solution been there posted as only place (or i just search badly)
Good Luck with sound.

---

### Post by jmooney on 2005-12-20
[QUOTE=veehell]a this does not help ?
[post#9 from this thread ]("http://www.ubuntuforums.org/showpost.php?p=549739&postcount=9")

Gnome usually use ESD to serve sound to Gnome and to programs. I dont know much about Xfce, but you have to check if using ESD too or if it use any other sound server or if it direct to /dev/dsp. Killing ESD is way ;) of workaround :) 
Also group.google.com has fine forums threads too, many times it save my "ass" because the solution been there posted as only place (or i just search badly)
Good Luck with sound.[/QUOTE]

no, quake +set_initsound.....didn't do it.  Only "sudo killall esd" so far

---

### Post by mhs on 2006-01-04
how do u enable pb w/ pmjdebruijns files
 i tried([http://www.xs4all.nl/~bruijn9/quake3/breezy/quake3-1.33-r438-i686.tar.gz](http://www.xs4all.nl/~bruijn9/quake3/breezy/quake3-1.33-r438-i686.tar.gz)) and it worked but it didnt load the pb :|  :. i cant play online

---

### Post by jpepin on 2006-01-14
[QUOTE=sinbad782]Note to others: have managed to fix this. I took two steps:


1.) Use dedicated Quake 3 binaries for Ubuntu:

For Quake 3, use the binaries provided at: [http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/)    - just extract the files into the matching folders, usually located under /usr/local/games/quake3


2.) Fix sound by adding settings to startup scripts:

To fix the sound problems, add the following three lines to your /etc/init.d/bootmisc.sh file:

#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------



Finally, reboot and you're done. Don't forget to adjust the shortcuts in your menus to point to the new Quake 3 binary (usually at /usr/local/games/quake3/linuxquake3 )[/QUOTE]


This worked great for me but now I have a different annoyance.  If I run the game by typing quake3 in the terminal it works fine with perfect sound.  If I run it via a menu shortcut, no sound!  I've checked and rechecked the links to make sure they pointed to the new binaries. Any clues??

---

### Post by Orunitia on 2006-01-15
I don't know if this will help, but all I had to do to get sound in quake 3 was run it as root.

---

### Post by bulken on 2006-01-17
i used the binaries  [http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/) , and now my sounds works, however i cant use the q3 console anymore, and there&#347; somethung wrong whith the shaft sound

---

### Post by matva on 2006-01-22
[QUOTE=mhs]how do u enable pb w/ pmjdebruijns files
 i tried([http://www.xs4all.nl/~bruijn9/quake3/breezy/quake3-1.33-r438-i686.tar.gz](http://www.xs4all.nl/~bruijn9/quake3/breezy/quake3-1.33-r438-i686.tar.gz)) and it worked but it didnt load the pb :|  :. i cant play online[/QUOTE]


i'm having the same problem... anyone have any ideas?

---

### Post by Heavy_Master on 2006-04-16
I fix the problem by using the Enlightened Sound Daemon and by adding the three lines

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

Into /etc/init.d/bootmisc.sh as sinbad782 says (many thanks to you :D ).

Only a question: there's a shell command to run quake3 or another application with a different audio device? For example quake3 -esd. It's so boring opening everytime kcontrol and choose esd ;) 

Ah! It even works on dapper! Many thanks to all!

---

### Post by 0b1ivion on 2006-05-14
i'm in dapper
i've got the sound working by uncheck the esd sound in the preference - sound - esd. 
seems to me the same as killall esd thou only you won't get the startup tunes and logoff ones. but you won't need to type everytime before playing :D

---

### Post by sanone on 2006-06-01
[QUOTE=matva]i'm having the same problem... anyone have any ideas?[/QUOTE]

Source: [http://www.icculus.org/quake3/?page=status](http://www.icculus.org/quake3/?page=status)
> **PunkBuster Support**

Even Balance's Punkbuster support can never
be included with any open-source version of Quake 3 due to it being removed from the
source-code before the release, and the binary-only nature of its anti-cheating software.

While it is possible that someone could write an open-source equivalent of PunkBuster,
it's not very feasible for a number of reasons.

Hope this answeres your question. I hope this post makes it clear for all that _if_ you want to play online you better use the official client instead of the open source version.

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

### Post by superjoe on 2006-09-15
epox is right, joss is the way to go for Quake 3 (and probably Enemy Territory).  I use the ALSA Intel 810 driver on Dapper, and had no luck with any of the other methods:

- aoss quake3 gave me crackly sounds
- esddsp quake3 brought up a blank screen
- the echo to /proc/asound/card0/pcm0p/oss got sound working in the menu, but when the game started, it froze

The only method I didn't try was arts, some people have reported success with that.  I finally found joss and it works great (spent way too much time on this, btw)

Getting joss to work isn't very straightforward, but here are some tips.

- You'll need to compile it, so you need a working dev environment.  Getting "build-essential" from synaptic or apt-get should do it.

- The other packages I needed were:

jackd
libjack0.100.0-0
libjack0.100.0-dev
libglib1.2-dev
libsamplerate0
libsamplerate0-dev

- I downloaded the source for joss from:

[http://www.konstruktiv.org/q3jack/](http://www.konstruktiv.org/q3jack/)

- Decompress the archive, "sudo make", then "sudo make install"

- Now start the jack server with:

# jackstart -R -T --silent -d alsa &

The "-T" tells it to shutdown after the clients disconnect (so that you can put this in a script), and the "&" will background it so you get your console back.

- Hit enter to see your prompt again, then type

# joss quake3

- Should now work with sound.  Mine froze for a couple seconds when the game first started (long enough to say "oh crap") but then it started working perfectly.  Didn't have another lag for a whole gaming session.

- If all that worked, put those two commands into a script ("q3start.sh" for example) and use the script to run the game.

Hope this helps other poor obsessed people like me.

---

### Post by slyvren on 2006-10-09
**TO FIX :**

[SIZE="1"]------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------[/SIZE]

**DO THIS:**
(you might have to kill esd or artsd, I dont use either one, so I dont know.)
open: ~/.q3a/baseq3/q3config.cfg
change: seta snddevice "/dev/dsp" ... to what? I had to use "dev/dsp1" you can try /dev/dsp0, /dev/adsp, or /dev/adsp1 .. I would play with those until it works.

**While I appreciate the ioquake3, I dont recommend it, you cant use PB, and i think its really nice if we keep everything "official" in the quake3 community.**

---

### Post by sleestak240 on 2006-11-16
I've been trying for several hours to get sound working in Enemy Territory and True Combat.  I finally succeeded by following superjoe's instructions on using JOSS posted earlier.  I did have to make a quick change which I'll outline here.  Some background, I'm using an ICE1724 based sound card that ET would simply not detect...I'd get "Cannot find /dev/dsp errors, can't mmap /dev/dsp errors and another where I couldn't set "sound=2".  I followed virtually everything out there, artsd wouldn't work, aoss gave me crackly sound, remapping the playback device didn't work, esddsp would freeze X.  I was about to give up just as I found this post.  superjoe's instructions are dead on for breezy, but for Edgy you need to make a quick modification to the makefile before you make the file.  Open the Makefile wherever you extracted the joss source and add the option "-fno-stack-protector" to the end of the CFLAGS line near the top.  Then sudo make and sudo make install and you should be able to use JOSS to launch ET or True Combat.  If you don't set -fno-stack-protector you'll get the error "undefined symbol: __stack_chk_fail_local" when you try to launch an app with JOSS.

Hope this helps anyone else avoid some of my frustration.

---

### Post by clean97gti on 2006-11-26
Hey folks, I've been trying to get sound working, but I can't find the q3config.cfg file.

I've got the game installed, it plays (sluggishly I might add) but no sound. I'm getting the same error others are getting, but I can't find the q3config.cfg file. In fact, I can't find the /.q3a/baseq3 directory its supposed to be in. I'm really lost on where to go from here.

Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp


any ideas?

---

### Post by dmn_clown on 2006-11-27
> **sanone said:**
> I hope this post makes it clear for all that _if_ you want to play online you better use the official client instead of the open source version.

No, you can play online just fine with the ioquake3 engine, you just will not be able to play on a pb enabled server.  

As many people as I've seen cheat on pb enabled servers (aim bots and such) it makes the entire pb system a waste of hard-drive space, but if you _must_ play on those servers feel free to use iD's engine and its lack of added features like OpenAl, SDL, flares, etc..

---

### Post by clean97gti on 2006-11-27
bump.

any ideas on where I can find my config file? Is it created every time the game runs?

I'm a real noob at this and just need a simple answer.

---

### Post by mrf on 2006-11-27
The cfg file should be ~/.q3a/baseq3/q3config.cfg (ie in your home dir) not in /.q3a/baseq3/ like your post above.

Also if you're playing mods it will be using ~/.q3a/<mod_name>/q3config.cfg. The mod cfg file is automatically created when you start that mod for the first time. The cfg it uses is effectively copied from the baseq3 one. So it's best to get your baseq3 q3config.cfg set up correctly first.

---

### Post by clean97gti on 2006-11-28
> **mrf said:**
> The cfg file should be ~/.q3a/baseq3/q3config.cfg (ie in your home dir) not in /.q3a/baseq3/ like your post above.

Also if you're playing mods it will be using ~/.q3a/<mod_name>/q3config.cfg. The mod cfg file is automatically created when you start that mod for the first time. The cfg it uses is effectively copied from the baseq3 one. So it's best to get your baseq3 q3config.cfg set up correctly first.

I've been looking all over and its almost as if I don't have a q3config.cfg

now I'm really lost. :(

---

### Post by slyvren on 2006-12-02
your config file is in a hidden folder under your home directory

/home/yourusername/.q3a/baseq3/

---

### Post by slyvren on 2006-12-02
you might want to use a console to get to it.. 

open a terminal and type 

gedit .q3a/baseq3/q3config.cfg

see if that does it..

---

### Post by PuZo on 2006-12-02
Try [**this**]("http://ubuntuforums.org/showthread.php?t=311319")... :)

---

### Post by delfick on 2006-12-21
> **PuZo said:**
> Try [**this**]("http://ubuntuforums.org/showthread.php?t=311319")... :)

THANKYOU !!!!!!!!!!!!!!!!!1

just today i started trying to make this work.....and i couldn't get it to work untill i did that :D :D:D:D:D:D:D

thankyou!!!!!!!!

---

### Post by daborg on 2006-12-28
> **PuZo said:**
> Try [**this**]("http://ubuntuforums.org/showthread.php?t=311319")... :)

Punkbuster doesn't work after installing that version of quake3.

Anyone have any solution to quake 3 hanging when starting a map after you echo "quake.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss?

This is the only way I've been able to get sound, but q3 hangs when loading. :-(

Isn't there anyone who's had this problem and actually got it working (with punkbuster)?

---

### Post by daborg on 2006-12-28
> **daborg said:**
> Punkbuster doesn't work after installing that version of quake3.

Anyone have any solution to quake 3 hanging when starting a map after you echo "quake.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss?

This is the only way I've been able to get sound, but q3 hangs when loading. :-(

Isn't there anyone who's had this problem and actually got it working (with punkbuster)?

Ok, I finally got it working with JOSS. The trick was not to start jackd with -R.

---

### Post by mrf on 2006-12-28
Punkbuster only works with the id released versions (1.32b and c, etc). You'll have install that rather the the icculus versions if you want to play online.

The sound is always muted by default in q3 in a new install of ubuntu, if you mess around in the gnome mixer applet, or alsamixer, eventually it starts working. Sorry, never figured out exactly what the channel that's muted is. Pisses me off too.

---

### Post by superjoe on 2006-12-29
> **daborg said:**
> Ok, I finally got it working with JOSS. The trick was not to start jackd with -R.

I think I used -R because it runs jackd in realtime priority.  Looks like I was running it as root, so that's probably why it worked for me.  I doubt there's a very noticeable difference either way. Glad to hear that you got it working!

---

### Post by fakie_flip on 2006-12-31
You can thank me by donation $500 big ones.

If dual-core smp == true, then do

echo "quake3-smp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

else do

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

