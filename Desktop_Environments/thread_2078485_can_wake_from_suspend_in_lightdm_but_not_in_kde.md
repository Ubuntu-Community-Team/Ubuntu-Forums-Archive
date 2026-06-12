---
title: "can wake from suspend in lightdm but not in kde"
date: 2012-10-31
forum: Desktop Environments
---

### Post by elguavas on 2012-10-31
hi there,

at the lighdm login screen i can successfully sleep my pc (suspend to ram)  and once it's asleep pressing any keyboard key will wake it up again, as expected.

however, once i am logged in to kde, i can sleep the pc, but once it's asleep i cannot wake it up again!! :(

pressing any keyboard key or the power button or a mouse button all do nothing, the pc stays asleep...

i have 'lock with a password when waking from suspend/sleep' turned off.

the only way to recover from this 'sleep of doom' is to hit the reset button... :( :(

so, why does waking from sleep work fine in lightdm but not when logged in to kde??

any help much appreciated.

---

### Post by elguavas on 2012-10-31
ehh, if i don't get any replies on this i guess i'll need to file a bug report...

just i know what a long row to hoe that can be, so i was hoping someone could at least point me in the direction of debugging the problem.

---

### Post by elguavas on 2012-11-30
just noting my findings here in case anyone searches this thread.

i found that the problem occurred in any 'heavyweight' desktop environment, but not in light wm environments like fluxbox... eventually i narrowed it down to being caused by pulseaudio.

without pulseaudio running my system suspends and wakes faultlessly, with pulseaudio the problem originally described occurs.

i'm now happily running kde _without_ pulseaudio (just plain alsa) and all sound works as expected and also the system suspends and restores without a hitch. :)

what a useless piece of junk pulseaudio is. :mad:

---

