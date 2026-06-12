---
title: "KDE4 Desktop Icons Don't Work?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by Megatog615 on 2008-02-06
Ever since I upgraded to KDE4, none of my desktop icons are launchable. They just sit there right now and are useless. If I click them they don't launch. I've looked everywhere and cannot find any info on this. Is this a known KDE4 issue?

---

### Post by Bubba64 on 2008-02-06
You probably need to post more information such as the computer information for a better response.

---

### Post by Megatog615 on 2008-02-06
I don't see how my computer information should make a difference. I'm running KDE4 on Gutsy Gibbon. On two machines my icons don't work.

---

### Post by jlacroix on 2008-02-06
The problem you're facing (I'm experiencing it too) is due to whatever genius out there decided to change the commands of the programs.

For example, under KDE4, Konsole is supposed to be launched with the command "konsole-kde4", and Dolphin would be "dolphin-kde4".

The commands were changed to remove the "-kde4" suffix, and you have a problem because your menu is expecting them to still have the -kde4 suffix. As a result, the commands in your menu are not correct, so they cannot launch.

You could use the file open dialog to open your programs. (ALT+F2). You will notice if you type any of the KDE4 application commands without the suffix they will all work.

You could run kmenuedit and correct them yourself. However, I don't know if an update is going to change the commands back.

My guess is that if you use kmenuedit to update your menu, the packages don't rename the commands like they're supposed to. I'm not sure about that, but whoever packaged KDE 4.0.1 should be slapped in the face. I bet the packages weren't even tested!!!

Edit: [https://bugs.launchpad.net/ubuntu/+bug/189793](https://bugs.launchpad.net/ubuntu/+bug/189793)
I just posted this bug there. If you have time please go there and let them know you too are having this problem.

---

### Post by hasinasi on 2008-02-06
well, as far as I can see, I now have to start Dolphin in kde4 by simply typing "dolphin" rather than "dolphin-kde4". well, let's assume there is a good reason for that. ok, I have to change all my shortcuts. not the end of the world. however, how the heck can I know start the kde4 version of dolphin (and all the other apps) in kde3? 
since kde4 is still not very usable, using the kde4 apps and getting used to them while still operating in kde3 was an interesting route for me. is this now gone? (of course "dolphin" in kde3 will simply launch the kde3 version). 
any ideas, here? 
--hasi

---

### Post by Megatog615 on 2008-02-06
> **jlacroix said:**
> The problem you're facing (I'm experiencing it too) is due to whatever genius out there decided to change the commands of the programs.

For example, under KDE4, Konsole is supposed to be launched with the command "konsole-kde4", and Dolphin would be "dolphin-kde4".

The commands were changed to remove the "-kde4" suffix, and you have a problem because your menu is expecting them to still have the -kde4 suffix. As a result, the commands in your menu are not correct, so they cannot launch.

You could use the file open dialog to open your programs. (ALT+F2). You will notice if you type any of the KDE4 application commands without the suffix they will all work.

You could run kmenuedit and correct them yourself. However, I don't know if an update is going to change the commands back.

My guess is that if you use kmenuedit to update your menu, the packages don't rename the commands like they're supposed to. I'm not sure about that, but whoever packaged KDE 4.0.1 should be slapped in the face. I bet the packages weren't even tested!!!

Edit: [https://bugs.launchpad.net/ubuntu/+bug/189793](https://bugs.launchpad.net/ubuntu/+bug/189793)
I just posted this bug there. If you have time please go there and let them know you too are having this problem.
No, what I mean is, my **desktop icons** don't work. You know, icons on the desktop, not in the menu.

---

### Post by jlacroix on 2008-02-06
> **Megatog615 said:**
> No, what I mean is, my **desktop icons** don't work. You know, icons on the desktop, not in the menu.

Yeah, and I'm saying that it's probably the same problem.

---

### Post by coolclassic on 2008-02-07
Why not recreate your desktop icons and remove your old ones?

---

### Post by landcross on 2008-02-07
No doubt everyone has the same problem. I have now removed KDE 4 and gone back to version 3.
I expect that renaming Icons would create a problem for me as I also use Gnome and XFCE.

---

### Post by jlacroix on 2008-02-07
If you rename the icons, who's to say that an update won't change the commands back, making the icons useless again?

---

### Post by samwyse on 2008-02-07
The KDE4 apps are in /usr/lib/kde4/bin/. Launch Dolphin from KDE3 with /usr/lib/kde4/bin/dolphin

My menu entries have the proper path.

---

### Post by jlacroix on 2008-02-07
> **samwyse said:**
> The KDE4 apps are in /usr/lib/kde4/bin/. Launch Dolphin from KDE3 with /usr/lib/kde4/bin/dolphin

My menu entries have the proper path.

I'm glad it's working for you, but it doesn't work for me and several others.

---

### Post by samwyse on 2008-02-07
> **jlacroix said:**
> I'm glad it's working for you, but it doesn't work for me and several others.

Working is a bit subjective. I don't think it's currently worth running other apps than the games, or just kpat in my case :)

---

### Post by Megatog615 on 2008-02-07
Well they didn't work even before they renamed the binaries.

---

### Post by hasinasi on 2008-02-09
thanks very much for your contribution, samwyse!
using /usr/lib/kde4/bin/, I got everything to work again. 
--hasi

---

