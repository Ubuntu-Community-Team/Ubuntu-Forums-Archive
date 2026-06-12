---
title: "Banshee apparently hates Sansa Fuze"
date: 2009-04-15
forum: General Help
---

### Post by Trogdor Burninator on 2009-04-15
I installed Banshee and on it's own it runs ok, but when I plug my 8 gig Sansa Fuze into my computer Banshee freezes up. I also tried downloading and installing Songbird, but have no clue how to install it correctly as the instructions have been less than helpful, and I can't get the botched installation to run(error message that says its already running) or get rid of it so I can try again. Is there any way to get these to work?

Can someone help a noob out?

---

### Post by zouhair on 2009-05-02
You should try installing the launchpad newer version.

[here]("https://edge.launchpad.net/~banshee-team/+archive/ppa")

---

### Post by Mr_Bumpy on 2009-05-30
The Sansa Fuze can work in two USB modes: MTP and MSC.  In MSC mode, it behaves as any other USB storage device--you can drag and drop files onto the device through your file manager.  In MTP mode, you can't manipulate the device at the file level, but it works instead through music-management programs like Amarok and Banshee.  However, be aware that the Fuze version 2 (not sure what version you have) isn't properly supported in libmtp until version 0.3.7, and the version in Ubuntu 9.04 is 0.3.0.  Ubuntu 9.10 will have Fuze v2 support out-of-the-box.  Your options for MTP mode are to wait it out until Ubuntu 9.10, or compile libmtp yourself (or find a package/repository somewhere with libmtp already compiled).  If you're happy running in MSC mode, that's probably the easiest way for now.  You can choose which USB mode the Fuze operates in through the settings on the device.

If you decide to compile the latest libmtp yourself, here's what you need to do (instructions are for Ubuntu Jaunty).
[LIST=1]
[*]Download the libmtp source from [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/downloading.php?group_id=158745&filename=libmtp-0.3.7.tar.gz&a=3278902"), and extract it somewhere.
[*]Install some tools we'll need to compile this sucker:
```
sudo apt-get install build-essential checkinstall libusb-dev
```
[*]Make sure that mtp-tools is not installed (the tools will be included in your compiled version):
```
sudo apt-get remove mtp-tools
```
[*]Using a terminal, go into the folder that you extracted in step 1, and run:
```
./configure --prefix=/usr
```
[*]Assuming you get no errors, next run:
```
make
```
And then after that process completes:
```
sudo checkinstall
```
Note: By running **checkinstall** instead of the usual **make install**, you will create a package that will be maintained by the system, which will help to avoid dependency problems.
[*]The checkinstall program will ask you some questions about the package you will be creating.  Answer 'no' to the question about documentation.  For the description, put whatever you want, or "A library for communicating with MTP aware devices."  Then, you will be asked to specify which elements of the package details you would like to modify.  Change the package name from **libmtp** to **libmtp8** to make sure your package will satisfy the dependencies of other programs that make use of the library.  The other package details aren't important right now.
[*]Once the package has been created and successfully installed, run one final command (from within the same folder):
```
sudo ./hotplug.sh
```
Hit 'yes' to all the options (you might get an error on the last one, but don't worry about it).
[*]Finally, make sure your Fuze is set to MTP mode, *not* autodetect.  For some reason, it seems to bug out in autodetect mode (at least it did for me...).
[*]Connect your Fuze to your system with the USB cable, and if all went right, you should be able to access your device through Amarok.  I haven't tried other players, but they should work too, as long as they support MTP devices.[/LIST]

---

### Post by Mr_Bumpy on 2009-05-31
Crap.  After more testing, it doesn't seem that the MTP transfers from Amarok are very reliable (is it libmtp's fault?)... I'm getting some MP3s that crash the player, and occasional connection glitches with the Fuze.  Looks like I'll have to use MSC mode until the situation is improved.

---

### Post by Zylstra555 on 2009-11-10
I had a similar problem, and what I did was reset the USB mode to "Autodetect" again, since it somehow got switched over. Changing it to something else, and back again worked out just fine for me. 

Also, assure that your firmware is up-to-date. 

Anyways, I wrote an article about this since I had a very hard time finding the solution: [http://zylstrablog.co.nr/wordpress/?p=231](http://zylstrablog.co.nr/wordpress/?p=231)

---

