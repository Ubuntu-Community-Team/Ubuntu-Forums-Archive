---
title: "Problem installing Hitman with wine!?"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by doh224 on 2007-07-18
hi all.... 

I have been searching the forum for a similar thread about problem installing Hitman in wine, but I couldn't find one with the same problem.. (I found a thread with someone saying that they had hitman installed in wine, so I guess that it is possible ;)) 

But here's the problem:

I inset the cd. Open the terminal and type:

```
 cd /media/cdrom(nummer)
```

```
wine setup.exe
``` (also tried with sudo wine ... but with same problem in the end)

And then the installation is running. 

I set the language to English, I agree to the licent agreement, chose the path that already is chosen, I create the program folder where it's already suggested that I should make it, I don't make any shortcut on the Desktop, and I don't install Directx 7.0.
NOW THE INSTALLATION STARTS............ and it's working fine until I make the 95%, and it's says:
"error making program folder" and the installation stops! :( (I've tried to change the program folder but with no success) the terminal type this while all this is happening:
```

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
akaran234@unix-desktop:/media/cdrom0$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoGetClassObject class {fbf23b40-e3f0-101b-8488-00aa003e56f8} not registered
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```  

thanks for any help :) 

-doh

---

### Post by DoktorSeven on 2007-07-18
If it goes to 95% it's probably already installed, does the directory exist under ~/.wine/drive_c/(wherever you said to install it)?

Sometimes installers have trouble making *launcher* directories (for the start menu).

---

### Post by doh224 on 2007-07-19
> **DoktorSeven said:**
> If it goes to 95% it's probably already installed, does the directory exist under ~/.wine/drive_c/(wherever you said to install it)?

Sometimes installers have trouble making *launcher* directories (for the start menu).

Yeah.... there is a folder with the name I gave it, but there's nothing but a setup folder with a locale.zip in it, and a small .ini file?

---

