---
title: "Edubuntu 10.04 crashing"
date: 2010-11-03
forum: Desktop Environments
---

### Post by Costas100 on 2010-11-03
I had a couple of strange incidents in a reasonably new installation of Edubuntu 10.04, dual boot with windows XP home. All worked fine for a while until a couple of days ago I started getting strange crashes, especially when I had more than one program open and in use. The screen will almost get lost with lines and pictures intermixed.

I suspected that I may have a hardware problem, so I decided to restart from the live CD and do more or less the same work I was doing when the install version crashed. Only very minor problems were encountered in the live CD session, where again I had 3 or 4 programs open including a browser with 5 tabs open. If anything the live CD session was more overloaded than the previous normal session.

After spending about 30 minutes in the live CD, I decided to close and do a restart. During closing two errors were presented and was asked if I agree to file a bug report. I agreed and then filed the report shown in [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/670437](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/670437). 

In this same computer until maybe two month ago I had ArtistX -07 based on Ubuntu 8.10 and never had a problem until I switched to Udubuntu 10.04 installed in the same partition that ArtistX was installed (reformat and manual full install).

I will check my computer for possible hardware problems, although in XP it has no apparent problems and I may downgrade the Udubuntu 10.04 to Ubuntu 9.10, which I have installed in another machine much older that the one I am using now and have no problems.

My understanding of the terminology in the bug reports is rather limited. I will appreciate any help, suggestions or possible causes.

I tried the live CD of the new Ubuntu 10.10 which unfortunately does not start in this machine.

Thank you all

Costas

PS: I have the output of sudo lshw with all the information of my computer, but I cannot see any way of attaching a text file. If it will help I will submit it as a reply in this thread, it is about 10 pages long.

---

### Post by sikander3786 on 2010-11-03
Hi Costas100.

It would be really nice to hear the details about your hardware. You can paste that 10 page long test from lshw in your post and then wrap your text with code tags # from the post menu. [ code] at the start and [/code] at the end

Most probably seems a graphics card/driver problem. It also may be relate to compiz. Did you install it?

The best way of switching between releases is to first try out the live CD and see if all of your hardware works with the newer versions.

When the OS crashes, do you remember any specific applications running? If it appears to be related to a specific one say firefox, you can switch to some other browser and see if it still crashes.

If I was in your place, I would first of all rule out the RAM by doing memtest from Grub menu and secondly the HDD, scan it for bad sectors (although I know Windows in working fine, going for a scan wouldn't hurt).

Also we would like to know why 10.10 is not working. Does it give a blank screen? Or it just crashes? Can you post some more details on the errors please.

---

