---
title: "how to get full bluetooth support for Samsung S8000? Or at all..."
date: 2010-08-19
forum: Desktop Environments
---

### Post by barna on 2010-08-19
Hi,

I have a Samsung Jet S8000, which reports to have the following bluetooth services: Headset, Handsfree, Bluetooth stereo headset, Serial port, Dial-up, Basic printing, File Transfer, Object push, SIM access, Phonebook access. 

When I search for bluetooth devices and find my notebook (kubuntu 10.04, kbluetooth installed), my phone reports that this device (i.e. the notebook) has only the Object push bluetooth service. Whereas Windows (without installing any software) offers to use my mobile as a modem, to browse its content, to be a handsfree headset, etc...

From my phone I can send files to the notebook, but I need to make about 4 trials to succeed once - in the other 3 cases the file sending process stops on the phone with a 'Sending failed' message...

What is the problem with this? Where should I debug? What software should I install to have full access to my phone? Is there an app to easily synchronize my phonebooks? bitpim and gnokii don't seem to support this phone. 

Thanks

---

### Post by jotjot on 2010-09-21
**Re: ubuntu and samsung jet phone** 			
 			 			 		   		 		 		**ubuntu and samsung jet phone**

I just got an S8000 yesterday, and have begun exploring it.  I got the   same result when I hooked it up via USB, although I haven't tried the   media player route yet.

But I'm even more interested in the GPS capability.  Can you (or anyone  else) shed some light on Samsung phones (S8000 Jet, primarily) and Lucid  Lynx 10.04, and GPS?
And any other relevant info. 

And yeah, bluetooth sort of crawls; amazingly slow.

---

### Post by Zorael on 2010-09-21
KDE is transitioning from an old bluetooth framework (provided by kbluetooth) to a new one called Bluedevil. I don't think it's available in Lucid.

You could try booting a live CD of Maverick Meerkat, which does run Bluedevil, and see if you get better results there, in the live session. You may have to install the package **pulseaudio-module-bluetooth** to get headset/headphone support (unless they fixed that already).

If it does work, you can find some solace in that Maverick is due release in October (around the 10th).

You can find daily live images of Kubuntu [here](http://cdimage.ubuntu.com/kubuntu/daily-live/current/). If you have a usb pendrive, you can just use [Unetbootin](http://unetbootin.sourceforge.net/) to extract it onto there. (This requires your computer to be able to boot from usb devices, though.)

---

### Post by barna on 2010-09-24
Ok, thanks, than I will wait for 10.09. Anyway, I think that there is a problem with the phone itself as well. I managed to mount it via obexfs, I think... (I forgot what I exactly did) I could then open the mounted directory and list it, but it only listed directories, which were all empty. I was upset. Then I tried it from Windows, with the same result. 
The Jet S8000 has anyway quite a few other bugs as well.

---

### Post by barna on 2010-12-03
With Ubuntu 10.10, the new kde bluetooth module was functioning better than the older one. 'Better' means that if I tried to send a file from the mobile to the pc, about 1 trial out of 10 succeeded. So if I was patient enough, I was able to send a file. I still wouldn't call it a full success, though. 

Unfortunately, with some recent update (I believe the kde bluetooth was also affected this) even this 'semi-success' was gone: now I can not anymore send any file from my mobile to the pc. 

Any idea what to change, what logfile to look at? Or just wait until this bug gets fixed in some future release?

---

### Post by Zorael on 2010-12-04
You may want to report the bug over on the [KDE bugtracker](http://bugs.kde.org). Remember, unreported bugs can only be fixed by accident.

---

