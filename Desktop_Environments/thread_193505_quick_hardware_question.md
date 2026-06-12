---
title: "quick hardware question"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Polygon on 2006-06-10
Hello,

Ok, so i am planning to move my sound card (which is in a lower pci slot) to a higher pci slot, mostly because ive read that this way, the sound card (along with the video card) get better priorties to the processor, and its also a suggestion to help a very bad stuttering and then freezing problem that occurs with half life 2 while im running windows

ok so now on to the question, if i move around my pci cards (like video, sound, network adapter, firewire, etc) to different slots, but they are all still there and nothing new is added, will this screw anything up in ubuntu? Do i have to edit anything to make it realize what card is where, or will this be detected automatically when i boot up ubuntu after the changes

thanks

---

### Post by ayoli on 2006-06-10
yes, i suppose you can move your pci card without problems, on boot udev startup scripts will detect them anyway and load suitables modules.

---

### Post by patrickfromspain on 2006-06-10
you can do it without problems. I moved my wireless pci card and had no problems. I had in windows, where it was detected as a new card.

---

### Post by Polygon on 2006-06-10
thanks

---

