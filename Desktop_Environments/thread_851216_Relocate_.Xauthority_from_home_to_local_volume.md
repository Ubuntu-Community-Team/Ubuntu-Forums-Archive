---
title: "Relocate .Xauthority from /home to local volume"
date: 2008-07-06
forum: Desktop Environments
---

### Post by zihafiz on 2008-07-06
In our network consisting of 8.04 machines (i386,AMD64,SPARC), the /home/.Xauthority file routinely gets messed up upon ssh -X to another machine in the network ("no protocol specified", workaround: ssh -X localhost will regenerate ~/.Xauthority). This is due to lack or broken locking of the /home/$USER/.Xauthority file (and /home/ is mounted via nfs3). Exporting the home directories with sync instead of async solves the problem but totally destroys performance. 

For that reason I want to relocate the .Xauthority file to a local volume: i.e. /tmp/${USER}/.Xauthority

I tried by adding a file /etc/X11/Xsession.d/28setXAUTHORITY
containing


[ -d /tmp/${USER} ] || mkdir /tmp/${USER}
export XAUTHORITY=/tmp/${USER}/.Xauthority
touch $XAUTHORITY

with the result that X does not start any longer.

What is the canonical way to relocate .Xauthoriy? Suggestions? Thankful for input!

---

### Post by tormod on 2008-07-06
If you are using gdm, see the comments above "UserAuthDir" in /etc/gdm/gdm.conf

HTH, Tormod

---

### Post by zihafiz on 2008-07-07
Thanks for the hint. I was previously using kdm and now switched to gdm and it does solve half of my problem.

I set UserAuthDir=/tmp and now I have the initial Xauthority on my local volume. However, when I do an ssh -X somehost, the Xauthority will be generated on the nfs volume again. A second, cascaded, ssh -X will ruin the Xauthority once more.

I assume that /etc/profile.d/ or the .ssh/environment file is the next spot for action.

---

### Post by zihafiz on 2008-07-07
Thanks for the hint. I was previously using kdm and now switched to gdm and it does solve half of my problem.

I set UserAuthDir=/tmp and now I have the initial Xauthority on my local volume. However, when I do an ssh -X somehost, the Xauthority will be generated on the nfs volume again. A second, cascaded, ssh -X will ruin the Xauthority once more.

I assume that /etc/profile.d/ or the .ssh/environment file is the next spot for action.

---

