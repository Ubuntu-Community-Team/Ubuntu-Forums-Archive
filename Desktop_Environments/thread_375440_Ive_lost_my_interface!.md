---
title: "Ive lost my interface!"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Mrwasab1 on 2007-03-03
Hi guys, brand new to the world of unix/linux/ubuntu and all the such. 
Been playing with it for about a week solid and been doing a lot of reading. 
So far my self teaching techniques have been paying off and ive been able to solve all the problems ive encountered.

However i have Ubuntu 6.10 Edgy and i was playing around with the boot manager (much less unforgiving than its windows counterpart).

I think i must have disabled something critical because when i hit apply, it took me to a black screen with a blinking cursor, and no sings of life at all.

So a reboot got rid of that however, i seem to have lost the gnome interface, because when ununtu loads, it brings me to a command prompt with Login:_ 
i log in with my creds and im back to the command prompt

i can still go around the file structure and see all of my files etc.. but ive killed the gnome interface. 

obviously i know its not as easy as typing gnome...(yes i tried) but i cant seem to figure out how to get back to the GUI.

Any help would be very much appreciated.

Thanks

---

### Post by tbodine on 2007-03-03
Okay, all you did was tell GDM to not load at boot time, this is very easy to fix.
Go to your computer and login in the command line interface. After you login, simply type startx, that should bring you to GNOME. Now just got into the System menu, Services, and check the GDM entry. Try rebooting and it should boot into GDM like it used to.

---

### Post by Mrwasab1 on 2007-03-03
Thanks for your help. that seems to have fixed it.

However i do have some more questions.

The whole reason i was playing with the bootup manager was because i have an error message that comes up when i start up.

it says "the network manager applet could not find some required files" it could not start

i guess what i was trying to do was to stop what ever was loading to cause that problem.

i have some gdesklets running but none of them are for network. 

the second reason i was playing with the BUM was that every time i start i have to manually launch my gdesklets. i want them to start up. as well as my gmail notifier.

if you could shed some light as to how about doing this, i would be very greatful.

---

