---
title: "HOWTO: Repackage i386 deb for in lpia (for Dell Mini9)"
date: 2008-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by feranick on 2008-10-29
I am reposting this with more visibility. You can easily repackage any deb outside the repos into an lpia one. The reason you want lpia packages instead of forcing the i386, is that while the former will show up as an installed package on synaptic, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for Skype into an lpia package:

1. Download the [Ubuntu version of Skype]("http://www.skype.com/go/getskype-linux-ubuntu")
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the "debian-binary" file
6. Decompress "control.tar.gz". There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: lpia"
9. Open the other archive "data.tar.gz". There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files "control.tar.gz" and "data.tar.gz"
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!


This has been tested (and currently working) with: Skype, Opera, Picasa, Adobe Flash 10.

---

### Post by starcannon on 2008-11-17
This is something most of us new mini9 owners need to know. Thanks for the tut, it needs put somewhere handy at least while the min9 is hitting the market.

Subscribing to this thread so I can link it in the future.

Thanks again!

---

### Post by peril62 on 2008-11-23
> **feranick said:**
> I am reposting this with more visibility. You can easily repackage any deb outside the repos into an lpia one. The reason you want lpia packages instead of forcing the i386, is that while the former will show up as an installed package on synaptic, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for Skype into an lpia package:

1. Download the [Ubuntu version of Skype]("http://www.skype.com/go/getskype-linux-ubuntu")
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the "debian-binary" file
6. Decompress "control.tar.gz". There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: lpia"
9. Open the other archive "data.tar.gz". There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files "control.tar.gz" and "data.tar.gz"
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!


This has been tested (and currently working) with: Skype, Opera, Picasa, Adobe Flash 10.
To install Picasa I have used:
sudo dpkg --force-architecture -i (route to my picasa deb)
and it has worked perfecty well. This seems a much easier method than the one reported above and plan to keep usisng it with other debs. Should I expect any problem with it? Thanks.

---

### Post by mecrider on 2008-11-23
There is an Italian bash script that automates this process of converting i386 debs to lpia, available at [http://www.blogwol.com/2008/11/08/script-per-convertire-deb-da-i386-a-lpia-per-intel-atom/]("http://www.blogwol.com/2008/11/08/script-per-convertire-deb-da-i386-a-lpia-per-intel-atom/"). Of course it works fine on other language systems. Just put the script in your path, and it will convert all the .debs in the directory you run it from.

---

### Post by mecrider on 2008-11-23
> **peril62 said:**
> To install Picasa I have used:
sudo dpkg --force-architecture -i (route to my picasa deb)
and it has worked perfecty well. This seems a much easier method than the one reported above and plan to keep usisng it with other debs. Should I expect any problem with it? Thanks.

As the first post said, this way the package doesn't show up in Synaptic, so you can't use that to remove or update it. However, you should still be able to use "dpkg -r" if you want to remove it. (DISCLAIMER: I haven't tested this, as I don't have my Dell Mini yet.)

---

### Post by runningdoc on 2008-12-11
These directions worked beautifully and this is from a person who received the mini about 2 weeks ago, never worked with Linux or Ubuntu until then and still was able to make it work with these excellent directions.  Thank you so much for sharing your knowledge.

---

### Post by feranick on 2008-12-12
I took liberty of translating the script, which does pretty much what the howto does, but automatically. I also fixed it so that it converts ONLY i386 packages (the original one converts packages with any architecture, when only i386 can be really converted).

To run the script: 
1. Copy the script in the same folder as your i386 packages

2. Run the script either from the command line or by double clicking on it. This last step requires you to change permissions to make it executable (right click on the script file and check the "Allow executing file as program" in the permission tab.

3. Enjoy.

---

### Post by anjilslaire on 2008-12-13
This is all great, bit I wish Canonical would support full-blown lpia repositories so we could install & update freely. 
Then we could choose from
x86
x64
PPC
lpia

Or am I the only one?

---

### Post by Fatjuan on 2008-12-13
Just used feranick's procedure. 
Thanks so much!

---

### Post by dragonmojo on 2008-12-15
> **Fatjuan said:**
> Just used feranick's procedure. 
Thanks so much!

Ditto.
I am such a noob to Ubuntu/Linux. Followed the instructions and was successful installing Skype!

---

### Post by jsonder on 2008-12-18
> **anjilslaire said:**
> This is all great, bit I wish Canonical would support full-blown lpia repositories so we could install & update freely. 
Then we could choose from
x86
x64
PPC
lpia

Or am I the only one?

Far from being the only one.  An lpia option IS needed.

---

### Post by kelvin911 on 2008-12-24
dpkg-deb: failed to open package info file `skype-debian_2.0.0.72-1_lpia/DEBIAN/control' for reading: No such file or directory

what did i do wrong?

---

### Post by kelvin911 on 2008-12-24
oh, i use the script and it works perfectly,

---

### Post by bobdi on 2008-12-25
I am having the same problem installing Adobe Flash 10 on my new dell mini

I can not get the package to reassemble manually

no matter what i get an error like this:

dpkg-deb: failed to open package info file `flash10/DEBIAN/control' for reading: No such file or directory

also tried to run the script several ways.  it appears to complete quickly but nothing changes

can anyone help with a adobe flash 10 install on my dell mini?

---

### Post by hthakar on 2008-12-26
1.) Put the script file in the folder with your deb files.... *[COLOR="Red"]*_i386.deb[/COLOR]*

2.) right click on the downloaded *[COLOR="Red"]deb2lpa_en.sh[/COLOR]* and goto *[COLOR="Red"]properties[/COLOR]*

3.) Click on *[COLOR="Red"]Permissions[/COLOR]* Check the box to the right of *[COLOR="Red"]Execute[/COLOR]*

4.) Now double click on the *[COLOR="Red"]deb2lpa[/COLOR]* file and choose either "run in terminal" or just "run". 

5.) You should see new deb files in the format *[COLOR="Red"]*_lpia.deb[/COLOR]* as well as your old i386.deb files. 

6.) goto command prompt and cd into the Deb files folder. use the following command
[COLOR="Red"]sudo dpkg --install *lpia.deb[/COLOR]

I just used this to install openoffice 3.0 on an acer aspire1 with intel atom processor. It works like a charm.

---

### Post by bobdi on 2008-12-26
I got the script to convert my deb.  I first had to rename the Adobe Installer to end in *._i386.deb
 
Adobe flash 10 installed fine but is does not work!!

any flash webpage says "plugin required"  as if firefox thinks it is not installed

removed and reinstalled....no luck

removed and installed flash 9 from synaptic and it still does not recognize

so i am stuck with no flash

any other ideas before i format and reinstall?

---

### Post by nshm on 2008-12-26
Many thanks for feranick's script (& those that came before). It worked seamlessly with my mini installing Picasa.

---

### Post by sirebral on 2008-12-27
Could this be placed in the WiKi?

There doesn't seem to be any place for Netbooks yet.  This would be a good start.

---

### Post by sirebral on 2008-12-27
> **anjilslaire said:**
> This is all great, bit I wish Canonical would support full-blown lpia repositories so we could install & update freely. 
Then we could choose from
x86
x64
PPC
lpia

Or am I the only one?

Also, no you are not the only one.  And this tutorial is nice, but it is now one huge reason why I feel LPIA is a waste of time.  Sorry for my prejudice here but Intel missed the mark and reinvented the wheel.

---

### Post by slyman66 on 2008-12-28
I have spent days trying to upgrade to flash 10 and I am almost at the reinstall stage as its driving me mad !
I need help please.
I have the zipped folder "install_flash_player_10_linux.deb" on my desktop and I have dowloaded the script but cant get it to create anything.
I really want to get on with linux but this is just a terrible start
:(
Ok i have managed to get the scriptto produce a folder named "install_flash_player_10_linux._lpia.deb" on my desktop.
I know its "cd" in the terminal but i have no idea where the desktop is :)

---

### Post by sirebral on 2008-12-28
cd Desktop

The terminal is case sensitive.  Also, when you are changing into directories that have a space you need to provide a '\'.  Example: My Documents

You would type:
cd My\ Documents

good luck. :)

---

### Post by anselm13 on 2008-12-28
bobdi:
Try this
[http://mydellmini.com/forum/howto-upgrade-to-flash10-t956s25.html](http://mydellmini.com/forum/howto-upgrade-to-flash10-t956s25.html)
I didn't have flash 9 uninstalled before I had flash 10 installed (I built an lpia deb, but either using an lpia deb or force i386 deb appears to work).  So I had to reinstall flash 10 deb and then it worked.

---

### Post by slyman66 on 2008-12-28
Thnkyou :) I got it to install ok but flash is still broken. Im starting to hate linux/dell. What does an xp install run like ?

---

### Post by slyman66 on 2008-12-28
thanks for the  link, used the terminal commands and got it working at last :)

---

### Post by feranick on 2009-01-04
I made a lpia package for the script presented above in this thread. The script converts i386 packages into lpia packages. 

After installing the package, the script is accessible from the command line using the command: 

```
deb2lpia
```

inside the folder containing the i386 package to convert.

---

### Post by cyberwill on 2009-01-05
> **feranick said:**
> I took liberty of translating the script, which does pretty much what the howto does, but automatically. I also fixed it so that it converts ONLY i386 packages (the original one converts packages with any architecture, when only i386 can be really converted).

To run the script: 
1. Copy the script in the same folder as your i386 packages

2. Run the script either from the command line or by double clicking on it. This last step requires you to change permissions to make it executable (right click on the script file and check the "Allow executing file as program" in the permission tab.

3. Enjoy.

Script fails with "dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)". I am newbee, any suggestions?

Thanks,

---

### Post by yakinikku on 2009-01-06
i would like to add that this does not mean every package will install properly.  one example of this is with google gadgets.

while the repackaging process works and the program installs, it doesn't install the dependencies for google gadgets, nor is there any indication of what dependencies they are.  running the force architecture tells you the dependencies.

TO OP: kudos to you for writing this, it has helped me tremendously!

---

### Post by feranick on 2009-01-10
> **cyberwill said:**
> Script fails with "dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)". I am newbee, any suggestions?

Thanks,

You could just set a new permission to the control file. To make life easier I fixed that in the script, which you can find attached (along with the deb package).

---

### Post by feranick on 2009-01-10
> **yakinikku said:**
> i would like to add that this does not mean every package will install properly.  one example of this is with google gadgets.

while the repackaging process works and the program installs, it doesn't install the dependencies for google gadgets, nor is there any indication of what dependencies they are.  running the force architecture tells you the dependencies.

TO OP: kudos to you for writing this, it has helped me tremendously!

A deb package is composed by two main objects, the control file and the data. The data is obviously the set of binaries and libraries, while control is a file with all the info required to track the package (version, dependencies etc). The repackaging basically extract these two sets of files, and changes one bit of info in the control file (the type of architecture, from i386 to lpia). Everything else is the same, including the dependencies, which are then tracked by apt. So if dependencies are required, they are in fact installed. If the package doesn't work may mean that the actual dependencies are different in the mini than those expected by the application. But again, this is not dues to the packaging or the repackaging not tracking the dependencies, but instead to the customized libraries in the mini itself.

---

### Post by feranick on 2009-01-10
> **bobdi said:**
> I got the script to convert my deb.  I first had to rename the Adobe Installer to end in *._i386.deb
 
Adobe flash 10 installed fine but is does not work!!

any flash webpage says "plugin required"  as if firefox thinks it is not installed

removed and reinstalled....no luck

removed and installed flash 9 from synaptic and it still does not recognize

so i am stuck with no flash

any other ideas before i format and reinstall?

Unfortunately Flash 10 as a deb package is very different than any other regular debs. It contains a script that actually download the binaries and runs a specific adobe installer. I know this doesn't work well in the vanilla hardy.

---

### Post by emnii on 2009-01-11
Thanks for this, I was really going nuts trying to install Truecrypt!

---

### Post by vickoxy on 2009-01-23
Hi,
i am newbie to Ubuntu, so i need little help. I want to install two original Canon drivers for my MP620:
   1. cnijfilter-common-2.80-1.i386.deb
   2. cnijfilter-mp610series-2.80-2.i386.deb

 But when i try to do that i become these results (see pictures).
I have dell mini 9, and i described my problem also here:
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)
I think i should adapt these drivers to lpia but don´t know how.
So, any help will be appreciated
Thanks

---

### Post by vickoxy on 2009-01-24
Hi, me again. I am reading here that is possible to make these files to work with command *force* or with some *lpia* converter, but they are all talking about packages-does it work with files/drivers? If someone, please, can write me commands i should use, i will appreciate it.
Thank you

---

### Post by feranick on 2009-02-02
Just to clear up some confusion: drivers, files, program, are usually distributed as packages in Ubuntu. Packages are nothing more than containers, with extra info for the package manager to know where to place such files, how to configure them, etc.

In your case, your original drivers actually are packaged as debs. These debs are for the i386 architecture. As you found out you can force them to be installed, but it is recommended to repackage them for the lpia architecture (the files will end up with ..._lpia.deb. This is nice and convenient because then you can uninstall them using Synaptics or apt. You can find the deb and instruction above in this thread.

One thing, however, the package manager and the repackaging process in general, won't do. If there are some missing libraries that the drivers will require, than such driver might not work (as it seems from your attached image 2). You might want to check for update drivers, and system requirement. Also, keep in mind that these are most likely closed source drivers, and there is thus little modification you can apply to make them work.

---

### Post by runningdoc on 2009-02-08
I am trying the script above and don't know where to put the files.  I saved adobe flash download to the desktop and then saved deb2lpia to the desktop and don't know what to do from there. I opened the deb2lpia but guess I am doing it wrong and not understanding where to put the files or what to open first and where to put it.  Any help would be appreciated.

---

### Post by ugm6hr on 2009-02-09
Flash 9 is installed as default.  Why do you need to install it?

Even if you do, I would suggest installing from [here]("apt:flashplugin-nonfree").

---

### Post by feranick on 2009-02-09
> **runningdoc said:**
> I am trying the script above and don't know where to put the files.  I saved adobe flash download to the desktop and then saved deb2lpia to the desktop and don't know what to do from there. I opened the deb2lpia but guess I am doing it wrong and not understanding where to put the files or what to open first and where to put it.  Any help would be appreciated.

If you need just flash (version 9.0), as it was said, it should already installed by default. If you want to install version 10, here some guidelines.

[LIST=1]
[*] Download the [deb2lpia script as the deb package]("http://ubuntuforums.org/showpost.php?p=6528287&postcount=28").
[*] Install it by double clicking on it.

[*] Download your [flash 10 deb package]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb"). Save it on your desktop

[*] In order to have the script to work, rename the name of the package (select it and push F2) so it ends by "i386.deb". For example, if the package name is:

```
install_flash_player_10_linux.deb
```

rename it to:

```
install_flash_player_10_linux_i386.deb
```

[*] Open the terminal, and redirect to the desktop:

```
cd Desktop
```

[*] Run the script by typing: 

```
deb2lpia
```

[*] After completion, you should have a new deb package on your desktop, called:

```
install_flash_player_10_linux_lpia.deb
```

[*] Install it by double clicking on it.

[*] It should be installed, now.

[/LIST]

---

### Post by runningdoc on 2009-02-09
Thank you for the instructions as i will be able to use this with more than just flash.  I somehow goofed up the current install of flash as I haven't had it work correctly for a while now and was trying to fix it.  I hadn't included that small tidbit in my first post and appreciate your help.

---

### Post by nightalon on 2009-02-26
So I just had a crazy idea.

I love the idea of a simplified interface such as that in Ubuntu Netbook Remix.  I'm looking at buying a Samsung NC10/EeePC 1000HE, modding in a touch screen, and using UNR.

I've already tested the desktop-switcher package to switch between UNR and standard Ubuntu, and it works great.

However, Ubuntu UMPC/MID version is a whole 'nother can of worms!

Since it's LPIA and the repos don't have any sort of Nvidia drivers, I can't test it out on my tablet PC.  (LPIA works on more than just Atoms by the way...:D)  I hope to use this script to convert the Nvidia binaries from their website, or possibly just use the force-architecture option.

FYI, I'm using a Toshiba Tecra M7, and can boot into the UMPC/MID images using the boot option "xforcevesa."  Tricky, I know.  The Jaunty daily build crashes pretty regularly, but I think that's because it's a daily build.

I actually think LPIA is a good thing.  It sucks right now since the repositories aren't full.  However, it allows Intel to build chips with functions that can take advantage of compile-time optimizations.  For example, it might take less wattage to add 3+3+3 than to multiply 3*2.  Ideally, i386 binaries would perform the latter (faster) method when plugged in and the former (less-power) option when on batteries.  I don't think we've reached that point in any OS with any binary.  But LPIA is a step in the right direction.  Maybe LPIA will one day be the optimal choice for any x86 architecture.

Gotta love the 'Buntu.

---

### Post by nightalon on 2009-02-27
Oh, also: I think it would be AWEsome to have one X "Session" for UMPC/MID edition and one for Regular Ubuntu with the desktop-switch app.  Seriously guys.  Friggin' awesome.

Now all I need is a netbook/netvertible/netbook-with-modded-on-touch screen.  CRAzy.

---

### Post by nightalon on 2009-02-27
It turns out that UMPC is i386, not LPIA.  If you successfully do a first boot with xforcevesa, the open source drivers automatically get installed.  This holds true for MID edition as well.

The i386 to LPIA package doesn't work with the ATI drivers because they have md5 sums.  Will update if I succeed.

UPDATE:

The latest ATI fglrx driver will install on Ubuntu MID with LPIA!  Craziness.  I even had Google Earth running.

I still never really found the true "Clutter" GUI.  Oh well; I give up for now anyway.  I wonder if the NVidia binary drivers would install if I had figured out a way to terminate hildon without it restarting immediately thereafter.  As far as I know, the NVidia installer will not create .deb packages, so I can't use the same tricks there.  The NVidia installer will likely just freak out.

---

### Post by momokuri on 2009-03-08
I made a yet another script independently, so it may help you to improve your script.  This uses fakeroot, dpkg-deb tool chain to manage package.
Also it try to manage some package  not to install unused files, such as i386 kernel driver not lpia.  (Now virtualbox is only a target.) 

> **feranick said:**
> You could just set a new permission to the control file. To make life easier I fixed that in the script, which you can find attached (along with the deb package).

You may want to know how to use repack-deb.sh script,
please just run with -h option.

```
$ repack-deb.sh -h
repack-deb Version 0.94 Release 20090307
Copyright 2009, Hiroshi Miura <miurahr@acm.org>

usage: repack-deb.sh [-d][-v][-t target directory] <debian packages..>

  -t target: set a directory stored converted packages
      if not set, default is current directory.
  -d: verbose messages
  -n: disable specific process for some application.
      eg. VitualBox, etc.
  -k: keep working directory for debug
  -v: display version
```

---

### Post by kevindubrow on 2009-07-31
> **feranick said:**
> I took liberty of translating the script, which does pretty much what the howto does, but automatically. I also fixed it so that it converts ONLY i386 packages (the original one converts packages with any architecture, when only i386 can be really converted).

To run the script: 
1. Copy the script in the same folder as your i386 packages

2. Run the script either from the command line or by double clicking on it. This last step requires you to change permissions to make it executable (right click on the script file and check the "Allow executing file as program" in the permission tab.

3. Enjoy.

This script works awesome, thank you. I do have one question though. Is there any way to write this script so that if soles any dependency issues? 

I tried installing zsnes on my HP Mini 1000 and got this:
Selecting previously deselected package zsnes.
(Reading database ... 83827 files and directories currently installed.)
Unpacking zsnes (from zsnes_1.510-2.2ubuntu2_lpia.deb) ...
dpkg: dependency problems prevent configuration of zsnes:
 zsnes depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian is not installed.
dpkg: error processing zsnes (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zsnes

I'm just not sure what to do now. Thank you!

---

### Post by Jane41 on 2009-10-27
hiya im also new to linux and having problems getting skype to run i did all the steps to change skype to lpia and i got the same message but i dont understand wat u meant about the script please could you explain to me how to do this 

many thanks

---

### Post by Jane41 on 2009-11-07
Hi please can anyone help, i posted a note on here about repacking skype i386 to lpia about a week ago needing some advice but have so far had no response, my problem is that although i go through all the steps to repackage skype it still does not recognise it, someone mentioned about a script but i havent a clue wat that means please please help as i love my little netbook but cant get skype on it.

Many thanks

---

### Post by shiningkenmonster on 2009-11-07
jane41, what kind of computer are you using?
Do you have a Dell mini 9?
What operating system is it? Was it pre-installed when you first purchase your computer? Or did you install Ubuntu by yourself. if so, what version are you using? Ubuntu 8.04, Ubuntu 9.10?

---

### Post by djangayo on 2009-11-09
@jane41, you could just use the medibuntu repositories to get skype for lpia:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```Skype will be available next time you use apt (synaptic or whatever).

---

### Post by Jane41 on 2009-11-11
ok thanks will give it a try and let u know if it works

---

### Post by Jane41 on 2009-11-11
i get error message 404 not found so dont know wat to do from here pls can anyone help thanks

---

### Post by Jane41 on 2009-11-11
hi im using dell mini 10v operating system ubuntu 8.04 (hardy) with kernel linux 2.6.24-22-lpia but nothing seems to work and also get the error message 404 not found

---

### Post by martingugino on 2010-03-08
Is there any excuse for Dell mucking around with Ubuntu, so that there is a "Dell" UBUNTU?

---

