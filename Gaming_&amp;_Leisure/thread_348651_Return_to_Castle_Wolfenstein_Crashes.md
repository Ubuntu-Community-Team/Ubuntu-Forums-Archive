---
title: "Return to Castle Wolfenstein Crashes"
date: 2007-01-29
forum: Gaming &amp; Leisure
---

### Post by NotPhil on 2007-01-29
The Linux version of "Return to Castle Wolfenstein" doesn't play any sound on Ubuntu 6.10 and crashes after the introductory cutscene. The terminal output says ...

> Received signal 11, exiting...
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 91
Shutdown tty console

I ran "sudo sh wolf-linux-1.4-goty.x86.run" then I moved the *.pk3 files from the CDs of "Game of the Year: Return to Castle Wolfenstein" to [...]/wolfenstein/main like install.txt said.

I'm running 32-bit x86 Ubuntu 6.10 on an AMD Athlon 64 with an nVidia Geforce 6150 video card with the proprietary drivers installed. 

The [ID Software site]("http://www.idsoftware.com/support/activision/") tells me to follow a link to [Activison support]("https://activision.custhelp.com/cgi-bin/activision.cfg/php/enduser/std_adp.php?p_faqid=7805&p_created=1007071260&p_sid=*zehVTsi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PWRmbHQmcF9ncmlkc29ydD0mcF9yb3dfY250PTUyMCZwX3Byb2RzPTAmcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9Y2FzdGxlIHdvbGZlbnN0ZWluIGxpbnV4&p_li=&p_topview=1"), which tells me that "Activision did not make nor do we support the Linux version of Return to Castle Wolfenstein." Then it says that I should read either [this FAQ]("http://zerowing.idsoftware.com/linux/wolf/") on the game, which doesn't address my problem, or I should read the [Quake3World Linux forum]("http://www.quake3world.com/cgi-bin/forumdisplay.cgi?action=topics&%20forum=*nix+Discussion&number=15&DaysPrune=10&LastLogin="), which doesn't seem to exist.

Help, please.

---

### Post by thx_1138 on 2007-01-29
I almost drove myself crazy trying to get RtCW working with sound, I was getting a similar error appearing. I had to scour the forums quite a few times and try a few different things including those things they mentioned on id linux game site. But the only thing I found that allows me to run the game as it should be ran was

killall esd
sudo -i
echo "wolf.x86 0 0 direct">/proc/asound/card0/pcm0p/oss
echo "wolfsp.x86 0 0 direct">/proc/asound/card0/pcm0p/oss
exit

 then run your game and (hopefully) you should hear something from the game
Running 6.10 on 
2.4 GHz
1.5 GB RAM
Geforce 6200

---

### Post by NotPhil on 2007-01-29
That works. Thank you.

---

### Post by thx_1138 on 2007-01-29
Sorry I forgot to mention that these commands will have to be re-entered after a reboot, unless someone has a shell script that can take care of this

---

### Post by thecheeseeater on 2008-09-28
You can make this permanent by adding these lines to /etc/init.d/bootmisc.sh

{
echo "wolf.x86 0 0 direct">/proc/asound/card0/pcm0p/oss
echo "wolfsp.x86 0 0 direct">/proc/asound/card0/pcm0p/oss
}

---

