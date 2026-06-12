---
title: "Ring switcher (in compiz) now requires pressing Enter to select"
date: 2012-04-11
forum: Desktop Environments
---

### Post by msundman on 2012-04-11
The ring switcher used to select the focused window when releasing the key, but now when I release the key the ring just stays there on screen and I have to press Enter for it to acknowledge my selection.

Is there any way to make it work like it used to (and like pretty much all other window switchers do)?

---

### Post by msundman on 2012-04-11
Btw, I'm running precise.

Also, if my description was inadequate:
1. My "Next Window" keybinding is "<Super>Tab".
2. I press and hold down 'Super'.
3. While holding down 'Super' I'm pressing 'Tab' until my terminal window is focused.
4. I'm releasing 'Super'.
5. Now the ring switcher should close and select my terminal window, but nothing happens!
6. I have to press 'Enter' for the ring switcher to close and select my terminal window. :(

---

### Post by sparhawkthesecond on 2012-05-10
Hi, not sure if this is solved yet, but [this]("http://ubuntuforums.org/showthread.php?t=1966852") might be related?

---

### Post by msundman on 2012-05-10
Changing the key for the launcher did indeed solve this for me. However, I would like to use the <Super> key for the launcher as well, but at least now I know where the bug is. Thanks!

---

### Post by sparhawkthesecond on 2012-05-10
You might also be seeing [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/995885"). I'm finding Unity quite frustrating at the moment!

---

### Post by bigbig999 on 2012-05-13
I have the same problem, I'm trying to use Compiz ShiftSwitcher with <Super><Tab> & <Super><Shift><Tab>. I first disabled the conflicting entries in the Unity Plugin then enabled ShiftSwitcher. I can change the windows fine, but I got to press enter or click with he mouse to select the window to focus on.

I don't get how you fixed this problem, please explain in detail.

Thank you very much.

---

### Post by sparhawkthesecond on 2012-05-13
I'm not sure, I just came across both threads while googling something unrelated. Perhaps msundman can help you, or you could try posting in the original (linked) thread.

---

### Post by brunobliss on 2012-06-01
I'm having this problem as well,

Shift Switcher behaviour should be:

SUPER+TAB to display cover mode, tapping TAB (while holding SUPER) to switch between applications. Release SUPER to focus on selected application.

Current status is:

SUPER+TAB enters shift swticher's cover mode and it stands there. Pressing SUPER+TAB or enter will close it and focus on the selected application.

---

### Post by sparhawkthesecond on 2012-06-01
> **brunobliss said:**
> I'm having this problem as well

Did you read the thread I linked above?

---

### Post by msundman on 2012-06-04
IIRC I just selected Ubuntu Unity Plugin and changed the "Key to show the launcher" from "<Super>" to "<Alt><Super>" and then it started working.

---

