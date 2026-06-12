---
title: "dvi &gt; vga results in blank screen."
date: 2009-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by -Q- on 2009-01-22
Dear people,

For my first real post :) I want to ask you all for help in the last step of finishing my ubuntu 8.10\xbmc media center. All works well now, en while I hooked op my Dell SX270 to my Samsung LE32A436 i found out that the Dell didn't support vga.....
Went to the shop and bought me a brand new DVI > VGA-cable. And where my xbmc worked fine on my monitor....it didn't work on my tv....
I see the Dell picture..and the grub...but no ubuntu or media center.....
Is there anybody who knows the answer to this problem?

thanks in advance,
-Q-

---

### Post by Paegus on 2010-08-14
Am having the same problem here. Everything seems to be working fine except that the screen goes no signal. I think it's an output setting issue of some kind myself...

so just our of curiosity, have you manager to resolve this yourself?

---

### Post by Lencons on 2011-07-05
Bit of a bump.

I am experiencing the same problem with 10.04LTS on this machine.

Boots into single user mode ok, but normal boot is doing something with the video driver that makes it drop signal.  Have played with settings in /etc/default/grub but nothing at this stage.

- David.

---

### Post by Paegus on 2011-07-07
I've sort of solved it on my box with adding "nomodeset i915.modeset=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/defaults/grub and then adding...

```
$ nano ~.drirc
<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```
 
 Hope that helps

---

