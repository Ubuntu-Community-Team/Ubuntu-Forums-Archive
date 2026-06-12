---
title: "Can't Play Audio CDs"
date: 2006-02-17
forum: Desktop Environments
---

### Post by malacoda on 2006-02-17
I'm a bit puzzled on this one...

I can't play audio CDs.  Konqueror shows the files - whether they be wav, mp3, ogg, or whatever, but no matter what app I use - Amarok, Kaffine, Juk - none can play them.  

The drive is a Rosewill DVD-RW (capable of all the usual CD-RW functions as well of course).  If I put in a DVD - whether it be an off the shelf movie or a disc of burned tv shows - they play just fine.

One thing I don't understand (still being somewhat of a noob) - when I put in a DVD, say of burned tv shows for example, the system automounts the drive and when I'm done watching it I naturally have to unmount before I'm able to eject. 

When I put in an audio CD (haven't tried any data cds as I don't have any on hand) it doesn't show as 'mounted' even though I can see all the files contained on the disk.  

Now I thought the reason it didn't show as mounted was because audio CDs don't contain a file system, only loose files.  But if that's the case why does a DVD with no filesystem - just burned tv shows - show as mounted and require unmounting before it can be ejected?

Anyway, because of this confusion on my part I don't know if the audio cds should 'mount' and so don't know if this is a mounting issue or shouldn't mount and meaning it's some other problem... so I have no idea where or how to start troubleshooting.

If anyone has any suggestions as to why DVDs are accessed and files accessed/played just fine - regardless of the file type (divx movie, mp3 audio, pdf document all opened just fine) - but CDs aren't and what I can try in order to fix it I'd appreciate any input you have.

regards,
Malac

---

### Post by amoser on 2006-02-18
Does Armork, Juk, etc... give you any errors about playing the Audio CD, or do you just not have any sound.

~Alan

---

### Post by Jucato on 2006-02-18
My Kaffeine is able to play Audio CD's. weirdly, KsCD has no sound.

Btw, you don't need to unmount CD drives to eject them. Just right-click > Eject. Otherwise, it won't automount anymore when you insert another CD.

---

### Post by infoseeker on 2006-02-18
I presume you do have the analog audio cable connected between the back of the CD player and the sound card/motherboard.  Some players use digital playback and others analog.  The cable normally has 3 pins and is black and flat ;)

---

### Post by malacoda on 2006-02-18
Thanks for the replies.

The message Kaffine gives is "No AudioCD in drive or wrong path to drive."
Amarok responds "Some media could not be loaded, not playable."

I'm almost positive I did connect the analog cable on the back of the drive but will crack the case to verify.   In fact, I can play CDs in Windows - which I assume would also rely on the analog cable - and I'm fairly certain I did play one or two music CDs about 6 months ago just after first installing Kubuntu. (can't remember for sure though... at the ripe old age of 35 my mind just isn't what it used to be...)

Again, any help/input you can offer would be appreciated.

Regards,
Malac

---

### Post by Video Toaster on 2006-05-11
[QUOTE=malacoda]Thanks for the replies.

The message Kaffine gives is "No AudioCD in drive or wrong path to drive."
Amarok responds "Some media could not be loaded, not playable."

I'm almost positive I did connect the analog cable on the back of the drive but will crack the case to verify.   In fact, I can play CDs in Windows - which I assume would also rely on the analog cable - and I'm fairly certain I did play one or two music CDs about 6 months ago just after first installing Kubuntu. (can't remember for sure though... at the ripe old age of 35 my mind just isn't what it used to be...)

Again, any help/input you can offer would be appreciated.

Regards,
Malac[/QUOTE]
*bump*

I'm having the exact same problem now!  Playing Audio CDs works sporadically for me in Kubuntu - I get the same message as malacoda got in Kaffeine.  The only way I got it to consistently work was:

1.  Open Kaffeine and click "Audio CD"
2.  Click cancel on the error box
3.  Go to Open URL
4.  Type in media:/hdc

It doesn't work if I don't first click "Audio CD" and get the error message.

Any ideas for how to fix this?  Is this a KDE problem or something to do with xine?  (or is it just a Kubuntu problem?)

---

### Post by Video Toaster on 2006-05-11
Just found this bug:

[https://launchpad.net/bugs/41962](https://launchpad.net/bugs/41962)

---

