---
title: "iPod Touch 32GB Won't sync photos (Windows)"
date: 2009-06-21
forum: General Help
---

### Post by ShinHadoken on 2009-06-21
I have a brand new iPod Touch 32GB (running the new v. 3.0 iPhone OS firmware) that I am syncing with iTunes (v8.2) on Windows XP SP3. I restored this new touch from a backup file that was made for my 8GB touch. Now, when I try to sync photos, it fails with "iTunes could not sync photos to -----'s iPod Touch. The required file could not be found." Does anyone know what the problem is?


Thanks in advance,

--SH

EDIT: PROBLEM ISOLATED!!!!! THERE IS A FOLDER IN MY PICTURES THAT IS CORRUPTED. I can put files in it, and delete them out of it, but I CANNOT DELETE THE FOLDER ITSELF. Thank you, faulty filesystem. 

So, I have this corrupted folder that I can't delete, not even through a Command Prompt. Suggestions please?

EDIT: SOLVED! Defragmenting didn't do it--I decided to boot up into a Jaunty Live CD and see what I could do, and I deleted it! The corrupted folder is gone, I moved all the pics back into My Pictures, and the iPod is syncing fine!

---

### Post by Chronon on 2009-06-21
nevermind

---

### Post by blueridgedog on 2009-06-21
As it is covered by warranty and you are using it as recommended, you have free support form Apple.  Give them a call.  I have always been happy when I called them.

---

### Post by emshains on 2009-06-21
Why would you use the 8gb restore ? Just make a new one. It won't hurt you, I think.

---

### Post by ShinHadoken on 2009-06-21
Well, using the old restore meant I didn't have to configure any settings... I'm formatting the thing now, using the "Erase all content and settings" options in Settings > General > Reset. I'll then try starting from scratch and see if that fixes the problem.

---

### Post by ShinHadoken on 2009-06-21
EDIT: PROBLEM ISOLATED!!!!! THERE IS A FOLDER IN MY PICTURES THAT IS CORRUPTED. I can put files in it, and delete them out of it, but I CANNOT DELETE THE FOLDER ITSELF. Thank you, faulty filesystem. 

So, I have this corrupted folder that I can't delete, not even through a Command Prompt. Suggestions please?

---

### Post by ShinHadoken on 2009-06-21
Due to the corrupted folder, I am currently attempting a defrag. I'll let you know how this turns out.

---

### Post by Chronon on 2009-06-21
Since you can't use the device in MSC mode I think you need to Restore it with iTunes.

---

### Post by ShinHadoken on 2009-06-22
> **Chronon said:**
> Since you can't use the device in MSC mode I think you need to Restore it with iTunes.
Let me clarify, there is a corrupted folder in the actual "My Pictures" folder, not on my pictures on the iPod. I did not, not could I, access the iPod through the Windows Command Prompt.

---

### Post by ShinHadoken on 2009-06-22
SOLVED! Defragmenting didn't do it--I decided to boot up into a Jaunty Live CD and see what I could do, and I deleted it! The corrupted folder is gone, I moved all the pics back into My Pictures, and the iPod is syncing fine!

---

