---
title: "oh dear lord... somebody help"
date: 2009-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brianlpowers on 2009-02-06
so i installed intrepid with wubi from vista just to try things out. loved the os, so i decided to start installing everything in ubuntu so it would be a windows replacement.

no problems whatsoever... i even got my graphics card and  microphone working (xps m1330)

the problem came when i needed to use gsak (geocaching program) that i could never install on ubuntu. i went to boot into vista, got about halfway through the green bar scrolling at the bottom of the screen, when i got sent to the automated recovery.

as most vista users know, this is essentially worthless. i don't think any startup problem i have ever troubleshooted has ever been solved by this.

anyway, i ran chkdsk /r twice from the cmd prompt, fixed all issues and tried to load up vista again. no such luck, same result. i ran through basically everything i could think of, to no avail. as a last ditch effort, i tried to rebuild the BCD with bootrec.exe to no avail. then microsoft said to do this:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd

so i did

and now my laptop is bricked. i realize now that was a bad idea since vista actually did start to boot... now i can't start in windows, or ubuntu.

the worst part is that i'm in new zealand, and don't have my vista disc with me. i burned a copy of the ubuntu cd, and so i'm going from there.

does anyone know how to reverse this from booting into ubuntu from live cd?

---

### Post by armandh on 2009-02-06
use the live ubuntu cd to backup all the files you wish to save.

get some one from home to send you the vista disk and reinstall vista.

reinstall the saved files.

use vista's partition editor to reduce the vista partition by 10G

install ubuntu to the unpartitioned space by selecting the "guided use largest unpartitioned space" option.

discard wubi disk

---

### Post by caljohnsmith on 2009-02-06
Can you boot your Ubuntu Live CD? If you can, I think it would help to first get some more info about your system, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully give some clues what might be wrong with your Vista install.

---

