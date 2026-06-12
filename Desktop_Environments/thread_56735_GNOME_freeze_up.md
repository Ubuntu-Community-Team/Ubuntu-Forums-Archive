---
title: "GNOME freeze up"
date: 2005-08-13
forum: Desktop Environments
---

### Post by faceoftheearth on 2005-08-13
I was just browsing through Synaptic when suddenly everything just froze completely up. The mouse didn't move, none of the things on the top GNOME bar moved. I couldn't kill GNOME with ctrl-alt-backspace. I'm not really sure what happened, but I had to hold down the power button and reboot that way. When I got back into GNOME, my Firefox profile was gone even though I hadn't been using Firefox at the time of the freezeup. In addition, my folder with the contents of my NTFS partition was suddenly in the Places menu as well as in the "Computer" folder. I think my CD/DVD drive is also labeled differently in the computer folder, but I can't be sure. Anyone know what happened? The computer is a Dell Inspiron 9300 with a Pentium M, 1 GB of RAM and an Nvidia 6800. I'm pretty worried that Linux is unstable and will end up destroying my computer. I've never had a BSOD in my many years with Windows and I'm not too keen on switching permanently to an OS that seems to be very unstable. Can anyone help me out? 

Thanks

---

### Post by wiraone on 2005-08-14
I've the same problem too. I had no problem with most distribution before .. I've just build a new PC, 1GB RAM, AMD64 2800+ .. had FC4 on it before but I have had no problem with it.. but after installing Ubuntu 386, I got few freezes .. totally unusable, couldn't shutdown the PC either .. checking the swap space .. it seems that it hasn't been touched at all .. 

> [FONT=Courier New]             total       used       free     shared    buffers     cached
Mem:       1036296     450752     585544          0      68104     179144
-/+ buffers/cache:     203504     832792
Swap:      1068280          0    1068280[/FONT]

Is yours the same?

---

### Post by faceoftheearth on 2005-08-14
Yeah, my swap space isn't being used at all. I made swap space when I partitioned and Ubuntu made some on install, so I have something crazy like 1.8GB of swap space. It's never used even when my 1GB of RAM is maxed out.

---

### Post by dsethuraman on 2005-08-14
i too have this problem a couple of times, doing simple stuff like surfing the net etc. again my swap is not used at all as i can see from the system monitor, eventhough my ram is pretty low at 256mb and is used at 100% most of the time.

---

### Post by dsethuraman on 2005-08-14
well, since the previous post above, i have been watching the sys monitor and i stand corrected. the swap does indeed get used esp when i use multiple applications. so swap is not at fault.

---

### Post by faceoftheearth on 2005-08-14
I'm really quite surprised no power users have attempted a go at this problem. Perhaps it's some laten unresolved issue that no one wants to talk about. I haven't booted into Ubuntu much at all since because I'm really not too happy with it doing that. To reiterate, does anyone know of a solution to or cause of the entire OS completely freezing up?

---

### Post by lark012 on 2005-08-14
I have the same issues.  I tried plenty of things, but the machine still locks up.  I've read that it's due to the Nvidia drivers.  The thing is, it's happened to folks that have ATi cards as well.  I've been looking for an answer for the past 2 months, but nothing's come up :(

---

### Post by aveline on 2005-08-14
[QUOTE=lark012]I have the same issues.  I tried plenty of things, but the machine still locks up.  I've read that it's due to the Nvidia drivers.  The thing is, it's happened to folks that have ATi cards as well.  I've been looking for an answer for the past 2 months, but nothing's come up :([/QUOTE]
 I'm no poweruser lol, but i'll give this a shot.

next time it freezes, try hitting Ctrl-alt F1-12, see if you can get to a term... if not um lets see... I don't know the exact sequence of keys... someone else should chime in with them but you can try: 

alt-sysrq/prtscn *its one key*-Y ... this syncs files then
alt-sysrq/prtscn-b (reboots)

see if that works and if it does, then look through your log files and dmesg to see if theres any anomalies.

so do on a cmd line after a reboot:
tail /var/log/<name of logfile, there will be several you can look at>

that will print the last 50 or so lines of a log file.

aveline

---

### Post by faceoftheearth on 2005-08-14
Thanks for the advice, I'm pretty new to Linux. I've always loved various operating system options and would really like Linux to be another one I'm proficient at. If this is a problem that is systemic within the ubuntu community, it really needs to be ironed out because ubuntu has the greatest chance, small though it may be, of any Linux distro making it to the regular desktop market.

---

### Post by dsethuraman on 2005-08-15
well, i have tried the ctrl+alt+f12 with no effect. 
the rescue mode: the keys are 
alt +sysres(which is print screen) along with sequentially r (to put the keyboard in raw mode), alt+printscreen+s, alt+pntscn+e , alt+pntscn+i, alt+pntscn+u, alt+pntscn+b. the s is for the syncing, dont know what e and i are for, u is to unmount disks and b is for boot. 
this did not work when my ubuntu froze ](*,) . only a reset ( from windows legecy!!) :-?  worked.

---

