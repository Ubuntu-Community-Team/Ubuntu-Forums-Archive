---
title: "Internal Speakers won't mute. Dell XPS 2710"
date: 2012-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yinnus on 2012-12-16
I'm having an issue with the internal speaker not muting when speakers are plugged into the headphone jack.  if i unplug from the headphone jack and then plug in again it mutes.  but once i reboot it unmutes.

I've tried gnome-alsa-mixer.  it works until i reboot
I've tried hda-jack-retask.  it works even after reboot but not after a complete shutdown.

i'm on 12.10 with kernel 3.5.0-17-generic. and my card is a Realtek ALC275

any ideas?  maybe i need to put a new line in alsa-base.conf??

---

### Post by ohnonot on 2012-12-17
[http://ubuntuforums.org/showthread.php?t=1689548](http://ubuntuforums.org/showthread.php?t=1689548)
[http://forums.debian.net/viewtopic.php?f=7&t=77928](http://forums.debian.net/viewtopic.php?f=7&t=77928)

...i just made a quick search and this came up.
since they perfectly describe your problem and are marked as solved, i didn't even look into it.
if they don't help, lets dig some more together, otherwise thread tools->solved!

---

### Post by yinnus on 2012-12-17
thanks for the reply.

1.  everything in alsamixer is set as it should be with "speaker" muted. 

2.  with gnome alsa mixer speaker is on mute but for some reason automute mode keeps being unselected after shutdown and startup again.

3.  i have no idea the syntax for model in alsa-base.

options snd-hda-intel model=XXX.  XXX should be my model number but i have no idea what to put in.  dell2710?

hope to get some input from you soon.

Thanks again..

---

### Post by ohnonot on 2012-12-18
ok, this is very confusing.
first of all, there's a utility called gnome-alsamixer, not gnome-alsa-mixer.
then i don't know what hda-jack-retask is. where did you get it and why?
i found [this]("http://lists.freedesktop.org/archives/pulseaudio-discuss/2011-December/012342.html") info, it doesn't seem to apply to your problem.

a bit of unscientific and blurry explanation:
linux uses different sound architectures, alsa, jack, oss, pulseaudio.
i *think* pulseaudio doesn't work by itself but uses the underlying alsa architecture, which is closer to the hardware.
unity (and thus ubuntu 12.10) uses pulseaudio.
"jack" in this case does not mean your headphone jack but is the name of another sound architecture, mostly interesting for linux musicians.
in my opinion, jack should not come into the equation at all while trying to solve your problem.

> i have no idea the syntax for model in alsa-base.
options snd-hda-intel model=
how about > model=dell?

my system is quite different from yours so i can't give you any walkthroughs.
just be sure you always remember what you do and trace back / undo your steps.
otherwise you might make it worse.
in linux, YOU are the master of your computer.
if you are inexperienced i recommend you read the ubuntuforums link i've given, instead of the debianforum.

edit: not sure what the newest kernel is - are you sure your system's up to date?

edit2: i've seen forum posts asking for this:> Do you have CONFIG_SND_HDA_INPUT_JACK enabled in the kernel?- i guess in this case "JACK" really means your phone jack.

edit3: and fwiw [another forum thread]("http://forums.debian.net/viewtopic.php?f=7&t=79077") 

- but i think you should go with alsa-base.conf (or what was the name of that file?) first.

---

### Post by yinnus on 2012-12-18
sorry if i confused you.

i found this retask idea on another forum.

[http://askubuntu.com/questions/128099/restore-speakers-headphones-option](http://askubuntu.com/questions/128099/restore-speakers-headphones-option)

i have tried the alsa-base.conf suggestion you had but no change even tried dell-m3 and dell-2710 but still nothing.

this is sooooo frustrating.

---

### Post by ohnonot on 2012-12-19
ok i don't know if i can help you, i'm only just beyond noob... but there's other people on this forum probably reading your thread right now, waiting for some piece of information that would enable them to help you.

first of all apologies for *me* making all this even more confusing - i forgot to notice that your thread prefix is lubuntu.

i am myself not using lubuntu, but have debian lxde installed on another comuter - there's no pulseaudio installed. afaik, all lxde-distros use alsa only.
also the alsa-base.conf looks very much like on my other machine and there's no snd-hda-intel on either.

now before i can even try to help you, i have to make sure what you already did to your system.

did you have the problem from the start, since installing lubuntu?
what exactly did you install/uninstall/update since the problem started?
if you had it working first, and then it started to break, did you do sth, however unrelated it might seem, shortly before?

how does your /etc/modprobe.d/alsa-base.conf look NOW, and how did it look originally?

what other files did you edit?

is your system updating automagically? or, if not, did you make system updates/grades? when last time? no problems?
open synaptic and look if everything is up-to-date.

exact specs of your computer? how old is it?

that should be enough for starters...

edit: sorry again, i had a closer look at hda-jack-retask: it has nothing to do with jackaudio. however i still don't see how it could possibly help here.

---

### Post by yinnus on 2012-12-19
I have no idea why it says lubuntu.  i made sure this time around to select ubuntu.  i'm using 12.10 on kernel 3.5

This has been an issue since i got the computer.  it came with win 8 preinstalled and i have the same issue with it.  i can get the speaker to mute by uninstalling it, rebooting, and then using the fix hardware thing.

Yesterday i did a clean install so everything is factory.

---

### Post by ohnonot on 2012-12-20
> This has been an issue since i got the computer.  it came with win 8 preinstalled and i have the same issue with it.i think that's very important, that you had it with the preinstalled windows, too.  Maybe you should take a look in the bios.> i can get the speaker to mute by uninstalling it, rebooting, and then using the fix hardware thing.sorry, i didn't understand that. at all. uninstalling what? and what fix hardware thing?> Yesterday i did a clean install so everything is factory.so now you have ubuntu only, no windows on another partition? 12.10 with unity desktop? installed with a network connection, so everything is up to date now?

anyhow you should be looking for forum threads on the windows side, too.
maybe it will help you get closer to the answer.

you know, from what i gather from your descriptions, you're really gonna have to get much deeper into that.
if you want to continue this here, there's still plenty of unanswered questions in my previous posts.
good luck.

---

