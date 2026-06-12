---
title: "hosting ubuntu install party...help"
date: 2008-12-02
forum: General Help
---

### Post by manchu02 on 2008-12-02
I am encountering more and more windows users with computer issues and thought it would be a neat community service to host an ubuntu install party, which would give people a chance to try linux and hopefully kick windows to the curb. I just had a few questions about logistics before i advertise such an event.. first, so they get ubuntu on their machines, how do I help them with peripherals, like printers scanners and so forth. I have only been able to get HP printers to work with linux (lexmark has been a no go for me) so I don't want that to be a turn off for them. Also, is there legal issues to be considered, like what if partition resizing fails and the windows partition gets blasted or a power surge that fries something? thanks in advance!

---

### Post by cashman04 on 2008-12-02
The easiest way for you to install it for people that are just wanting to test it out would be to use wubi.exe.  

Put wubi.exe and the iso of the version you are installing on a thumb drive.
Run wubi when in windows, set a size, username, and password, and let it go.
It will restart and install off the thumb drive.  It much easier with wubi, then you dont have to do any partition editing, and worry about something being lost.  It installs it just like any application in windows.  If you want to uninstall it, just go to control panel, add/remove programs.

No clue on the logistics of it.  Thats one downside of linux, not everything is as cut and dry as with windows, but overall its a much much much much better user experience than using windows.

---

### Post by manchu02 on 2008-12-02
Oh i agree, I have been using linux for about three years now and there is no way I am going back. I am constantly cleaning viruses and cleaning up friends and co-workers computers who use both vista and xp. i have never once had a problem with linux in those three years. the handful of times i crashed a linux box was when i was playing around with graphical settings just experimenting. that and the money is why i want to get the word out about linux. Ubuntu has developed enough that you don't have to be a programer to use it, especially thanks to this forum.

---

### Post by realgt on 2008-12-02
don't use wubi if you want to get *rid of windows*. i had something like an ubuntu install party a while back with all my brothers (they brought over their laptops) and i found myself lacking **slow burned** ubuntu install CDs. also one machine had a bad CDROM and at the time, unetbootin was not an option and there was no USB thumb drive installer. might want to make sure you are covered on enough CDs and some thumb drives that are ready to go.

i ended up making a list and making sure i had gone through it on everyone's box
- install ubuntu
- enable any restricted drivers
- enable multiverse, universe, main & restricted software sources
- install wine
- install some neat desktop apps (awn, wallpaper-tray, conky, etc)
- install sbackup or some other backup app
- install ubuntu-restricted-extras, dvd codecs, vlc, etc.
- setup deb software sources (medibuntu, google, ppa)
- configure power management settings (some laptops did not default to good settings)


you'll probably save yourself some time with a list, but in any case, good luck!

---

