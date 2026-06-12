---
title: "Speeding up Xubuntu"
date: 2006-08-29
forum: Desktop Environments
---

### Post by DMAthlon on 2006-08-29
I went from Ubu to Xubu a few days ago and experienced a noticable increase in speed. however many programs are still sluggish and take a while to load. are there any processes i can disable to noticeably increase speed? As you can see in my signature I'm using an old goat of a machine so anything will probably help, thanks!

(I dont have much knowledge of linux but I'm learning so forgive me if i say anything incredibly stupid about linux, thanks.)

---

### Post by xyz on 2006-08-29
Just a couple of ideas to try and lighten things up:
[http://www.ubuntuforums.org/showthread.php?t=189192/](http://www.ubuntuforums.org/showthread.php?t=189192/)
[http://www.pcworld.com/article/id,119699-page,1/article.html#](http://www.pcworld.com/article/id,119699-page,1/article.html#) Here look for Xfce.

---

### Post by twowheeler on 2006-08-29
I am in the same boat -- my old goat is an AMD K6/2 500 MHz running xubuntu.  The system services can be enabled or disabled with System --> Administration --> Services.  Do this *cautiously* however as you could shut down something important.  For example, I have mysql installed and running, and am not using it now, so I could disable that.  Similarly my postfix service could go since I get all of my mail on the web.  When in doubt, leave it running.

However the best thing you could do would be to add memory if your machine will take it.  Raising my total to 640MB made a big difference, and I would take it to 1GB if the machine would accept it.

Finally, make sure that DMA is turned on for your disk(s), it makes a big difference in everything you do.  Search the forums for how to use hdparm if you are not sure how to do this.

---

