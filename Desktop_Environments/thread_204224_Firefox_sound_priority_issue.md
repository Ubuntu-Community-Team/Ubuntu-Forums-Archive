---
title: "Firefox sound priority issue"
date: 2006-06-26
forum: Desktop Environments
---

### Post by th3james on 2006-06-26
I have a problem with sound in firefox. It works on sites like youtube or google video if I launch firefox with no other sound apps open. However, if I then open amaroK, or another media app, sound will not function in videos. I've seen this on every install ive done of dapper.
Its the only problem I have with ubuntu, which is amazing considering how much trouble i've had with other distros. Please help me fix it!

---

### Post by irv on 2006-06-26
Loooking at your Avatar it looks like your are into music so I thought I would just send you this link to fixing sound problems in linix. I am not sure it deals with firefox, but it cover most aspects of sound. Hope it helps?
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")

---

### Post by th3james on 2006-06-27
Thanks for the link, (you guess right, i am into music :) ) it was quite interesting (i always like learn more about linux), unfortunatly, i didn't find anything to help with my problem.

I'm pretty sure it's xine related, because the sound stops working when I'm using amarok, or kaffeine, both of which are using xine as a backend.

---

### Post by henriet on 2006-06-27
Hello.

Here is what I've done on my computer. I hope it will be useful.

First, install alsa-oss 
```
sudo apt-get install alsa-oss
```

Then, create the file ~/.asoundrc and copy these lines in it:

```
pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}

ctl.mixer0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmix"
}
```

Restart alsa 
```
 sudo /etc/init.d/alsa-utils restart
```

After that, edit /etc/firefox/firefoxrc and replace the line beginning with FIREFOX_DSP by this one :```
FIREFOX_DSP="aoss"
```

Finally, make Amarok and all other applications use alsa. ( For Amarok, choose xine and alsa).

I hope I don't forget anything. Good luck!

---

### Post by th3james on 2006-06-27
Oh you utter legend, thank you!!! i didn't think i'd get a fix for this, it works brilliantly!

If you don't mind, could you explain what the .asoundrc file does, i understand the rest (getting firefox to use alsa through a wrapper?). I'm just trying to increase my understanding of alsa

Thanks again, you have made my day!

---

### Post by henriet on 2006-06-27
You're welcome!

In our case, the .asoundrc file makes alsa use dmix.
You can gather more information there :
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix)
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)

---

### Post by th3james on 2006-06-27
Thanks, the links were very useful, you are a credit to these forums. Im going to see if i can get this setup added into easyubuntu, automatix or bumps

---

### Post by Or'Enn on 2006-08-21
Thank you. This was very helpful :)

---

### Post by The Warlock on 2006-08-30
Hey, I know I'm bumping an old thread here, but does anyone know how to make those changes work with a second sound card? That .asoundrc stuff works with my onboard sound, but I'm trying to get stuff to play out of my SB Audigy 2NX, which (for whatever reason) doesn't do hardware mixing right, and so I can't have Gaim and amaroK work at the same time. When I try to put that in my .asoundrc file, it forces me to use the first sound card (crappy laptop speakers) instead of my good one, no matter what the sound card preference is set at.

---

### Post by xtknight on 2006-08-30
> **The Warlock said:**
> Hey, I know I'm bumping an old thread here, but does anyone know how to make those changes work with a second sound card? That .asoundrc stuff works with my onboard sound, but I'm trying to get stuff to play out of my SB Audigy 2NX, which (for whatever reason) doesn't do hardware mixing right, and so I can't have Gaim and amaroK work at the same time. When I try to put that in my .asoundrc file, it forces me to use the first sound card (crappy laptop speakers) instead of my good one, no matter what the sound card preference is set at.

Replaces all the zeroes in that above fix with ones instead (like dsp1)?  I'm not sure.

---

### Post by The Warlock on 2006-08-30
> **xtknight said:**
> Replaces all the zeroes in that above fix with ones instead (like dsp1)?  I'm not sure.

Nope. The settings must somehow be overriding the settings in .asoundrc.asoundconf, which sets the default sound card with:

!defaults.pcm.card NX
defaults.ctl.card NX
defaults.pcm.device 0
defaults.pcm.subdevice -1

---

### Post by Caislean on 2006-09-01
My problem is similar to this one, and is actually the only problem I had with any of the installation of ubuntu. Sound in firefox does not work for me at all under any circumstances, whether other sound programs are open or not, whether it is the first program I run (i made sure to boot once and try running firefox before I open and closed a sound program).

Sound works perfectly on all other programs, just not firefox.

---

### Post by Anonii on 2006-09-01
I will trully worship you like the Elder Gods, if you fix this too:

I'm using Banshee as the audio player, and the only sound engine available is Gstreamer . I dont know if I can make it use ALSA >:
 Like the thread creater, I'm getting no sound from videos in firefox, if I have another sound application open. 
Is there a way to fix this?

---

### Post by Caislean on 2006-09-01
I tried the fix posted at the beginning of this thread and it fixed the firefox sound problem, but sound doesn't work in any other programs. Is there a way to change the sound to asla system wide?

---

### Post by henriet on 2006-09-02
I think you're using Gnome, so go into System -> Multimedia System Selector. Then select output : ALSA in the audio tab.
This should make most of your applications use ALSA.

---

### Post by Hotaru on 2006-09-02
@henriet

Thanks! It works for me too! :)

---

### Post by mamillapalli on 2006-10-14
that was amazing.....

      I am newbie to linux Operating System. i was struggling to figure out why is that firefox is not playing audio when it is palying video. Thanks a lot for ur solution.:)  

can anyone help me out in getting acquainted with linux system as how OS is organised, where are the system files stored and all other required information. 

thanks in advance.

Regards,
Aditya Mamillapalli

---

### Post by afkun on 2008-04-27
Henriet and xtknight, you guys saved me with the first responses you each posted. I'm using Ubuntu Hardy Heron and have a Creative Sound Blaster Audigy SE (ca0106) sound card, and I did both of your tricks and that fixed Firefox and Opera's sound issues. For some reason I was only able to run sound from one program at a time to Audigy card (so VLC would get Audigy, Opera and Firefox at the same time got the onboard soundports).

Big thanks you everyone for posting.

---

### Post by dulbirakan on 2008-05-13
I am also using Hardy and I could not fix the problem. When I set Firefox's output to aoss I hear clicks from the speakers when firefox is working...

---

### Post by rOoNy911 on 2008-07-02
I'm just wondering where the .asoundrc file is and should be put in after you've created it. 

Thanks 
-rOoNy

---

### Post by tssge on 2008-07-10
Thank you henriet now my sounds working too :):):guitar:

---

