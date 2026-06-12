---
title: "Help I am not able to boot into ubuntu"
date: 2006-04-07
forum: Desktop Environments
---

### Post by abhishekp on 2006-04-07
Hi, I don't know exactly what happened, I shutdown my computer normally but when i tried to reboot i got so many errors after loading the HP printer module like the one which says

              :command not foundine 4:

and two fatal errors
 
       1.  FATAL:Error inserting speedstep_inh(/lib/modules/2.6.12-9-386/Kernel/arch/i386/kernel/cpu/cpufreq/(speed-ich.ko)no such device

       2.  FATAL:Error inserting acpi_cpufreq(/lib/modules/2.6.12-9-386/Kernel/arch/i386/kernel/cpu/cpufreq/(acpi_cpufreq.ko)no such device

I am not able to boot into ubuntu. My computer freezes after *Checking battery state.

---

### Post by bscbrit on 2006-04-07
I suggest that reboot into recovery mode, and then edit /etc/modules to remove the references to the modules that are causing the problem.  Reboot again and see if that helps.  However, it might be another module entirely that is causing the problem but at least it will be after the ones in the list that you have seen the problems with.  That might give you a clue to help pin it down.

---

### Post by abhishekp on 2006-04-08
that did not help any other ways to get it back working or is there a way to reinstall all the modules from the install CD

---

### Post by ec2 on 2006-04-08
if hacking modules doesn't help, i suggest you reinstall ubuntu, but to save ur documents, you have to have some free (unused) room to copy ur documents to. You'd have to use some live cd (i suggest knoppix) to copy the documents to another partition, and with knoppix, u can use qtparted to create a new partition, but then you have to have some unused room too.

---

### Post by abhishekp on 2006-04-08
That means all my current settings will go and i'll have to reinstall everything. Is there a way that i can repair the current installation? I get the message      :command not foundine 4: repeatedly while loading modules.

---

### Post by bscbrit on 2006-04-08
I assume that you successfully booted into recovery mode - in which case you have a working system but it has a few problems.  Please confirm that you have successfully booted into recovery mode.

If you _can_ boot into recovery mode, we can try to find where the problem is and perhaps can fix it.

---

### Post by abhishekp on 2006-04-09
Yes I can boot into recovery mode but still I get the error messages. That is   :command not foundine 4:. But everything else works fine in recovery mode. What should I do now?

---

### Post by bscbrit on 2006-04-09
What video driver are you using?  If you do not know, use your favourite command line editor (I recommend nano if you do not yet have a favourite - it is simple to use).  Under a section named 'Device' you will probably see references to NVidia and in that it will tell you the 'Driver'. Let me know what you find - there are quite a few threads where this particular problem is caused by the NVidia driver - but it is easily fixed.

---

### Post by abhishekp on 2006-04-09
I found the details which is as follows

	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Driver		"savage"
	BusID		"PCI:1:0:0"

IS this the one.

---

### Post by bscbrit on 2006-04-09
OK, I now need details of your hardware e.g. computer motherboard (if you know it), PCI cards, CPU, memory etc.  Just for your information (because the file it produces will be much too big to include here) you can get all the information from the command line by typing 'sudo lshw >hardware.txt'.  If it asks for your password, give it the usual password that you enter when you log on. 'lshw' means list hardware and, in the example above, I have sent all the output to a file called hardware.txt.  That way you can look at it at leisure and jump back and forth between sections easily.  You can achieve the same using 'sudo lshw | less' but I prefer to keep a semi-permanent record.

---

### Post by abhishekp on 2006-04-09
Posting from ubuntu. I just backed up and reinstalled everything. Anyway thank you  very much bscbrit for your help.

---

### Post by bscbrit on 2006-04-10
Good news - Is the current installation working correctly?  Have you any idea why the first installation didn't work?  Anyway, good luck with Ubuntu.  See you around the forum.

---

