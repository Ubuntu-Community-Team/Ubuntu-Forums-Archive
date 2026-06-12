---
title: "add a line inside text document"
date: 2011-04-07
forum: Desktop Environments
---

### Post by 71GA on 2011-04-07
Hello!

I have a quite tricky task to do. I have a text document listed below (that is just a part of it but you can see the repeating sample):

```
[COLOR="RoyalBlue"]lpc_api.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/lpc_api.c \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_api.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h[/COLOR]
[COLOR="SeaGreen"]lpc_arm922t_cp15_driver.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/lpc_arm922t_cp15_driver.c \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_arm922t_cp15_driver.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_arm922t_arch.h[/COLOR]
[COLOR="SandyBrown"]lpc_bmp.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/lpc_bmp.c \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_bmp.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_colors.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_heap.h  [/COLOR]

```
I need to add lines betwen colored parts of text, so the document would be changed like this:

```
[COLOR="RoyalBlue"]lpc_api.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/**lpc_api.c** \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_api.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h[/COLOR]
          gcc -c **lpc_api.c**
[COLOR="SeaGreen"]lpc_arm922t_cp15_driver.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/**lpc_arm922t_cp15_driver.c** \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_arm922t_cp15_driver.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_arm922t_arch.h[/COLOR]
          gcc -c **lpc_arm922t_cp15_driver.c**
[COLOR="SandyBrown"]lpc_bmp.o: \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/source/**lpc_bmp.c** \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_bmp.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_types.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/include/stdint.h \
 /home/ziga/projects/cs_lite/bin/../lib/gcc/arm-none-eabi/4.5.1/../../../../arm-none-eabi/include/stdint.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_colors.h \
 /home/ziga/Dropbox/diploma/86x_linux/IDE_eclipse/eclipse_projects/LPC3141_SHELL_timer_makefile/include/lpc_heap.h  [/COLOR]
          gcc -c **lpc_bmp.c**
```

Note that behind gcc comand there should stand a file with extension ".c" (this file is allso found in colored parts of text and I made it bold for easier reading). I made it bold for easier reading. And important! BEFORE gcc there should be one TAB.

---

### Post by gobbledigook on 2011-04-07
man sed :)

---

### Post by 71GA on 2011-04-07
> **gobbledigook said:**
> man sed :)
HUH? that tels me very little :)

---

### Post by gobbledigook on 2011-04-14
my apologies.... 

type it in the terminal or [google it]("http://www.google.co.uk/#sclient=psy&hl=en&site=&source=hp&q=man+sed&aq=f&aqi=&aql=&oq=&pbx=1&fp=e942b200032f8d2a")

man = manual 

sed = stream editor

it will enable you to write a script to insert a line/s at whatever point you wish of your text document

---

### Post by 71GA on 2011-04-14
Thank you.

---

