---
title: "Card reader and SD Card problem"
date: 2009-05-19
forum: General Help
---

### Post by kingnothing189 on 2009-05-19
Hello,

I 've got this problem here. I insert my SD card on my card reader and i try to copy some mp3 files in it. The file manager seems to do its job (I can see the files in the SD) but when i try to see the files from my mobile phone they just aren't there. Any possible explanation and/or solution..?

P.S. I tried copying the files with both dolphin and konqueror. My mobile has windows mobile 6.0 if that really matters.

I'm using kubuntu 9.04

---

### Post by SuperSonic4 on 2009-05-19
Are you looking in the right place on your phone? Some phones may not use the same directory structure as your computer.

FYI: Pressing F3 in dolphin will give you a twin panel file manager for easier copy and pasting ;). F4 will give you a terminal plugin

---

### Post by kingnothing189 on 2009-05-19
Thanks for your response SuperSonic4, and also thanks for the tips, didn't know dolphin could do that ^_^.

Yes I'm looking in the right directory on my phone but I can't see the files, I can only see them from my computer. I must mention that ONLY one time I succeeded in copying a file and the phone was able to see it, so I think something is wrong with kubuntu, a bug perhaps?

---

### Post by SuperSonic4 on 2009-05-19
I doubt it's a bug with kubuntu because it seems to be copying the files over. Do you unmount the SD card after copying the tracks or just pull it out?

If the card works in another device whether phone or computer it's like to be a phone bug, if it does not copy it's a card at all or kubuntu bug

---

### Post by kingnothing189 on 2009-05-19
I just pull the card out, does that matter?
Also... yes, it seems to be copying the files to the card but it takes zero-time to do it. I mean from the moment I drop the file to the card to the moment the copying process is completed not even a second passes...

I can see the files in another computer with Windows Vista though...


EDIT: I can see the file but i can't really read or copy it to the computer

---

### Post by SuperSonic4 on 2009-05-19
It could say it's written before it has actually written - particularly if you get seemingly instant transfers. Does the little info thing come up in the system tray when copying?

I think it'd be best to give it 30s-60s after the transfer is finished before unmounting it (right click in Places on the left and unmount)

---

### Post by kingnothing189 on 2009-05-19
No it doesn't come up at all. It should come up saying that I'm copying a file to a location, shouldn't it?

The only info I get about the copying process is a little description on the lower left window in dolphin saying that the copying is completed.

I must say this problem really pisses me off :P

---

### Post by SuperSonic4 on 2009-05-19
Yeah files not transferring is annoying - I'm using my SD card for the same reason, needing some tunes xD

What happens if you use the terminal. From the source directory press F4 for a terminal and try```
cp -v ~/file.mp3 /media/disk
``` - can you give the output of that?

where file is the path to the file (either drag and drop into terminal or use tab completion) and where /media/disk is the location of your SD card (you can find this out by pressing the location in dolphin)

---

### Post by kingnothing189 on 2009-05-19
Hmmm...

cp -v /media/WD Sata II/Music/Virgin Steele/(1998) Virgin Steele - Invictus/Virgin Steele - 13.Dominion Day.mp3 /media/MICROSD/Music
bash: syntax error near unexpected token `('

is there some wrong in the command I put and i get this error? :S

EDIT: I tried more simple paths like /home/user/Desktop/file.mp3 and I get the same error

---

### Post by SuperSonic4 on 2009-05-19
bash is mistaking the brackets for syntax, using an inverted comma should work:

```
cp -v '/media/WD Sata II/Music/Virgin Steele/(199 Virgin Steele - Invictus/Virgin Steele - 13.Dominion Day.mp3' /media/MICROSD/Music
```

I assume the SD card is mounted without any problems

---

### Post by kingnothing189 on 2009-05-19
I got the command working but I still can't read the file. It's getting annoying as you can guess... haha

---

