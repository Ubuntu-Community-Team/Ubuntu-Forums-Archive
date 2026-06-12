---
title: "Intrepid~ how do you run .pif apps?"
date: 2009-04-07
forum: General Help
---

### Post by KEE on 2009-04-07
I have a game comache 3 and I couldnt install it in ubuntu so i installed on a flashdrive in win 98. cant run it. any help or suggestions appreciated =)

---

### Post by deanjm1963 on 2009-04-07
I think you'd need wine to run them as they're windows executables.

Here's some more info for you. [http://www.fileinfo.com/extension/pif]("http://www.fileinfo.com/extension/pif")

Hope this helps.

---

### Post by KEE on 2009-04-07
> **deanjm1963 said:**
> I think you'd need wine to run them as they're windows executables.

Here's some more info for you. [http://www.fileinfo.com/extension/pif]("http://www.fileinfo.com/extension/pif")

Hope this helps.

yeah got wine but it dosent cooperate with ms-dos apps, well not this one

---

### Post by jdong on 2009-04-07
Running them in WINE should theoretically work. PIF is just a proprietary "shortcut to a MS-DOS .EXE with additional options set".

Someone did a great reverse-engineering bit on it at [http://www.smsoft.ru/en/pifdoc.htm](http://www.smsoft.ru/en/pifdoc.htm)


Note that you may need more than just WINE if the app is DOS in nature (i.e. DosBox and the likes)

---

### Post by KEE on 2009-04-07
> **jdong said:**
> Running them in WINE should theoretically work. PIF is just a proprietary "shortcut to a MS-DOS .EXE with additional options set".

Someone did a great reverse-engineering bit on it at [http://www.smsoft.ru/en/pifdoc.htm](http://www.smsoft.ru/en/pifdoc.htm)


Note that you may need more than just WINE if the app is DOS in nature (i.e. DosBox and the likes)

oh yeah, I get those description codes  in errors when I try to run it in ms-dos in winxp. looks like this is a bust

---

### Post by jdong on 2009-04-07
You should be able to fidn an EXE that corresponds to a particular PIF. It might be easier to view the PIF's properties under Windows itself to get a hint, as I don't expect any non-nerdy people to actually take the time to parse what the heck the PIF format is on disk :)

---

### Post by KEE on 2009-04-08
> **jdong said:**
> You should be able to fidn an EXE that corresponds to a particular PIF. It might be easier to view the PIF's properties under Windows itself to get a hint, as I don't expect any non-nerdy people to actually take the time to parse what the heck the PIF format is on disk :)

hmm, maybe I didnt explain very well.  the exe works!! just NOT in win xp or wine...only win 98/95. I wouldnt know were to begin to "reverse the engineering" =D

---

### Post by yota on 2009-04-08
If I can remember correctly Comanche 3 is a game for DOS, so probably you can get a better emulation with [dosemu]("http://dosemu.sourceforge.net/docs/HOWTO/").

It's available in the official repositories.

Otherwise you can always use a virtualbox/vmware virtual machine.

Hope this helps!

---

### Post by jdong on 2009-04-08
Yeah if it only works in 98/95, that sounds like a DOS game where DosBox is the more appropriate emulation tool.

---

### Post by 3Miro on 2009-04-08
There is a Wine config manager ( winecfg in the shell), it will let you select the "emulation mode". You can make wine emulate win 95/98 or even earlier win 3.1.

---

### Post by The Cog on 2009-04-08
It's lost ion the mists of time, but I thought that pif files were for DOS executables. In which case, either dosemu or dosbox should to the trick.

---

### Post by lisati on 2009-04-08
PIF = "Program information file" - I thought they were files to let Windows run MS-DOS programs.......

Speaking of MS-DOS programs, some are designed to check the DOS version, there might be some kind of compatibility setting somewhere - perhaps with the MS-DOS SETVER command if memory serves correctly.

---

### Post by KEE on 2009-04-09
yeah, i was hoping i didnt have to download anything ...snort is causing issues on my computer with all updates and installs. I wish I never got snort =( I dont know how to remove it or fix it ```
E: snort: subprocess post-installation script returned error exit status 1

``` Details here->```
Setting up snort (2.7.0-19ubuntu)...
update-rc.d: warning: /erc/init.d/snort missing LSB style header
invoke-rc.d: initscript snort, action &#8220;stop&#8221; failed.
Dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1 
Setting uplibsdl-net1.2.7-2)...

```

---

### Post by jdong on 2009-04-09
> **KEE said:**
> yeah, i was hoping i didnt have to download anything ...snort is causing issues on my computer with all updates and installs. I wish I never got snort =( I dont know how to remove it or fix it ```
E: snort: subprocess post-installation script returned error exit status 1

``` Details here->```
Setting up snort (2.7.0-19ubuntu)...
update-rc.d: warning: /erc/init.d/snort missing LSB style header
invoke-rc.d: initscript snort, action “stop” failed.
Dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1 
Setting uplibsdl-net1.2.7-2)...

```

That's a separate issue and you should probably open up a general help thread on that.

---

### Post by KEE on 2009-04-09
> **jdong said:**
> That's a separate issue and you should probably open up a general help thread on that.

i did but even if that error is shown the program still runs so i got it working. dosbox though is weird since it wont mount the directory. I am going to try switch the / to \ maybe that's what happening =P any way i have enough here to get the old apps working thanks a bunch yall

---

