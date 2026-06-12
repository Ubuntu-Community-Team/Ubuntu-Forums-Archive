---
title: "Never had sound out of quake3 based games :("
date: 2006-07-04
forum: Gaming &amp; Leisure
---

### Post by RawMustard on 2006-07-04
OK so I've never had sound from quake3 in Ubuntu ever.  So now I'm determined to get it working. My kids want to play and to be honest, so do I.  But sound outta this sucker just doesn't wanna play ](*,)

I've read every thread on these forums and others and have tried all manner of tips tricks and religious sacrifice's, except for sacrificing my first born, but nada!

My last attempt was using joss to emulate OSS with JACK(This was new to me and seemed I was on a winner).  I compiled joss and everything went fine.  I then made sure I had all necessary requirements, but here's the hitch - Instructions!  The brief docs on this little lib says type joss quake3, but all I get is

joss: cannot connect to jackd
/dev/dsp: No such file or directory
Could not mmap /dev/dsp

Which is strange because I can see /dev/dsp with my own eyes right there next to /dev/adsp, which by the way doesn't work either.  I've also got jackd installed.

Now what, I can't find a single thing on the net anywhere that suitably describes how to use joss.

Can some kind soul please offer some advice here before my kid breaks down and thinks I'm a hack :oops:

---

### Post by joft on 2006-07-04
Hi,

the first error message is a bit strange. Did you start jackd before joss? I don't know joss and I don't know about quake under linux, but this seems to be a case for oss2jack (maybe).

[ Some time ago a wrote a HOWTO on jackd+oss2jack for breezy to get OSS only apps running and playing sound in parallel. You can find an updated version for dapper here: [http://www.ubuntuforums.org/showthread.php?t=208488](http://www.ubuntuforums.org/showthread.php?t=208488) ]

---

### Post by RawMustard on 2006-07-04
Thanks for the reply, yes that was the problem, starting jackd first, but nowhere does anyone say that.

Anyway using this command "jackd -d oss & joss quake3" I get sound and it woks without crashing, it's a little staticy but it does work. Now to try and get the static out, tho I can live with it for a little while :)

---

### Post by dranger003 on 2006-07-04
Actually, I had the same problem.... until I did this:

sudo chmod o+r /dev/dsp

The thing is, if I reboot my system then the permissions are reset and I have to set them again... But it works!

Any ideas how to make this permanent?

Thanks,
Dan.

---

### Post by mayonesiac on 2006-07-04
ok i'm sort of a ubuntu newbie and i want to play jedi outcast which is based on the quake 3 engine, but i can only play it using cedega. this looks like a problem solver for me but i have no idea what to do. please help!!

---

### Post by RawMustard on 2006-07-04
Here's what I did, hope it helps some.

make sure you  have build-essential installed.
```
sudo apt-get install build-essential
```

I also use checkinstall

```
sudo apt-get install checkinstall
```

Next I installed these.

```
sudo apt-get install libsamplerate0 libsamplerate0-dev libjack0.100.0-0 libjack0.100.0-dev jackd
```

I also installed alsa-oss, but I don't think this is needed.

Download this file [joss-0.3.tar.gz]("http://www.craknet.net/joss/joss-0.3.tar.gz")

right click it and select extract here, which will make a folder called joss-0.3
In your terminal type cd and drag that folder onto your terminal, then hit enter.  This will take you inside that folder.  Now type make and when it's finished with no errors, type sudo checkinstall. Follow the instructions it's pretty easy(More info [here]("http://monkeyblog.org/ubuntu/installing/#source") if you need it)

If everything went ok, you should be able to start quake or I guess any quake3 based game with this command in a terminal  ```
jackd -d oss & joss YourGameName
```

Like I said above, the sound is a bit scratchy, but not too bad.  I'm not smart enough to solve this yet, perhaps someone else could offer some solution to the scratchiness?  This is the only way I've ever been able to get sound out of quake 3 without it crashing hard and locking my whole system in Ubuntu ever!

Have fun!

---

### Post by Loomy on 2006-07-05
Try this it fixed my sound issue in Americas Army.

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=asound.conf]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=asound.conf")

---

### Post by lH)4~mK0e on 2006-09-16
Would this be a VIA AC97 card?  I had to add this to /etc/modprobe.d/alsa-base in order to get the sound to work correctly on q3a based games.

```
options snd-via82xx dxs_support=4
```

This will require nothing else but restarting alsa and loading the game.

Cheers :)

---

### Post by Nehvrook on 2007-05-13
> **miwarlock002 said:**
> Would this be a VIA AC97 card?  I had to add this to /etc/modprobe.d/alsa-base in order to get the sound to work correctly on q3a based games.

```
options snd-via82xx dxs_support=4
```

This will require nothing else but restarting alsa and loading the game.

Cheers :)

I don't have permission to change that file? I know there's a command to use to change that but I'm new and I don't know what it is, can you tell me?

EDIT:

I got my sound working :D   This is how I did it incase anyone else is having trouble

Go to wherever you installed Quake III (For me this was /home/lee/ProgramFiles/Quake3) and in that folder find the baseq3 folder. Inside there will be a bunch of archive files. Using the archive manager (comes with Ubuntu) open the one called pak0.pk3 (You'll have to change the permissions to let you read and write to this file) and find the music and hit delete. (I made a backup of pak0.pk3 (Just copy it somewhere else on your hard drive in a folder called backup or something) just incase)
Once you've deleted the music close the archive manager and go to the root terminal. In the root terminal type in
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
hit enter then type in
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
and hit enter
Then point the terminal at your quake 3 file (For me this was /home/lee/ProgramFiles/Quake3/quake3) and it will launch the game with sound and it shouldn't crash when you load maps


EDIT2: Just thought I'd link to this thread [http://ubuntuforums.org/showthread.php?p=2646720#post2646720](http://ubuntuforums.org/showthread.php?p=2646720#post2646720) 
Someone helped me make a launcher icon so you don't have to enter this code every time you want to play the game

---

