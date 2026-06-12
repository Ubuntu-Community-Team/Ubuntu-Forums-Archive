---
title: "Mugen wont start on ubuntu 7.10"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by fuh on 2007-10-19
Hi, this is my first post here,so if it's in the wrong place,i'm sorry.
also excuse if my english is no good. :)

..I don't know if you are familiar with this game.
M.U.G.E.N.  is a 2D fighting game engine.
i had been using it on ubuntu 7.04 with no problems,
with enlightenment,fluxbox,gnome,xfce, etc.

but now it just doesn't start,tried to run it by terminal to see if there was an error
and nothing happens.

  Does anyone knows why could  this be ?
maybe something is missing,or have to configure something new ??
or ,do i have to install anything extra to be able to play it ?

here you can download the game if you want to try it: (the engine is only 3 MB)
look in the left menu for programs and download "Mugen v14.04.2002 (Linux)"

 ... [http://www.mugenation.com/index.php/cat=programmi](http://www.mugenation.com/index.php/cat=programmi)

that's what i play the most. and i dont wanna have to go back to 7.04 just for that. 
since  7.10 is working better.  
greetings O:)  and thanks.

---

### Post by noodles12 on 2007-10-21
I would also like to know how to fix this. I have installed mugen and when i do the command "./mugen" it just shows another line, which means mugen is opening and closing right away. 

I checked permissions and it looks like it's meant to open up in wine but i thought this was native to linux so what is up with the wine?

---

### Post by fuh on 2007-10-22
wine ?? .. maybe the "winmugen" .. or something 
but i  play  linux mugen on 7.04 with no problems.

is like 7.10 is missing something
to be able to run the executable
it's a binary file.. right ??
 (i don't know if that is spelled correctly.)

or what is necesary to do so .. like some libs ?? i don't know 

for now i went back to 7.04 .. but still want to know if that is fixable.
so i can upgrade..

---

### Post by snide on 2007-10-22
Hi, I was having this problem the only thing you have to do is to disable the apparmor.

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove

hope it helps. :)

---

### Post by noodles12 on 2007-10-23
wow thanks man! it works. Now i can't seem to get sound to work but i'm sure i'll figure it out. 


Is there a way to just add programs to apparmor to get it to work? 
I want to guess it's similar to "systems safety monitor" in windows and we can just add programs to allow right?

thanks again, I never would've figured this out on my own.

---

### Post by fuh on 2007-10-23
> **snide said:**
> Hi, I was having this problem the only thing you have to do is to disable the apparmor.

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove

hope it helps. :)

all right !!!  thank you **snide** :KS
thanks a lot. 
i'll try it .

---

### Post by xjgnsdof on 2007-11-07
Worked for me, too. Good stuff! Thanks.

---

### Post by fuh on 2007-11-09
I updated to 7.10 now, and mugen works with no porblems, : )

thanks again snide.
now i'll try what noodles12 says.
so i wont have to disable the apparmor everytime.

bye.

---

### Post by CarpKing on 2007-12-08
Thanks!  I've been wondering about this since I upgraded.  Is there any particular benefit to leaving AppArmor around?  Is it intended to stop people from running malicious executables?

---

### Post by disturbedite on 2007-12-09
no, its a crash reporter afaik.

---

### Post by MaximB on 2008-01-07
Thanks
I got another problem - for some reason MUGEN is running in Debug mode.
I wonder how can I disable it

any ideas ?

P.S
How the hell did you manage to think that the problem was indeed in Apparmor ?

---

### Post by fuh on 2008-01-07
> **MaximB said:**
> Thanks
I got another problem - for some reason MUGEN is running in Debug mode.
I wonder how can I disable it

any ideas ?

P.S
How the hell did you manage to think that the problem was indeed in Apparmor ?

hi, maxim.

mugen by default comes in debug mode.
search in your data folder for a file named : **mugen.cfg**

and look for this line :

;-------------------------------------------------------
[Debug]
 ;Set to 0 to disable starting in debug mode by default.
**Debug = [COLOR="Red"]0[/COLOR]**

set it to 0 and that's it.

bye.

---

### Post by MaximB on 2008-01-07
Thanks got it.
Now I just have a major characters/stages problem
I got about 1000 characters from the Windows version (the Linux version wasn't updated since 2002) so the config files are different and many of the characters doesn't work on the Linux version. (yes after I "fix" them in the Linux MUGEN config).
I can't really check all 1000 characters and stages manually and wine is out of the question.
So what can I do ?
Isn't there an updated Linux version or something ?

---

### Post by fuh on 2008-01-07
mm..  i think the problem you say it's because 
for in linux every file inside the char's folder 
must be in lower-case

and you have to open the .def file 
to change the files names to lower-case too.

i do that with **gedit** .. 
it has a plugin that allows you to highlight the text 
then in the edit tab..  all down-case

for example..
everything from here:

**[Files]**

cmd     =ibuki.cmd
cns     =ibuki.cns
stcommon =common1.cns
sprite  =ibuki.sff
anim    =ibuki.air
sound   =ibuki.snd
st=ibuki.cns
pal1=normal_ibuki.act
pal2=black_ibuki.act
pal3=red_ibuki.act

**[Arcade]**

and this:

intro.storyboard=intro/intro.def

ending.storyboard=ending/ending.def


all down case
-----------------------------------
-----------------------------------

.....and for the folders and files.. there is the bulk renamer 

/usr/lib/thunar/ThunarBulkRename

i think it comes with thunar ( a file manager) 
or with one thunar plugin.. it's in the repositories.

there is also an aplication called pyrenamer.. you could try it.

bye
hope it helps.. :)

**EDIT**

i forgot, for the stages.
it may be, because in the stage.def
there could be this ** \ ** somewhere, and it has to be like this :** /**

i use gedit to search for that too

---

### Post by heartburnkid on 2008-03-16
Enter... the Thread Necromancer.

Hi, I'm running Ubuntu Gutsy, and trying to get Mugen running myself.  I've followed the advice in this thread, and it's at least working now, so thank you much for that.  However, now I've got a problem with sound -- namely, there isn't any  This seems specific to Mugen, as I have no problem playing audio in Exaile or the like.  Any help that can be given would be appreciated.

---

### Post by fuh on 2008-03-16
> **heartburnkid said:**
> Enter... the Thread Necromancer.

Hi, I'm running Ubuntu Gutsy, and trying to get Mugen running myself.  I've followed the advice in this thread, and it's at least working now, so thank you much for that.  However, now I've got a problem with sound -- namely, there isn't any  This seems specific to Mugen, as I have no problem playing audio in Exaile or the like.  Any help that can be given would be appreciated.

hi heartburnkid . 

...could you run mugen by console and post the output here ?
it may be because of the screenpack you are using, 
or , are you using the default mugen ? , have you tried with the default ?

it could also be the mugen.cfg , this part:

[Sound Linux]
  ;Set the following to 1 to enable sound effects and music.
  ;Set to 0 to disable.
Sound = 1


  ;Wave device to use. Choose from:
  ; NONE    - No wave device
  ; AUTO    - Autodetect
  ; OSS     - Open Sound System
  ; ESD     - Enlightened Sound Daemon
  ; ALSA    - ALSA sound driver
WavDevice = AUTO


  ;Midi device to use. Choose from:
  ; NONE    - No midi device
  ; AUTO    - Autodetect
  ; OSS     - Open Sound System
  ; ALSA    - ALSA sound driver
  ; DIGMID  - Allegro's Digimid driver
MidiDevice = AUTO



  ;This is the master volume for all wav sounds (affects mp3 volume).
  ;Valid values are from from 0 to 255.
MasterWavVolume = 255

  ;Set the volume of wav, midi, mods and CD audio.
  ;Note: WavVolume does not affect mp3 or mod volume.
  ;Valid values are from from 0 to 255.
  ;For CDAVolume only, using -1 will leave the volume unchanged.
WavVolume = 128
MidiVolume = 128
MP3Volume = 135
ModVolume = 80
CDAVolume = -1

  ;Set the following to 1 to enable and 0 to disable MIDI, MP3, MOD and CD
  ;playback.
PlayMIDI = 1
PlayMP3 = 1
PlayMOD = 1
PlayCDA = 1

that's from mine, and it's working fine, although .. i am using debian now..
since when do you have this audio problem ?

or is it the first time you trying mugen ? 
i mean...have you had that problem before ?

---

### Post by heartburnkid on 2008-03-16
It's a fresh download of it, default screenpack and all.  I haven't even added any other characters to it yet.

And yes, this is my first time using Linux Mugen.  I used to play the DOS version a lot, a long time ago, but I've never tried this version before.  Once I get it working, I'm going to dig up my old backup disc and see what characters I can get running (hopefully including my own).

EDIT: Ran it in a console, and I did notice the line "Initializing sound...failed to init hardware."  Which tells me the why, but not the specifics that I need to solve it.  Little help?

---

### Post by fuh on 2008-03-17
...then, try playing with your alsa settings.

tha volumes and stuff. in the preferences,activate every option there is.
then restart the gnome-alsamixer ,so you can see all the new options
(at least i had to do that way)

or run by console 
$ alsamixer

or you could also try first , as root :
# alsaconf

also , play with the gnome-sound-properties

...i don't know what else could be.. bye, hope it helps.

---

### Post by heartburnkid on 2008-03-18
I'm not quite sure what you meant by "enable every option there is".  I've got everything set to autodetect, and I ran alsamixer and unmuted everything except "External Mixer" et voila! Sound!  So thanks for the advice.

One thing that should be clarified though, to avoid future noobs like me, is that alsaconf isn't part of Ubuntu.  So you're going to run into trouble trying to run that. :)

Other than that, thanks for giving me a kick in the right direction!

Now to get Midi working...

---

### Post by fuh on 2008-03-18
ok,you are wellcome .. :)

..with alsamixer you can already see every option.

but, when you use gnome-volumen-control or "gmix"
you can only see a few options to play,an unmute with.

about alsaconf , thanks for clarifying that..


bye. :KS

---

### Post by Lota on 2008-05-07
I'm also on ubuntu gutsy .but when i put "./mugen" the console says:" bash:./mugen is a repertory "
and it's all....
help me please

and sorry for my very bad english

---

