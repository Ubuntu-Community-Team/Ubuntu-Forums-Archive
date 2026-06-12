---
title: "LIRC....willing to pay, if neccessary"
date: 2009-06-13
forum: General Help
---

### Post by beattyml1 on 2009-06-13
I need help getting lirc set up, I consider my self highly competent with computer related issues(I edit my grub menu.lst and built a computer), but this has thwarted me at every turn, I am beyond just asking for help I need an intervention, I had at one point gotten things as far as starting a program, but never much further than that.  My setup has changed a lot and I am starting from scratch with a lircrc that someone gave me a while back, which I can't seem to get work.   Right now I have GUI 'Infared Remote Control' program I have seen that it knows what buttons I am pressing but....I just don't know....I will post whatever files need to be done.  If one of you can manage to guide me through I would be more than willing to give you/donate to a mutually agreed upon orginization, $5 for your time, provided we can find a secure method of doing so.....................HELP


What it needs to do if you want to be payed:
Work with:
Rhythmbox
Banshee
Elisa
VLC
Other functionalities would be nice but not essential

---

### Post by fillintheblanks on 2009-06-13
getting lirc set up for me was a bit of a pain

it took me maybe several weeks just for irw to recognise my remote button presses, lol..

having said that though you will need to have a .lircrc file in your home folder, and have irexec and irxevent to run at startup as daemons (irexec -d /path/to/.lircrc)

irexec executes commands (good for launching programs) and irxevent simulates keystrokes (good for controlling applications)

then make sure to configure your .lircrc file the way you see fit. you will need to know the names of all your remote buttons, the file with all your button mappings is located somewhere in your /usr/share/lirc/remotes/ folder

---

### Post by beattyml1 on 2009-06-13
I have tested out what you said and as of right now lirc starts programs as it should, it is now also able to control rhythmbox, but it always controls rhythmbox, and will not control anything else, any ideas

---

### Post by beattyml1 on 2009-06-27
Hey no one has posted for awhile so I'll ask again: any ideas?

---

