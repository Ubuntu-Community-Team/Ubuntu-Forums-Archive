---
title: "Help! Steam, Launching TF2"
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by xs123 on 2007-10-20
I have installed Wine, Steam, Portal, and TF2. Steam works perfect when I open it up, but When i try go into Portal or TF2.. It pauses for a min and gives me this message

ERROR

Steam.exe (main exception): Win32 StructuredException at 7A8B3C65
Attempt to read from virtual address 0 without appropriate access rights.

I am assuming i need access rights, but not sure what this means... Can anyone help here?

I should state my specs..

GA-M55-SLI-S4 mobo
AMD X2 3800+
1GB DDR2 800
160GB IDE HDD
SLI'd Gigabyte 6600GT's 256MB
Ubuntu 7.10 (Gutsy Gibbon)
Latest Wine (Whatever that is)


Thanks. :)

---

### Post by xs123 on 2007-10-20
same for css :(

---

### Post by xs123 on 2007-10-20
Help! this is really annoying

---

### Post by xs123 on 2007-10-20
also deleted clientregistry.blob with no luck

---

### Post by xs123 on 2007-10-20
anyone?

---

### Post by Vadi on 2007-10-20
I had this error before - I googled it, and it turns out it's a steam error (windows people were getting it too).

I think there's some .blob file in your directory that you can delete, and should fix this - but keep in mind, it'll wipe some of your settings too.

---

### Post by xs123 on 2007-10-20
yep, i said i deleted clientrgistry.blob with no luck :(

---

### Post by Vadi on 2007-10-20
Sorry man. All I know is this isn't wine's fault entirely, but steams :/

---

### Post by xs123 on 2007-10-20
ok.. so theres no way to fix steam >< ?

---

### Post by xs123 on 2007-10-21
Reinstalled ubuntu and wine. HL2 / CSS runs fine now. Will try TF2 later

---

### Post by VinylPusher on 2007-10-21
It might be worth noting that Steam crashes on Windows too due to improper memory accesses. At least, it does if you have DEP turned on for all programs.

Sounds like there's an uninitialised pointer somewhere within Steam's code. Tut tut, Valve ;)

---

### Post by Vadi on 2007-10-21
Doesn't it suck that steam isn't open-source? If it was, you could probably just email a dev with this / someone would have discovered this, and made a patch.

:|

---

