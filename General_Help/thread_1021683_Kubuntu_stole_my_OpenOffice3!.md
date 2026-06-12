---
title: "Kubuntu stole my OpenOffice3!"
date: 2008-12-25
forum: General Help
---

### Post by solwic on 2008-12-25
I was running Ubuntu 8.10 with OOo3 installed.  All was well.  Then I installed Kubuntu Desktop, so I have KDE and Gnome both, and apparently it removed my OOo3 and replaced it with OOo2.4.

Now, I've tried to install 3.0 in KDE before, and it borked the install, ending with me reinstalling the whole OS, switching from Kubuntu to Ubuntu.  I know I'm glutton for punishment by doing this, but I'm wondering how I can get my OOo3 back?  

Would reinstalling it in Gnome, where it worked, force Kubuntu to use it, too?  Or would it not work in Gnome now because KDE is on the system?  

Any help would be awesome.  I made the mistake of trying to upgrade it once before, and I want to be sure I'm doing everything right.  I'm a writer by profession; I kind of need OOo.  

Thanks!

---

### Post by solwic on 2008-12-25
Also, my spell checker does not work.  Any help here would be awesome.  

Please.

---

### Post by abn91c on 2008-12-25
this guide will work with kubuntu, after the install if the OOo3 menus look funky remove this file only openoffice.org-kde
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by solwic on 2008-12-26
> **abn91c said:**
> this guide will work with kubuntu, after the install if the OOo3 menus look funky remove this file only openoffice.org-kde
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Says it needs to recover from an error, but then fails and closes.  I've heard people say that Kubuntu looks a little like Windows...but I didn't know it acts like Windows, too!

Anyway, that's 0 for 2 on installing OOo3 in Kubuntu.  One more format tonight and reinstall Ubuntu, and I'm leaving that piece of junk Kubuntu alone.  :P

Thanks for trying, though.

---

### Post by p_quarles on 2008-12-26
How did you install OOo 3? The .deb packages at Sun's site install in /opt, so should not interfere with anything that (k/x)Ubuntu does normally.

---

### Post by solwic on 2008-12-26
> **p_quarles said:**
> How did you install OOo 3? The .deb packages at Sun's site install in /opt, so should not interfere with anything that (k/x)Ubuntu does normally.

Same way in Ubuntu and Kubuntu:

1.  Remove old OpenOffice

```
sudo apt-get remove openoffice*.*
```

2.  Untar tarball from openoffice.org website (the Linux DEB, English)

```
tar xvfz OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

3.  Change to DEBS folder

```
cd DEBS
```

4.  Use ```
 sudo dpkg -i *.deb
```

Once all that's done, then:

5.  Change to desktop-integration folder

```
cd desktop-integration
```

6.  Unpack .deb

```
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

Works in Ubuntu 8.10.  Does not work in Kubuntu 8.10.  Same instructions, same file (saved on my HDD), same hardware, same internet connection, same everything.  The problem (broken part) is in Kubuntu.  

At least for me.  Maybe I'm the only person in the whole world who has the issue.  But it keeps me from Kubuntu, which is sad, because I actually like the looks of KDE.  

Ah well, I'm moving data now after a format.  Back to Ubuntu Ibex.  Just finished OOo3 install...works perfectly.  

:)

---

### Post by abn91c on 2008-12-26
> **jrock612 said:**
> Same way in Ubuntu and Kubuntu:

1.  Remove old OpenOffice

```
sudo apt-get remove openoffice*.*
```

2.  Untar tarball from openoffice.org website (the Linux DEB, English)

```
tar xvfz OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

3.  Change to DEBS folder

```
cd DEBS
```

4.  Use ```
 sudo dpkg -i *.deb
```

Once all that's done, then:

5.  Change to desktop-integration folder

```
cd desktop-integration
```

6.  Unpack .deb

```
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

Works in Ubuntu 8.10.  Does not work in Kubuntu 8.10.  Same instructions, same file (saved on my HDD), same hardware, same internet connection, same everything.  The problem (broken part) is in Kubuntu.  

At least for me.  Maybe I'm the only person in the whole world who has the issue.  But it keeps me from Kubuntu, which is sad, because I actually like the looks of KDE.  

Ah well, I'm moving data now after a format.  Back to Ubuntu Ibex.  Just finished OOo3 install...works perfectly.  

:)
once installed in kubuntu you need to remove this file 
sudo apt-get remove openoffice.org-kde

---

### Post by solwic on 2008-12-26
> **abn91c said:**
> once installed in kubuntu you need to remove this file 
sudo apt-get remove openoffice.org-kde

I did...that's what broke spell check.  At least, spell check worked before I removed that, and it didn't afterward.  

Also, that made it ugly, and there shouldn't be aesthetic sacrifices for the sake of functionality; not when the program is perfectly functional *and* aesthetically pleasing in Ubuntu.

Still...it's all good.  I've got Ubuntu installed and and OOo3 works flawlessly, so I'm happy.  :)

Thanks again for trying to help, but I think this issue is beyond fixing.  Until, that is, KDE pulls itself off the junkheap and starts behaving like a DE again.  :P

---

### Post by fooman on 2008-12-26
> **jrock612 said:**
> Same way in Ubuntu and Kubuntu:

1.  Remove old OpenOffice



no need to uninstall openoffice 2.x if you use the repos to install (should work for kubuntu as well...i think)...it will just update the old packages to the new versions:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

---

### Post by solwic on 2008-12-26
> **fooman said:**
> no need to uninstall openoffice 2.x if you use the repos to install (should work for kubuntu as well...i think)...it will just update the old packages to the new versions:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

That made it crash, as well.  Someone said there was an error with the updates for KDE.  I don't know, but that was the first thing I tried.  I found the remove/reinstall method later, and it didn't work either.

Like I said, I've got it figured out - I went back to Gnome, where everything works.  It's ugly, but it's functional.  :)

---

