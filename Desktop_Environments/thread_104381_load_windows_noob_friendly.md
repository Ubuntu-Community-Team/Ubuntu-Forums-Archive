---
title: "load windows noob friendly"
date: 2005-12-16
forum: Desktop Environments
---

### Post by emm721 on 2005-12-16
i want to load windows on my machine again, for games and stuff, but i want to keep ubuntu. i have a lot of unallocated space, so thats good, and my friend told me when i install again it will delete my grub. i am a ubernoob, i saw [http://www.ubuntuforums.org/showthread.php?t=81873&highlight=install+grub](http://www.ubuntuforums.org/showthread.php?t=81873&highlight=install+grub) and it looked like exactly what i wanted, but i didnt understand it. so, how do i install a grub through windows or on a ubuntu live cd?

---

### Post by anil_robo on 2005-12-16
Get a geek by your side. Physically. Or just use linux with cedega or wine for games. Search on the forums for "cedega" or "wine" with the name of the game you want to play, read help, follow instructions and play! :D

There's no harm in experimenting anytime anyway! :D

---

### Post by emm721 on 2005-12-18
alright, but there are also some other things i like about windows. like the fact that dell support will actually help me when i have a problem instead of going "oh, you use linux. oh well, too bad." and also, i should open another thread for this, but can i remote control a ubuntu computer with windows? if so, how? i tried the remote desktop part already.

---

### Post by snellgrove on 2005-12-18
I can never get the built in "Terminal Services Client" to work at all.

I mean, it turns up but wont connect to nowt :p

Fire up a terminal, and type in "sudo apt-get install grdesktop"

this will install another terminal services client that I find works a treat, connects to the other PC (XP Professional) in the house just fine :) have to specify the workgroup / domain though, before it can resolve the host.

if you can't find grdesktop, you need to enable some repositories - post back if you need the info, im sure theres a sticky somewhere on here that'll say, or i'll try and guide you through how to do it! :)

:edit:

doh, I read your post wrong. thought you wanted to control windows from ubuntu lol, oh well. Yes, its possible to do it the other way though - I never tried it but, i believe you use something called VNC. I dont know if Ubuntu comes with a server listening for connections by default - i'd imagine it doesn't so you would need to configure that somehow.

As for games, yeah I know how you feel... I sure use my PS2 a lot more since I got ubuntu LOL - haven't tried wine / cadega yet.

---

### Post by emm721 on 2006-01-04
ok, thanks. both ways are good to know, the program is called "VNC viewer" and it works fine. the only problem with it is that i wanted it as a computer with no monitor/keyboard/mouse, for playing music and stuff. since its not a static ip, any new computers throw it off and i have to keep a monitor and keyboard on at all times. but, ill find that out on my own. thanks

---

