---
title: "Steam - Game sounds work, except when I launch from Big Picture Mode"
date: 2013-11-11
forum: Gaming &amp; Leisure
---

### Post by MrBackhand on 2013-11-11
I am running Mythbuntu 12.04 LTS as a HTPC.  The video card is a NVidia 610 which has a HDMI connection out to my 7.1 receiver.  I installed Steam and was having problems getting any sounds to use the HDMI connection until I came across this post [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/) and followed the instructions to stop Pulse:

echo autospawn=no > ~/.pulse/client.conf
pulseaudio -k

then created /etc/asound.conf with the following:

pcm.!default {
    type plug slave.pcm {
        type hw card 1 device 3
    }
}

Now my games have sounds through the HDMI, and Big Picture Mode also has sounds, except when I launch games from BPM they do not have sounds. When I exit the game the sounds return in BPM.  I suspect I need to configure dmix in /etc/asound.conf but I am unsure exactly how, or where, in asound.conf I should do that.  I have found several solutions online but their asound.conf seemed a bit more complicated that my simple 3 line config. Anyone know how I can add dmix into my config?

Thank you

---

### Post by DanglingPointer on 2013-11-11
Mate try Steam Support!  They usually get back to you within 24hours.

---

### Post by MrBackhand on 2013-11-11
I finally solved it by looking at [http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc) and copying the code from the dmix header, pasted it into my asound.conf, and changed the pcm "hw:1,0" to [COLOR=#000000][FONT=monospace]pcm "hw:1,3".  I also removed the ctl.dmixer section as I did not need that.  Now, when I launch a game from Big Picture Mode they have sounds.

[/FONT][/COLOR]

---

### Post by DanglingPointer on 2013-11-11
Oh that's great!
Perhaps set the title to solved as I'm sure there will be others out there with similar issues which could use your solution.

---

