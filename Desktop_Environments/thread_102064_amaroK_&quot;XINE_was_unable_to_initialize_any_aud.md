---
title: "amaroK: &quot;XINE was unable to initialize any audio-drivers&quot;"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Ninnghizidha on 2005-12-11
Hello!

I got a problem, which I can't solve at my own. Its with amarok, which works very good with the gstreamer-engine, but i'd like to use the XINE-Engine. But if i choose it in the settings, i get the "Xine was unable to initialize any audio-drivers"-message.

But i cant belive this is true, cause if i use the comamnd "xine <file.mp3>" i can play every mp3 I own. The problem has to be somewhere else, and i'd be happy about every hint I can get from you, fellow ubuntuians. :-)

Ninnghizidha.

---

### Post by Simon80 on 2006-04-24
I solved this issue by removing my existing Amarok settings file and thus resetting Amarok:

```
mv ~/.kde/share/config/amarokrc ~/.Trash
```

---

### Post by zhuomingliang on 2006-06-19
thanks, I solved this issue for your help

---

### Post by Ramses de Norre on 2006-06-22
Is there any other way then deleting all config files? It just happend for the second time here and it's a really annoying bug.. 
All help is apreciated =)

---

### Post by herr-k on 2006-07-02
I had the same problem after playing with the device configuration and I got rid of it by editing this line

[Xine-Engine]
Output Plugin=alsa

in the amarokrc file from "alsa" to "oss". Afterwards I was able to start with this engine again and set decent values for devices.
But I guess more responsible is the entry in  ~/.kde/share/apps/amarok/xine-config:

audio.device.alsa_default_device:plughw:0,0
audio.device.alsa_front_device:plughw:0,0

If they're set to  reasonable values (plughw:0,0 works on my system but not necessarily on your's) everything should be fine either.

---

### Post by Panik on 2006-07-07
I too was having this problem.  Searched all over earth for a fix, and this seems to fix it.

Took me forever to figure out the happy face issue.  : p  without the space in between.  Edited my xine-config file by finding those lines and editing.  I hope that was correct.

Edit: I also had to comment out one of the lines (eg remove the #)

---

### Post by Panik on 2006-07-07
SHOOT!!!  This did not fix the problem.  I though it did, but no.  It seems to be random.  I can shut amarok down and restart.  Sometimes I get the error, sometimes I do not.  It is driving me nuts.

---

### Post by phormion on 2006-10-28
I also got the XINE error message after the upgrade to Edgy ("Xine was unable to initialize any audio-drivers"). I wouldn't recommend deleting the old amarok config file, it only messed up things for the worse for me. After only removing the configuration file, amarok was hanging with this stupid small window saying "updating the database", and then after killing it and re-running it wouldn't even start. 

After that I removed the xine-config file (mv ~/.kde/share/apps/amarok/xine-config{,.old}, so there's a backup), and also removed the old collection files - ~/.kde/share/apps/amarok/collection*. I guess getting rid of all the settings could also work, but then you lose all the player history, etc.

Later edit: whoops, no luck. The player died on my a minute after posting this. Quite funny - the last song was still playing, but there was no amarok window in sight!

---

### Post by robin.w on 2006-10-28
Hi guys,

I've got exactly the same problem as you. This is my provisional solution: Run amarok like the superuser root and everything is gonna be ok. If anybody get any better idea, let me know.

 See ya.

 Robin

---

### Post by Ramses de Norre on 2006-10-28
That's a pretty dangerous solution..

---

### Post by robin.w on 2006-10-29
Yes, you are right. But I've not found any better solution yet. It's pretty strange. 

Run your amarok just once like the superuser root and after use it as usually you do (no root). It's working. I think that something is wrong with the xine engine's output plugin.

---

### Post by Ramses de Norre on 2006-10-29
Oh only once? That changes the problem, that's in fact not so harmless. I thought you meant running it always like root.

---

### Post by jsma on 2006-10-29
According to another thread ([http://ubuntuforums.org/showpost.php?p=1653178&postcount=4]("http://ubuntuforums.org/showpost.php?p=1653178&postcount=4")) all you need to do is delete your .asoundrc file (in your home directory) and then alsa playback will work fine. This fix worked for me. I'm posting here since this is the first xine thread I found for this problem.

---

### Post by puchat3k on 2006-10-30
thanks jsma that worked. that was the single problem i had with my upgrade to edgy.

---

### Post by robin.w on 2006-10-30
Ok, not only once. My fault. Sorry. But I'm not runnig amarok like root. 

Fortunately *jsma* found the best and working solution. 
Thanx a lot!

---

### Post by catchbubbles on 2006-11-20
copy content of amarokrc file from root and paste get yours amarokrc contents replaced by that

roots amarokrc file

/root/.kde/share/config/amarokrc

Yours amarokrc file
/home/<user>/.kde/share/config/amarokrc

It will work.



> **robin.w said:**
> Hi guys,

I've got exactly the same problem as you. This is my provisional solution: Run amarok like the superuser root and everything is gonna be ok. If anybody get any better idea, let me know.

 See ya.

 Robin

---

### Post by GaryR13G on 2006-12-06
Step 1: Rename ".asoundrc" in home folder to "backup"
Step 2: Start Amarok
Step 3: close Amarok
Step 4: Rename "backup" in home folder to ".asoundrc"
Step 5: Start Amarok
Step 6: Enjoy...

---

### Post by Ramses de Norre on 2006-12-07
I don't have such an ~/.asoundrc file..

---

### Post by flapane on 2007-02-09
same problem here on feisty and no one of these methods worked

---

### Post by iSE on 2007-02-16
I don't know if this is the same with anyone else but I got this issue after w32codecs, does that help anyone with a possible cause/solution?

EDIT: I changed the settings to ALSA in Amarok and it now works. The problem is I have my own soundcard as well as the on-board one. ALSA is used by the on-board soundcard and I have to use OSS to get it through my PCI card. Maybe this is the same problem as the others but with a different cause. Can anyone help?

---

### Post by darkNiGHTS on 2007-03-26
I was able to solve this problem on my Archlinux, you go into ~/.xine and you delete the file "config".  Should work for you ubuntu guys too.

---

### Post by orawax on 2007-03-29
> **jsma said:**
> all you need to do is delete your .asoundrc file (in your home directory)

This worked for me in Edgy. However, with USB speakers I had to do it carefully in the right order:

1) select ALSA output plugin in amaroK engines
2) close amaroK
3) delete .asoundrc
4) set USB Speakers as Default (in System > Preferences > Sound > Sounds)
5) logout/login (not sure if this is necessary)

---

### Post by Pikestaff on 2007-04-05
Has anybody figured out a sure-fix for this yet other than restarting X (which is what I have to do)?  I've tried basically everything in this thread with no success and I don't have a .asoundrc file from what I can find... and having to stop everything I'm doing to restart X several times a day just to get sound back is getting tiring... =/

---

### Post by chrisvp on 2007-05-13
I had tried everything listed above but nothing worked for me...

I ran amarok in a terminal:

++++++++++++++++++++++++++++++++++++++++++++++
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/chris/.DCOPserver_subserver__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-chris/ksycoca'! Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-chris/ksycoca'! Permission denied

++++++++++++++++++++++++++++++++++++++++++++++

I changed privledges on /var/tmp/kdecach-username directory and the problem fixed itself. I have no clue how the permissions got changed...Or maybe amarok just didn't need to cache anything before?

---

### Post by oconnor663 on 2007-06-08
I had a very similar problem on Gentoo. I'm going to post it here in case it might be of help to someone.

I could play music with simple programs like mpg123 just fine, and alsamixer was working fine too. But I couldn't play anything with amaroK. Every time I tried to play a track, I got the error popup "xine was unable to initialize any audio drivers." Deleting the amaroK config file did not help.

The problem ultimately turned out to be that my xine-lib package was not compiled with alsa support. I must've emerged it before I added "alsa" to my /etc/make.conf useflags. (Again, I don't know how much help this will be to Ubuntu users...) Anyway, the simply fix was to re-emerge the xine-lib package. Everything worked fine with no further configuration.

---

### Post by bunker on 2007-06-08
I believe the problem is that ALSA under certain configurations and hardware will only allow one program to use the sound card at a time.  That's why the error is so hard to pin down and reproduce.  Often a fix will be specific to your sound card's chipset (and documented), or you can install a sound server like esd.

See here for soundcard issues: [http://bugtrack.alsa-project.org/main/index.php/Matrix:Main](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)

I'm not positive if it's a definitive fix for everyone, but I remember enabling software mixing (a la [this page](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-via82xx)) sorted it out for me a while ago; this box still has the problem but I haven't been bothered to fix it yet.

Edit: eugh they've changed their wiki page - it no longer gives the solution to problems for that chipset, but it should be on those docs somewhere.

---

### Post by jjatria on 2007-08-08
i get this error at random times... amarok just dies on me and all i'm left with is this message.
i think bunker might be right, though, because no of the fixes on this thread work for me, and the only way i have of fixing it (short of restarting) is closing down programs that may have sound playback. more often than not it's firefox, but i think i remember it happening without firefox on the background.

---

### Post by sloik on 2007-10-15
Greetings.

I was encountering this error on Fedora 7 when switching Amarok to play through my on-board soundcard which was hooked up to my speakers rather than my headphones. It would only occur when switching between tracks on my playlist. After quite awhile, I found that disabling crossfading made this error dissappear. I'm assuming this is due to multiple processes using the same sound card, as some previous posts pointed out.

Hope this helps someone!

---

### Post by bunker on 2007-10-17
I attempted to post a tutorial for this a while ago but evidently it was not up to scratch.

The problem is that your card does not support hardware mixing to a high enough degree [some cards support it in different ways, some are just re-sampling... it all gets strange].

Anyway, here is my /etc/asound.conf annotated:

```

# Stuff for my sound card (via 82xx chipset)
pcm.my_card {
  type hw
  card 0
  # use device 1 - device 0 is for 4 channel output and sounds pants (I think it 
  # upsamples to 48khz  (maybe it's for DVD's? )) - note this information is just for
  # my sound card, but if you have similar weirdness you might want to look at
  # a similar solution ;).  Be aware that often it's only possible to detect strange 
  # audio problems on good headphones.
  device 1
}

# The mixer device for output
pcm.dmixed {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false   # let multiple users share
    ipc_perm 0666           # IPC permissions for multi user sharing (octal, default 0600)
    slave {
    pcm "my_card"
       # match sample to music because upsampling to 48000 sounds terrible for my machine.  YMMV.
       # If you do use this then you need to tell your DVD player to downsample in order to have mixing OR create
       # another plug for it to use.  With the latter you won't be able to play DVD and listen to music.
       # Possibly I might be able to use hw0,0 with my card for DVD and 0,1 for audio [see note on pcm.my_card]
       # but I haven't tried it because I don't play DVD's on this box anyway
       rate 44100
       # Can improve skipping - experiment though.  Different cards perform better with different settings.
       buffer_time 0

       # changing these two can improve the pops you sometimes get - again, experiment
       buffer_size 2048
       period_size 512
    }
}

# The mixer device for input
pcm.dsnooped {
    type dsnoop
    ipc_key 2048
    slave {
    pcm "my_card"
       rate 44100
       period_size 128
    }
}

# Create a full duplex device (in and out)
pcm.asymed {
    type asym
    playback.pcm "dmixed"
    capture.pcm "dsnooped"
}

# Use the 'plug' plugin
pcm.pasymed {
    type plug
    slave.pcm "asymed"
}

# For OSS
pcm.dsp0 {
    type plug
    slave.pcm "asymed"
}

# Map the default to out duplexed-mixed device - some apps still do not support named
# ALSA devices (for some reason)
pcm.!default {
    type plug
    slave.pcm "asymed"
}

# What the alsamixer controls
ctl.!default {
  type hw
  card 0
}



```

Even with this setup, it is still up to your audio program to do the tricks that are sometimes necessary to make audio work properly on linux (eg playing silence after a track to stop the popping and pre-buffering to stop the gap between tracks).  So far, the best at this is audacious, but it messes with the master volume control so I stay away from it - kinda takes the whole point of dmixing away if one program will mute everything whenever it feels like it.

To test you're up and running, create a .wav file and in two different shells run:
$ aplay your_wav_file.wav

If they play together then you're set!  No more 'xine cannot initialise...', and you can watch a DVD with your own home-made sound track ;).

Hope this will help.

[Aside: audio is still a damn pain in Linux, especially on a cheap card like mine.  Unfortunately it seems to be one of those things that just doesn't stick out enough as a problem for anyone to *really* solve.  I think Ubuntu teams should really look into an auto configurer for asound, because a good portion of Ubuntu users aren't going to have a clue what half of the stuff in asound.conf does.  For me, it's the only area that windows really sticks out as being simply 'better'.]

---

### Post by SigmundFreud on 2007-11-14
I stopped using Amarok because I just can't get rid of this error. Getting rid of amarokrc usually helps, but it's annoying because you lose your config settings (and it doesn't always help, too!) If anyone has a new idea about getting rid of the xine problems I'd be happy to try it.

---

### Post by heinrich on 2007-11-27
Hi, i had the same problem. Occurd accidently.
Fixed it by installing 

  libxine-dev libxine1-dbg libxine1-misc-plugins

Now its working fine again.

---

### Post by elkang on 2007-11-27
thx soooooo much @heinrich: installing those packages worked for me =D me happy now ;)

---

### Post by SigmundFreud on 2007-12-04
> **heinrich said:**
> Hi, i had the same problem. Occurd accidently.
Fixed it by installing 

  libxine-dev libxine1-dbg libxine1-misc-plugins

Now its working fine again.
I have trouble installing libxine1-dbg. I get an error: 'Depends: libxine1 (= 1.1.7-1ubuntu1) but 1.1.8-2ubuntu2~gutsy1 is to be installed' (using Gutsy). 
Only installing libxine-deb wasn't enough to solve this irritating bug.

---

### Post by Fadsjeik on 2007-12-06
> **heinrich said:**
> Hi, i had the same problem. Occurd accidently.
Fixed it by installing 

  libxine-dev libxine1-dbg libxine1-misc-plugins

Now its working fine again.

Wow! Thanks a million, worked like a charm!

---

### Post by RgnKjnVA on 2007-12-21
Heinrich = The Man

I love it when the solution is already in the thread by the time I find it. =oD

---

### Post by nugator on 2008-01-27
sloik is The Man!

My problem was not related to playing music more switching between songs. First song would always play perfectly but when switching to the next Amarok broke down totally.

[SIZE="6"]**Disabling Cross Fade solved my problems!**[/SIZE]

---

### Post by JRAlkire on 2008-04-02
Way to go, you fixed it for me too! For me I think it was caused by some kind of change that made PulseAudio no longer appear in the "output plugin" list. Installing those packages you mentioned fixed the problem so long as I select ALSA or autodetect (which probably chooses ALSA) even though I use PulseAudio (so I can make the sound play on my other computer, [the only one with decent speakers]).
Thanks!

---

### Post by jimbo99 on 2008-04-02
You guys are honestly saying that you can't find the configure amarok dialog box inside amarok?  Or are you saying that this causes you grief when you choose it?

You can change the sound engine in amarok by using the configure amarok dialog box.  On the left is an icon representing various categories of tasks.  Choose the Engine icon and select the sound engine you want to use.

Sometimes you also have to make it match in your sound preferences.  Under the system menu in Preferences is an entry for the sound.  Choose that and set it to OSS.

Sound in Linux is still pretty bad, all things considered, but it isn't so bad as it was a couple years ago.  I use Amarok all the time and I've encountered that problem on virtually every linux box I've put it on.  OSS seems to work the best all round for all applications.

---

### Post by Kiri on 2008-04-03
Tried every suggestion on this thread. It still is not working :(

---

### Post by mikwig on 2008-04-07
> **Simon80 said:**
> I solved this issue by removing my existing Amarok settings file and thus resetting Amarok:

```
mv ~/.kde/share/config/amarokrc ~/.Trash
```

so simple - worked for me thankyou

---

### Post by ceelow on 2008-04-09
None of the suggestions (deleting the collection or the directory settings, etc.) has worked for me.  Only amaroK has this issue with sound, everyhting I can run to produce sound (inernet, other apps, not a problem) Is there a real solution to this problem with xine?

---

### Post by Kiri on 2008-04-09
I've found it to be a bug in the flash plugin of firefox. After rebooting, try opening amarok before firefox or any other programs and see if it works then.

---

### Post by jaws31415 on 2008-04-10
, I tried to uninstall xine and it crashed my whole system

---

### Post by feranick on 2008-04-25
I am using Hardy Heron, final release. I can solve the problem by selecting OSS:

Settings menu: Configure Amarok
Engine: Output plugin: OSS

I guess for Hardy Heron the problem is ALSA not properly functioning with PulseAudio.

Anyway this worked for me.

---

### Post by tigersrock on 2008-05-30
i agree with you kiri, i have the problem with amarok after i run firefox and some flash video.

---

### Post by P.Crespi on 2008-06-02
I had the same error (XINE was unable....) on an OpenBSD 4.3. My solution was to install the artsd audio output module for xine-lib: xine-lib-arts-1.1.10.1. I hope this helps Ubuntu users. Unfortunately I didn't get amaroK to play CDs correctly. The sound skips.

---

### Post by tigersrock on 2008-06-02
I don't know exactly what fix it, i installed libxine1-all-plugins and changed the output to alsa (using oss didn't work). Amarok is normal again.

---

### Post by wfarr_08 on 2008-06-07
> **feranick said:**
> I am using Hardy Heron, final release. I can solve the problem by selecting OSS:

Settings menu: Configure Amarok
Engine: Output plugin: OSS

I guess for Hardy Heron the problem is ALSA not properly functioning with PulseAudio.

Anyway this worked for me.


Re:amarok: "XINE was unable to init any sound drivers"

I am Using MEPIS 7 And I Can't Get It to work either. Please
Advise, Cause I Cant figure it out..Is it a problem With My OS??

---

### Post by Roasted on 2008-07-17
I got this error randomly and had no idea how to fix it. I reinstalled Amarok many times, got the additional plugins people suggested here, nothing worked.

I only got it to work under two circumstances. For one, I had to delete my amarokrc folder, and also... Amarok only works if I have sound preferences - auto detect + my preferences in Amarok are auto detect.

I'm running ALSA, so you'd think setting it to ALSA would work. But under ALSA, it failed, prompting me with the error. With auto detect, it works.

Why in the hell is it like this?

---

