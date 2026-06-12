---
title: "Help with modem install please"
date: 2006-01-26
forum: Desktop Environments
---

### Post by comsec10 on 2006-01-26
Hello there everyone, I need some configuration help with my modem for Ubuntu 5.10. I am running an AMD 64 and the install went perfect except for my modem. 
The following is the readme right off the driver disk. I apologise if this is a bit long.
//insert//

ReadMe file for the
Intel® 536EP V.92 chipset Linux driver

contents:
1.  License
2.  Release Notes
3.  Installation
4.  File Descriptions
5.  International Users
6.  Beta Tester appreciation
7.  Security issues
8.  Compilation issues
    a. Instructions for Debian Users
    b. Kernel Source
9.  What is the Hamregistry?
10. what's v92 and v44?
11. The Hamregistry tool (for persistance)
12. Known Bugs/Issues
13. Comments, ideas, problems, fixes

-------------------------------------------------------------------------------
1. LICENSE

IMPORTANT - read the file "LICENSE.txt" for the INTEL SOFTWARE LICENSE 
AGREEMENT BEFORE COPYING, INSTALLING OR USING.

-------------------------------------------------------------------------------
2. Release Notes 

      This release supports 2.4.x kernels.

      This release is not compatible with kernels prior to 2.4.

      The 536EP corecode binary was compiled with gcc version 3.2

      v92 support added:  modem on hold AT command set,
      PCM upstream, v44, and quick connect are implemented.			 

      Linux Compatability tests are performed on the latest or previous 
      versions of the following distributions: Mandrake, RedHat, and SuSE

-------------------------------------------------------------------------------
3.  INSTALLATION

Prerequisites:
   1. root access
   2. bash shell to run install scripts
   3. a 536EP modem
   4. KERNEL SOURCE HEADERS FOR THE KERNEL YOU ARE RUNNING.
      and programming development tools installed as well

6 steps to install
   1. login as ROOT 
   2. extract the archive into a directory with "tar -zxvf <archivename>.tgz"
   3. cd into the directory it created.
   4. Type: make clean
   5. Type: make 536ep
   6. Type: make install


Please examine the 536ep-inst script if you have a different distribution.

The driver is split in two.  A serial driver and core driver.
The core driver must be loaded first since the serial driver depends on it.
The serial driver registers itself as character device 
   major number 240, minor number 1.


ATTENTION:  if the driver compiles but the script just wont work for you.
   Here are the bare minimum steps to get your modem to work.

   0.  log in as root.
   1.  insmod -f 536epcore.o
   2.  insmod -f 536ep.o
   2a. you can start "hamregistry" at this point if you wish.
   3.  rm /dev/536ep
   4.  mknod /dev/536ep c 240 1   (note "240" is the default, if it does not 
       work see what /proc/devices says 536ep's major number is)
   5.  ln -s /dev/536ep /dev/modem
   6.  start a comm application like minicom and use the modem.
   7.  see section 3 (International Users) for info on setting the correct 
       country settings.


-------------------------------------------------------------------------------
4.  FILE DESCRIPTIONS

536ep-inst installation script to install 536ep modules and supporting files


files copied to /lib/modules/(kernel-version)/misc
   536epcore.o	driver core code module
   536ep.o	pseudo serial driver for 536ep, depends on 536epcore.o

files copied to  /etc/rc.d/...  (path differes per distribution)
   536ep-boot		boot scrip to start and stop 536ep modules

files copied to /usr/sbin
   hamregistry	hamregistry is the "registry" like tool that the modem uses to 
   get and store persistant data such as county info and profile strings.

files copied to /etc
   hamregistry.bin	file that stores the initial persistant data for modem.


-------------------------------------------------------------------------------
5.  INTERNATIONAL USERS

hamregistry will store the last country setting you
set in the modem.

in minicom (or equivalent comm application)
the commmand to change country setting is "AT+GCI="
the command takes a t.35 country code in hexadecimal.
below is a list of currently supported t.35 country codes.
you can also put this "AT" command in the init string of
the comm application you are using.

if you are a CTR-21 country I think you should be able to 
choose a CTR-21 country on the list and be ok.  but 
that's no guarantee.
The same goes for countries that are "USA" compatable.
(this table also exist in the source file wwh_dflt.c that
ships with the 536epcore driver)

inspect the wwh_dflt.c file provided to find out what your country's t.35 code is.

-------------------------------------------------------------------------------
6.  Thanks to the following beta testers for their valuable input and 
    suggestions during the HaM 333 beta test between January 2 - 26, 2001

Dorian S. Araneda
Sean Walbran
Rob Clark
Marvin Stodolsky
Dominique Duval
Roman Krais 
Ulrich Guenther
Marcelino Viana Pinheiro
Thomas S. Iversen
Jospeh Teichman
Michel Bartolone (MED)
Ramon Gonzalez Montoiro
Ryoji Kawagishi
Torsten Vogel
"jandro"
Ian Carr-de Avelon
Helga Weindl
Ed Casas
Bernhard Hoelcker
Alexander "Sasha" Voytov
Albert Woo
Peter Hirschmann

and all of the helpful Linux HaM users
around the world and at [www.linmodems.org](www.linmodems.org) 

-------------------------------------------------------------------------------
7. Security issues

the 536ep-inst and 536ep-boot file install the files and device nodes as 
root for the owner and group.  
this will cause problems for those who want to user the modem to dialout
using an account other than root.

In SuSE, "dialout" is the group used to install the files and device node.
This way, anyone belonging to the "dialout" group can use the modem to dialout.
(take a look at /etc/group)

I did not want the script to allow full access of the modem to everyone without
"root" knowing.

Edit the 536ep-boot and 536ep-inst scripts to fit your needs.

-------------------------------------------------------------------------------
8. Compile issues
   a. this driver will now compile with the this path:
   /lib/modules/<kernel version>/build/include
   the 2.4.4+ kernels says to copy the /boot/vmlinuz.version.h
   over to the kernel build path.  I have the makefile do this
   if this file exists.  You must install the kernel source
   code anyways.  It should be on your distribution's CD.


-------------------------------------------------------------------------------
9.  What is the Hamregistry?
   The hamregistery is an application that stores data for the 536ep driver onto
   the disk.  hamregistry stores information from the driver that needs to 
   persist from reboot to reboot such as you current country setting.
      The 536ep-inst install script and the 536ep-boot script start this utility 
      automatically for you.
   If this tool is not present when the driver gets used your profile, 
   quickconnect, and current country setting will not be saved but the driver
   should still work fine.	The only step that would need to be done is to
   make sure that the driver is set to the correct country with 
   at+gci= (see section 5)


-------------------------------------------------------------------------------
10. What's v92 and v44?  

   a. modem on hold: (ISP and your ISP dialer must also support this)
      This will allow you to pause your ppp connection to answer an incoming
      call. You will need call waiting, dialer, and ISP support for this to 
      work.  When you are done with the call you can resume your ppp connection
      without having to reconnect.  The AT command set for this feature exist
      in the driver.

   b, pcm upstream: 
      (ISP must also support this, as of version 4.32 I
       dont know any ISP's that do)
      This will allow faster upload speeds.
      to enable: at+pig=0
      to disable: at+pig=1

   c. quickconnect:
      Once you make a call to a v92 modem, your phoneline characteristics are
      stored.  Whenever you make a new v92 connection it will use this data 
      to make the call negotiation  quicker (approx 10 seconds).
      to enable: at+pqc=0  at+pss=0
      to disable: at+pss=2

   d. v44: (ISP must also support this)
      A better compression protocol than v42 which can give you better transfer
      speeds.

-------------------------------------------------------------------------------
11. The Hamregistry tool
   
   The hamregistry tool is used to provide persistance of settings across
   reboots.  The haminst and hamboot scripts automatically setup and start
   the hamregistry background task for the modem to use.
   The hamregistry tool has command line arguments for those who wish to 
   customize persistant settings.  To use these command lines
   you must first stop the driver with "bash hamboot stop".
   Once the driver has been stopped you may run hamregistry with one of these
   arguments to store into the /etc/hamregistry.bin persistance file:
   (supply value for items in < >)
      -mfg <Modem manufactures name>
      -mod <Modem model name>
      -hookflash  <0,1,2>
        hookflash method:  0=(default)without tone  1=with tone  2=reserved
      -v92rptopt  <0,1>
        control v92 reporting:   0=PCM upsteam only       1=(default) all v92
      -gpio_lpohd <0,1>
        Handset Hook detection:  0=not supported          1=(default)supported
      -currentcountry <t.35 code>

   This info is written to the /etc/hamregistry.bin file.
   If hamregistry.bin exists along with the installation files, haminst will
   copy it to /etc/hamregistry.bin when installing the modem.

-------------------------------------------------------------------------------
12. Known Bugs/Issues

   a. If you see this message
      "536ep:rs_open: DSP did not reset. try again or restart computer"
      and you KNOW you have a HaM modem installed
      Disable "PNP OS" in your bios.  There is a problem with the driver and 
      linux PNP.  After a time, Linux PNP will disable the card and the driver
      currently can not reenable itself.
   b. Be aware that the build replaces your 
      /lib/module/<kernver>//build/include/linux/version.h file with 
      /boot/vmlinuz.version.h
      (this is what Linus T. told me to do with a compiler error)
   c. There may be an incompatibility with DevFS. The 536ep device may be located
      in /dev/tts/536ep
      instead of /dev/536ep.  Be aware of this and link /dev/modem to the 536ep
      device that corresponds to your setup.
   e. Incase you are having problems making a ppp connection try using wvidal
      with this information below. execute the script and it will have wvdial
      make the ppp connection

   ------my script----------------------
   #! /bin/sh
   /usr/sbin/pppd -detach lock asyncmap 00000000 \
      defaultroute debug /dev/modem 57600 \
      ipparam ppp0 linkname ppp0 \
      noauth \
      connect "/usr/bin/wvdial --chat bellsouth"

   ------my /etc/wvdial.conf section ---
   [Dialer bellsouth]
   Modem = /dev/modem
   Baud = 57600
   Init1 = ATZ
   Inti2 = ATQ0 V1 E1 S0=0 &C1 &D2
   Dial Command = ATDT
   Phone = 6859500
   Username = myloginname
   Password = mysecretpassword
   #Ask Password = 1
   Stupid Mode = 0
   ------------------


-------------------------------------------------------------------------------
13. Comments, ideas, problems, fixes? please contact:

Linux Voice Band Modems (VBM) of Intel Residential Access Division (RAD)

[email]vbm.linux@intel.com[/email]
[http://developer.intel.com/design/modems/](http://developer.intel.com/design/modems/)

To restrict email volume, please email only development related issues that are
needed to fix a bug or improve the driver. General questions on how to use the 
Linux may not be responed to.

Other resources and information on Linux controllerless modems can be found on 
these usefull sites

[http://www.linmodems.org](http://www.linmodems.org) 
	and
[http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)

//FIN//

I am slowly pulling what is left of my hair out and could really use an espresso right about now.

TIA

---

### Post by fairdoes on 2006-01-27
I've got the same file that you display, and plenty of others, and none of them work.
 Bill Gates must be delirious with joy if he browses forums like this. 'Oh good,' he'll say. '95% of the world will never get online with linux!'

 Help please?[-o< , preferably in English, non-abbreviated, and not composed of Acronyms. Thanks:)

---

### Post by ddtmsa on 2006-01-27
Here's the things I did to get my Intel537ep modem to work, guessing that there shouldn't be too much difference.

Firstly you need to get the tools to compile your own driver set up:

Run the following commands with the Ubuntu CD in the drive

> 
sudo apt-get install build-essential
sudo apt-get install linux-headers2.6.12-9-386

Note that second install is for generic intel distribution, for the OP I'm not sure what the exact file name for the 64 bit distribution, you should be able to search via Synaptic for the linux headers files on the CD.

Now assuming you still have internet access, download the following files

> 
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)


and then copy over to your ubuntu files and install them

> 
dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb


and then make an appropriate link for compiling:
> 
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc


The next step is to compile your driver following all the steps in the readme the OP listed in his original post.


You may have to get a more recent version of the driver from [www.intel.com](www.intel.com) as Ubuntu5.10 is based on the 2.6.x kernel, not the 2.4.x kernel as indicated in the readme.

Don't get disheartened, you may have to do little bits of tinkering, but it is possible without too much effort just .... Don't Panic!

---

### Post by fairdoes on 2006-01-27
I've had to remove ubuntu in order to spend hours re-installing windows 98 in order to get online, but i believe the ubuntu system showed a desktop with about 3 options at the top of the page.

As a newbie, i have two possibilities at each stage - i can either navigate with the mouse, or I can type at the keyboard.

Are there instructions anywhere on how to proceed? Because commencing with typing, at the desktop, as per this reply, achieves nothing.[-o<

Where, for example, does one run the quoted commands?

Which part of the reply is the 'second install'?

What is 'the OP'?

What is 'Synaptic'?


I've checked my site stats and 99.7% of visitors aren't using Linux - maybe there's no instructions in English /French / German / Spanish, etc, for installing a dial up modem:mad:

---

### Post by comsec10 on 2006-01-27
Hey thanks for that. I had no problem with the setup in RH & SuSE but all the tinkering is worth it. I appreciate everyone's comments.

CS10

---

### Post by ddtmsa on 2006-01-27
[QUOTE=fairdoes]I've had to remove ubuntu in order to spend hours re-installing windows 98 in order to get online, but i believe the ubuntu system showed a desktop with about 3 options at the top of the page.

Are there instructions anywhere on how to proceed? Because commencing with typing, at the desktop, as per this reply, achieves nothing.[-o<

Where, for example, does one run the quoted commands?

Which part of the reply is the 'second install'?

What is 'the OP'?

What is 'Synaptic'?


[/QUOTE]

Ok, first up, what you describe in your first paragraph sounds like a fully installed system.

Next, to get a window you can enter commands in, go through the first of the options at the top  Applications -> Terminal  This is where you can type the commands.

When I said second install, I meant the second command I listed in my original post.

OP means Original Poster ... that is the person who sent the first post in this thread.

Syanptic is the built in 'Windows' type installer programme; no need to use a terminal. Go through System -> Administrator -> Synaptic at the top of the screen.

p.s. I would suggest looking through some of the Linux/Unix for new users faqs/sites for some essential information ... Linux tends to work best as a text command interface rather than a point and click one.

---

### Post by DarkW0lf on 2006-02-25
ddtmsa

what is the file sizes of the three deb packages?
I do not have access to net from ubuntu without the modem working.
If I can put them on a floppy I can transfer that way from a pc that is connected. (Maybe I should try downloading them from your post) :)

I haven't tried making a cd that ubuntu can read yet so I want to know if they fit on a floppy (or three). Otherwise I think I can follow those instructions.

To me OP always meant Operator, guess I get that from Amateur Radio and the like.

---

### Post by DarkW0lf on 2006-02-25
Okay I got the three deb packages.

Are debs already compressed?
Compressing a second time won't give me much leeway.

What is the working directory for all this?
Where am using 'dpkg' and 'ln' at?

Do I have to keep an eye out for any conflicts between gcc 3.4 and gcc 4

---

### Post by ddtmsa on 2006-02-26
[QUOTE=DarkW0lf]
What is the working directory for all this?
Where am using 'dpkg' and 'ln' at?

Do I have to keep an eye out for any conflicts between gcc 3.4 and gcc 4[/QUOTE]

You need to open a terminal window and enter the commands in that window. I've not come across any conflicts, but I am no expert.

---

### Post by DarkW0lf on 2006-02-26
After Step 6 (make install)

the system returns:
unknown distribution. no boot scripts installed
make: *** [install] Error 1

Is this an ignorable error? Is the driver built and I am just left without any scripts?

What do i do about boot scripts?

---

### Post by ddtmsa on 2006-02-26
Not sure about that error message, though if you have gotten through the previous **make** commands then you would appear to have installed the necessary packages.

My best guess is that you have not downloaded (or otherwise obtained) the correct file from intel.com. For example, the method I outlined works for the Intel-537ep file I downloaded for the 383 kernel for my Intel celeron processor; however, I have not been able to persuade the 686 kernel (which I have been playing about with) to let me go online with the same file and using the commands I outlined above. 

You appear to be making significant progress, and if absolutely nothing else, you will be learning more and more about linux/ubuntu. For perspective, I dual boot ubuntu and XP and I view playing about with ubuntu as ... well a pastime, which some day might become something more.

---

### Post by DarkW0lf on 2006-03-04
It seems that everything is ok.

No script for ubuntu in current package, so I went with the second set of steps they had and it works now. I have to manually set the modem in the networking tool to /dev/modem myself because it doesn't autodetect it.

I can dial-out and connect to the ISP, but firefox can't resolve url's.
Will it not use the ISP DNS automatically ?

I am searching the forums for this as I type.

---

### Post by rooman on 2006-03-08
howbout some thing for us point &clik users:confused:

---

### Post by DarkW0lf on 2006-03-25
Are you asking me ?
What are you asking for ?

---

### Post by peopaiva on 2006-04-13
I had this same problem, but my modem is a Intel HaM V92, and i´m using Ubuntu 5.10 with kernel 2.6.12. It´s said that there is no driver for this case, that this modem is no longer supported. What would you say? Can you help me? ](*,) 



[QUOTE=DarkW0lf]After Step 6 (make install)

the system returns:
unknown distribution. no boot scripts installed
make: *** [install] Error 1

Is this an ignorable error? Is the driver built and I am just left without any scripts?

What do i do about boot scripts?[/QUOTE]

---

### Post by DarkW0lf on 2006-04-21
Do you know the actual modem model ?
Ubuntu does not appear to be supported by some manufacturers yet.
But since it is based on debian, the idea is that debian drivers may work.
That was my case but I had to compile them.
The instructions for my model worked except there are no boot scripts.

I also need to get the right DNS server ip's from my ISP.
I can connect to the internet I just can't seem to get any url resolved.

---

### Post by az on 2006-04-21
[QUOTE=peopaiva]I had this same problem, but my modem is a Intel HaM V92, and i´m using Ubuntu 5.10 with kernel 2.6.12. It´s said that there is no driver for this case, that this modem is no longer supported. What would you say? Can you help me? ](*,)[/QUOTE]

You can try the sl-modem drivers.  They work with a lot of the ac97 codec modems.

[QUOTE=rooman]howbout some thing for us point &clik users:confused:[/QUOTE]

If modem manufactureres made proper open-source free-libre drivers for linux, there already would be.

---

### Post by lifeartist on 2006-04-24
I succesfully installed Intel 536ep modem, with the instructions included in attachment, but whenn i connect, there's no way of getting on the net, and connection brokes after 30-35 seconds. I connect via gnome-ppp that works with wvdial. Does anyone have an idea whut could be problem whit this?](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by pellgarlic on 2006-05-05
can i point anyone having problems installing an intel 536ep based modem to this thread:

[http://ubuntuforums.org/showthread.php?t=169793&page=2](http://ubuntuforums.org/showthread.php?t=169793&page=2)

where i came to a solution for the "unknown distribution. no boot scripts installed" problem, thanks to the help of the others in the thread.

basically, these prerequisites have to be filled (i used the _uncompiled_ "Intel-536EP-4.71.tgz" download from [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng) for this):

1. build-essential must be installed (best done using synaptic, and the ubuntu install cd as a repository - for me, it was already listed as a repository, but you may need to "add cd". using the cd means that "make", which is also necessary, and a few other packages are also installed automatically).

2. gcc-3.4 must be installed (links have been provided earlier in this thread, and also in this thread: [http://www.ubuntuforums.org/showthread.php?t=79896](http://www.ubuntuforums.org/showthread.php?t=79896). this is needed to compile the "kernel module" - i.e. the modem driver, as it must match the version used to compile the kernel itself, which for ubuntu 5.10, was gcc-3.4, but ubuntu installs gcc-4.02 and not 3.4)

3. the "Intel536_inst" script file (can be found in the folder that the drivers were extracted to) must be edited to include a new section for recognising the ubuntu distribution and installing the files in the correct place. the necessary edit can be found on the first thread i linked to. 

(disclaimer: the edit seems to work for me, but i am not 100% sure that i have told the script to put the files in the right place. i use breezy 5.10, so if you do too, it probably should work. although i'm just a beginner, so i can't say for certain it won't do damage. i felt comfortable experimenting, and accepted the possibility that i could mess up the system and have to start again. it's your choice).

good luck! :)

---

### Post by peopaiva on 2006-06-21
It ran ok until making the module but when it came to run command "# make install" a message like "the modem is not listed in /proc/modules" appeared. I believe when the module is compiled the /proc/modules has to be changed to include the modem, am i right? So, what do i do now???

Thanks for the help!

---

### Post by pellgarlic on 2006-06-22
@peopaiva - are you sure the "make 536" command worked properly? that command should create the actual module itself, and that error sounds like it hasn't been created. you should read the last ten lines or so of the text that is produced after you type the command - there may be errors mentioned. don't assume that just because there is lots of lines of text, that it has worked - these things can often fall over at the last hurdle.

---

### Post by DarkW0lf on 2006-06-28
"the modem is not listed in /proc/modules"

peopaiva, I know I had to add the modem to /proc/devices I am not sure about proc/modules I don't recall getting that exact message.

Does anyone know about installing drivers for this modem under Drake 6.06. Do I still need to installl those other packages to compile properly or can I use the version that comes with 6.06. I mean do I need the 3.4 version of cpp and gcc or do I use some other version ? The dialup how-to has info on the 536ep modem but nothing specificly for dapper drake users.

---

### Post by pellgarlic on 2006-06-29
@darkwolf -

you don't need to install gcc3.4 and cpp3.4 for dapper - the version of gcc that comes with dapper is the same version that was used to compile dapper's kernel (4.0), so it will work. you still need to install build-essential.

---

### Post by DarkW0lf on 2006-07-07
pell have you tried your script in drake 6.06 ?
I am looking to create the boot script to avoid having to manually add my modem to the system each time I want to use it.

---

### Post by pellgarlic on 2006-07-17
hi - sorry for late response - i've been on holiday for two weeks.

i am currently still using the same modem successfully with dapper drake (6.06) using the same modification of the "Intel536_inst" file i used for breezy badger (5.10).

---

### Post by DarkW0lf on 2006-07-26
That's ok, mentally I have been on holiday for five years...

or was it six ?

I'll see if the script works this weekend when I have more time.

---

### Post by DarkW0lf on 2006-07-29
Tried the script by itself (no visible prompts or errors displayed) and also retried "make install".

Bash reports an error :

rm -f /etc/hamregistry.bin
bash Intel536_inst
running kernel 2.6.15-25-386
'ntel536_inst: line 208: syntax error near unexpected token 'in
'ntel536_inst: line 208: 'case $KERNVER incase $KERNVER in
make: *** [install] Error 2

---

### Post by pellgarlic on 2006-07-31
darkwolf - are you definitely following the instructions included in the driver download? (i.e. run "make clean", "make 536", then "make install").

also, make sure there are no typos in the Intel536_inst file - that error looks like it might be a typo somewhere in the file.

double-check the edit i have suggested on: [http://ubuntuforums.org/showthread.php?t=169793&page=2](http://ubuntuforums.org/showthread.php?t=169793&page=2)

---

### Post by DarkW0lf on 2006-08-07
It appears that I copied the script as it is listed in your posting.

I'll redo the compile and install and still see if it hangs at the same point.

I am not that famaliar with shell scripting and do not know what typo may be causing this.

---

### Post by DarkW0lf on 2006-08-07
no same error as I posted on 1 week ago (I wish the forum software didn't do that).

---

### Post by DarkW0lf on 2006-10-13
Tried the dialup howto a second time and now the modem is functional though I do not know how well it is working. But at least I can connect.

I don't know what is wrong when I tried the install sricpt you modified pellgarlic.

---

### Post by pellgarlic on 2006-10-14
yeah, sorry i wasn't more help DarkW0lf - i've been really busy with other things recently, and i'm by no means an ubuntu expert anyway :) 

i honestly don't know why the script didn't work for you. it possibly has to do with variations from system to system, and the changes i made to the script file were enough to make it work on my system, but not on yours.

glad you seem to have got your modem working anyway. you could also consider checking the various sites that list which modems work well with linux, and splashing out on a new one for christmas (or asking for one for xmas ;) ) altho if you've got things working just now, maybe you don't need to do that...

---

### Post by DarkW0lf on 2006-10-18
This is an internal hardware modem that is listed as supported.
I didn't have a particular problem with having to compile drivers, which did work for me. It was installing the driver that became the problem for me. Now the only hardware I have an issue with is the sound card. Cool only one more to go.

---

