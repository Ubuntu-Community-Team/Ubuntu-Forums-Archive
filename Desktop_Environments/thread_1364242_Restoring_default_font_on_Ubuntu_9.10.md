---
title: "Restoring default font on Ubuntu 9.10"
date: 2009-12-25
forum: Desktop Environments
---

### Post by s0ulkeeper on 2009-12-25
I installed some new fonts and everything looks horrible now , how do i restore my fonts to ubuntu's default font set


using  ubuntu  9.10

---

### Post by gsmanners on 2009-12-25
I suppose you created a .fonts folder and copied files there? Just delete whatever fonts you don't want out of that folder.

---

### Post by s0ulkeeper on 2009-12-25
i did a sudo apt-get install msttcorefonts
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

---

### Post by ajgreeny on 2009-12-25
Uninstall msttcorefonts for a start.  I admit I have no idea what the second command you show actually does, but with the msttcorefonts gone, perhaps you will be back to normal.

However, what fonts now look bad?  I have all of the msttcorefonts installed, though not via that package, but installed manually, and all my fonts look good to me. 

The defaults shown in the fonts tab of System->Preferences->Appearance are as showing in the screenshot below.  I think I changed only the window title font to bold, and the size of desktop fonts to 9, but otherwise all are as at install, if I remember correctly.  Perhaps you can change yours back to that and see if it all looks right again.

---

### Post by s0ulkeeper on 2009-12-26
if i uninstall it via terminal would it go back to the default font set ? if not how do i make sure it does
fyi my font preferences are the same as yours right now

---

### Post by hariks0 on 2009-12-26
Try booting from your live CD and note down the settings. Reboot as usual and change the settings to the ones of live CD.:)

---

### Post by s0ulkeeper on 2009-12-26
thanks

---

### Post by slacka-vt on 2010-02-08
FYI

Application font = Sans   10
Document font = Sans   10
Desktop font = Sans 10
Window title font = Sans Bold   10
Fixed width font = Monospace   10

Some times if the fonts look crappy you need to adjust the Rendering ( i.e. Subpixel smoothing for LCD displays )

~slacka

---

