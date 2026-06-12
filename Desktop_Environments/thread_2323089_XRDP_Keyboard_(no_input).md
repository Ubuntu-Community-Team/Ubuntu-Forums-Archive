---
title: "XRDP Keyboard (no input)"
date: 2016-05-02
forum: Desktop Environments
---

### Post by dal19802 on 2016-05-02
Hi

Ok I'm stuck. I'm a noob when it comes to Linux but I'm learning fast! [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG] Be gentle with me please [IMG]http://www.linuxforums.org/forum/images/smilies/icon_lol.gif[/IMG]

I hope these terms and assumptions/understandings are right...

I originall had XRDP setup using KDE as the GUI.
I had keyboard layout set to US so I've tried about a dozen ways to set  it as GB and used guides posted around the web to do this. None of them  worked. I've not got a problem where the keyboard just won't type for  the login box to XRDP and I've began trying to get this solved...

I tried upgrading XRDP package (SSH) which hadn't done anything. I was  hoping that it would rewrite the keyboard settings in /etc/xrdp/. I  tried uninstalling 'remove' and reinstalling 'install' which I thought  would have definitely re-wrote the /etc/xrdp/ keyboard mappings.

I since have setup Mate GUI in hopes to rewrite the whole keyboard issue but alas this has not solved the problem.

If I go to the machine directly the keyboard is working fine under the  standard Lubuntu default desktop (sorry I'm not sure what desktop this  actually is)

Other things I've tried (can't remember them all)

#$ sudo xrdp-genkeymap km-0409.ini
xrdp-genkeymap:  unable to open display ''

$ sudo xrdp-genkeymap /etc/xrpd/km-0409.ini
xrdp-genkeymap:  unable to open display ''

~$ cd /etc/xrdp
/etc/xrdp$ dir
backups      km-040c.ini  km-041d.ini       rsakeys.ini  xrdp.ini
km-0407.ini  km-0410.ini  km-0809.ini       sesman.ini
km-0409.ini  km-0419.ini  km-0809.ini.save  startwm.sh

(please note that backups here was created after the issue.. this was another thing I tried and was listed as one of the steps).

~$ setxkbmap -layout gb
Cannot open display "default display"

/etc/xrdp$ sudo loadkeys --verbose gb
...
huge list of keys
...
Changed 13824 keys and 26 strings.
(No change in compose definitions.)

~$ sudo loadkeys gb
Loading gb

I've tried all of the above (I think, at least in most cases) under 'us'  too to try and reset it at least back to a keyboard I can sort of use.  This hasn't worked either.

Any suggestions on how to solve this?

Many thanks
Dal

---

### Post by dal19802 on 2016-05-05
FYI:

I've managed to fix this. Not sure if the first step is necessary

Step 1: renamed the /etc/xrdp folder (i.e. /etc/old_xrdp)

Step 2: use apt-get to purge xrdp

Used this answer which worked out beautifully simple [http://askubuntu.com/questions/580415/how-to-remote-desktop-from-windows-to-lubuntu](http://askubuntu.com/questions/580415/how-to-remote-desktop-from-windows-to-lubuntu)

I had to restart the PC after following this answer to get it to work properly but the keyboard input is now working.

[FONT=arial]Note for other noobs: I removed the gnome reference completely when it said to make sure it says "lxsession -e LXDE -s Lubuntu" in the file. Not sure why the other is default

Hope this helps someone.

[/FONT]

---

