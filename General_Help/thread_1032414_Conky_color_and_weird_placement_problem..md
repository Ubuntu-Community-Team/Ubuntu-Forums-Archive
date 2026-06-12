---
title: "Conky color and weird placement problem."
date: 2009-01-06
forum: General Help
---

### Post by iamyourdemize on 2009-01-06
Let me preface this by saying that I am an Ubuntu newbie having just installed it. I feel like I am picking things up quickly however. I am having a problem with my conky file that I just cannot figure out. If you notice my RAM bar you can see that the icon that I used is misaligned to the right. This happens no matter what icon I use, or even if I put the CPU code up there instead. I am at a loss about how to change this.

The second problem is under “MEM Usage” you will see a bright hard to read orange. It is the exact same orange (CC6600) that I used on the date and time. Why is it so much brighter? Sorry in advance if my conky file is poorly constructed….it is my first attempt.

Thanks for any help!

---

### Post by chamber on 2009-01-06
I think that you it could be a good idea to post your conkyrc [HERE]("http://ubuntuforums.org/showthread.php?t=281865").  I've had great help with my conkys there.

---

### Post by easybake on 2009-01-06
> **iamyourdemize said:**
> Let me preface this by saying that I am an Ubuntu newbie having just installed it. I feel like I am picking things up quickly however. I am having a problem with my conky file that I just cannot figure out. If you notice my RAM bar you can see that the icon that I used is misaligned to the right. This happens no matter what icon I use, or even if I put the CPU code up there instead. I am at a loss about how to change this.

Spacing can easily get messed up from switching between fonts. You can put a $font variable before the section that has the Ram bar that way it goes back to default spacing size. 

In the future, rather than deal with spaces, you can use the goto variable. This allows you to tell where to place everything to the exact pixel. You would use it by like ```
 ${goto 24}Hello
``` This would place the word Hello 24 pixels in from the edge of the conky.

> The second problem is under “MEM Usage” you will see a bright hard to read orange. It is the exact same orange (CC6600) that I used on the date and time. Why is it so much brighter?

Sometimes font size can change the way a color looks. Your best bet would be to just find a darker orange for those lines.

---

