---
title: "Another Person with a Suspend/Resume Issue"
date: 2008-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HydroModeler on 2008-06-19
I have a Dell Inspiron 1420 with the Nvidia video card that I got about a month ago.  When I got it, it had Vista Home Ultimate on it. I immediately turned it into a dual boot so it now has Vista and Ubuntu Hardy installed.  Everything worked right away except suspend/resume which works sometimes, but never great.  

I only get the screen that prompts me for my password after the first suspend/resume cycle.  After that I get either a white/grey screen or a black screen with a small multi-colored box wherever the mouse is located.  I can just type my password and it resumes.

Also, it seems to take quite awhile to suspend  sometimes (30 to 50 seconds), other times it is relatively quick (8 to 9 seconds).  When it is suspending the screen is black with a blinking cursor in the upper left of the screen.

So I have two questions:

1) I have tried all of the suggestions to get resume working properly that are listed in the following link (which also show up in many posts/blogs on the web), but it does not seem to work. I have also tried variations of this which also don't seem to work. Is there anything else to try?  Dell Hardy ISO?

[http://ubuntuforums.org/showthread.php?t=602806]("http://ubuntuforums.org/showthread.php?t=602806")

2) Is there any way to speed up the suspend process?  8 to 9 seconds seems good to me.  How long should it take?

Thanks in advance.

---

### Post by fragos on 2008-06-20
Suspend and hibernate work best with 8.04. Since you ordered a 1420 instead of a 1420n with Ubuntu you may have a Broadcom WiFi card which may require special configuration on your part. The Intel Wifi works flawlessly.

---

### Post by HydroModeler on 2008-06-20
Thanks for the reply.  I am a little confused by your response.  Did you mean to say "Suspend and hibernate work best with 1420n"?  If not, I am not sure that I follow.  Are you saying that it might be my wifi card that is causing my suspend/hibernate issues?  The model I bought is supposed to have the Intel 4965 802.11a/g/n Dual-Band Mini Card in it.  Does that help?  Any suggestions to fix it?

---

### Post by fragos on 2008-06-20
What I meant was suspend and hibernate work in 8.04 but had problems in prior releases. My Intel Wifi card works flawlessly. You may have a newer Intel card than I do. Prior to 8.04 resuming from a suspend or hibernate had problems restoring wireless connections. You never mentioned what version of Ubuntu you were running. If not 8.04, you will experience problems.

---

### Post by HydroModeler on 2008-06-20
Ah yes sorry I should have mentioned that I am running 8.04, but still suspend/resume don't seem to work quite right.

---

### Post by quadra on 2008-06-21
Can you disable the built-in wireless card in the BIOS? So you'll at least know where the problem comes from. I have an Inspiron 510m with the Dell Wireless 1450 802.11a/b/g mini PCI card (Broadcomm chipset) and when I disable the MiniPCI in the BIOS, I can standby and hibernate normally. (However this is not a solution yet, just a test)

---

### Post by HydroModeler on 2008-06-21
Interesting!  I will give that a try later on today when I get a chance.

---

### Post by HydroModeler on 2008-06-22
Well, I tried disabling the wi-fi from the BIOS, and it did not seem to work.  So I tried disabling the Visual Effects from the System>Appearance menu (which I should have done before) and it seemed to fix the issue.  But I really want the effects to be enabled.  It seems that most people have been successful using workaround linked in my first post, but it doesn't seem to be working for me.  ????  Well I don't know.  It isn't so bad the way it is, but i would really like to get it fixed.

---

### Post by HydroModeler on 2008-07-21
Well I would just like to post an update relating to the suspend issue I was having.  I am not sure exactly which update fixed the problem, but it seems to work quite well at this point.  I believe that I have installed updated video driver and a new kernel (just via regular updates) since I posted last and it seems to have fixed its self.

---

### Post by quill3033 on 2008-07-28
I'm not sure that this is the right place to ask, but it seems the most relevant. I have a desktop Dell Pentium 4 and have 8.04 installed on the internal hard disk and also installed it on an external usb drive. 

Since I used the suspend or hibernate button the computer just shuts down the monitor. I can hear something happening in the box - as though the hard disk is spinning - it also makes this noise at other times like a swooshing sound) and then the screen goes off into what appears to be a power saving mode. But the power in the box is still on as though it is suspended. I've tried changing preferences in the Session, power management etc. but I can't really predict what has caused it. I did do a fresh re-install but it's still doing this. It sometimes happens if I try to open too many applications like ff and thunderbird all at once soon after booting the machine. I'm wondering if it's an electrical problem with the motherboard or something... 
It's started happening to the usb hard disk too, so I can't figure it out. But this makes me think it could just be an electrical problem.

---

### Post by aidave on 2008-07-29
I'm also having better luck with suspend/resume on my 1420n, after installing 8.04.1, 32 bit, and the latest NVIDIA driver.

Although now my wireless doesn't always resume, and requires a reboot every 4-5 times.

It also defaults to a white screen 90% of the time, which is cleared with a password entry.

---

### Post by fragos on 2008-07-29
Highbernate and susspend roam for Wifi when they restart. There's a good chance you've changed locations. I've found that some WiFi access points take a while to be recognized. That isn't a failing of Linux. Scince highbernation is a power down it's appropriate for a password to be requested -- that's how it works. I'm not positive but I believe suspend doesn't ask for a password as suspend is normally used for user breaks as when closing the lid in a coffee house to talk to a friend. In my case, 1420n with 8.04 32 bit has performed as described prior to 8.04.1.

---

### Post by aidave on 2008-07-29
> **fragos said:**
> Highbernate and susspend roam for Wifi when they restart. There's a good chance you've changed locations. I've found that some WiFi access points take a while to be recognized. That isn't a failing of Linux. Scince highbernation is a power down it's appropriate for a password to be requested -- that's how it works. I'm not positive but I believe suspend doesn't ask for a password as suspend is normally used for user breaks as when closing the lid in a coffee house to talk to a friend. In my case, 1420n with 8.04 32 bit has performed as described prior to 8.04.1.

I dont seem to have any troubles changing locations upon resume.  I have no problem going from work to home and back... its just after a while, the wireless stops being detected at all.

I have never had Ubuntu's suspend/resume feature work properly on any laptop or system, either from regular install or updates.  For over two years.  I dont know why, but it is getting ridiculous, they should definitely fix this as it is a crucial feature IMO.

---

### Post by framallo on 2008-08-09
hi!
I have a 1420n inspiron and nvidia with suspend issues only when I'm running on batteries. When i send it to suspend the screen show a blinking cursor and never suspend after a second suspend and/or randomly.
I have nvidia binaries from envy.

I used to have the blank issue, and using ctrl+alt+F1 and ctrl+alt+F7 refresh the screen and solved the issue. I would check DOUBLE_CONSOLE_SWITCH in /etc/defaults/acpi-support.

There are other options that need to be checked. This is how i have it:

```

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true


```

Today i checked this, and apparently  it fixed :)!
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Failed_Studio_Suspend]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Failed_Studio_Suspend")

Also followed:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
dmesg says
```
Magic number: 4:393:533
```
but I can't find what module/code/whatever belongs.

---

### Post by fragos on 2008-08-10
My 1420n has the Intel video. It seems that this suspend hibernate thing has been a linux issue for some time that might be impacted by power control hardware and in some instances the video hardware. Each release of Ubuntu has improved in this area. With my 1420 and 7.04 it just didn't work. 7.10 seemed to work except the internet connection wouldn't and counldn't be restarted. 8.04 did the trick for my box. I did have one occasion a while back where the network didn't restart but manually restarting it worked.

---

