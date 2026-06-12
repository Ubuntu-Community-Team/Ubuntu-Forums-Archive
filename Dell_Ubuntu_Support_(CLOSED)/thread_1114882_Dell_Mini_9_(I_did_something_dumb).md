---
title: "Dell Mini 9 (I did something dumb)"
date: 2009-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denimwizard on 2009-04-03
Yes so I did something dumb. I removed the boot flag off of one of the partitions of my HD. 

Is it possible to boot from a USB and flag the partition ?

The reason the hard drive has multiple partitions is because when i got my mini back in October, Dell didn't partition the whole drive. So I took it to my brother who has more knowledge of linux than I do and he created an additional partition that used the rest of the drive. Everything was fine until last night when Tried to install something and I got an error saying the boot partition was full. So I tried using the Partition manager to either resize it or combine the two. It wouldn't let me so I thought may be removing the flag would open up the tools  and allow them to be used, that wasn't the case (yes I know..Foolish). 

Anyway, any help with this problem would be appreciated. I have a spare USB HD as well as a Thumb Drive.

---

### Post by anjilslaire on 2009-04-03
I would try booting ubuntu via your thumb drive, load up gparted and try to set the flag again.

---

### Post by Denimwizard on 2009-04-06
Yeah i did that Friday and it works, Still couldnt resize the partition so i reloaded it with 8.04.2, I love the effects however the sound doesnt work now. It did when I first reloaded. Now i have checked the alsa C0 command in the terminal and everything set to high. So I am not sure what is wrong.

---

### Post by anjilslaire on 2009-04-06
For sound, check this:
[http://ubuntuforums.org/showpost.php?p=6178990&postcount=3](http://ubuntuforums.org/showpost.php?p=6178990&postcount=3)

---

### Post by Denimwizard on 2009-04-06
Thanks I will try that !

---

### Post by Denimwizard on 2009-04-07
Hey it worked thank you!

---

