---
title: "Increase Volume Maximum"
date: 2006-01-05
forum: Desktop Environments
---

### Post by hopspitfire on 2006-01-05
Is there a way to increase the maximum volume level to a higher one and to have the volume controller in gnome still be able to manage it? In other words, I want to make the sound louder than the maximum, and when i do, can it still be controlled by the volume manager? Hope that made sense... Thanks in advance

---

### Post by encompass on 2006-01-05
Perhaps you should tell us the goal... what your wanting to do... they may be another, better way ...

---

### Post by hopspitfire on 2006-01-05
I'm hard of hearing (actually half deaf), nobody can actually tell since I compensate well, but the problem is that the only alarm that has been able to do its job was in windows by using Karen's Alarm Clock (google for it) and town.mid (Its in C:\Windows\Media, can't post it due to copyright restrictions). The only reason for me to boot back into windows every day is just for the alarm clock, so that would be the final barrier before becoming ms0ft free. 

I got midi support working earlier today, except when town.mid is played it comes out quite soft (even on the highest volume). So, my goal is to simply make the volume threshold higher. I hope that was detailed enough :P

---

### Post by mcduck on 2006-01-05
You can't increase the overall volume higher, as the max volume _is_ the max volume your hardware can do. But you can set the notes in a midi file to play at max volume instead of what the maker of the midi file has set them to. (that must be what your windows program does)

I don't know any program that would to that automagically, but you could use any midi editor to make the notes in your midi file as loud as possible.

What kind of speakers/audio setup you have? wouldn't it be easier to connect some active speakers to your computer and turn their volume higher? This would be the best solution, unless you are laptop user and need the alarm everywhere (and don't want to carry speakers around).

---

### Post by BUXjr on 2006-01-05
This is an interesting point.

I too have noticed that the MAX volume that my Ubuntu PC can put out, is significantly lower than when I had Winblows installed.  ON THE SAME PC.  But, I have had to manualy crank up the volume on my speakers to compensate for this.

I wonder if there isn't a config file buried somewhere that would allow us to increase the overall output volume of the OS.  I know my Sound Blaster can put out more -- I've heard it do so.

Experts?  Any help here would be appreciated.

BUXjr

---

### Post by encompass on 2006-01-05
By default you can't see the adjustment for the midi valume... check out the valume and what it is set at by going to... Applications --> Sound and Video --> Volume Control
Then....
Edit Preferences... select them all... if you want... and turn um all up to full bore... and play with some of dem switchs.  They might help you out.    There may be some setting somewhere like the external amp setting or others that may greatly increase you volume.  Hope that helps out.

---

### Post by bulldogzerofive on 2006-01-05
[QUOTE=BUXjr]This is an interesting point.

I too have noticed that the MAX volume that my Ubuntu PC can put out, is significantly lower than when I had Winblows installed.  ON THE SAME PC.  But, I have had to manualy crank up the volume on my speakers to compensate for this.
BUXjr[/QUOTE]


I am no expert, however i did notice this, too.  I also noticed that it went away when I changed from the Gstreamer engine to the xine engine to play files.

---

### Post by encompass on 2006-01-08
Going back to your solution... in the middle of the night I just realized that you could convert your midi to an ogg then play it with xmms with the alarm plugin... with audacity you can convert midi to anything you want.  then increase the valume of the midi itself from there... then play the midi as an ogg.
What do you think?

---

### Post by hopspitfire on 2006-01-09
I reinstall ubuntu to fix my network problem, which is an entirely different issue. I dl'ed audacity, and when i tried to import town.mid it said the file wasn't recognized, and to try importing it as raw. Did that too, and it does not work... is this because I haven't installed the midi drivers yet? Or another issue all together? Thank you for your replies, they have been very helpful :)

---

### Post by encompass on 2006-01-09
awsome... I would install the midi drivers, you can't record the sound wihtout something to play it... right?  I could be wrong... if you watn to send me the file... email me... and we can get in touch... I am detrmined to find some way for you to wake up in the morning! :P

---

### Post by hopspitfire on 2006-01-10
I sent you a pm with a link to the file, hope you can get it to work :P thanks for the help

---

### Post by encompass on 2006-01-10
It works!! I got the file to convert to ogg format... that will work for you... not only can you play it as an alarm in xmms, but you can increase the valume with audacity. just run this command....
> timidity -Ov town.mid

That will create town.ogg
DON't be running anything while that is going cause it might be a little touchy on the recording...  and be patient it is recording for all 81seconds of the song.  Takes a while.  Hope this works for you.

---

### Post by hopspitfire on 2006-01-12
Ok, I went and did all that with audacity and found out that half of the instruments are missing :(. I asked a friend of mine what he thought i should do, and his suggestion was to use his comp and record the sound with windows sound recorder and boost the volume a few db's with Sound Forge (he works in the music industry). I did just that, and it worked wonders. Thank you for all your support here, i am one LARGE step closer to being a full linux user :P

---

### Post by encompass on 2006-01-12
Phew, glad it is working now for you... on another note... I want you to understand that I am not the only one to go the extra mile... thousands here do it for free.  Take that MS!

---

