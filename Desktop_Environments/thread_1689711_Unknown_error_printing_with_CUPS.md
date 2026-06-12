---
title: "Unknown error printing with CUPS"
date: 2011-02-17
forum: Desktop Environments
---

### Post by JeroenML on 2011-02-17
Hi,

I was wondering if anyone could help me with the following:

I have Ubuntu LTS 10.04.2 x86-64 running with default Cups installed.
Now I am trying to print on a Canon iRC1021i network printer using a x64 PPD file.
Trying to print a test page delivers a "server-error-internal-error". 

After this I ran the debugging mode which delivered the troubleshooting.zip file.

Does anyone have an idea what goes wrong at my system?

Kind Regards,

Jeroen

---

### Post by garyjmellor on 2011-02-17
Hi, I just checked Open Printing ([http://openprinting.org](http://openprinting.org)) and your printer isn't listed. Check here: [http://www.openprinting.org/printers/manufacturer/Canon](http://www.openprinting.org/printers/manufacturer/Canon) . Now this doesn't mean that you can't get it working but.... I would say it doesn't look hopeful. I'm sorry this wasn't more positive.
 
*EDIT* - how did you install the printer? If you go to System > Adnministration > Printing and then click 'New' (might be 'Add') and then expand 'Network Printer' does the OS detect your networked printer (might take a short while)? You may need to just click 'Find Network Printer' and let it idle for a short time to enumerate the printers it can find. Is the printer attached to a Windows box or print server? If so you might also want to try Selecting 'Windows Printer via SAMBA' and then clicking 'Browse' to see if it can find the printer. Try and 'attach' to it again and then send a test page to it. Post back with how you get on.
 
*EDIT* - you could also try grabbing Canon's driver from here ([http://software.canon-europe.com/products/0010628.asp](http://software.canon-europe.com/products/0010628.asp) - RPM/DEB/TGZ versions. I looked for Dutch versions but there aeren't any. English was available though. This may produce different results to the PPD perhaps(?)
 
*EDIT* - you could also try pointing your browser (on your Linux box) to [http://localhost:631/help/network.html](http://localhost:631/help/network.html) for some troubleshooting or [http://localhost:631/admin](http://localhost:631/admin). If this gives the same 'server-error-internal-error' message then I would say there is an issue with CUPS itself.
 
*EDIT* - I see from the log file that on line 745 you have: "...(/usr/lib/cups/filter/foomatic-rip) crashed on signal 13" and on line 754 you have: ""...Job stopped due to filter errors...". I think this points to a problem with the backend somewhere. For the latter problem I would check what the permissions for foomatic.rip are (I would expect them to be rwxr-xr-x . For the former I would check you have all the latest updates from Update Manager and that CUPS has the correct printer type selected.

---

### Post by JeroenML on 2011-02-17
Wow thank you garyjmellor!
I hope the following makes sense ;-)

* The printer may not be supported, but I had it working in the past. That time I used Ubuntu 10.10 x86-64 with the same drivers. But for Long Term Support I choose to install this version LTS 10.04. 

* There aren't any updates I cannot do for my LTS 10.04 besides a dist-upgrade to 10.10.

* For the Canon driver, I picked the ones from the Canon site. My OS language is English so that shouldn't be a problem ;-)

* the foomatic-rip file is a link in the given directory, but the file is rwxr-xr-x:

```
jeroenh@nb-jeroenh:/usr/lib/cups/filter$ ls -la foomatic-rip 
lrwxrwxrwx 1 root root 25 Feb 16 10:45 foomatic-rip -> ../../../bin/foomatic-rip
jeroenh@nb-jeroenh:/usr/lib/cups/filter$ cd ../../../bin/
jeroenh@nb-jeroenh:/usr/bin$ ls -lah foomatic-rip 
-rwxr-xr-x 1 root root 105K Feb 15  2010 foomatic-rip
``` 

* I tried to install the printer both ways, from our shared printer on the Windows Domain using SAMBA and directly using port 9100. Both did not work :-(

Hope this helps!!!

Thanks in advance :-)

Jeroen

---

### Post by garyjmellor on 2011-02-17
OK, so we can rule out a permissions issue on the filters. That's good.
 
If I understood correctly, there are no outstanding updates available for your system (the reason I asked about this was because CUPS got broken with some updates to 10.04 a while ago and then fixed with more updates a little later on. This affected some printers (notably, Lexmark - not your brand I realise) and the log files stated something very similar in this instance).
 
One thing I forgot to ask - this is a desktop install of Ubuntu, right?
 
Did you try pointing your browser at CUPS at the URL I quoted? If so, were you able to connect OK (to both URLs) without receiving the server error and does CUPS show it is using the correct printer?
 
One thing I would try as a 'catch all' would be do to do a 'sudo apt-get purge cups' and then reinstall it again. I'm unsure if this is going to fix it but the purge parameter works exactly like 'remove' except that it removes packages and deletes config files as well. If you have an issue in your config files that is causing this issue then this *may* sort it out. I would then reinstall CUPS through the Package Manager (or 'sudo apt-get install cups' from the command line) and then try configuring the printer again. One thinge to note is that *all* your configured printers will be lost as a result of this - so if you have lots of printers configured in your installation then you might want to think twice about this step.
 
If you still get the same result I'm afraid I'll have to hold my hands up and say "I don't know what's wrong". In that event it might be worth raising a defect..... or waiting to see if somebody who is a bit more CUPS/printer savvy than us posts here!
 
Please post back with how you get on.

---

### Post by whiteman on 2011-02-18
Couldnt find where to squeeze in. Just put a new motherboard in this old Dell xps 400. It had Lynx on it. Prior to this I had total file sharing between Ubuntu(printers here) and windows 7(ethernet) and Macbook Pro(wifi) and paavillion(Winxp-wif) Everybody could print and file share. It was a thing of beauty!
Since then I got me a mac mini. It is also wifi. The Ubuntu is back where it was. Ethernetted to dlink 655 and also the win 7 machine. Evwerybody can swap files and see each other. The win7 can print.(I had to use Turboprint system, as I have never found linux drivers for my Pixma) But this was what I had before, so that shouldnt matter.
WHen I use smaba gui, I nootice some oddities.  If I click on props, i get two users, me(wth) and Nobody. 
I have all of my shareable drives listed and also have allowed sharing with Nautilus(Overkill?)
I also have at the top var/lib/printers--print$--r/w--visible
Then my drives are the same, all three are r/w and visble. On props --access--I have everyone.
Preferences/Samba users---I have two...wth and nobody. If I click on Edit user...for wth everything looks OK. But If I click on EDIT USER on NObody, at the top you will see NObody with wth written overtop of it. Like a dblestrik on an old typewriter. This is beside Unix username only.
CAn this be part of problem?
In the past my macs were easy to setup printers. When you went to ADD Printers, they literlly jumped out at you. On Default and Windows .On windows, you were able to follow from left to right....Workgroup(dlink) then computername(xps) and then the two printers. 
Bith printers are working fine in LInux(lynx10.04) and seem to be OK in windoze7.
What causing the wireless machines to be blind to the printers only?
Files are fine. I can see everything.Copy paste, etc. Only printer sharing between Ubuntu and Macs(both wireless) and probably the xp latop as well. Havent looked.
I have inclued my workgroup name in smb.conf. At one point I lost my smb.conf file altogether and had to reconstruct(copy it from defalult) I also noticed that sioftware ctr wont let me install the Samba gui. In fact itwouldnt do anything. I had to use synaptic. Be that as it may I only mention it in passing. I rarely ever used it anyway.Im lost.

---

### Post by whiteman on 2011-02-18
On thsose Canon printers..I tore myhair out over mine not even being visble. I went form no problem with 8.10 to nothing but...with 9.10, 10.04....nothing would allow me to even see my canon pixma. Then I found Turboprint system. Its afree 30 day thing then they will charge you 29 bucks. I am still on first 30 day thing..BUT IT WORKS. I mean it works good. Right away, after weeks and months of not using my Canon Pixma MP470. They seem to specialize in Canon or something. Well its just an idea. I know...the 29 bucks is irritating. But I was at my wits end on this thing.

---

### Post by JeroenML on 2011-02-21
Hi garyjmellor,

Thanks for the feedback!

I can connect to both URL's no problem. I have tried to add the printer using these pages, with no result. I have seen an other message though:

Printing a Test page:
"/usr/lib/cups/filter/foomatic-rip failed"

Purging the cups package resulted in reinstalling a lot of packages but no result... 

I even Upgraded from Ubuntu LTS 10.04 x86-64 Desktop to Ubuntu 10.10 Desktop x86-64. But no result...

WHELP! ;-) Don't hold your hands up :-)

Kind Regards and thanks!

Jeroen

---

### Post by JeroenML on 2011-02-22
Well.... I am "I think" a bit further.

The printer prints.... but it only prints the following text:

**** Unable to open the initial device, quitting.

Any idea?

Kind Regards,

Jeroen

---

### Post by kervin on 2011-08-27
I got the same issue. Any solutions to that?

---

### Post by fguitart on 2011-11-21
> **JeroenML said:**
> Hi,

I was wondering if anyone could help me with the following:

I have Ubuntu LTS 10.04.2 x86-64 running with default Cups installed.
Now I am trying to print on a Canon iRC1021i network printer using a x64 PPD file.
Trying to print a test page delivers a "server-error-internal-error". 

After this I ran the debugging mode which delivered the troubleshooting.zip file.

Does anyone have an idea what goes wrong at my system?

Kind Regards,

Jeroen


I had the same problem with one Canon IRC2880. In my case it was Ubuntu 11.04 64 bits and I had all drivers gziped in /opt/cel/ppd. I solved this gunziping the PPD and adding again the printer pointing to this unziped driver.


-- 
Francesc Guitart

---

