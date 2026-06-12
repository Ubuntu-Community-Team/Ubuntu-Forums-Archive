---
title: "Display manager and Compiz fusion not working"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by Crashing on 2008-03-12
Due to the release of Compiz Fusion, I have decided to give linux a second try. I have seen it working on an Asus Eee PC and thought that it should work on the ATi Radeon graphics in my laptop. 
My system specs are:
Pentium 4 2.4 GHz
ATi Radeon graphics (Don't remember the model number but the beryl website said it was compatible last time I tried it.)
700-something MB of Ram

I followed the installation instructions on the Ubuntu website, typed "compiz --replace", and the title bars of the windows dissapeared. I have heard that many people have this problem an I have also had it before. I got this back from the terminal after i tried to run Compiz:
caffine@Burn:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c57 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/kwin

Since it said that the max 3D texture size was 1024, I assumed that that might mean screen resolution. So, I opened up display properties but it said that "the module Monitor & Display could not be loaded." I am no expert, but I think this may be why Compiz isn't working. I used to have Kubuntu Fiesty but just installed Hardy alpha 6 today. 

Can anyone help me?

---

### Post by Crashing on 2008-03-12
I just checked my system specs and found out that my graphics card is a Ati Mobility radeon 7500 series. If it was a 1xxx series i would apparently need the fglrx driver. I think i might try reformating the hard drive tomorrow and reinstalling kubuntu.

---

