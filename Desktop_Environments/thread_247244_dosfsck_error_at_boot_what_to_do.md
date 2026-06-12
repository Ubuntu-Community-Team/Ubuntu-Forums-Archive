---
title: "dosfsck error at boot: what to do?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by suoko on 2006-08-30
Hi, 

the following message appear at boot while checking all filesystems.

"There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/69, 432:4c/6d, 433:44/75, 434:52/6f, 435:20/76, 436:6d/65
  , 437:61/72, 438:6e/65, 439:63/20, 440:61/73, 441:6e/75, 442:74/70
  , 443:65/70, 444:ff/6f, 445:0d/72, 446:0a/74, 447:45/69, 448:72/2e
  , 449:72/ff, 450:6f/0d, 451:72/0a, 452:65/45, 453:20/72, 454:64/72
  , 455:69/6f, 456:73/72, 457:63/65, 458:6f/20, 459:ff/64, 460:0d/69
  , 461:0a/73, 462:50/63, 463:72/6f, 464:65/ff, 465:6d/0d, 466:65/0a
  , 467:72/50, 468:65/72, 469:20/65, 470:75/6d, 471:6e/65, 472:20/72
  , 473:74/65, 474:61/20, 475:73/75, 476:74/6e, 477:6f/20, 478:20/74
  , 479:70/61, 480:65/73, 481:72/74, 482:20/6f, 483:72/20, 484:69/70
  , 485:61/65, 486:76/72, 487:76/20, 488:69/72, 489:61/69, 490:72/61
  , 491:65/76, 492:0d/76, 493:0a/69, 494:00/61, 495:00/72, 496:00/65
  , 497:00/0d, 498:00/0a, 506:bd/c2, 507:cc/d1"

I then tried to run dosfsck manually after unmounting the affected partition (which is /dev/hda1 with Xp on it) and the result is a question:

1) Copy original to backup
2) Copy backup to original

What do I choose not to lose anything of my windows ?
Consider I have ALREADY executed scandisk and defrag within windows.


Many thanks.

Gabriele

---

### Post by xtknight on 2006-08-30
Have you run **chkdsk /f C:** in Windows (with fix option)?  Replace C: with the affected drive letter.  This should sync your MFT with the backup MFT.

---

