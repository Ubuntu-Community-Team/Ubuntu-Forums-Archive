---
title: "DR-DOS boot problems????"
date: 2005-01-10
forum: General Help
---

### Post by Matt Dickins on 2005-01-10
I downloaded it, and burnt it as a bootable disk. Put it in my drive changed the BIOS to boot from CD before my HDD and then restarted. All looked hopeful until now it displays. Something about Caldera DR-DOS and wants me to input something into an A:\ prompt??????? P.S. There's no floppy in the floppy drive. :sad:

---

### Post by crandol on 2005-05-11
I got this same problem when I tried to run a Live CD for the first time. I'm not sure what the problem was but I suspect that the ISO was not burned to the CD properly. I overcame the problem by using a Windows XP based ISO image burner. I also set the burn speed to 8x (DO THIS!). The result was a bootable Unbutu CD.

When I had the problem listed above I had used Nero Express to try to burn the ISO image to the CD. I had selected the "make Bootable CD option" and I think that this did not extract the files from the ISO image onto the CD but rather simply copied the entire ISO to the CD as a single file. This is not, I believe, how the ISO works.

Here's that ISO "copy ISO to CD" utility.  

Filename:  ISORecorderV2B2.zip
Last know site available: [http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip](http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip)

Comments? I barely know what I'm talking about. . . :)  crandol.

---

### Post by Scud89 on 2005-07-01
[QUOTE=crandol]I got this same problem when I tried to run a Live CD for the first time. I'm not sure what the problem was but I suspect that the ISO was not burned to the CD properly. I overcame the problem by using a Windows XP based ISO image burner. I also set the burn speed to 8x (DO THIS!). The result was a bootable Unbutu CD.

When I had the problem listed above I had used Nero Express to try to burn the ISO image to the CD. I had selected the "make Bootable CD option" and I think that this did not extract the files from the ISO image onto the CD but rather simply copied the entire ISO to the CD as a single file. This is not, I believe, how the ISO works.

Here's that ISO "copy ISO to CD" utility.  

Filename:  ISORecorderV2B2.zip
Last know site available: [http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip](http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip)

Comments? I barely know what I'm talking about. . . :)  crandol.[/QUOTE]
 and what program did you use to burn it into, because i tried again with nero and it didnt work

---

### Post by xmastree on 2005-07-06
[QUOTE=Scud89]and what program did you use to burn it into, because i tried again with nero and it didnt work[/QUOTE]With Nero, you must use the "disk image or saved project" option. Then select the ISO as the file to burn.

I just looked at my dad's (this PC) installation of nero 5. If you close the wizard, go to file>burn  image and select the ISO from there, that ought to do it.

Once you have made the disc, you should be able to see files and directories on it if yoou look at it with explorer.

---

