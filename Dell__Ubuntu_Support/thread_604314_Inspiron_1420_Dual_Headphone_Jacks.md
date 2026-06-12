---
title: "Inspiron 1420 Dual Headphone Jacks"
date: 2007-11-06
forum: Dell  Ubuntu Support
---

### Post by MikeRussell on 2007-11-06
Hey all,

    I've got an issue that I can't find an answer to by googling...  I've got an Inspiron 1420 with the Sigmatel 9228 (uses the intel-hda codec).  This laptop cam with Vista, which I promptly wiped and replaced w/ Gutsy.  I've got everything working fine, but I am struggling to get both front headphone jacks working.  Does anyone have these both producing output?  I've tried adding "option snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base.  It might be worth adding that I have followed the steps on the Dell Ubuntu wiki to allow sound after resuming from suspend.  Sorry if this fix has been posted elsewhere, but I can't find it...   Any ideas would be greatly appreciated.  Thanks!
Mike

---

### Post by carnagex420x on 2007-11-06
I have the same situation, after a bit of searching i  around a couple post that just simply said its not supported. There are suppose to be Dell DMKS support soon but no real help yet.

---

### Post by deserthowler on 2007-11-06
I know this is no real help, but I have a 1420n with Ubuntu preinstalled and both jacks work for me.  One plays headphone only and the other plays headphone/internal speakers simultaneously.

Earl

---

### Post by carnagex420x on 2007-11-06
I had to look on a Dell 1520 forum to get my sound card to be able to play sound from two applications at once. But even after that fix i still only have 1 out still.

---

### Post by MikeRussell on 2007-11-07
So the closest I've been able to come (and it's a terrible 'solution') is as follows:  I've manage to at least somewhat enable a second channel by enabling mic as output.  Right clicked on the volume applet and selected "Open Volume Control" then Edit--> Preferences.  Checked 'Mic as Output' then 'Input Source'.  Clicked the tab that says 'Switches" and turned on 'mic as input', then clicked the tab that says 'Options' and changed mic input to 'Front Mic' (may or may not be necessary).  This enables the Mic output to be use as a (somewhat crappy) headphone jack.  Plugging headphones into this jack does not mute the speakers (although if you have someone also listening on the main headphone jack this should happen anyhow).  The real drawback of this 'hack' is that the output is (for now) in MONO.  If anyone can improve upon / fix this please let me know.  Cheers.
Mike

---

### Post by flowbot on 2007-11-07
Here's how to do it:

1. From a terminal, issue this command: **alsamixer**.
2. Make sure **Master**, **PCM**, **Front**, and **Surround** are all unmuted and the volumes up.
3. Use the arrow key to move across to the **Line In as Output** channel and press the '**m**' key on your keyboard to unmute it.
4. You should now get sound out of your second headphone jack.
5. From here, you can use the **Front** channel to control the laptop speakers (or first headphone jack), and the **Surround** channel to control the second headphone jack - ie, if you want only sound out of the second headphone jack, then mute the **Front** mixer channel.

Here's what my alsamixer looks like when I have sound coming out both the laptop speakers and the second headphone jack:

[[img]http://i188.photobucket.com/albums/z30/gnuworld/screenshots/Alsamixer.png[/img]](http://s188.photobucket.com/albums/z30/gnuworld/screenshots/?action=view&current=Alsamixer.png)

---

### Post by MikeRussell on 2007-11-07
Thanks Flowbot!  Worked like a charm...

---

### Post by carnagex420x on 2007-11-07
SWEET! now the only thing that doesnt work is my media keys!:D THANX

---

### Post by rkj90266 on 2008-01-12
Hey that really does work.  Does that mean that the second headphone jack can also be used as a line in? If so, how do you set the "Input src" to be "Line in" instead of "Mic"? Or, does it just record from both? (Haven't tried that)?

---

