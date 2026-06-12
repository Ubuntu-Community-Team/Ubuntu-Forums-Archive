---
title: "Accessing a MUX client, how?"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by crazyfish666 on 2008-01-15
I am trying to access a MUX, the page on which the MUX can be found recommended downloading Papaya for Linux distributions which I did through Synaptic. I then went to Applications and looked for Papaya but I can't seem to find it. I tried uninstalling Papaya and installing Tintin, same problem so I am now back to Papaya. 

The instructions on the site say to 'telnet' mux.their-name.net port 4201 ('their-name' is replaced with their actual name) but I can't figure out how to do this if I can't access the program. I have searched the web for instructions on how to access a MUX, but to no avail, all I can find seems to expect greater knowledge of what they are talking about then I have. 

The 'mux.their-name.net port 4201' text on the instruction page of their site is a link and I tried clicking on it but I get this error 'Firefox doesn't know how to open this address, because the protocol (telnet) isn't associated with any program.' 

I'm pretty stumped on where to go next. Any help would be appreciated.

---

### Post by Omnios on 2008-01-15
Right now I use gnome mud as it has a character wizard.

 I really like mudmagic but it will install properly on Ubuntu right now. I installed a menu program called menu and it shows the old Debian menu. 

 Another option is to go into synaptic and right click properties.

 Then choose installed files. 

 There is some info here and what I usually do is copy the menu entry into run to get the menu information. Or look for the bin run command for the program.

 You can then go into 

 Menu bar/

System/Preferences/Main menu.

 This will launch the menu app which will allow you to enter a custom menu for the app with the name and run command and als also set up a icon.

Hope this helps.

 Also you can copy the address/bin into the run to see if it launches.

---

### Post by crazyfish666 on 2008-01-15
> **Omnios said:**
> 
Hope this helps.

Ok, so I uninstalled Papaya and installed gnome-mud, I still don't see it anywhere in the Applications menu so I went into Synaptic and right clicked on gnome-mud and went into Properties. I looked at installed files and found what I assume you were calling the 'menu entry' (be warned, I am an absolute newbie not only to ubuntu but to any form of advancedish computing so if you meant something different please explain in an idiot proof way :) ) it was '/usr/share/menu/gnome-mud'. I didn't really understand what you meant by put it 'into run' so I just typed in 'run /usr/share/menu/gnome-mud' in the terminal, but the command 'run' doesn't exist. Beyond that I am stumped.

Yes I am an idiot when it comes to computers, can't you tell :) . I am learning though and I hope to become at least independently functional. Thank you so much for helping me out!

---

### Post by Omnios on 2008-01-16
Hi fellow muder.
 
 K the gnome mud menu entry shows up under games.
 
 Though is no run command so usually in terminal you can use say this for a bin .game.
 
 As for the installed info copy and click /bin/..../game int the run command as it is shown this is the exact command to run the game. It does not need run in front of it.

---

### Post by devi on 2008-01-16
I just run TinyFugue. :) It makes me feel all 90s-nostalgic. ;)

---

### Post by crazyfish666 on 2008-01-16
> **Omnios said:**
> Hi fellow muder.


Got it! Thanks!

---

