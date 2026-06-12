---
title: "howto change font size in Konsole ( KDE )"
date: 2019-03-08
forum: Desktop Environments
---

### Post by anderbuntu on 2019-03-08
Hi

any advice howto change font size permanently  in Konsole ( KDE  Desktop) ?
Ubunto 18.10



I found below  howto , but not working on my side

dpkg-reconfigure console-setup
[https://securitronlinux.com/debian-testing/how-to-change-the-virtual-terminal-font-in-debian-and-ubuntu-easily/](https://securitronlinux.com/debian-testing/how-to-change-the-virtual-terminal-font-in-debian-and-ubuntu-easily/)

---

### Post by CatKiller on 2019-03-08
That page has nothing to do with the terminal: that page is about the virtual TTYs that you get to by pressing Ctrl-Alt-F2.

To change the font size in Konsole you can either use Settings -> Edit Current Profile -> Appearance in Konsole itself, or Fonts -> Fixed width in System Settings.

---

### Post by thehipho on 2019-03-08
Right click anywhere in Konsole select "Edit current profile" and click the Appearance tab and there you can select any font/size.

---

### Post by anderbuntu on 2019-03-09
Hi 

Yes This works but only temporary.
When I open new Konsole > fonst size is again like before...

A.

---

### Post by vidtek on 2019-03-09
> **anderbuntu said:**
> Hi 

Yes This works but only temporary.
When I open new Konsole > fonst size is again like before...

A.

I just use ctrl+ several times, it's an automatic muscle memory for me now when I open konsole.

Tony

---

### Post by anderbuntu on 2019-03-09
OK, so there is no global settings to change the  font size permanently ?

A.

---

### Post by CatKiller on 2019-03-09
> **anderbuntu said:**
> OK, so there is no global settings to change the  font size permanently ?

A.

Yes there is. It's in literally the first reply you received. System Settings -> Fonts -> Fixed width.

---

### Post by vidtek on 2019-03-10
> **anderbuntu said:**
> OK, so there is no global settings to change the  font size permanently ?

A.

Yes, you can go to konsole->settings->Manage Profiles

Then delete the profile with the small font and just have one profile as default with your preferred font.

Thanks for keeping on about this, now I don't have to ctrl+  all the time!

Tony

---

### Post by anderbuntu on 2019-03-11
> **CatKiller said:**
> Yes there is. It's in literally the first reply you received. System Settings -> Fonts -> Fixed width.

Thanks, works this way !   :)

---

### Post by anderbuntu on 2019-03-11
> **vidtek said:**
> Yes, you can go to konsole->settings->Manage Profiles

Then delete the profile with the small font and just have one profile as default with your preferred font.

Thanks for keeping on about this, now I don't have to ctrl+  all the time!

Tony


Hi

I dont know why but this way not works, when I setup my profile and setup as default, > new terminal  was not changed...

---

### Post by vidtek on 2019-03-12
> **anderbuntu said:**
> Hi

I dont know why but this way not works, when I setup my profile and setup as default, > new terminal  was not changed...

That's wierd, mine sticks, using Kubuntu 18.04 and kernel 4.17.9-041709-generic.

Tony

---

