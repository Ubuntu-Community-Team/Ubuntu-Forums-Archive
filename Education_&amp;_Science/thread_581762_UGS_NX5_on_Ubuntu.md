---
title: "UGS NX5 on Ubuntu"
date: 2007-10-19
forum: Education &amp; Science
---

### Post by Showan2 on 2007-10-19
hi

Has anyone got luck on installing NX5 on Ubuntu? I just managed to install with lot of hacks (Don't get me wrong, I have a legal license file).
When it boots up it the terminal complaints:

"X Toolkit Warning: No font found"

And the program gives an error about missing Motif file.
Some of the menu's don't have text where they are supposed to be.

Suggestions?

thanks

---

### Post by Showan2 on 2007-10-23
OK I managed to solve all problems... if anyone has experiencing problems installing NX on Ubuntu they can always contact me...

---

### Post by lcardoso on 2007-11-23
Showan2,
What version of Ubuntu are you using? Is it 64 bit?
Could you post your hardware configuration?
Thanx,
LC

---

### Post by meastp on 2007-12-04
> **lcardoso said:**
> Showan2,
What version of Ubuntu are you using? Is it 64 bit?
Could you post your hardware configuration?
Thanx,
LC

What he said...

We are using NX5 at the university, and I'd really like to run it in ubuntu, rather than rebooting into windows.

---

### Post by Showan2 on 2008-01-06
Hi

Sorry for this late reply!

Because I had a few people asking questions about installing NX 5 on Ubuntu, I will try tro explain here how I managed to install and run it:

My system specs are: C2D E6300, 2GB of RAM, Geforce 7600 GS with Gutsy 64 bit now. Remember, ***you need a 64 bit OS!***

**_Step 1: Get a CID key (Composite ID)_**
First of all, you need a CID key for Linux. This is a key based on your hardware and OS.
On the GTAC support site (contact you school for a webkey) you will find 2 CID key generators, one for Suse 64 bit and one for Red Hat 64 bit. Both will work and both will generate the same key on all 64 bit Linux OS. Strangely they are named xxxx.exe but don't let they fool you you can just run it with ./xxxx.exe. The windows CID key generator generates a different key, so it's useless!
Send your CID key to your school, employer or directly to UGS/Siemens and they will send you a license file.

**_Step2: Get a copy of NX5 for Linux _**
Secondly,  get a legal copy of NX5 for Linux (Suse 64). If you have a webkey account with fixed IP you can just download the install files from the GTAC support site.
Otherwise, your school can get the install DVD's for you via UGS/Siemens .There's also a Linux version of other interesting software (Nastran/Cast/...), you might want them to.

**_Step 3: Installation of the files_**
Now begins the actual installation of NX5 and it's components. Unpack all the installation files. Inside there is usually a few compressed maps with a complex ksh script (I used pdksh). 
The ksh script is the install script, but it has to be slightly modified. It's designed to handle all sort of UNIXes but as a drawback it's unnecessary complex. I can't remember exact all of the modifications I made, because I don't have the install files anymore. But I will try:

***Step 3a: Make the install scripts executable***
Easiest way is to rightclick them and make them executable in the properties dialog.

***Step 3b: Decide where you want to install the files***
I made a map /opt/UGS where I installed all the files. Standard install goes to /usr/ugs and usr/ugslicensing.

***Step3c: Install ugslicensing***
cd *dir-with-installation-files-of-ugslicensing* && ./*name-of-installscript*
Respond to questions asked, you will likely get some error.
 With every install script always check the Linux parameters: when you see something like  
 ;;
  Linux) # Linux machine.
check if all  parameters are ok for you (for example installation dir for the software)
I remember also an error about the used uncompressing package, replace it with the one that's installed in Ubuntu. (find the package name with synaptic)

***Step 3d: Install NX5 basefiles***
If you try to run the unmodified ksh script (cd *dir-with-installation-files-of-nx5* && ./*name-of-installscript*) it will get stuck at a certain point in a loop. Open the script with a text editor (probably you need root permissions), find the message that it returns, and just comment that part of the script. Also modify the parameters as described in 3c.
Now try to run it and respond to the questions asked.
If this still doesnt work give me the error I will try to help you.

***Step 3e: Install NX5 maintenance packs, maintenance relases, NXNastran solver, nxcast, documentation,....***
Just repeat Step 3d for this kind of software. Remember to direct updates to the right install dir.
Maintenance releases and updates can be found on GTAC Support Site, webkey is needed.

:::::::::::::::::::::::::::::::::::::
ALTERNATIVE INSTALL METHOD: (Instead of 3c-3e)

If the above didn't work for you, I don't know if this procedure would work, I never tested it.
*make a map like /opt/UGS
*unzip all the pieces in the installation folder (admin,bin,catiav5,....,ugii(base dir)) and copy the maps to /opt/UGS
:::::::::::::::::::::::::::::::::::::::

Ok now installation is hopefully successfull, a fews more things need to be done for we can run NX5 and all it's components:

**_Step 5: modify license file_**
Hopefully by now you got your license file from UGS.
Open it with sudo.
Modify 16th line: SERVER *hostname* COMPOSITE=xxxxxxxxxxxxx  *portnumber*
Replace hostname and portnumber (usually 28000). Hostname is usually the hostname of your computer.
I named the license file ugs.lic.

**_Step 6: modify /etc/profile_**
sudo gedit /etc/profile
At the bottom, add: 
UGII_BASE_DIR=/opt/UGS ; export UGII_BASE_DIR
UGII_ROOT_DIR=/opt/UGS/bin/ ; export UGII_ROOT_DIR
UGS_LICENSE_SERVER=*port*@*host* ; export UGS_LICENSE_SERVER
Fill in the portnumber and your hostname!!! (see step 5)

**_Step 7: modify the Environment Variables_**
Set up the .ugii_env file in the basedir (ugii): Open it with root permissions and check if the most important environment variables are set (if you have NXNastran don't forget it ex UGII_NX_NASTRAN=/opt/UGS/nxnastran/nxn5p0m1/x86_64linux/nastran )
If you plan to use browser features via NX5 (like documentation, cast/training) change the browser variable (ex UGII_HTML_BROWSER=swiftweasel32). Most people want to probably fill in firefox there.

**_Step 8: create the Motif resource files_**
For some reason these files aren't created at the installation, which results in strange window behavior (ex no text,...).
Create a map /usr/lib/X11/app-defaults, and copy Ugmenu10_default and Ugnx5_default in this map and rename them Ugmenu10 and Ugnx5.

**_Step 9: reboot & start up NX5_**
Ok it looks now that everything is set, now reboot.
When you now want to start up nx do:
cd /opt/UGS/ugslicensing && ./lmgrd -c *ugs.lic* 28000@*hostname*
replace /opt/UGS by your install base, ugs.lic by your license file name and hostname by your...hostname ;-)
This command start the license file server and has to be executed every time your computer boots up and you want to NX!!!

now to start NX5:
cd /opt/UGS/ugii && ./ugii

Normaly it now works! If you are a student don't forget to select the ACD bundle (File >Utilities) or manufacturing won't work. Sadly, you have to reselect this bundle every time you boot NX5

I made a desktop entry and a startup script for the license server and NX, so it just starts when you click an icon If somebody is interested I will post it later

I know it's a long way to get there but once it works it's great!

Note: GTAC support site: [http://support.ugs.com/](http://support.ugs.com/)

**_Know issues:_**

* I have to reselect the ACD bundle very time I start up NX

* One of the main differences with the Windows version is the lack of the "slider". Sometimes the windows on the left get out of their position.
Solution: Preferences > User Interface > Layout > Reset Window Position

**_Tips and Tricks:_**

* To greatly increase graphic quality (smoother edges): 
Preferences > Visualization Performance > General Graphics > Deselect "Disable (Full Screen) Anti Aliasing"
Only for powerful graphical cards!

* For better performance with NXNastran solver & dualcore CPU's:
sudo gedit /opt/UGS/nxnastran/conf/nast5rc
At the bottom, add:
Parallel=2

---

### Post by Showan2 on 2008-01-06
hello

please try this methods and let me know how it worked!!

Please feel free to modify / complete my 'howto' and to ask questions!

If I can get some feedback and make it better we can maybe open a thread in the tips and tutorials section.

---

### Post by tanderson on 2008-01-18
Sweet! I am running kubuntu and have been dreaming about loosing my last window anchor UG. I think I will give this a try soon. I have been running UG for about 8 years now, so if anyone has questions I will try to answer. Unfortunately I have no UG machining experience, but I have plenty of modeling, surfacing, drafting and assembly experience. If somebody wants some play models I have plenty.

---

### Post by zvadinov on 2008-05-16
first, I thank you for the HowTo that you have wrote!! Second  I'm not sure, if this is the right place for my post?!
I've done all the ways you explain and I got NX to work.
I can open it, make changes at Visualisation a.s.o. but when I try to make a new Part or open one, I get a Freez and sometimes a Crash 

I use  Ubuntu 8.04 64bit, Intel Dual Core, Nvidia GeForce 8800 GTS (640MB), 4GB RAM
 
First I think the freeze comes from Compiz, so I turn it off, but I get freeze again!
I tried to make some changes in nvidia-setting and also Desktop setting but I still get an freeze!

I think this is a Nvidia problem using 3D, can you help me to solve the Problem, or probably tell me where/how I can find a solution  ?

I would be happy If you can help me. If you need some logfiles I will post it.
But tell me the Name of the logs, I'm sorry of this, but i'm new at linux!
It's like tanderson wrote, UG was my anchor to Windows so I couldn't change earlier!

Zvadi

P.S. Sorry for my bad English!

---

### Post by Showan2 on 2008-05-26
hello sorry for the late reply.

Since hardy heron, I also have lockups with the propietary nvidia drivers

solution: use the open-source nv drivers

go to Hardware Drivers and deselect it.

now it should start without a problem.

feel free to ask other questions

bye

---

### Post by zvadinov on 2008-07-20
what to say Showan2 :) you are the Master :)
NX5 works but I have some small Problems!

1) I cant use shortcuts if the Mouse courser is on the work view, only out of the WorkView the Shortcuts are working.
2) The Scroll button for zoom won't work but it works normally in ubuntu! 

thank you very much for you help!

bye

---

### Post by Showan2 on 2008-08-02
hi

don't forget to install the latest maintenance packs and releases, they solve a lot of bugs and they are frequently released.

you can find them at [http://support.ugs.com/](http://support.ugs.com/) , you need a login for this area of the site

At [http://uganswer.ugs.com/](http://uganswer.ugs.com/) you can find problems and bugs and their solutions

kind regards

---

### Post by zvadinov on 2008-08-10
Hi Showan2

thank you for the Answer!
I have update the system and the scrollbutton is now working!
The shortcuts wont work again ...and the nvidia-problem is also not solved by ug! But, ok
it is posible to work with! :-)

regards
zz

---

### Post by mag00 on 2008-11-15
It is not possible to run NX5 under wine?

[]'s

---

### Post by ytu_cyc on 2009-03-31
Hello...
When i run the script of "/usr/ugs060/bin/ugmenu" to start the NX6.0,after seconds,a Error was appeared:

[COLOR="Red"]NX License Error:Invalid(inconsistent)license key or signature. The license key/signature and data for the feature do not match!
[/COLOR]
When i use the "PS -A",I can see the lmgrd and ugslmd are all running well.

what's the matter?

Thanks in advance.

Please forgive me for my poor english.

---

### Post by firefox66 on 2009-09-05
I got this error measage when start ./ugii
./ugii[34]: UGS_LICENSE_SERVER: variable must be set to run UG

in windows i set it on environment variable and add UGS_LICENSE_SERVER = port@hostname

Starting NX ... /opt/ugs/ugii/ugraf: symbol lookup error: /opt/ugs/ugii/libklo.so: undefined symbol: _Z18FUSION_init_modulev

So please, what i went wrong ????

---

### Post by goliveira on 2012-02-24
HI!

I have install NX8 on Ubuntu 10.04, and i was perfect with nVidia Quadro FX-380 and driver 2.90.10.. this was fine until i install some Ubuntu updates, and the nVidia driver 2.95.20.

Now i have the ugraf, metacity and Xorg process "eating" my cpu, NX hang, and this message in my dmesg:
```
CE: hpet increasing min_delta_ns
```

So, what could it be? The nVidia's driver update, the Ubuntu's updates?

Some bad configuration, some i missed?


*** But thanks to your post i solve the Ugnx8 file mistery message - NX could not find it ****

---

### Post by overdrank on 2012-02-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

