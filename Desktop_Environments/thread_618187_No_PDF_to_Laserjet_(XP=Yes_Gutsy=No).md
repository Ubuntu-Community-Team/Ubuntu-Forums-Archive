---
title: "No PDF to Laserjet (XP=Yes Gutsy=No)"
date: 2007-11-20
forum: Desktop Environments
---

### Post by McHenry on 2007-11-20
I have multiple Ubuntu desktops none of which can print PDFs to the Jetdirect laserjet.

Everything else prints fine and pdfs can be printed to other network printers on the lan.

Printing of pdfs was fine in Feisty and initially worked in Gutsy too however I believe there may have been a cups update and now... no go.

Can anyone suggest what the problem may be or how I can diagnose it further.

XP boxes on the lan can print PDFs to the laserjet.

Thanks in advance...

---

### Post by McHenry on 2007-11-20
Nobody ?

---

### Post by jcrow on 2007-11-21
I too have been having problems printing PDF's and images. There are a few bug reports on it, but no resolution. You may want to try printing with non gnome programs.  Some people can print from acroread. I can only print scanned pages (PDF's) from Foxit through Wine or through the HPLIP Toolbox. I can't print images from EOG either. I am using a HP 1018 and had the same problem with a deskjet 3660.

---

### Post by McHenry on 2007-11-21
I find it hard to believe that an inability to print PDFs to a HP laserjet would not be regarded as a very serious problem.

If Ubuntu is to be considered as a serious alternative for corporate desktops then some fundamental basics MUST be in place.

---

### Post by McHenry on 2007-11-26
Where can I track the progress of these bugs.

I cannot believe being unable to print PDFs to a laserjet is not a very high priority.

---

### Post by neilengineer on 2007-11-26
Did you try System->Administration->Printing??

And do you have the service "cups" running?

Or how about go to HP website to download printer drvier for linux??

I don't know, I have no problem with my HP laserjet

---

### Post by McHenry on 2007-11-27
Cups works as other networked lasers are able to print pdfs and the laserjet can print from OO it's just PDFs that don't print.

Is you laserjet using a jetdirect interface ?

---

### Post by McHenry on 2007-12-02
Can anyone advise or is there a way to determine when the problems encountered with Gutsy and printing PDFs to laserjets may be resolved ?

Thanks

---

### Post by 11hjpphty76lkjj on 2007-12-04
Can you run the ubuntu printing bug info script and post the output?  link is in my sig.

Thanks!

A

---

### Post by McHenry on 2007-12-05
Thank you... please find attached the report as requested.

God I hope this solves the problem, being unable to print PDFs is killing me...

---

### Post by 11hjpphty76lkjj on 2007-12-06
Everything looks good.

Although check here:

[https://answers.launchpad.net/ubuntu/+question/18575](https://answers.launchpad.net/ubuntu/+question/18575)

apparently running:
```

sudo aa-complain cupsd
```

may fix this for you.

A

---

### Post by Happy_Man on 2007-12-06
If nothing else works, you can use Synaptic to roll back the package to the version where it was working.

---

### Post by McHenry on 2007-12-06
Looking through the synaptic logs I am guessing ti was the following:

Commit Log for Wed Nov  7 08:22:25 2007


Upgraded the following packages:
cupsys (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1
cupsys-bsd (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1
cupsys-client (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1
cupsys-common (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1
gnome-system-monitor (2.20.0-0ubuntu1) to 2.20.1-0ubuntu1
libcupsimage2 (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1
libcupsys2 (1.3.2-1ubuntu7) to 1.3.2-1ubuntu7.1

How do I roll it back ?

---

### Post by McHenry on 2007-12-14
Is there any alternative way to print other than CUPS as being unable to print PDFs is about to force me back to Windows.

How can I check progress on any resolution for this problem ?

Thanks in advance...

---

### Post by 11hjpphty76lkjj on 2007-12-14
Does this help?

[https://answers.launchpad.net/ubuntu/+question/18575](https://answers.launchpad.net/ubuntu/+question/18575)

A

---

### Post by McHenry on 2007-12-14
No... but thanks anyway.

My problem is not that I cannot "print to pdf" but I cannot "print pdfs"

---

### Post by stchman on 2007-12-14
What does print out?  Nothing or blank pages?

---

### Post by McHenry on 2007-12-15
Varies...

For example:

a single page PDF may do nothing... no response from the printer or anything.
a multi page pdf will indicate data being sent to the printer and simply hang with the printer data light flashing.

I've posted log data here in the hope someone may help...
[http://forums.linux-foundation.org/read.php?20,3914](http://forums.linux-foundation.org/read.php?20,3914)

---

### Post by McHenry on 2007-12-15
Progress has been made but it is still not fully resolved.

I printed the same pdf using the Feisty live and Gutsy live CDs then compared the cups error logs:
Feisty used DEVICE_URI=socket://192.168.1.21
Gutsy used DEVICE_URI=hp:/net/HP_LaserJet_400* 0_Series?ip=192.168.1.21

Once I changed the URI to what Feisty used the printer stopped flashing error codes after every printjob and now PDF printing has settled down somewhat but not fully.

For example I have faxes received by HylaFax as PDF attachments in an email which I cannot print. When I print the fax from Evince then it sits in the print queue with the printer data light flashing indefinitely however if I save the fax to disk I can print it using lpr fax0001.pdf]".

Must be a problem with Evince...

---

