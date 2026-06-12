---
title: "gnome-ppp"
date: 2005-05-22
forum: Desktop Environments
---

### Post by zxee on 2005-05-22
Hi, I have a strange modem inital string problem, and I hope someone can point me in the right direction. I have a multitech (MT5600ZDX) external modem that for some reason that I've never been able to work out won't recognize the command "ATZ" I've done a fair amount of experimenting with the AT commands in minicom so I know how to get the modem intialized and dialing  
For what it's worth I need to change the 1st intial string to AT&F (I've been using AT&F&C&D2V1) the 2nd string is ATE1. This configuration works on almost all the distros I've used by editing kppp.
With Ubuntu I have been able to get the modem to work by editing /etc/wvdial.conf  but I can't get gnome-ppp to work because for some reason it tries to intialize the modem by using the "ATZ" command. I thought that gnome-ppp uses the wvdial conf file but there must be another file it's using for the intial strings. I have edited those strings in the GUI that gnome-ppp provides but initial 1 is not available to be edited.
Does anyone have any clues on this? Thanks

Added 5-23: Although it's not exactly the solution I had looked for I did apt-get install gpppon and edited the /etc/chatscripts/myisp file and I can get gpppon to dial out-using it right now. gnome-ppp still does not work-still tries to use the init string "ATZ" that my modem won't recognize. But hey it was pretty easy to create a launcher for gpppon and with 2 clicks I'm on.  :)

---

### Post by jazzer on 2005-05-22
Under the Setup options for GNOME-PPP in the Modem Tab there is an option for editing init strings, I haven't personally had to adjust to my settings so I can't vouch for it working but I would hope/expect it does... ;)

---

