---
title: "Audigy2: Gnome Vol. Control segfaults on switches"
date: 2005-07-05
forum: Desktop Environments
---

### Post by shu on 2005-07-05
Hi!

I have Audigy 2 ZS soundcard and my problem is that gnome-volume-control isn't showing any switches, just the sliders. So I can't set the Tone Control or Mic Boost on/off state. When I try to add those switches via preferences gnome-volume-control segfaults. The same happens on other machine with SB Live!. 

Things are working fine with onboard Realtek ALC650 codec tough.

Can anybody point me in right direction? I already lost enough time googling around and found nothing.

---

### Post by scoon on 2005-07-14
Hey there, 

Lost enough time ?  Anyway, you can make adjustments with alsamixer but the problem sounds like you don't have alsa conf'd correctly.  I would guess if you disable your onboard sound, that the audigy and gnome vol control will work.  If you don't want to do that, search on how to have more than one sound source w/ alsa.  You can also strace gnome vol control and see if anything helpful shows up.

regards, 

scoon

---

### Post by shu on 2005-07-14
The thing is I have on board disabled. It's just that audigy doesn't work! I mean I can adjust any switches like 'Tone Control On/Off', 'Mic Boost On/Off', 'Digital Out On/Off' etc. Same thing was with SB Live!

I really don't know what is the problem with it.

---

### Post by UKer on 2005-07-14
I have the same problem with my Audigy 2zs, and just use alsamixergui, that does the job fine without crashing.

---

### Post by shu on 2005-07-14
I like gnome a lot, but there are choices being made that I can't understand. THIS WAS working with 2.8 gnome and then they replaced mixer with new shiny 'alsa' compatible one that doesn't work at all.

---

### Post by stamy on 2005-07-16
It is quite simple:

launch alsamixer in a root console (or sudo alsamixer)
then search for this option: Audigy Analog/Digital Output Jack and press 'm' on your keyboard to unmute the channel => it work's now  :smile:

PS: On some laptop (HP nx6110) you need to enable (unmute) the external analog amplifier to hear any sound ...

---

### Post by Boggles3 on 2005-07-16
ok that doesnt work for me and i have audigy 2 value...
i have to do all this crap

Firstly you have to have the development packages install during installation. Now the guide I followed was at this website below.

[http://alsa.opensrc.org/index.php?page=Quick+Install](http://alsa.opensrc.org/index.php?page=Quick+Install)

Firstly you need to download the alsa source files.

Alsa-driver download > [ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2](ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2)
Alsa-library download > [ftp://ftp.alsa-project.org/pub/lib/...b-1.0.8.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/...b-1.0.8.tar.bz2)
Alsa-utilties download > [ftp://ftp.alsa-project.org/pub/util...s-1.0.8.tar.bz2](ftp://ftp.alsa-project.org/pub/util...s-1.0.8.tar.bz2)
Alsa-OSS download > [ftp://ftp.alsa-project.org/pub/oss-...s-1.0.8.tar.bz2](ftp://ftp.alsa-project.org/pub/oss-...s-1.0.8.tar.bz2)

Right click on each of the four files once downloaded and select extract...extract here and you should see a folder popup with for example alsa-driver-1.0.8.

You download those four files first and after you downloaded extracted them goto the guide at alsa.opensrc.org and skip down towards step 3 which should be compiling and installing.

Do all of these as root just to be safe and I'll go further now.

Enter this first.

cd alsa-driver-1.0.8
./configure --with-sequencer=yes && make
make install
./snddevices

Enter this second.

cd alsa-lib-1.0.8
./configure && make
make install

Enter this third.

cd alsa-utils-1.0.8
./configure && make
make install

Enter this fourth.

cd alsa-oss-1.0.8
./configure && make
make install

If you get no errors doing the above you got the hard part done.

Now onto step 4.

First type at a terminal windows as root lsmod and look at the whole readout and make sure you don't have anything that starts with SND such as snd-emu10k1 and such. You should not have anything listed there like that but if you do you can still try this next step but if you get an error I can't help you.

type at a terminal shell as root this below.

modprobe snd-emu10k1;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

Please note the above command in the guide will show

modprobe snd-ens1371;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
but that is not right because the snd-ens1371 will error because it isn't for a SB Audigy 2 card so again please enter in this below and I will bold it for you.

modprobe snd-emu10k1;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

Now at a command prompt in terminal as root type nano /etc/modprobe.conf and you should the file. Enter this below by copy and pasting it at the bottom of the file. I'm assuming you know how too navigate using the arrow keys.

Copy and paste this below. Also please make sure you backspace each line so its all the way to the left.

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-emu10k1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Once that is copied and pasted press CRTL+X. Now press Y to save the buffer and press Enter when the file name shows.

Now type at a command prompt in terminal as root alsamixer.

It should say at the top that you have an audigy 2 value. Slide using your up arrow key the master volume and use your right arrow key to move to PCM and turn the volume up on that using your up key. I've noticed that anything can be up and it doesn't hurt anything. Just make sure all the PCM options are up and master is up too.

Now this is important below. Do this after you exit alsamixer by pressing the ESC key.

Open KMix and select the switches tab and make sure the second option from the right is one and yellow. It should be called Audigy Analog/Digital Output jack. That has to be yellow or you will get no sound at all.



and then i do /etc/init.d/gdm restart and then i have sound when it restarts...  the only problem im having is so that when i reboot and start up again that it no longer works and oss is no longer one of the devises and i have to do all that crap over again..
   i dunno why its really anoying.. nut ya if just changing the analog doesnt work try this stuff and see if it does .. and if you can meke it so you rebood and it doesnt dump everything lemme know

---

### Post by shu on 2005-07-16
Well guys, the problem is that gnome-volume-control doesn't work as it should with creative cards. I've tested it on SB Live! Value and SB Audigy 2 ZS. And it doesn't work because:
[list]
[*]it puts all controls in playback tab
[*]switches like "mic boost" cannot be added at all and result in seg. fault
[*]still shows tons of gauges that simply do nothing
[/list] 

I know what are the workarounds, but I don't want to use them! It's a damn mixer and a popular soundcard it should just work!

---

### Post by scoon on 2005-07-17
Hey there, 

Just open up a shell and use alsamixer.  When you have the settings that you like you can make them be the system default with sudo alsactll store.  I bet gnome will have their mixer fixed in the next version. 

regards, 

scoon

---

### Post by Boggles3 on 2005-07-17
maybe it will be fixed but im not sure..
i have to have alsa oss stuff installed on my ne for it to work at all and still when i reboot it all goes away and my oss is not configured anymore and i think it might be gone but im not sure

i posted my steps above.
shu can you get the sound to work at all???
   if you right click on your uper right volum icon and go to properties and click on devices is it showing two of them??.. when my sound works it shows the chip in audigy  and then ses(oss) behind it and the other ses audigy 2 (alsa).  i had to do all that crap i sed above in order to get the oss thing to show.
then i go and make sure audio dig output jack is not off and my sound works 
(ONLY AFTER I RESTART THE GUI THO MAK SURE YOU DO THAT.. DO NOT REBOOT I CANT GET IT TO STAY FOR SOME RESON)
 just do the 'sudo /etc/init.d/gdm restart' and when your gui comes up again you should have sound.

then everything seems happy and stable untill i restart.. then my sound does not work and that oss thing in prefs is missing...  ??i dont know why.. i am fairly nw i just know i can get the card to work and then when i reboot all my progress is gone and i have to do everything over again ](*,)

---

### Post by scoon on 2005-07-17
Hey there, 

Read my post above or open up a shell and type: man alsactl

regards, 

scoon

---

### Post by Boggles3 on 2005-07-17
no its not the alsa mixer settings that are not carried over... they are storring but something wierd with drivers or something is going on... maybe i can just start over completely i dunno its wierd..

i found this tho maybe it will tell you whats wrong with my stuff... 
after i get the sound working i can go to music player and pick a station and play it right..
but after i reboot i get this errer msg
error: could not open resource for writing(this a popup error and there are three of them 
then theres a fourth popup error that reads like this error:could not pause playback

even when i didnt have sound in the begining before i even messes with sound i didnt get errors i just didnt hear anything

---

### Post by shu on 2005-07-18
Boggles:
Everything works ok on my system. I started this tread because gnome-volume-control isn't working as it should and I hoped there is some solution known. I looks like there isn't unfortunately.

---

