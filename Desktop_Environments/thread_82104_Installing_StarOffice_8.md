---
title: "Installing StarOffice 8"
date: 2005-10-25
forum: Desktop Environments
---

### Post by ProfBib on 2005-10-25
As an educator, I am able to download a free copy of StarOffice to use on my computer.  Though I am generally pleased with OpenOffice.org (and have been for well over 2 years now), StarOffice will give me access to several more pre-installed fonts, templates, and clipart, all of which I use heavily on a regular basis.

My question is this:  Am I able to install StarOffice 8 without removing OpenOffice.org, or might having both installed cause conflicts?  Any and all insights will be appreciated.

Thanks,
Evan

---

### Post by ecobuntu on 2005-10-25
[QUOTE=ProfBib]As an educator, I am able to download a free copy of StarOffice to use on my computer.  Though I am generally pleased with OpenOffice.org (and have been for well over 2 years now), StarOffice will give me access to several more pre-installed fonts, templates, and clipart, all of which I use heavily on a regular basis.

My question is this:  Am I able to install StarOffice 8 without removing OpenOffice.org, or might having both installed cause conflicts?  Any and all insights will be appreciated.

Thanks,
Evan[/QUOTE]


Hi Evan-
I downloaded StarOffice 8 for free as well since I am a graduate student and I got it free :)
To answer your question...I had absolutely no issues with StarOffice 8 and OO.org2 installed at the same time.  I am not sure if you are familiar with SO 8 but it's not very much different than OO.org2.  But since it's free why not go for the one with a little bit nicer eye candy.
When you d/l it it's going to be in .rpm format.  So...
At terminal****
1.  sh so-8-ga-bin-linux-en-US_en.sh (or which ever language you choose)
2.  cd in to rpms.  delete the rpms you don't care about i.e. java if you've got it already installed and suse-menu.
3.  sudo alien *.rpm --scripts
4.  sudo dpkg -i *.dpkg
5.  killall gnome-panel

And you're in business!

---

### Post by ProfBib on 2005-10-25
Awesome!  Thanks for the info!

---

### Post by ecobuntu on 2005-10-25
[QUOTE=ProfBib]Awesome!  Thanks for the info![/QUOTE]

No problem.  If you have problems installing it just post back here.  I've gotten it to work in both Ubuntu and Debian.
Cheers

---

### Post by brisamrus on 2005-11-01
Hello,

I tried as you oultined in your post...

> At terminal
1. sh so-8-ga-bin-linux-en-US_en.sh (or which ever language you choose)
2. cd in to rpms. delete the rpms you don't care about i.e. java if you've got it already installed and suse-menu.
3. sudo alien *.rpm --scripts
4. sudo dpkg -i *.dpkg
5. killall gnome-panel

On step "3. sudo alien *.rmp --scripts" i got the following error message

> sudo: alien: command not found


Am I doing something wrong or missing something I need?

Thanks.

---

### Post by brisamrus on 2005-11-01
Found alien and installed it from Synaptic. Thanks

---

### Post by s|k on 2006-05-12
Trying this now.

---

### Post by wondering on 2008-01-13
where is the FREE Star office for ubuntu?

---

### Post by BryanFRitt on 2008-04-18
How can I install StarOffice in the _64 bit_ version of Ubuntu from the StarOffice 8 CD?
(or at least extract the fonts, or anything else useful from the CD)

---

### Post by BryanFRitt on 2008-05-02
I get this error when trying to install
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
and a bunch of warnings
...shouldn't be linked with libncurses.so.5

I'm using the 64 bit 8.04 version of kubuntu

---

### Post by BryanFRitt on 2008-05-05
StarOffice 8 can be installed via Wine with the Windows version, even on 64 bit Linux.

---

