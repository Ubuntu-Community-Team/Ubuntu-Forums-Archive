---
title: "Enemy Territory Sound"
date: 2006-04-08
forum: Gaming &amp; Leisure
---

### Post by OlineSixtyOne on 2006-04-08
Everywhere I've looked, people say the solution to lack of sound in Enemy Territory is to run:
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
Well, whenever I run this, I get:
```
andrew@ubuntu:~$ sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied
andrew@ubuntu:~$
```
I've checked, and root has write permissions for the file, and the folder that it's in. Can anyone help me?

---

### Post by lotheac on 2006-04-09
Try this.
```
$ sudo -i
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
# exit
```

If you use sudo, what happens is that the echo command is run as root but you're trying to write to the file as a regular user, because ">" redirects the output of the command before it (ie. sudo echo). You could always just use vi or nano or whatever to edit the file as well.

edit: clarified explanation.

---

### Post by jon_benge on 2006-04-09
I have this problem too. All i type is this

```
killall esd
```

This kills the sound in ubuntu BUT allows sound in Wolfenstein. If you want the sound back in ubuntu either reboot or press Ctrl+Alt+Backspace

---

### Post by vod_ska on 2006-04-09
I've got the same problem with sound. I've tried killing esd, but console says any process has been killed. I tried this, as root:

# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
# echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0p/oss

But nothing.

I copy what I get from console, after closing ET:

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/dani/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/dani/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dani/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xadc2bf40
Sys_LoadDll(ui) succeeded!


I'm playing normally, but without sound.
Anyone have any idea of what's happening?

Thanks in advance!

---

### Post by OlineSixtyOne on 2006-04-09
[QUOTE=lotheac]Try this.
```
$ sudo -i
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
# exit
```

If you use sudo, I think what happens is that the echo command is run as root but you're trying to write to the file as a regular user. You could always just use vi or nano or whatever to edit the file as well.[/QUOTE]
Thanks that worked, but still no sounds. Same problem as vod_ska.

---

### Post by kvonb on 2006-06-04
Try my instructions here:

[http://ubuntuforums.org/showthread.php?t=167679](http://ubuntuforums.org/showthread.php?t=167679)

Let me know if it works.

Regards,

Kev :)

---

### Post by Sukarn on 2006-06-04
Try this -
```
sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
```
This allows sounds in both Ubuntu  and enemy territory.
Someone told me this but I forgot who. I'll edit this post with their name if I can remember it.
It works for me anyway.

---

### Post by Christopher on 2006-06-05
[QUOTE=Sukarn]Try this -
```
sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
```
This allows sounds in both Ubuntu  and enemy territory.
Someone told me this but I forgot who. I'll edit this post with their name if I can remember it.
It works for me anyway.[/QUOTE]

Very nice this worked for me. Is there a way to make my 5.1 surround sound work properly? Thank you in advance.

---

### Post by chadk on 2006-06-07
Do you have to reboot after this?
I've tried all of the above and it's not working. - Right after I installed ET, I chose to PLAY NOW and it worked with sound fine but today after rebooting it's not working.  No sound, though I have sound if I play a movie or mp3.

---

### Post by damien82 on 2006-06-08
has any of you guys 2 soundcards? one onboard and one a pci etc.? if so, try disabling the onboard card, that worked for me

---

### Post by Christopher on 2006-06-12
[QUOTE=damien82]has any of you guys 2 soundcards? one onboard and one a pci etc.? if so, try disabling the onboard card, that worked for me[/QUOTE]

Yea my onboard sound is diabled, i have sound in 2 or 3 of my speakers but i would like 5.1. :confused:

---

### Post by kybishop on 2006-06-12
kvonb, i tried your solution and it worked the first time, but now doesn't after rebooting

how do you disable an onboard sound card, my onboard sound card is being a pain in the *** an im having trouble disabling it

---

### Post by kybishop on 2006-06-12
forgot to mention i get this output from terminal

```
root@kyle:~# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: No such file or directory
```

confused i am

---

### Post by eggmanpete on 2007-04-03
I am getting this with a M Audio Delta 2496 card:

```
------- sound initialization -------
/dev/dsp: Invalid argument
Could not set /dev/dsp to stereo=2------------------------------------
Sound memory manager started
Sys_LoadDll(/home/eggman/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/eggman/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/eggman/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xed9cdf40  
Sys_LoadDll(ui) succeeded!

```

no sound for me

---

### Post by damien82 on 2007-04-09
> **Sukarn said:**
> Try this -
```
sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
```
This allows sounds in both Ubuntu  and enemy territory.
Someone told me this but I forgot who. I'll edit this post with their name if I can remember it.
It works for me anyway.

This worked for me as well, thanks a lot =)

---

### Post by fakie_flip on 2007-04-12
The problem seems to be only with Dapper. I can get the sound working in Edgy and Feisty development version, but none of the tricks are getting the sound to work on the computer with Dapper. Are all of you using Dapper who cant get it to work with the command?

---

### Post by ferx on 2008-05-09
another result:

```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
```

---

### Post by Luister on 2008-05-10
try this:

```
ls -l /dev/*dsp*
```

if you see any /dev/adsp* then run ET like this:

```
<path-to-ET>/et +set snddevice /dev/adsp 
```
or /dev/adsp1 or whatever you got.

.

---

