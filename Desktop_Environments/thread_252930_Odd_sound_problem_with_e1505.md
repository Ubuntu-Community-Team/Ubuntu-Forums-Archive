---
title: "Odd sound problem with e1505"
date: 2006-09-07
forum: Desktop Environments
---

### Post by hunter186 on 2006-09-07
I've got a Dell e1505, running Dapper.  It's been a great linux computer for the most part, but I've had a strange problem with the sound for several months.  Every 5th or 6th time I boot the machine, I have no sound.  This applies to every application.  Restarting X has no effect, but restarting the entire machine fixes it.  Not even sure where to start looking on this one, because I haven't been able to consistantly reproduce the problem.  Maybe a hardware issue, but I don't know.  Any help would be great.

---

### Post by hunter186 on 2006-09-14
bump

---

### Post by NTolerance on 2006-09-18
I have had this same issue with my E1505.  I installed the 2nd Edgy alpha release and haven't experienced the sound problem, but Edgy doesn't like to cleanly startup/shutdown most of the time, so I can't use it.  I really want to run Ubuntu but this issue is frustrating.

FYI, I also installed Mepis 6 and didn't have any sound problems.

---

### Post by hunter186 on 2006-09-20
I recently reinstalled dapper stable on the laptop and have noticed this sound problem again.  I suppose it's minor as it usually works, but it seems like such a strange problem.

---

### Post by NTolerance on 2006-09-20
Which kernel are you running?  I'm running 2.6.15-27-686.

---

### Post by jamesrl on 2006-09-22
I've had the same problem with audio; works intermittently on Dell e1505.  Running 2.6.15-27-686 SMP.  Months ago was running breezy (and probably not SMP) and don't remember this problem coming up, though its gotten annoying lately.  I've noticed it occurring often after coming back from hibernation (and or screensaver).

A reboot only sometimes corrects the problem.  Also I have a dual boot into windows XP and have noticed some problems along the same line (having to reboot to get sound), but browsing the help at Dell has been of no use.  I use Win XP much less often and the only times I've noticed problems with sound, is when I soft-reboot out of linux to go into windows after experiencing problems in linux.  

When its not working through the external speakers, it seems if I have the volume maxed out, I can hear a very very faint sound (of what should be playing) if I have my ear right up against the speaker.  If i put a plug into the headphones this goes away (found by plugging in external speakers that were turned off, or if I lower the volume level it goes away proportionally.

Very strange indeed.

Also doing /etc/init.d/alsa-utils restart
doesn't do anything.  I've read an old discussion 

[http://www.ubuntuforums.org/archive/index.php/t-190167.html](http://www.ubuntuforums.org/archive/index.php/t-190167.html)

Finally for what its worth, when the sound is "not working" through the internal speakers, there is a very faint signal coming from the speakers that I can hear if inI can hear very very faint audio coming out of the speakers when the volume is maxed

---

### Post by ysr on 2006-09-24
> **jamesrl said:**
>  When its not working through the external speakers, it seems if I have the volume maxed out, I can hear a very very faint sound (of what should be playing) if I have my ear right up against the speaker. Can you pls post the contents of your /var/lib/alsa/asound.state when this happens. (Have just started investigating this problem on my laptop, and would be interesting to see what the contents are...)

> **jamesrl said:**
> Also I have a dual boot into windows XP and have noticed some problems along the same line (having to reboot to get sound), but browsing the help at Dell has been of no use. Does this happen quite often? In which case, I might be following the wrong lead, since linux config files wouldn't have anything to do with windows sound behaviour, but any case do post your asound.state file when the problem occurs.

---

### Post by pteja on 2006-09-25
I have the same problem on my Sony VGN-FE21B. I need to restart to get sound. Sound stops working suddenly - Totem & XFmedia simply freeze.

I am using version 6.06.

My VMWare installation (XP) cannot find any sound recording or playback devices at all (also when host (Ubuntu) sound works.

---

### Post by ysr on 2006-09-25
> **ysr said:**
> Can you pls post the contents of your /var/lib/alsa/asound.state when this happens. (Have just started investigating this problem on my laptop, and would be interesting to see what the contents are...)

Today (after a long break), I had one of those episodes of no sound on reboot. After multiple attempts at manually editing the /var/lib/alsa/asound.state and running the "/etc/init.d/alsa-utils restart" to reload the driver configuration from the asound.state file, I miraculously had my sound back. Only problem is that I did not back up my asound.state file at regular intervals, so don't know which change exactly it was that brought the sound back.](*,) The next time this happens, I will make sure I keep track of each of my changes, and if I succeed in producing a recipe that works consistently (fingers crossed), I will post it.

---

### Post by jamesrl on 2006-10-12
So it stopped happening for a while (or at least I didn't notice it happening or had time to deal with it when it did), but the sound problem reemerged.  Again, I can faintly hear the sound if my ear is to the speaker and the volume is maxed out, and it is a loud song.  Now I just looked at my /var/lib/alsa/asound.state file and it has really weird values:

> 
state.Intel {
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Master Playback Volume'
                value.0 7
                value.1 7
        }
EDIT: Snipped irrelevant part out; also this part is attached as a file in my next post.
}


I'm going to try and manually edit out the values that consist of approximately 350 consecutive 0's appended to a reasonable looking value and see if it works.


Btw, the spaces that put the zeros into groups of 50 is some artifact of posting it here, and is not in the actual file.

---

### Post by jamesrl on 2006-10-12
Manually editting out the long 0s didn't work, and in fact they should be there.  However, I eventually rebooted and it worked from the start (as opposed to the previous fresh boot from being halted over night where the sound didn't work).  The only difference in the working asound file and the old asound.state file was 

> 
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Master Playback Volume'
                value.0 7
                value.1 7
        }

where in the working one after reboot when it randomly worked,
value.0  and value.1 both have values of 30.

I did have the volume maxed out (according to the buttons in the front and ubuntu's gui graphic).  In the past I have also checked with the alsamixer and it also showed volume maxed out with no sound, though I didnt this time.

The current file (asound.state) and the old file (asound.state.old) are attached.  

Note: I also made some changes adding the text from Debugging Sound Problems about software mixing [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")
but I think the main difference is the change in the volume from 7 to 30 that occurred after reboot.

---

### Post by TheGoshem on 2006-10-23
Heres my asound.state > state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Playback Volume'
		value.0 19
		value.1 19
	}
	


Please note the problem HAS occured with this particular one.

---

### Post by TheGoshem on 2006-10-23
And upon rebooting, ahh working sound!

> state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		iface MIXER
		name 'Master Playback Volume'
		value.0 54
		value.1 54
	}

---

