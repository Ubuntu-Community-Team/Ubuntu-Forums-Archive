---
title: "need help Installing CS3 from CD"
date: 2009-04-15
forum: General Help
---

### Post by noelc on 2009-04-15
Hm,

When I double click Autorun to install CS3 master collection I,m present with a box to install which when installed clicked nothing happens. 

I then located the setup.exe for CS3 only double clicked nothing happened. I then tried to open with Wine again nothing happened

I then heard you could set up a virtual machine - install windows then install cs3 on that . I downloaded this virtual program from [www.virtualbox.org/wiki/Downloads](www.virtualbox.org/wiki/Downloads) and now cant find where it downloaded to?. 

I,d prefer not to run this virtual windows as I,m told CS3 will run on Linux.

Help?


What am I doing wrong?

---

### Post by Elegia on 2009-04-15
I think your best bet is to run it on a virtual machine. It's what I do and it works great. Wine might run it, but I doubt the stability.

Try to download virtualbox again, this time to the desktop. You should pick the correct .deb file for your system from [here]("http://www.virtualbox.org/wiki/Linux_Downloads"). Afterwards, double-click the .deb to install it (you'll need the root password). After that, start virtualbox, create a virtual machine, insert a windows cd and off you go.

---

### Post by noelc on 2009-04-15
> **Elegia said:**
> I think your best bet is to run it on a virtual machine. It's what I do and it works great. Wine might run it, but I doubt the stability.

Try to download virtualbox again, this time to the desktop. You should pick the correct .deb file for your system from [here]("http://www.virtualbox.org/wiki/Linux_Downloads"). Afterwards, double-click the .deb to install it (you'll need the root password). After that, start virtualbox, create a virtual machine, insert a windows cd and off you go.

OK Thanks, How do I know the right Deb file?

I,ve notice I cant play any of my DVD CS3 tutorials either? Do I need to also run these via the virtual setup? I was hoping these sort of things autorun?

---

### Post by Elegia on 2009-04-15
Which version of Ubuntu did you install and what system do you have?

If it's the 8.10 or the 9.04 version and you have a 32-bit machine, you should download the [i386 version]("http://download.virtualbox.org/virtualbox/2.2.0/virtualbox-2.2_2.2.0-45846_Ubuntu_intrepid_i386.deb"). 

The same goes for every other version of Ubuntu you might have installed. Simply look for the corresponding line on the download page and select the i386 or AMD64 version based on your PC's architecture. If in doubt, you can't really miss with the i386 package.

The video tutorials should also work through the virtual machine. In fact, everything that works in windows (apart from heavy 3D applications), should work with your virtual machine.

---

### Post by noelc on 2009-04-15
> **Elegia said:**
> Which version of Ubuntu did you install and what system do you have?

If it's the 8.10 or the 9.04 version and you have a 32-bit machine, you should download the [i386 version]("http://download.virtualbox.org/virtualbox/2.2.0/virtualbox-2.2_2.2.0-45846_Ubuntu_intrepid_i386.deb"). 

The same goes for every other version of Ubuntu you might have installed. Simply look for the corresponding line on the download page and select the i386 or AMD64 version based on your PC's architecture. If in doubt, you can't really miss with the i386 package.

The video tutorials should also work through the virtual machine. In fact, everything that works in windows (apart from heavy 3D applications), should work with your virtual machine.

OK Thanks,

I had download and installed the right Virtual box but cant find where it installed to or how to activate it.

By creating a virtual windows world to operate in doesnt this defeat the purpose of moving away from Windows. Seems like a lot of effort to end up with the same outcome:lolflag:

---

### Post by Elegia on 2009-04-15
After installation, I got a link in the applications menu to start it. If you don't find it, try opening a terminal and enter the command 'virtualbox' or 'vbox'.

About virtual windows machines, I agree it's kind of annoying having to keep windows around. But I guess it depends on what you use it for. Personally I only use it for photoshop and do everything else on linux, so for me it's not really a problem. Of course if you find yourself working more with the VM, you might want to reconsider installing windows as your primary OS ;).

---

### Post by noelc on 2009-04-15
> **Elegia said:**
> After installation, I got a link in the applications menu to start it. If you don't find it, try opening a terminal and enter the command 'virtualbox' or 'vbox'.

About virtual windows machines, I agree it's kind of annoying having to keep windows around. But I guess it depends on what you use it for. Personally I only use it for photoshop and do everything else on linux, so for me it's not really a problem. Of course if you find yourself working more with the VM, you might want to reconsider installing windows as your primary OS ;).

OK Found Virtual,

Thanks

---

