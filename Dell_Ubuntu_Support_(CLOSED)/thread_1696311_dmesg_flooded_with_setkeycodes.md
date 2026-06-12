---
title: "dmesg flooded with setkeycodes"
date: 2011-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tyraen on 2011-02-27
Hi folks,

I have tons of lines like this in my kernel log:
[ 1059.992925] atkbd serio0: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
[ 1059.992938] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.

I know that it is because the BIOS is notifying me that "The AC adapter cannot be identified", but I want to stop it somehow. I can run the command suggested and have it stop showing in the logs, but I'd like to have those key release messages ignored completely.

And I think those solutions are distinct; ever since this started happening, I occasionally get weird pauses in my typing, missed keys, and pauses in cursor movement that I think are caused by those key events flooding the keyboard interrupt handler.

Maybe I'm way off base, but anyone have any ideas where to start? If I can't have those thrown out, where can I drop a script to execute the setkeycodes on each reboot?

Thanks.

---

