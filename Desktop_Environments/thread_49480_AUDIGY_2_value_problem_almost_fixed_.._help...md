---
title: "AUDIGY 2 value problem almost fixed .. help.."
date: 2005-07-16
forum: Desktop Environments
---

### Post by Boggles3 on 2005-07-16
OK  
         i am able to get sound by doing this stuff here so if anyone is having lits of sound issues try this...





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


then i do /etc/init.d/gdm restart 
   the gui loads again and goes to login screen and i have sound now.. .. remember befor you  restart gnme to go into console and use command alsamixer to open the mixer there..

press the over right arrow key and you will keep scrolling to the right untill you fund the analog jack thing.. and unmute it..


MY PROBLEM IS THAT I HAVE SOUND NOW BUT IF I REBOOT I LOOSE OSS FROM MY SOUND PREFFS AND I HAVE NO SOUND ANYMORE..
the even wierder thing is i get the little drum role thing when login screen comes up but after i log in i have no sound at all again.. i have to do all of this stuff over again to get sound..
   any time i reboot restart,i loose it

any suggestions..??? ](*,) 
thanx

---

### Post by evilghost on 2005-07-16
Shouldn't you be modifying /etc/modprobe.d/alsa-base instead of /etc/modules.conf?

---

### Post by Boggles3 on 2005-07-17
umm? maybe i could try that.. im new so your saying it looks lke i am moding the wrong file..

but then why would the sound work for me  in the in the first place untill i reboot???

thanx for your input man keep it commin

---

### Post by evilghost on 2005-07-17
[QUOTE=Boggles3]umm? maybe i could try that.. im new so your saying it looks lke i am moding the wrong file..

but then why would the sound work for me  in the in the first place untill i reboot???

thanx for your input man keep it commin[/QUOTE]

I think because you typed "modprobe snd-emu10k1;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss"..

---

### Post by Boggles3 on 2005-07-17
i went in the file and read it to check it out... looks like you might be right so ill try this again only wif ur mod suggestion .. cross our fingers lol.

---

### Post by Boggles3 on 2005-07-17
ok i just reinstalled the entire os and now my sound works... i got something cobbled up cuz i thuoght i had to do more than i did.

anyways all i had to do was the analog thing so i dunno lol what ever i dunno what happened the first time lol

---

