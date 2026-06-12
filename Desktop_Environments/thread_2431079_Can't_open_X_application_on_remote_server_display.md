---
title: "Can't open X application on remote server display"
date: 2019-11-11
forum: Desktop Environments
---

### Post by ajkessel on 2019-11-11
I am connecting via ssh to a remote Ubuntu 19.10 system and attempting to open X applications locally on that system's display. This is not an ssh/X forwarding issue -- I don't want applications to open locally on my client -- but rather on the display of the user that is already logged in on the remote system.

When I connect to the remote system as a user [let's say 'username'], I see that username is already logged in and `who` indicates its display is :0:

```
# who
username     :0           2019-11-11 10:56 (:0)
```
But the following does not work to open a local application:
```
# export DISPLAY=:0
# xclock
```
It gives the error:
```
No protocol specified
Error: Can't open display: :0
```
I've tried "xhost +", which gives the same error. I've added "DisallowTCP=false" to the [security] section of /etc/gdm3/custom.conf. No difference. I've also tried "export XAUTHORITY=/home/username/.Xauthority" and experimented with various "xauth add :0 . hexkey" type commands. I have also tried disabling and enabling wayland in the GDM conf. If I add "Enable=true" to the [xdmcp] section of gdm conf, I still get the "can't open display" error, but not the "no protocol specified" error. In summary, no matter what I do, I always get the same errors trying to run an X application locally.

I've also tried opening an application from the text console on the remote computer with the same method (export DISPLAY=:0) and I get the same error, so it doesn't appear to be specifically related to the ssh login method.

I note that user gdm is running gdm-wayland-session, and user username is running gdm-x-session as well as /bin/bash /etc/gdm3/Xsession. I suspect this issue has something to do with how gdm is managing the display but have not found any solution.

Any suggestions for how to fix/troubleshoot?

---

