---
title: "dell bios update fail"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chris1274 on 2010-07-08
I've tried downloading Dell's recent update to the Latitude 2100 BIOS several times, in both 9.04 and 10.04, but every time the download fails. Here's the message I get:

Archive:  /tmp/M2100A05.EXE
[/tmp/M2100A05.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/M2100A05.EXE or
          /tmp/M2100A05.EXE.zip, and cannot find /tmp/M2100A05.EXE.ZIP, period.

Can anyone interpret this?

---

### Post by mikewhatever on 2010-07-08
What failed exactly, the update or the downloading? What exactly are you doing there?

---

### Post by Chris1274 on 2010-07-08
Sorry, I should have included more info ...

I was having some minor keyboard issues (cursor randomly skipping around while typing, something that, from my experience, seems endemic to Dell keyboards) so I got on the phone with Dell and the tech guy suggested I update the bios from A03 to the more current A05. On the Dell support page you first select your OS (Ubuntu 9.04 is on the menu) and then download the update. When I tried to download, the above error message came up.

The problem has since been mooted, as I'm now using 10.04 and the keyboard issues seem to have stopped, but the issue is still an interesting one to figure out. Could it be that Dell is having Linux users download files with .EXE extensions? That doesn't seem right, at least to my (admittedly untrained) eyes.

---

### Post by anjilslaire on 2010-07-09
Yes, in most cases the BIOS updates are windows .exe's with Dell. I had to extract the actual file for my Dell Mini 9 and create a .bat file to patch it via a DOS-bootable usb stick.

---

