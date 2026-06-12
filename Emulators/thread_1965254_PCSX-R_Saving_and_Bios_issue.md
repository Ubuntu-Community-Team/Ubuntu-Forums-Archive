---
title: "PCSX-R Saving and Bios issue"
date: 2012-04-25
forum: Emulators
---

### Post by Bardolf on 2012-04-25
I apologize now if this was already covered (If it has been please link me to the thread with a solution).

I recently downloaded PCSX-Reloaded and am having issues saving. Everytime I go to save it tells me there is no memory card then gets stuck trying to find one over and over.

I also have an issue when trying to run Bios, it gives me this message "Running BIOS is not supported with internal HLE BIOS".

Thank you in advance for your assistance.

---

### Post by DoktorSeven on 2012-04-26
For memory cards, make sure there are new, formatted cards in the Configuration->Memory Cards option.

You can only run the BIOS when you have a real Playstation BIOS image.  The simulated BIOS just provides support for system booting and game BIOS calls and doesn't have the BIOS startup sequence the real one does.

---

### Post by mister_playboy on 2012-05-24
I have gotten memory cards to work with the inbuilt BIOS (and it saves/loads far faster than normal), but I found that the game saves get corrupted very frequently so you have to get a real BIOS.

Discussed where to find that isn't allowed here... ask your search engine of choice instead.

---

