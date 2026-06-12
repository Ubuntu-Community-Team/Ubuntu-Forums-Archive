---
title: "TTY startx"
date: 2014-08-10
forum: Desktop Environments
---

### Post by Andy_Crowd on 2014-08-10
Hi!
AlsaMixer doesn't work if window manager doesn't start in the same TTY. How can I start window manager in the same tty. Now when I am in tty1 and the X starts on tty7. I want start from tty1 and X must run in the same tty. 

1) I found a part of solution workaround: «xinit -- vt1» if I start from tty1 then X will run on tty1, «vt» option is for choosing of tty.

2) Work for any tty by getting and using current:
$ xinit -- vt$(basename tty | sed 's/^...//' ) 
$ xinit -- vt$(tty | sed 's/[^*]*y//' )
$ xinit -- vt$XDG_VTRN

3) Edited **/usr/bin/startx** script:
Added variable:
**myvt='vt'"$(tty | sed 's/[^*]*y//' )"**
Used* $myvt* as an argument for *serverargs*:
**serverargs="$myvt"**
This works only for using of the *startx* command but not for *xinit*.

4) Use in the «~/.xinitrc» or «/etc/X11/xinit/xinitrc» scripts:
*exec startx /usr/bin/yourwindowmanager*
But startx must be edited as in example workaround **3)**

5)Run a **custom** windowmanager with *xinit* **not** the one that is in the *xinitrc* start up configuration scipts:
$ xinit /usr/bin/yourwindowmanager -- **'vt'"$(tty | sed 's/[^*]*y//' )**"

6) Use aliases with xinit:
$ export MYWM='/usr/bin/yourwindowmanager'" -- "**'vt'"$(tty | sed 's/[^*]*y//' )**"
$ xinit $MYWM

7) Need to find how to edit default xinit settings for starting of xserver in current tty.

Best Regards 
Mr. Me

---

### Post by steeldriver on 2014-08-10
Hello and welcome to the forums

Can you give us some background here? it should not be necessary to change the VT on which the X server runs just to use alsamixer. What exactly are you trying to do?

---

### Post by Andy_Crowd on 2014-08-10
I thought that it depends on *tty* and *xinit* (my workarounds helps but is not a solution) but it has to do with user rights.

I found a bigger problem now. It depends on user rights. **I need to make alsamixer work in windowmanager**.
When I start xserver from any tty it always opens on tty7, if I start alsamixer in a terminal in a windowmanager (I am using wmaker and openbox) then I getting errors like _"cannot open mixer: No such file or directory_", but then I do** sudo alsamixer** then it opens without any problems. I* don't use any desktop managers* as Lightdm/mdm/gdm, I prefer console for myself.

I preparing hard drive with ubuntu in vmware for my laptop, and _I used mini.iso_ for installation for getting only apps that I will need. I am running Arch Linux on my PC, Ubuntu will be only on laptops (installing ubuntu to my friends sometimes and need to practice some command from time to time).

Please help to find where I need to change access rights or add user to a correct group?

**I really need to make it work until tomorrow**.

.... Look like the mission is impossible.... still waiting .....

---

### Post by Andy_Crowd on 2014-08-10
Can someone **test** to confirm my problem with **mini.iso + alsamixer + openbox + startx/xinit + ***_no gui desktop managers_* (like mdm,gdm,lightdm,kdm,...)?
I am testing  in VMware, you can too.

---

### Post by Andy_Crowd on 2014-08-12
I found another part of soulution to my problem:
$ *usermod -a -G adm,cdrom,sudo,**audio**,dip,plugdev,netdev,lpadmin,sambashare   myusername*
I had to _add_* myusername* to an **audio** group. 

0) I can open *alsamixer* but is no sound even if everything is on max.
1) I can open alsa mixer _now_ and it shows bars.
2) I still cannot listen a music as normal. 
3) So far I can listen music only by using my workarounds, modified */usr/bin/startx* script and added[COLOR=#808080] *[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && exec startx*[/COLOR] to the my [COLOR=#808080]*$HOME/.profile*[/COLOR] file.
5) Restarted computer and now it works without any problems (using *xinit* to start X, it using settings from $HOME/.xinitrc).[B][COLOR=#800080]

Thanks for me! I solved it by myself![/COLOR][/B] Too [COLOR=#ff0000]sad[/COLOR] for so low help I got here.

---

