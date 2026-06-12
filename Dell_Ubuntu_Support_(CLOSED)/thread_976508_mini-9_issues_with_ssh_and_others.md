---
title: "mini-9 issues with ssh and others"
date: 2008-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ARhere on 2008-11-09
I am noticing some really strange things with the mini-9 and I would like someone to at least confirm some of these if you own one; if you don't know the answers.

1.  When I try to ssh into my server, I get asked the password fine, but then it just goes to a new line and sits there.  :confused:  SSH'ing into my server using another PC gives me no problems. CTRL+Q or CTRL+Z does nothing, terminal is just frozen.

2.  Mashing  'TAB' key for auto-complete after typing **sudo** will no longer auto-complete.  Typing "apt-g" then TAB will auto-complete, but "sudo apt-g" then TAB and _nothing_!

3.  The wireless networking deamon "nm-applet 0.6.6" does not seem to monitor the status of the wireless driver or hardware.  Try... ```
sudo ifconfig eth1 down
``` and the stupid applet has no clue.  You have to reconnect manually using the applet or reboot.

4.  This is the weirdest one, changes made to the desktop, like adding shortcuts to the tool bar, do not stay.  Or if my changes stick it appears at random.

-Any clues on these four?  I am going to check the "known bugs" again and see if the wiki has changed since I last looked.

-AR

---

### Post by 2damncommon on 2008-11-09
> **ARhere said:**
> 1.  When I try to ssh into my server, I get asked the password fine, but then it just goes to a new line and sits there.  :confused:  SSH'ing into my server using another PC gives me no problems. CTRL+Q or CTRL+Z does nothing, terminal is just frozen.
I just tried ssh on my Mini. It connects just fine.
Is it a network/permission issue?
> **ARhere said:**
> 2.  Mashing  'TAB' key for auto-complete after typing **sudo** will no longer auto-complete.  Typing "apt-g" then TAB will auto-complete, but "sudo apt-g" then TAB and _nothing_!
Yes, same here, auto-complete works on my desktop computer with Ubuntu 8.04 but not on the Mini.

---

### Post by simusid on 2008-11-09
> **2damncommon said:**
> I just tried ssh on my Mini. It connects just fine.
Is it a network/permission issue?



If I ssh from my macbook TO the mini, I have this same problem (enter password, then nothing).

If I ssh from my windows desktop using putty TO the mini it works FINE.   I find that very very puzzling!

---

### Post by jbloodwo on 2008-11-09
> **simusid said:**
> If I ssh from my macbook TO the mini, I have this same problem (enter password, then nothing).

If I ssh from my windows desktop using putty TO the mini it works FINE.   I find that very very puzzling!

that is strange...

if you install tcpdump and watch the connection process do you see anything difrent

---

### Post by 2damncommon on 2008-11-09
> **simusid said:**
> If I ssh from my macbook TO the mini, I have this same problem (enter password, then nothing).

If I ssh from my windows desktop using putty TO the mini it works FINE.   I find that very very puzzling!
Is one wired and the other wireless?
Unless they are connecting through the same interface it could be a network restriction that needs investigation.

---

### Post by cmspider on 2008-11-16
Apparently this is a bug in the wifi driver shipped with the mini.

ssh doesn't work if you're behind a NAT.

There is a fix coming in a kernel upgrade at some point, but there are some workarounds.

sudo iwpriv eth1 set_vlanmode 0
fixes it till you reboot.  Probably needs to be done after suspending too.

I stuck:
modprobe wl
iwpriv eth1 set_vlanmode 0

in /etc/rc.local so it gets set on every boot,

and then 

created a file: /etc/pm/sleep.d/2-local-misc
with the following:

case "$1" in
    resume)
      /etc/rc.local
     ;;
esac

so that it happens on every resume as well.

---

### Post by yakker.yak on 2008-11-17
Yes, the ssh problem has been reported by other users.

It only happens trying to login to a server using the Mini's wireless interface, wired seems fine.

Adding the following line to the end of /etc/network/if-pre-up.d/wireless-tools fixed it for me:

```
/sbin/iwpriv eth1 set_vlanmode 0
```

---

