---
title: "widescreen resolution borked"
date: 2007-12-09
forum: Desktop Environments
---

### Post by skills on 2007-12-09
hi there.

i just installed Ubuntu on my ASUS M6N laptop. It has a 15" widescreen LCD that is natively 1280x800.

now the problem is Ubuntu will let me select the resolution ( its currently running 1024x768 ) however when i try to use the resolution i have pixel mayhem. the majority of my screen in the middle looks fine but near the task bars etc it is all scrambled. im guessing it has something to do with the graphics driver maybe?

my laptop has a mobility radeon 9600, im not exactly sure if i need to install a driver for it maybe or if i need to patch my ubuntu or something else crazy? could anyone help me?

---

### Post by mcduck on 2007-12-09
Yes, installing the Ati's driver for your graphics card should help. Go to System/Administration/Restricted Drivers and there should be option to install the fglrx driver.

---

### Post by skills on 2007-12-09
thanks for the pointer.  i installed the fglrx driver through restricted drivers like you said.  however now i cannot choose my widescreen resolution, i can only choose 640x480, 800x600 and 1024x768...

do i have to go digging in xorg.conf?

---

### Post by skills on 2007-12-09
no worries, i just added "1280x800" to all the depth modes in xorg.conf and it worked just fine =]

---

