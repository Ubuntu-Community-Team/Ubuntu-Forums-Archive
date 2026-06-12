---
title: "Ubuntu Beeps For No Reason"
date: 2005-08-14
forum: Desktop Environments
---

### Post by SuperMike on 2005-08-14
I have a strange problem. About once an evening while I'm using Ubuntu, my Ubuntu beeps for no reason that I can determine. About the only hunch I have is that it's either a downloaded apt package with an exploit inside, or it's the search indexing saying it's done.

I check 'dmesg' and 'cat /var/log/messages' and I cannot correlate it to an event there.

Does anyone have any idea where I might finds clues?

---

### Post by nix4me on 2005-08-14
Mine beeps when there is a new email in Thunderbird.

Mark

---

### Post by Fotinakis on 2006-01-05
I am having this same problem, and it happens whenever I am doing anything that is taxing the processor almost at all.  Changing tabs in Firefox, opening programs, etc.

I am also having a new error appear when I try to shutdown that says something along the lines of "umount: cannot unmount tmpfs, remounting as read-only" and it stays on this line and never shuts down.

Not sure if they're related.  Any ideas guys?

---

### Post by djroadrash on 2006-02-10
same problem here two beeps one after i click to load (Programs, webpages, scroll up and down pages to long, etc...) and a second one once the page is finish loading.
tried both 5.4 and 5.10, i selected acpi=off since i would not get ethernet detected otherwise.. i see now there are other people with the same problem. lets see if we can solve it. im dual booting debian and ubuntu 5.4 for now, no problems in debian. iam starting to think is a alsa problem, because i dont use alsa on debian. this is just my own idea, dont put too much into it, am a new still to linux.:)

---

### Post by viz_e on 2006-02-15
By me it beeps either when I get an Email in Thunderbird or apparently at random, which is annoying, since I really use the "beep" as email notifier.

Since yesterday I also have a shutdown problem, but I cannot say why, since the screen is blanking. Is there any log file for the shutdown process?

---

### Post by viz_e on 2006-02-16
The failed shutdown was a problem with the ibm_acpi modules (v 0.11) with option experimental activated. So the two problems are not related by me.

---

