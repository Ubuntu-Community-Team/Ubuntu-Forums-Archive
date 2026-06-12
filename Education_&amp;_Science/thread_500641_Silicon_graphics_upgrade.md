---
title: "Silicon graphics upgrade"
date: 2007-07-14
forum: Education &amp; Science
---

### Post by Thomas Delbeke on 2007-07-14
Hi, 

I've been asked by my potential promotor for a PhD program (in cristallography) if I could suggest an upgrade strategy for their very old SG systems. I think the main problem is that there is some software (all freeware) that they would like to run that is still available only to the SG Unix dialect. I've noticed that under Ubuntu I can use the Wine emulator for Windows based software. Is there one for SG unix too? We could shift to Macintosh but it has less potent machines for the dollar, so I think that isn't advantageous either. Since I live in Belgium there is no preinstalled Ubuntu PC system available as far as I know. We use mainly Dell at our university. They had Red Hat available instead of XP, but it wasn't really impressive in my opinion and they sold it at the same price anyway. So I think we are going to go for a Microsoft preinstalled configuration  anyway. Since we will probably take rather potent machines I'm afraid the price for the MS will will probably go up though, since we then get professional and bussiness preinstalled probably. I am thinking about a dual boot potentially, or just try out the Vista platform with Cygwin installed on it and Ubuntu mounted on it. Provided that it has some kind of SG emulator ofcourse. Another question: should I try out Edubuntu, or is that mainly for schoolchildren?

Thank you very much!

Thomas

---

### Post by apoth on 2007-07-14
I'm not aware of an SG emulator, which isn't to say there isn't one. Is that IRIX that they run?

What does the software do? Is it something there might be a suitable alternative for?

---

### Post by Thomas Delbeke on 2007-07-14
Hi,

I think it's the IRIX OS indeed, but I haven't looked at it yet. I see the guy again on monday. I don't know exactly which freeware they use but for the majority of applications there certainly is an alternative. I don't know however if all their data files will be easy to convert. If not it will compromise the transition a little bit, but luckily I can ask a guy from another lab some things about that too, although they don't use all the same applications probably. So, as for the rest , do you think the Cygwin idea could work or should I stick with a seperate partition? It is also a fact that most scientific journals still like there paper applications in MS Word, and the open office .doc extension is not entirely the same if you open it in Windows. Will Cygwin be stable enough under Vista and can you connect easily with the internet or other PC's from Cygwin? And is there any possible use for the Vista Ultimate unix enabled version? 

Thank you very much for your help.

Thomas

---

### Post by apoth on 2007-07-14
I'm not fond of Cygwin, so I haven't used it enough recently to answer much about it, I'd put Ubuntu on its own partition, but the best way to find out if it meets your standards is probably just to install it and play with it.

I think Sun have brought out a plugin for opening openoffice documents in Word, I don't know if that does a better job of opening them as they would appear in openoffice and then saving them as Word documents. I don't find the differences that large these days if you stick to fairly middle-of-the-road features, as you would for writing papers. My girlfriend's still at university and recently wrote her master's dissertation in openoffice and she just opened it in Word before submitting it to make minor formatting and layout changes.

I wouldn't bother with Unix services from Microsoft. A dual boot with Ubuntu should give you the best of both worlds.

If the data files don't convert easily but there are alternative programs then you may find there are enough bored programmers around here that one might write a conversion program. :)

---

### Post by tweedledee on 2007-07-14
Having the same problem in our lab, I strongly recommend the Linux approach to dealing with this issue, unless there's really something key that only runs under Windows (and even then, VMware+XP is superior to Vista).  We're now running a Red Hat workstation to handle everything the SGI used to do, with 2 pieces of software running in a VMware windows install to replace two programs that only had Windows equivalents to the IRIX versions.  I'd much rather be running Ubuntu, but we have one piece of software that requires an older kernel, so we're stuck on Red Hat 4 until I have time to separate out that programm.  But long term, even if the cost is the same, you'll be much happier with Red Hat or other linux install rather than Vista, especially if they're used to IRIX.  We're all Dell as well, so it works out fine under that hardware.  Last, you probably don't want Edubuntu, that's definitely not targeted for research-level computers.

---

### Post by Thomas Delbeke on 2007-07-14
Ok,

thank you very much people, I'm going to try out the Cygwin now, if I can free enough space under my XP partition of my Dell Latitude D510. Otherwise I'll have to resize partitions since I only have 80 GB on the harddisk, but then I'll need to backup first. I'll be searching a little for an SG emulator on the net. I know in Microsoft you can run programs in XP in 95 or 98 compatibility mode by right clicking and selecting properties. But that's a totally different line of OS ofcourse. Another way might be to use somekind of translation script in Perl if it exists, since most programs or open source aswell as freeware I was told. But then again, it will still need debugging for the problems when communicating with the new OS kernel and I don't know if I'm really up for that. Certainly I lack the programming skills right now. 

Anyway, thank you very much for helping and I will post our solution here,

Thomas

---

