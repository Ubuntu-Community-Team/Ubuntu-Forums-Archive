---
title: "sound trobles in 2 debian installations ,i will be thankfull for help"
date: 2008-04-27
forum: Debian
---

### Post by cmay on 2008-04-27
hi . 
i am a non experienced debian user and i have 3 debian installations on 3 different computers now. i like to save old computers that others dont want so here i am whit 3 different debians . nr one works almost perfect. is a old fujitsu siemens that used to be a windows me machine. has got sound card/chipset that needs restricted firmware but it works whit debian. it can play sound and movies but does not record ? . any way that does not matter tome cos its very old 600 mhz processor and 300 mb ram . its my firts computer i dont wanna discard it since it works great.however i will like to learn how to fix these things by myselve. 

the other two are havin trouble whit sound. both of them are shuttle basics and at leats 3 years old. the test is to get them to play supertux whit sound and watch a dvd on totem. first one fails  playing dvd whit sound but has sound on supertux. great:)
but the other one can play dvd whit sound and not play supertux whit sound. 
having copied the right settings from my old comp that i love to play supertux on before i write any important letters or such since its my good old office machine. upgraded from windows me in 2006 i think to debian etch. 
they are all from the same dvd intallation dvds . i have also in the past had linux magazine dvd  etch version on my old computer but i just use the 3dvd set i had purchased as a burn per demand product. 

i dont use computers as a poweruser . i just need to acces the internet whitout getting virus or getting hacked and then i need to write an occationel letter once in a while. i have a new computer i just bourght whit the debian based 64studio as my computermusic studio. 
i wanna learn how to fix debian computers
 and then resell/give away them as a hobby. not to earn the living or for any kind of profit non what so ever. but help save the god old computers so they dont pollute that much. 
any assistance in my quest for an sollution to succefully pass the test of  play a game of supertux and then watch a dvd will be gratefully apriciated . 

sorry if have misspelled anything hope the meaning at leats is clear.
i have very poor eyesight so i dont cath all of the wrongspelled words evertime .

thanks for reading this.

---

### Post by markharding557 on 2008-04-30
post some more details about your malfunctioning computers such as specs,have you installed multimedia codecs etc

---

### Post by cmay on 2008-05-01
hi thanks for the reply,
i have two similar looking shuttles that i kinda saved.
or been ask to save any way. i try install linux on my freinds old computers when i can.

i have installed debian on both and libdvdcss2 thats all. from the 3dvd set and the libdcdcss2 i have from a cd i once burned as its not in the repo anymore. 
they have not been connekted to internet yet.
the motherboards are not the same. its a k9agm4 amdbased chipset the first one. the next is an asrock k7vt4a pro.
there is a extern grafich card in the one whit the asrock k7vt4a pro motherboard.
 i have also just  bourgt a brand new the same model as the the one whit k9agm4 motherboard.
 so i guess the one i need fixing is not that old any way. 
its the same cabinet whit the same options regarding sound in and out and usb devises. however i have wondered why the problems whit sound are so different. and its only whit some programs that dont seem to work as far i can see. can this be related to different chipsets or grafich cards or why else cos its basically the same install procedure i use. 

 the really old fujitsu siemens is first  computer.i dont need to fix that one cos it works great i think . there is some firmware that is on mandriva powerpack 2006 that makes it able to be recording but i figure its not that important cos i just use it to write a letter once in a while and print out. watch a dvd on it sometimes as well.   
 i have also a new one whit debian and then i have started to try get so many old computers as possible and try to fix them and have them last as long as possible. great gift items.

---

### Post by kerry_s on 2008-05-01
first make sure you have alsa->
[B]su
apt-get install alsa-base alsa-utils alsa-oss[/B]

while your still root, run->
**alsaconf**

to select your sound card. reboot to make sure the module loads.
in terminal run-> **alsamixer**

make sure every thing you need is on, use the arrow keys, "m" controls mute, if it shows "mm" it's muted, if it is green with "OO" it's on.

---

### Post by cmay on 2008-05-02
hi again
i made one of the computers work perfect. that is great cos its one i have promised a freind i will try install debian in.
the ohter one whit the supertux dont play but dvd and other sound
programs works.
 it records in audacity and it works great exept there is no sound in supertux. i have updated it so the new kernel is 2.6 18 6 on amd k7 and i thourght it would fix it selve but no sound in supertux. the rest of the programs works fine. also gnome sound works. i have installed alsa-base alsa utils alsa oss alsa gui and the firm ware loaders. 
does supertux by any chance needs alsa oss maybe?
any way i am gonna try adjusting it as good as i can i will see if i can figure it out. i renember i did something ike this whit the 64studio debain based distro when i had a problem whit the emu 1212m soundcard. so i think i can maybe work this out.
thanks for the help.

---

