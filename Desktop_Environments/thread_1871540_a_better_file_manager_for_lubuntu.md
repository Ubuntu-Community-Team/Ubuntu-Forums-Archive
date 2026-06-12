---
title: "a better file manager for lubuntu?"
date: 2011-10-29
forum: Desktop Environments
---

### Post by daniel227 on 2011-10-29
hello,

i don't like pcmanfm because it can't create shortcuts/links.

i replaced it with thunar, quite succesfully, but pcmanfm starts up automatically and still manages the desktop (if i kill the pcmanfm process the desktop icons disappear)

searching around on that i'm not so sure if thunar is the right choice with lxde?

is it possible to get thunar managing the desktop (and tell lubuntu not to start pcmanfm anymore)?

thx,

daniel

---

### Post by MG&amp;TL on 2011-10-29
You could try "default applications".

Anyway, see here:

[http://forum.lxde.org/viewtopic.php?f=8&t=533]("http://forum.lxde.org/viewtopic.php?f=8&t=533")

---

### Post by amjjawad on 2011-10-29
2 Seconds on Google Search, 4th result: [http://ubuntuforums.org/showthread.php?t=1463588](http://ubuntuforums.org/showthread.php?t=1463588)

---

### Post by daniel227 on 2011-10-30
@MG&TL:

thx, but the solution is far too user-unfriendly...

anyway, thunar does manage my files 100%, but pcmanfm still manages my desktop.

@amjjawad:

2 seconds? man you're fast. however chatting's nice, too, isn't it?

i tried the things suggested in the post you linked. the gconf thing did nothing, the script override finally yielded results - desktop stays black, no icons, no background. pcmanfm is not running, but neither is thunar.

_____________
my conclusion:
thunar does not manage the desktop, at least not under lxde. right or wrong?

asks daniel.

---

### Post by 3Miro on 2011-10-30
If you don't want pcmanfm to manage your desktop, you will need something else to do that. I know nautilus can do that and I think Compiz can draw background wall-paper instead of blank screen. Both of those are somewhat heavy. 

Thunar doesn't manage the desktop, xfce uses xfdesktop for that purpose. You can try to run xfdesktop in start to see if this gives you what you want. I am not sure of potential side effects.

---

### Post by amjjawad on 2011-10-30
> **daniel227 said:**
> 
@amjjawad:

2 seconds? man you're fast. however chatting's nice, too, isn't it?
I was referring to the time I spent to type that on Google Search and got some result. Nothing personal, please don't be offended :)


> i tried the things suggested in the post you linked. the gconf thing did nothing, the script override finally yielded results - desktop stays black, no icons, no background. pcmanfm is not running, but neither is thunar.
I must do some tests and get back to you. I've never needed to replace the file manager but it would be so interesting to know how to do that.

> my conclusion:
thunar does not manage the desktop, at least not under lxde. right or wrong?You need to understand that there is Desktop Manager/[Desktop Environment]("http://en.wikipedia.org/wiki/Desktop_environment"), there is [Window Manager]("http://en.wikipedia.org/wiki/Window_manager") and There is [File Manager.]("http://en.wikipedia.org/wiki/File_manager")
[Thunar]("http://en.wikipedia.org/wiki/Thunar") is a File Manager.

Differences between Thunar and PCManFM?
Have a look at [http://lxde.org/](http://lxde.org/)

---

### Post by daniel227 on 2011-11-01
thx to all, good answers, if i may say so.
right now i'm thinking to change to a different distro altogether so the whole thing's on ice.
anybody know about real-time kernel patch for lubuntu? dvd playback is chunky, could that help?
also i haven't found any way to change priority for processes, the taskmanager just shows 0 for everything regardless of my attempts to change?

just to keep the chat going... i know i could have googled allthis ;-)

---

### Post by cryptotheslow on 2011-11-01
Have a look into the hpet (high precision event timer - I think) kernel flag option.

It's just some rusty memory I have of problems I encountered with shoutcast DJ'ing on v9.10 with JACK getting itself all tied up and doing weird buffering and skipping when re-sampling tracks between bitrates. Cured by just adding the hpet option to the grub config for the boot options.

Just an avenue for investigation. hpet comes with a trade-off on system overhead. The problem didn't happen on 10.04 so the solution has been consigned to the great hangover in the sky unfortunately. I just seem to remember that the pro-type AV / Audio processing setups tend to use hpet as well as realtime.

Sorry - it's a kind of hazy memory :D

---

### Post by daniel227 on 2011-11-05
hm. thanx for that.
seems to be beyond me and i haven't found a how-to.
however i changed distros now and at least things are working normally now. choppy dvd playback remains, though it's much better in mplayer (i had this problem with vlc under windows, too: it seems to eat quite some cpu) - i'm gonna have to keep looking for ways to tweak my system.
anyway i should start a new thread on this.
greetings,
d.

---

### Post by amjjawad on 2011-11-05
> **daniel227 said:**
> however i changed distros now and at least things are working normally now. 

Good luck with the new one :)

---

