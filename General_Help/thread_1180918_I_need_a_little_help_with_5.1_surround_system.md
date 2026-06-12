---
title: "I need a little help with 5.1 surround system"
date: 2009-06-07
forum: General Help
---

### Post by Pobednik on 2009-06-07
):P I am Pobednik, and I have a little problem with my 5.1 surround system. I was using Windows XP before and there was no problem with my speakers, but when I was installed Ubuntu 9.04 Desktop edition, there were no sounds. I have found the problem, and now the left and the right speaker is good, but the subwoofer, the center speaker, and the back speakers doesn't work. How can I resolve the problem? If you can help me please contact with me.
By the way, I have another problem. I have Mustek BearPaw 2400 CC Plus scanner, but when I put it in the computer, it can't recognize it, and when I installed the driver with WINE windows emulator, thats not helped. So if you can help me, please help, because I will have excercise and I want to make cribs :D
Forward thanks.

---

### Post by Chris Musampa on 2009-06-07
I created a .asoundrc in my home directory and added the following:

```
pcm.!default {
    type             plug
    slave.pcm       "softvol"
    hint {
        show on
        description "All (softvol)"
    }

}

pcm.softvol {
    type            softvol
    slave {
        pcm         "ch51dup"
    }
    control {
        name        "All"
        card        0
    }
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
#    ttable.0.4 0.5
#    ttable.1.4 0.5
    ttable.1.5 0.5
    ttable.1.5 0.5

}

```
(the to commented lines would add center speaker which I didn't want).


I use Kubuntu though and route all phonon output to the above not sure how well that would work under gnome with pulseaudio.

---

### Post by Pobednik on 2009-06-07
Hi. I can't find .asoundrc file. Where is it? It isn't in my /home folder. It starts with /.cache folder, and there is no that file.

---

### Post by Chris Musampa on 2009-06-07
If it doesn't exist then you would need to create it:

gedit ~/.asoundrc 

then paste from the first post and save.  I had to restart alsa, play a sound through the newly created channel and then reboot before the new 'All' control showed up in the mixer.

As I said I don't know if it will work under Gnome but if it doesn't work then just delete .asoundrc and you should be back where you started.

---

### Post by VCoolio on 2009-06-07
Don't make the same mistake as I did and start configuring .asoundrc to get mpd working 5.1. Mpd is a system daemon and uses /etc/asound.conf, so as soon as other media players work copy .asoundrc to /etc/asound.conf (if you use mpd or its clients like sonata, otherwise it's not necessary).

---

