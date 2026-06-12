---
title: "Shared Graphics on Dell 6400n"
date: 2007-10-04
forum: Dell  Ubuntu Support
---

### Post by Yanski on 2007-10-04
How do I find out how much memory is being used for the shared graphics? And can I adjust it if I want..??](*,)

---

### Post by JBAlaska on 2007-10-04
Your bios should be the place that you may be able to allocate more shared video memory.

As to seeing how much, check the bios, or you can try ```
lspci -v | more
```, that may show shared video memory

---

### Post by Yanski on 2007-10-04
Thanks...will try the bios.
lspci -v | more just gave me too much about everything..!! :confused:

---

### Post by Yanski on 2007-10-04
According to the bios the shared graphics is only using 8mb of the 2 gig that is installed.. However the bios reports that those fields cannot be changed.. I have looked through every section and cannot find any part of it that lets you increase or decrease the amount..  ](*,)

---

