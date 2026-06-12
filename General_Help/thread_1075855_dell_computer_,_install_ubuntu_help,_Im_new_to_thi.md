---
title: "dell computer , install ubuntu? help, Im new to this"
date: 2009-02-20
forum: General Help
---

### Post by Thowsen on 2009-02-20
Hello, Ive tried ubuntu before on my workstation but i found out it wasnt such a good idea cuz i play alot of games n so on. but lately I got home a dell gx240 (the small one) from school, n its booting windows xp.

when i boot i first get the bootscreen n after that if i dont hit f12 (bootoptions) or f2 (setup) it boots a thing that says 
press enter to install windows
or press esc to resume.

if i press esc it boots windows xp (the school network, so i cant log on) 
n if i press enter with the feisty fawn live cd in, it just asks me to check the bootcd.

so how am i supposed to do, ive read alot of ''activating acpi=force'' n to press f6 to enter that option. but where do i press f6 n where do i write the acpithing.

all help is apprieciated. I would really like to run ubuntu on that pc =)









edit: its hardy heron x32 , not feisty fawn . pardon me
edit2: sry posted in the wrong part of the forum. please remove this thread

---

### Post by spiderbatdad on 2009-02-20
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Thowsen on 2009-02-20
> **spiderbatdad said:**
> [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I dont even get to that screen

---

### Post by spiderbatdad on 2009-02-20
if you dont get the grub menu screen, press esc just after booting. This should show the grub screen where you select which kernel to boot...use the methods outlined as the second method "changing options temporarily"...that is; press 'e' to edit the kernel. Then use the arrow key to move to the line that begins with the word kernel, and press 'e' again. Now use the arrow key and go to the end of the line of text, and delete 'quite splash' replace with your boot option: acpi=force then hit enter and then 'b' to boot.

If this solves your problem you will have to permanently edit the file /boot/grub/menu.lst

---

### Post by Thowsen on 2009-02-20
> **spiderbatdad said:**
> if you dont get the grub menu screen, press esc just after booting. This should show the grub screen where you select which kernel to boot...use the methods outlined...that is; press 'e' to edit the kernel. Then use the arrow key to move to the line that begins with the word kernel, and press 'e' again. Now use the arrow key and go to the end of the line of text, and delete 'quite splash' replace with your boot option: acpi=force then hit enter and then 'b' to boot.
well i dont think you understand my problem , the problem is that the computer doesnt even get to the step where it starts to read the cd.

---

### Post by spiderbatdad on 2009-02-20
So if I understand now...the cd will not load or run? I would say the cd is no good. Try downloading a new iso image and burn at no faster than 2x. Make sure you burn as an image and not as a file.

---

### Post by mpsii on 2009-02-20
It sounds like your boot order is network (LAN) card first. Press F2 and check your boot order. Make sure CDROM is the first in the list and LAN is last.

---

### Post by Thowsen on 2009-02-21
> **mpsii said:**
> It sounds like your boot order is network (LAN) card first. Press F2 and check your boot order. Make sure CDROM is the first in the list and LAN is last.
the cd is good. yeah the computer boots from cd first. but the computer is a office computer so it tries to find a lan connection i think. My school has a big lan that every computer log on to while accessing the computer

sry for my bad english , hope you understand.

---

### Post by jespdj on 2009-02-21
How did you burn your Ubuntu CD? It sounds like you maybe did this wrong, so that your Ubuntu CD is not a bootable CD. Did you just burn the ISO on an empty CD as a file? That's not how you should burn the ISO.

Read the following instructions on how to burn the ISO image that you downloaded to a CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Thowsen on 2009-02-21
> **jespdj said:**
> How did you burn your Ubuntu CD? It sounds like you maybe did this wrong, so that your Ubuntu CD is not a bootable CD. Did you just burn the ISO on an empty CD as a file? That's not how you should burn the ISO.

Read the following instructions on how to burn the ISO image that you downloaded to a CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
its bootable, I've used it before on my moms laptop ;)

---

### Post by spiderbatdad on 2009-02-21
Maybe the memory has failed. Do you have access to other RAM sticks? I actually had a similar experience recently with a computer the local school threw out. ( yes in the trash!) I thought the hard drive was bad...couldnt get booted up. Finally tried new RAM, and the machine is my server box now.

---

### Post by Thowsen on 2009-02-21
> **spiderbatdad said:**
> Maybe the memory has failed. Do you have access to other RAM sticks? I actually had a similar experience recently with a computer the local scholl threw out. ( yes in the trash!) I thought the hard drive was bad...couldnt get booted up. Finally tried new RAM, and the machine is my server box now.
well , it can boot xp if i press esc when the ''enter / esc'' screen pops up. 
Im thinkin about puttin the harddrive into my main computer and install ubuntu there, and then throw it back into the dell computer.
do you think that will work?

---

### Post by spiderbatdad on 2009-02-21
I dont think so but always worth a try. Funny I could get windows booted too. I tried clearing cmos, and everything I could think of. I had really given up. A month later I tried again. I dont know why, and it booted into the live cd...like magic. So I think the problem is in the ram, but not sure...even in my case.

---

### Post by Thowsen on 2009-02-21
> **spiderbatdad said:**
> I dont think so but always worth a try. Funny I could get windows booted too. I tried clearing cmos, and everything I could think of. I had really given up. A month later I tried again. I dont know why, and it booted into the live cd...like magic. So I think the problem is in the ram, but not sure...even in my case.

I'll try the ramsticks tonight. n the harddrive to. n i can send u an update. thanks man , I really apprieciate this

---

### Post by Thowsen on 2009-02-21
new update!
Ive tried to install ubuntu on the harddrive from my gamerig.
the one i use right now. the install was successfull.
but when i put the harddrive back to the dell computer i was givven this message from the kernel when booting ubuntu

'' starting up ...
this kernel requires an x86-64 CPU but only detected an i586 CPU.
Unable to boot - please use a kernel appropriate for your CPU. ''

what shall i do?
I guess i have to install another ubuntu dist. but which? n where do i find it?
its still a dell gx240

---

### Post by abn91c on 2009-02-21
> **Thowsen said:**
> new update!
Ive tried to install ubuntu on the harddrive from my gamerig.
the one i use right now. the install was successfull.
but when i put the harddrive back to the dell computer i was givven this message from the kernel when booting ubuntu

'' starting up ...
this kernel requires an x86-64 CPU but only detected an i586 CPU.
Unable to boot - please use a kernel appropriate for your CPU. ''

what shall i do?
I guess i have to install another ubuntu dist. but which? n where do i find it?
its still a dell gx240
I have a GX240, i Installed Kubuntu without problems, that PC has an ATI Rage 128 video card, it will not run compiz. The RAM is PC133 SDRAM. Here is a type of RAM I Added [http://www.geeks.com/details.asp?invtid=64X64PC133-16-MIC&cat=RAM](http://www.geeks.com/details.asp?invtid=64X64PC133-16-MIC&cat=RAM)
Just find a shop in you country where you can get some, BTW the max RAM for the GX240 is 1 Gig, aaaand it is a 32Bit system

---

### Post by Thowsen on 2009-02-21
> **abn91c said:**
> I have a GX240, i Installed Kubuntu without problems, that PC has an ATI Rage 128 video card, it will not run compiz. The RAM is PC133 SDRAM. Here is a type of RAM I Added [http://www.geeks.com/details.asp?invtid=64X64PC133-16-MIC&cat=RAM](http://www.geeks.com/details.asp?invtid=64X64PC133-16-MIC&cat=RAM)
Just find a shop in you country where you can get some, BTW the max RAM for the GX240 is 1 Gig, aaaand it is a 32Bit system
well.. thats not really my question. I already know that stuff since Ive been workin with those computers in school. but how did u get pass the ''safety card 3.1 max'' thing that comes up during boot for me? or did u even had that problem :(?

---

### Post by abn91c on 2009-02-21
> **Thowsen said:**
> well.. thats not really my question. I already know that stuff since Ive been workin with those computers in school. but how did u get pass the ''safety card 3.1 max'' thing that comes up during boot for me? or did u even had that problem :(?
My computer was a surplus from Indiana University, it has a standard integrated NIC as you know, I use a wireless USB network adapter. That"safety card" is not a standard card on Dells, If it's a separate card on the inside just pull it.

---

### Post by Thowsen on 2009-02-21
> **abn91c said:**
> My computer was a surplus from Indiana University, it has a standard integrated NIC as you know, I use a wireless USB network adapter. That"safety card" is not a standard card on Dells, If it's a separate card on the inside just pull it.
thanks man. I got to take a look ;) , i got mine from school too, for free

edit: man , i found that ******* :D lol.
now where do i found ubuntu for my cpu? the i586 dell cpu?

---

### Post by abn91c on 2009-02-21
> **Thowsen said:**
> thanks man. I got to take a look ;) , i got mine from school too, for free
You are welcome, one more thing just have the keyboard, mouse and LAN cable attached during set up, disconnect anything else like printers, external drives etc..

---

### Post by Thowsen on 2009-02-21
> **abn91c said:**
> You are welcome, one more thing just have the keyboard, mouse and LAN cable attached during set up, disconnect anything else like printers, external drives etc..
yeah but are all dists supported now? i got this error like '' kernel requires an x86-64 cpu but only detected an i586''

---

### Post by abn91c on 2009-02-21
> **Thowsen said:**
> yeah but are all dists supported now? i got this error like '' kernel requires an x86-64 cpu but only detected an i586''
Tha can only be you have the 64bit disk instead on the 32bit, go here to get it [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Thowsen on 2009-02-21
> **abn91c said:**
> Tha can only be you have the 64bit disk instead on the 32bit, go here to get it [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
what do you mean? I installed ubuntu with my gaming rig to the dell harddrive n then put it into the dell computer, then i got the error.
do you think it has something to do with that i installed ubuntu with my x64 q6600 cpu?

---

### Post by abn91c on 2009-02-21
> **Thowsen said:**
> what do you mean? I installed ubuntu with my gaming rig to the dell harddrive n then put it into the dell computer, then i got the error.
do you think it has something to do with that i installed ubuntu with my x64 q6600 cpu? the GX240 are older 32 bit systems if you download the 32bit version you will not have any more errors, and yes the HDD still thinks it is in the 64bit system.

---

### Post by Thowsen on 2009-02-21
> **abn91c said:**
> the GX240 are older 32 bit systems if you download the 32bit version you will not have any more errors, and yes the HDD still thinks it is in the 64bit system.
just realized what i did wrong, i installed a x64 ubuntu on the harddrive. thanks for everything. now my last question? how do i get the topic to say ''solved'' ?:popcorn:

thanks, Im sittin at the computer right now, i installed ubuntu from my gamerig :P the alternate ubuntu. n everything seems fine

---

