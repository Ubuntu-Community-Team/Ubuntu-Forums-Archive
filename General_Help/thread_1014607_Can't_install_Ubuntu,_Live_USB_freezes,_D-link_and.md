---
title: "Can't install Ubuntu, Live USB freezes, D-link and ACX driver??"
date: 2008-12-18
forum: General Help
---

### Post by chenguo4 on 2008-12-18
I'm trying to install Ubuntu on my friend's computer. He has a D-link AirPlus DWL-520+, which I think is the source of the problems here.

I made a live USB from system -> administration, checked it's integrety. On install, if I do Ctrl+Alt+F1, an error message shows up that's something like

main: error loading /lib/firmware/acx/default/tiacx100c0D for device something something.

So it continues loading, and it actually boots to the CLI. But after about 10 seconds, a crap load of error messages pop up and the system just kinda stops. All the messages have to do with ACX, like

acx_l_process_mgmt_frame+0x361/0x5d0 [acx]
or 
acxpci_i_interrupt+0x20b/0x320 [acx]

The last few lines are like "native_safe_halt," "default_idle," "cpu_idle," and "rest_init," which I assume makes the computer sit there and do nothing, essentially freezing it.

End it spits out one last line telling me the trace has ended, and the system's essentially frozen.

If anyone can help with this that'd be great. Thanks in advance!

---

### Post by Polygon on 2008-12-18
hmm, it might just be a problem resulting from running ubuntu from a usb key. have you tried it with a real live cd?

the error means it cannot load the firmware, most likely for the wireless card, and the other errors look like its trying to recover, but it can't and just freezes. 

I have a dwl-g520 (without the +) and it works fine.....so in theory the + version should also work fine as well

---

### Post by chenguo4 on 2008-12-18
I used a LiveCD like you said and now it installed fine, and the card detects wireless networks. But it can't connect to them, so I suppose this is now a D-link driver issue.

Polygon, did your D-link work out of the box, or did you do something special to enable it? Thanks in advance.

Also, forgot to mention... What version are you running? The live USB I tried was 8.10, but the live CD was 8.04. Is this problem fixed with Intrepid, like certain broadcom cards?

---

