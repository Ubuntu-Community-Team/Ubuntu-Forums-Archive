---
title: "Simple multiboot/grub question"
date: 2009-02-11
forum: General Help
---

### Post by paul.strickler on 2009-02-11
Hello,
I have a computer with 2 HDDs. One is a masters SATA. The other is a slave IDE.
 I already have ubuntu installed on the SATA and windows on the IDE.

I want to configure grub so that it autoboots windows. My parents can't figure out how to use linux and want the compute to work on windows when they start it.

All OSes show up in GRUB, I just need to know how to set it to autoboot the Windows Longhorn(Where does grub get these names?) OS.

Thanks.

---

### Post by kk0sse54 on 2009-02-11
Edit your /boot/grub/menu.lst file (sudo gedit /boot/grub/menu.lst)and just put Windows in front of Ubuntu. In other words copy and paste the windows section and add it before the ubuntu section because the order in which the different sections are listed is the order that they will be in grub.

---

### Post by bodhi.zazen on 2009-02-11
> **paul.strickler said:**
> Hello,
I have a computer with 2 HDDs. One is a masters SATA. The other is a slave IDE.
 I already have ubuntu installed on the SATA and windows on the IDE.

I want to configure grub so that it autoboots windows. My parents can't figure out how to use linux and want the compute to work on windows when they start it.

All OSes show up in GRUB, I just need to know how to set it to autoboot the Windows Longhorn(Where does grub get these names?) OS.

Thanks.

You set the default in /boot/grub/menu.lst

To be honest, IMO it is easiest to disable the hidden menu and when the computer boots your parents will get a text menu and be able to select which OS to boot, it is not that hard.

See : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by stanz on 2009-02-11
> **bodhi.zazen said:**
> You set the default in /boot/grub/menu.lst

To be honest, IMO it is easiest to disable the hidden menu and when the computer boots your parents will get a text menu and be able to select which OS to boot, it is not that hard.

See : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Ditto ~      :guitar:   That way...they may also learn something different

---

### Post by mb_webguy on 2009-02-11
> **paul.strickler said:**
> All OSes show up in GRUB, I just need to know how to set it to autoboot the Windows Longhorn(Where does grub get these names?) OS.

Longhorn was the [development codename]("http://en.wikipedia.org/wiki/List_of_Microsoft_codenames") for the Windows NT 6.0 codebase, which is the core of Windows Vista, Windows Server 2008, and Windows Small Business Server 2008.  If you have any of these OSes installed, they'll show up as Longhorn in GRUB.

---

### Post by Cloggsy on 2009-02-12
If you're a novice like me and a bit wary of using code then download the KGRUB application. This is a simple - must be, I can use it (!) - GUI (Graphical User Interface) application which allows you to mess with Grub and the default boot etc. Although written for Kubuntu it works OK in Ubuntu and you can simply edit the list of operating systems to put Windows (boo hiss) as first choice and the one that will automatically boot after x seconds unless otherwise clicked.

---

