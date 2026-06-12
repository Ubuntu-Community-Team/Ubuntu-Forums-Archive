---
title: "Help with mixed-cd games"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by nrgenova on 2007-09-03
I have, for weeks now, been trying to have any luck at all with my backups of Sega CD and PC-Engine-CD games. My game collection was stolen, and I am trying to restore/use backups.

I can not find a program on linux (including k3b and nero) that will burn a mixed-cd from a cue or ccd image. It always gives me various errors about not being a readable type of file, not being a valid image, etc. I know k3b and nero both support cue/bin and cue/img files, and from previous experience, k3b DOES burn ccd/img files as well.

I tried mounting all of them with cdemu (which works fine normally) and it gives me the same not a valid image speech. cdemu supports cue and ccd as well, so I really don't understand.

The cues and ccds ARE correct, I have used them to make perfect copies in Windows years ago, and I can get the files to play just fine in an emulator (The Sega CD ones, at least.)

Why won't anything read these? I'm tired of wasting blank cds!

I have been a loyal linux user for years now, and I would hate to have to install Windows just to burn some cds. I hate the thought of it.
Linux programs have always been weak in supporting cd images (other than iso) properly.

---

### Post by ddrichardson on 2007-09-04
Its a quick terminal job but the cue and bin files must have the same filename:```
cdrdao write --device 0,0,0 --speed 8 --eject filename.cue
```

Obviously put the numbers in that correspond to your device:```
cdrecord --scanbus
```Will tell you this.

---

### Post by edemark on 2007-09-04
Hi
I had some similar problems with bin/cue images. I found a cure that is somehow wierd. I use the ultraiso program via wine to remake the images (i use convert from bin/cue to bin/cue) then it can be written on cd with Brasero.

I know is something strange but i have saved up some good old games this way

hope it helps

---

