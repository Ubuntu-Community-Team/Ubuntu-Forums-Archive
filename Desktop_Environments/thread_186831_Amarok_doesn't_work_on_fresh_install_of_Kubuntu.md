---
title: "Amarok doesn't work on fresh install of Kubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by greggh on 2006-06-02
Just installed Kubuntu 6.06 from the live cd and everything seems to work but Amorok. When I click on Amarok in Kmenu I see the little spinning icon on the taskbar, but after about 30 secs it just disappears and never loads. If I type amarok in Konsole I get...
gregg@gregg-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/lib/amarok/amarokapp: error while loading shared libraries: /usr/lib/libpq.so.4: invalid ELF header
gregg@gregg-desktop:~$

---

### Post by Rackerz on 2006-06-02
Is your sound device working properly?

---

### Post by greggh on 2006-06-02
Yup. Sound is working fine. I can start and play oggs in Kaffeine no problem.

---

### Post by murph2481 on 2006-06-02
You need to change your sources.list file so that all the words that say universe are change to multiverse.  Then you need to run a apt-get update.  Then you need to search for the xine codecs.  Sorry I cannot remember them off the top of my head which ones they are but search by name and search for xine and download the one with the word libs in it.

---

### Post by greggh on 2006-06-02
[QUOTE=murph2481]You need to change your sources.list file so that all the words that say universe are change to multiverse.  Then you need to run a apt-get update.  Then you need to search for the xine codecs.  Sorry I cannot remember them off the top of my head which ones they are but search by name and search for xine and download the one with the word libs in it.[/QUOTE]

Yikes! That sounds a little complicated. I'm a brand Noob to linux, and it sounds like its going to take me a little while to learn how to do all that. Thanks for the info though.

---

### Post by murph2481 on 2006-06-02
haha it sounds way more complex then it is.  I have only been using it for about 6 months and consider myself a noob.  I find that the IRC channels are awesome at walking you through this stuff.

Under the internet menu there is a app called Konversation.  There is already an entry in there to get to you to the right IRC channel just click connect.  They will walk you through it

---

### Post by greggh on 2006-06-02
Thanks Murph. I'll check out that IRC channel. I realize its going to take me a little while to get the hang of everything, but I'm looking forward to the learning process. I can't wait to be 100% free of Windows. I don't even want to have it as a dual boot. :mrgreen:

---

### Post by murph2481 on 2006-06-02
Yea the learning curve is a little painful.  But the good thing if you screw it up too much you can always reinstall it very easily.  I find it takes me 10 times longer the first time to do something, then to do it again it takes a matter of minutes.  Its a pretty stable system so its hard to screw up beyond repair.

I am still using windows for web development and photo manipulation.  Dreamweaver and photoshop are hard to beat and I know them really well.  Still learning NVU and GIMP.  And the fact all my computers games are based on DirectX i am stuck with windowz.

Ill just have to wait till the new PS3 comes out!

---

### Post by greggh on 2006-06-02
Murph, I went on IRC and Robin quicky figured out from that Konsole error message that for some reason my libpq4 file was corrupted. He told me to...

sudo apt-get install libpq4
sudo apt-get install libpq4 --reinstall

--Now it works fine.

Don't know how that file got corrupted though, and everything else seems to work.

---

### Post by murph2481 on 2006-06-02
See I was close at least I was able to point you in the right direction :)  Sorry hard to fix while I am at work and stuck in Window$

Enjoy Amarok it rocks! Make sure you are using version 1.4 it's awesome

---

