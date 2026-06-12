---
title: "New to ubuntu and using wine with World of Warcraft."
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by Idealshu on 2007-05-10
I am very new to ubuntu and I've been using windows since I've touched a computer. I installed ubuntu and updated the nvidia drivers. I installed World of Warcraft using wine 0.9.36 and then proceeded to open it. When WoW opens, it goes to the desktop of the screen and the ubuntu panels are still present. Along with this the sound is a little choppy, and the mouse pointer is still there along with the WoW tooltip trailing behind it slow and choppy like as well. When I close WoW I get an error message and saying it had to terminate it. I was wondering what could be wrong with this? I've looked over the forums and I might have missed 1 or 2 topics but I did not see anything that helped my problem. I was hoping to get this settled before trying to install the Burning crusades expansion. I have an nvidia geforce 5500 vid card. I'm running unbuntu Feisty. Anyhelp and advise would be greatly appreciated. Thanks Again -Shu

screenshot of the problem:

The error after closing the problem
[IMG]http://img.photobucket.com/albums/v511/Darkideal/Screenshot-WoW.png[/IMG]

---

### Post by Tellisk on 2007-05-10
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The tweaks at the bottom are invaluable.
Also, make sure you're running in OpenGL

---

### Post by Idealshu on 2007-05-10
That is the page that I used to set it up. I did tweak #1 it said the 2nd tweak wasn't recommended. How do I make sure it's running OpenGL?

---

### Post by Idealshu on 2007-05-10
okay, had a friend come over and help me. Finally found the errors. Thanks for the help. -Shu

---

### Post by hikaricore on 2007-05-10
There are about 3 areas in that howto telling you how to start the game in OpenGL mode.

If you read it I'd imagine it to be nearly impossible for you to miss them all.

---

### Post by Idealshu on 2007-05-10
Alright, well I got Wow up and running with no errors. It won't go fullscreen so I made wine make a new desktop. The frame rate is so slow it's hardly even playable. The mouse is really slow to responce also. I was wondering if there was another way to speed things up? or what you would need to know to determine a solution. -Shu

---

### Post by willskills on 2007-05-11
If your FPS is low; have you followed the extra steps in the Howto? You need to make some changes to your wine registry. Just type "regedit" from a command prompt; and follow the steps here; [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) .

It seems people get shown the Howto - skim it, and think they have done everything.

Read it again, make sure you have done everything suggested. (Adding *.dll's, regedit, editing your config.wtf, making sure have the correct video drivers installed, and you are RUNNING IT IN OPENGL.

---

### Post by Idealshu on 2007-05-15
I looked over it again, made sure all the configs were right. The only one I didn't do was to make WoW run on a dedicated X server. The guide said it wouldn't do much if any, and that this step could be filled with bugs. WoW still runs pretty slow and the mouse on wow is even worse. The Nvidia 5500 card driver is the one that ubuntu installed itself. As for the tweaks I'm not sure what else to do....

---

### Post by graigsmith on 2007-05-15
did you install the nvidia driver?
go to system, administration, restricted drivers manager.

and it should allow you to install the right driver for your computer.

---

### Post by graigsmith on 2007-05-15
oh, also you can type
glxinfo 
in the command prompt, and it will display what driver and stuff you have installed
it should also say (direct rendering: Yes), that means your 3d is working.

---

### Post by Idealshu on 2007-05-15
The NVIDIA Graphics accelerator is working and "in use". Direct rendering is a YES. So all of those are up and running. Hmm...not sure what else to do. I might have to just dual boot and format my computer again. Keep windows for Gaming and keep Linux to learn something new.

---

