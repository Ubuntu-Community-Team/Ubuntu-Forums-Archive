---
title: "HAL failure due to Kleansweep"
date: 2009-06-11
forum: General Help
---

### Post by t1mb3rl1n3 on 2009-06-11
greetings~
Just went through this whole shebang today and figured I would post on this to save others some time.

I am running 8.10 Ibex on a HP Pavillion dv6000 and am quite happy with performance etc....
however, I did install Kleansweep to kind of help keep the clutter down etc.  I thought I was being cautious enough with it when i ran it earlier today, specifying only searching in my home directory etc etc etc

not so, after it finished tarballing everything it removed I was up for about 3 minutes, and then crash and I have no keyboard or mouse save for dropping to TTY

I thought at first my xorg.conf was fouled up, so i did some research on modding that to get my keyboard and mouse back up

found several threads specifying adding an entry to stop autoconfig of hotplug devices

that DID get my keyboard and mouse operating at the GNOME splash, but the real issue was a HAL error

i followed a set of instructions to de-tar and reinstall the stuff Kleansweep removed and the error persisted

I then had to move the lappie up to the room with the router, patch in via cable, manually restart HAL to get networking to pick up an addy and then re-install HAL from synaptic

that did the trick, afterwards i removed the added entry to the xorg.conf with no ill effects and got my hotplug items working again

Just thought this might be of help to others, xorg.conf is not the sole cause of loss of standard in 100% of the time, learning that this way took a lot longer.

cheers!
JT

---

