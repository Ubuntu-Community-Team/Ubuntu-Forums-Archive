---
title: "svgs library installation for  doing  computer  graphics program  using  c -lang."
date: 2010-08-11
forum: Education &amp; Science
---

### Post by manish_raj on 2010-08-11
hi,this is manish  raj   . *I* m computer science engineering student .I am not getting the output in computer graphics program using c on ubuntu .i had already install svga library .my program is  compiling but virtual console is not display output ............
                                      please help me .......

---

### Post by gunksta on 2010-08-11
There aren't too many threads in this forum focused on C, c-lang, etc. While there are a couple of people on the forum who use C, I have not seen them discuss SVG output. I'm not sure that this is necessarily the best place to post your question. The general programming sub-forum might be a better place for your question.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

I also recommend providing more information in your request for help. From your post, I can see that you are programming in C and compiled via c-lang. (I assume using gcc.) And I know that you have installed a SVG library. That's not a lot of information. I would suggest providing the following information:


[LIST]
[*]Version of Ubuntu
[*]The name/version of libraries being called in your routine.
[*]Any warnings produced by c-lang
[*]**The code itself.** This is critical. You wrote a program which compiles, but doesn't do what you want it to do. Why? I don't have a clue and it is unlikely anyone will figure out the problem without being able to see the actual code.
[/LIST]
It has been a long time since I used C as a primary language, so I doubt I can help you myself but I do think my suggestions will help you ask a better question. I'm sure there are people in the programming sub-forum with the expertise you need.

Good Luck.

---

### Post by kiran r on 2010-10-17
I to had the same problem n i was able to solve it by editing libvga.config
follow the steps below:
1. type this in terminal** sudo nano /etc/vga/libvga.config**
2.search for something that look like-------># If a chipset driver gives trouble, try forcing VGA.

# chipset VGA           # Standard VGA
# chipset EGA           # EGA
# chipset ET3000        # Tseng ET3000
# chipset ET4000        # Tseng ET4000
# chipset Cirrus        # Cirrus Logic GD542x
# chipset TVGA          # Trident TVGA8900/9000
# chipset Oak           # Oak Technologies 037/067/077
# chipset S3            # S3 chipsets
# chipset GVGA6400      # Genoa 6400
# chipset ARK           # ARK Logic
# chipset ATI           # old ATI VGA
# chipset Mach32        # ATI Mach32
# chipset ALI           # ALI2301
# chipset Mach64        # ATI Mach64 - deprecated
# chipset ET6000        # Tseng ET6000
# chipset APM           # Alliance Technology AT 24/25/3D
# chipset NV3           # nVidia Riva 128 / TNT / GeForce
#*here i have removed the # symbol to enable chipset driver vesa type (most probable type)*
 **_chipset VESA_ **         # nicely behaved Vesa Bioses
# chipset MX            # MX86251 (some Voodoo Rush boards)
# chipset PARADISE      # WD90C31
# chipset RAGE          # RagePro (and might work with some older mach64)
# chipset BANSHEE       # Banshee/V3.
# chipset SIS           # SiS 5597/6326/620/530 cards / integrated vga.
# chipset I740          # Intel i740 based cards.
# chipset NEOMAGIC
# chipset LAGUNA        # Cirrus Logic Laguna series (546X)
# chipset FBDEV         # Use kernel fbdev, instead of direct hardware.
3.save it (cntrl+x i believe u know it)
then again compile it....

I HOPE THIS SHOULD WORK.......IF THIS DOESNT WORK TRY THE CHIPSET U R WORKING WITH 
GOOGLE U R CHIPSET NAME U ILL GET SOME INFO..........BEST OF LUCK:KS

---

