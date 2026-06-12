---
title: "Nautilus problem (i think)"
date: 2009-05-15
forum: General Help
---

### Post by mcolson on 2009-05-15
I'm kind of new at trouble shooting, but I think I have a problem with Nautilus.
I wanted a trash icon on my desktop, so i did what this guy said to do <<http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/>> And immediately after changing the settings i lost the ability to look through my files, I can still search for them based on where i put them through file search, so they aren't "gone". I went into Synaptic and reinstalled all the files for Nautilus and the debug script but nothing restored my desktop or the file browsing.   And I have already tried changing the setting back, as i expected nothing changed.  Also, when i try to open Rhythmbox, it crashes.

I could either fix whatever ails Nautilus, or get a different program, but i don't know of what other programs would do the same thing.

Thanks everyone, i'll be waiting by the Inbox

---

### Post by dcstar on 2009-05-15
> **mcolson said:**
> I'm kind of new at trouble shooting, but I think I have a problem with Nautilus.
I wanted a trash icon on my desktop, so i did what this guy said to do <<http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/>> And immediately after changing the settings i lost the ability to look through my files, I can still search for them based on where i put them through file search, so they aren't "gone". I went into Synaptic and reinstalled all the files for Nautilus and the debug script but nothing restored my desktop or the file browsing.   And I have already tried changing the setting back, as i expected nothing changed.  Also, when i try to open Rhythmbox, it crashes.

I could either fix whatever ails Nautilus, or get a different program, but i don't know of what other programs would do the same thing.

Thanks everyone, i'll be waiting by the Inbox

Create a new user in your system and log in to see if things work correctly, if they do then you have a corrupted profile on your original login.

---

### Post by XCan on 2009-05-16
> **dcstar said:**
> Create a new user in your system and log in to see if things work correctly, if they do then you have a corrupted profile on your original login.

If it indeed is a corrupted profile. Would a deletion of the users .nautilus dir help?

---

