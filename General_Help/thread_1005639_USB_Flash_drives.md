---
title: "USB Flash drives"
date: 2008-12-08
forum: General Help
---

### Post by blazemore on 2008-12-08
Do USB flash drives fail after a certain number of writes or reads? Is it safe, for example, to put your swapfile on one, or use one for other intensive operations like a cache file.
At the moment I use mine for file storage and a working Cubase project.

---

### Post by Het Irv on 2008-12-08
I have had flash drives phisically break after heavy use, but that was the result of the actuall plugging and unplugging of the drive that weakened the outer casing...

but I don't know about the drive itself, but I think on of the new things that Microsoft did with Vista is allow users to uses their Flash Drives as a speed booster.  Without doing much reseach, I assume that it uses the Flash Drive as a cache or maybe a swap, so what you want to do may work... and even if the case breaks, I have more than one held together with tape.

---

### Post by Herman on 2008-12-08
A simple question, but it can have a complicated answer.

Just my opinion, (but I have been doing some reading and testing on this matter), good quality, or even average quality new flash memory will last for a very long time.
Old flash memory has about 10000 erase cycles per block, now flash memory commonly has more like 100000 erase cycles or even 10's of millions.

They use 'wear leveling' in the controller chip to rotate the blocks that get erased and then written to each time, so the wear will be spread out evenly around the whole flash memory stick, even if your operating thinks it's writing to the same partition or to the same file.

Therefore, a larger flash memory will last a lot longer than a small flash memory, and a flash memory with lots of spare room will last longer than one that's almost full.
Small flash memory is generally a little faster though.

Flash is fast to seek and read from, but writing to flash is relatively slow, because it needs to erase a whole block first, then write the data to a different block.

I use and recommend ReiserFS for flash memory, because it's ten to fifteen times faster for small files, making up for some of flash memory's slowness when writing to disc.
I don't do anything for saving disc writes like a lot of the experts recommend, but instead I find using most of the same tricks is good for increasing the speed anyway, so I use some of the same things now for the reason of speed, but not because I'm afraid of wearing out the flash.

Regards, Herman :)

---

### Post by dragos_iliescu_2005 on 2008-12-08
USB flash drives are designated mainly for files storage. Keep the swap or cache on the flash drive can be risky. I will not take this risk.

---

