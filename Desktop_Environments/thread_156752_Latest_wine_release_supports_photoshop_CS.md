---
title: "Latest wine release supports photoshop CS?"
date: 2006-04-07
forum: Desktop Environments
---

### Post by furryomnivore on 2006-04-07
I've heard a few reports that the latest version of wine supports photoshop CS. I've tried installing it (which it does without error, though it does take a heck-of-a-long time to do), and it opens, but upon opening there is a hold up for about 5 minutes while it searches for pluggins, and then afterwards, the area bound by the photoshop window fails to refresh on the monitor. The terminal reads the errors as such: 

fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:ole:create_server class {a1f4e726-8cf1-11d1-bf92-0060081ed811} not registered
err:ole:CoGetClassObject no class object {a1f4e726-8cf1-11d1-bf92-0060081ed811} could be created for for context 0x4
fixme:ole:CoCreateInstance no classfactory created for CLSID {a1f4e726-8cf1-11d1-bf92-0060081ed811}, hres is 0x80040154


it will hold at that for a while, then it will repeat this error message every 60 seconds:

err:ntdll:RtlpWaitForCriticalSection section 0x13f40f8 "?" wait timed out in thread 000e, blocked by 0009, retrying (60 sec)


Anyone have any clues on configuring wine for PSCS?

---

### Post by JurB on 2006-04-08
I just installed wine using [this]("wine "/home/jurb/.wine/c/Program Files/Adobe/Photoshop CS/Photoshop.exe"") How-to.
I then installed Photoshop cs and everything went fine , i even installed the ACR plug-in that reads RAW files... everything works, altough startup is a little slow.
Maybe you should check the How-to and try re-installing wine the way i did... 
Also make sure you have the latest wine version, mine is 0.9.11 i believe.

---

### Post by furryomnivore on 2006-04-10
[QUOTE=JurB]I just installed wine using [this]("wine "/home/jurb/.wine/c/Program Files/Adobe/Photoshop CS/Photoshop.exe"") How-to.
I then installed Photoshop cs and everything went fine , i even installed the ACR plug-in that reads RAW files... everything works, altough startup is a little slow.
Maybe you should check the How-to and try re-installing wine the way i did... 
Also make sure you have the latest wine version, mine is 0.9.11 i believe.[/QUOTE]


Could you link me to that HOWTO?

---

### Post by fatsamurai on 2006-04-10
Yeah, that would be handy :)

---

### Post by graigsmith on 2006-04-10
if you cant get that working, try gimp and also install the ufraw package. ufraw reads and imports raw files.

---

### Post by fatsamurai on 2006-04-11
I've been trying out the gimp for a couple of weeks. It's good - but it's not quite there yet.

---

### Post by NeghVar on 2006-04-11
Gimps problem is the interface, and they wont change, they just dont understand that.

---

### Post by Shay Stephens on 2006-04-12
Add to that no 16 bit support, etc, etc.  If you are shooting RAW, gimp is not ideal.

As to the OP, I just got PS7 loaded and working under wine 9.10.  I have not tried CS or CS2 yet.  But will soon.  This is very good news.

[QUOTE=NeghVar]Gimps problem is the interface, and they wont change, they just dont understand that.[/QUOTE]

---

### Post by Hairy_Palms on 2006-04-12
i personally think gimps interface is fine, i beleive its all up to which one you learn first, i used gimp for almost a year before i ever even saw photoshop and bcoz im useed to gimp i find photoshops interface horribly confusing. IMO

ps i wouldnt mind having a go at that HOWTO though if the link gets put up :)

---

