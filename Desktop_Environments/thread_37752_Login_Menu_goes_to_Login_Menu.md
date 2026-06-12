---
title: "Login Menu goes to Login Menu"
date: 2005-05-28
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-05-28
_Specs: PIII, 3Gb HD, 128M RAM, Hoary, XFCE4_

History of the install - Warty upgraded to Hoary, XFCE installed, Gnome uninstalled, Gnome REinstalled (after XFCE froze after login)

Now when I login , i get a grey screen and it goes back to the login. Before it would freeze at the grey screen... 

I am able to ssh from my Powerbook, but 'df' shows that I've used 100% of the hard drive. I'm thinking that might be a problem... 
So can I free up space? What do i uninstall/reinstall? All I can get to is the command line (no Synaptic;) ) 

Please help!!! 


Oh , and my other Ubuntu machine is sick too, but thats another post...  ](*,)

---

### Post by thrift on 2005-05-28
I would bet that using 100% of your disk is at least part of the problem.  

It is impossible to tell what to tell you to delete without knowing what is taking up the space.  You should get onto the command line of the machine, sudo bash or do whatever to become root, then start from / and do a du -sh *

This will tell you how much each directory is using, cd into each directory that is taking up a large amount of space and try to track down what is eating it all up.  

I would not be suprised if it was in /home/.  If it isn't there you are running out of luck and should probably look for a larger harddrive/uninstall unneeded applications.

---

### Post by nicholaspaul on 2005-05-29
Thanks for the tip. I'll free up some space and take it from there. :)

---

### Post by nicholaspaul on 2005-05-29
OK, i've been thru the directories, and the largest ones are usr and var. By the way, all this machine does is sit and play mp3s. I dont need anything except beep-media-player and network stuff.

aah screw it.. i think i'm just going to reinstall  :???:

---

### Post by thrift on 2005-05-29
3G is a very small drive.  You can try reinstalling, but your going to end up in this same position in not so long with Ubuntu.  I would suggest, either reinstall with a more minimalistic distro, or find another harddrive that is closer to 5G and reinstall onto that, or try to find an around 2G to  2.5G drive and move your /usr to it, or a close to 1G drive and move /var to it.

Good luck with whatever you decide to do.

---

### Post by nicholaspaul on 2005-05-31
Thanks for the well wishes, thrift : )

What I ended up doing was installing Ubuntu server and then adding xfce4 (along with ssh, samba and beep-media-player) to make a very tidy **606Mb** install !
I didn't explain that the machine in question is just an mp3 player, so it doesn't need a whole lot. I have my CD collection ripped on another harddrive and this thing just plays random selections all day. It's better than the radio, and I can control it via ssh from another machine in the house.

---

