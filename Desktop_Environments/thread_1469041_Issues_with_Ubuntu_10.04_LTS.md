---
title: "Issues with Ubuntu 10.04 LTS"
date: 2010-05-01
forum: Desktop Environments
---

### Post by mariolopezjr on 2010-05-01
It seems that when I adjust the volume with the volume wheel on the side of my notebook, the OS messes up. Nothing is clickable, I cannot type anything, in order to get a working computer again I have to hard reset it.

Why is this happening? I have never experienced this. I have a Toshiba Satellite that I recently installed Ubuntu on. Does anybody have a solution?

Thanks for your time,
Mario Lopez

---

### Post by MooPi on 2010-05-01
I cannot comment on your laptop or problem specifically. I have heard anecdotal posts suggesting the volume control being set low in Windows and corespondingly difficult to adjust under Linux. The solution was to boot into Windows set volume at highest desirable level then boot back to Linux. You haven't mentioned if your dual booting so maybe this is worthless info.

---

### Post by mariolopezjr on 2010-05-01
> **MooPi said:**
> I cannot comment on your laptop or problem specifically. I have heard anecdotal posts suggesting the volume control being set low in Windows and corespondingly difficult to adjust under Linux. The solution was to boot into Windows set volume at highest desirable level then boot back to Linux. You haven't mentioned if your dual booting so maybe this is worthless info.

Any information is not worthless information because it can help out anybody.

I am not dual booting so that does not apply to me. Anybody else have anything to add?

---

### Post by tgalati4 on 2010-05-02
Open a terminal:

xev

(turn the volume knob)

Post what the key is mapped to.

---

### Post by mariolopezjr on 2010-05-02
The CMD windows outputs this:

KeymapNotify event, serial 36, synthetic NO, windows 0x0,
keys: 2 0 0 0 0 0 0 0 0 0 0 0 0 0 0 4
      0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

FocusOut event, serial 36, synthetic NO, windows 0x4200001,
mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 36, synthetic NO, windows 0x4200001,
mode NotifyWhileGrabbed, detail NotifyNonlinear


So....? Hmmm....? Very detailed yes.

---

### Post by tgalati4 on 2010-05-02
This is what I get with a thinkpad t43p using the volume up button:

MappingNotify event, serial 42, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

But only for the first press.  Successive presses don't show up--probably because they are handled directly by the BIOS and don't go through the operating system.

That could be the issue in your case, the BIOS handles the volume control and due to a bug it causes the OS to freeze.

Is this machine dual boot?  If so, does the volume control work in Windows?

Look in the BIOS for any switches (like support legacy USB devices).  It could be that the volume control is really a USB device.

Look for errors in your dmesg:

dmesg | more       (spacebar to go forward, q to quit)

Look for any messages that relate to either USB or to conflicts with keymapping.

---

