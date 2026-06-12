---
title: "Intel audio problem"
date: 2009-04-19
forum: General Help
---

### Post by deusxechelon on 2009-04-19
Ive googled and googled and googled and cannot come up with a solution. I have no sound, but if i blow into the microphone, I can hear it on the speakers. I attempted to follow the guide here on the forums: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)  but it appears to not apply to me. Any ideas would be appreciated!

System board:
P5Q SE Plus w/ On board Audio

uname -r
2.6.24-23-generic

cat /proc/asound/card0/codec#* | grep Codec
Codec: VIA ID 397

aplay -l
Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
Subdevices: 1/1
Subdevice #0: subdevice #0

asoundconf list
Names of available sound cards:
Intel

lspci -v
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
Subsystem: ASUSTeK Computer Inc. Unknown device 82fe
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

---

