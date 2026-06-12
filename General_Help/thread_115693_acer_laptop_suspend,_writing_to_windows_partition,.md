---
title: "acer laptop suspend, writing to windows partition, other laptop Qs"
date: 2006-01-11
forum: General Help
---

### Post by jimmyp on 2006-01-11
I have an acer travelmate 4650 with breezy installed.  I can hibernate the machine by going System->Log Out->Hibernate but hitting fn+f4 doesn't do anything.  I don't get anything in dmesg or anything when I run acpi_listen and hit fn+f4.  Has anyone got this working?  How about suspend-to-ram?

Also, once I had suspended the machine from windows and booted into linux.  Then I wrote some files to the windows partition while in linux.  When I booted into windows though, the files weren't there.  Back in linux when I tried to ls the files I got an error (cpio maybe, I forgot) and then they weren't there anymore (just a file not found by ls).  Can you not write to the windows partition when windows had been suspended?

Also, does anyone's battery monitor show less time remaining in linux than in windows?  When I am running on battery my cpu frequency applet shows that the machine is running at its slowest speed, but the battery time remaining is setill lower in linux.

Is there a tool that I can use to graphically change the sensitivity of my synaptics touchpad?  I'd also like to be able turn tap-to-click on and off graphically (other people use the machine sometimes)

---

### Post by epostma on 2006-01-11
Hi,

I know an answer to only one of your questions: if windows awakens from being suspended / hibernated, it assumes nothing touched its partitions since it was suspended; if you do write to them, you can expect to find results like what you described. So I guess it's best not to do that.

HTH,

---

### Post by jimmyp on 2006-01-11
Ok thanks, that's what I was afraid of.

As for fn+f4, if I go to System->Preferences->Keyboard Shortcuts there is a Sleep action associated with fn+f4.  Through some testing and swapping I found out that fn+f4 is being recognized but that the Sleep action has no effect.  Does anyone know where I can find what Sleep is supposedly doing so I can try to fix it?

---

