---
title: "suddenly no sound anymore"
date: 2005-05-13
forum: Desktop Environments
---

### Post by ubuntu_demon on 2005-05-13
Hi,

When I booted my system in Ubuntu this afternoon it seemed to have stopped booting somewhere during LVM starting up. I disconnected my webcam (because it wasn't connected before) and waited a bit. Then I pressed ctrl-alt-delete and after a little while the system rebooted. It booted into ubuntu with no problems except that my sound stopped working.

I ran fsck in recovery mode. By typing just :
$sudo umount -a
$sudo fsck 

turned out .... the sound was just muted. I didn't check because I know I didn't mute the sound. For some reason it got muted. :-P

---

