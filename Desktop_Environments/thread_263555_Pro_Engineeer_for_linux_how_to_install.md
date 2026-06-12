---
title: "Pro Engineeer for linux: how to install?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by fedleo on 2006-09-23
I would like to try Pro/e wildfire 3 on Ubuntu Dapper but can't install it because an error occured...

```
 
effe@effe:/media/cdrom0$ sudo bash
root@effe:/media/cdrom0# sudo sh ./setup
./setup: /media/cdrom0/getpmt.csh: /bin/csh: bad interpreter: Permesso negato

Starting PTC.Setup, please wait ...
ERROR:  /media/cdrom0/dsrc//obj/ptcsetup - file is missing.
        Check the name of the CD mount directory.
root@effe:/media/cdrom0#

```

Is there someone that could gently explain me where I'm wrong?

Thanks to all.

---

### Post by doghouse-(ocau) on 2006-09-25
Yes, it seems that your problem is the same one I have encountered and not been able to solve. PTC say that Red Hat Feodra is the supported OS but I am sure that someone can figure it out. Being a complete and utter Linux newb such as myself does not help.

---

### Post by nikhilk on 2006-09-25
```
 
./setup: /media/cdrom0/getpmt.csh: /bin/csh: bad interpreter: Permesso negato

```
"getpmt.csh" is a "C" shell script file and it seems you do not have "C" shell.
```

ERROR:  /media/cdrom0/dsrc//obj/ptcsetup - file is missing.
        Check the name of the CD mount directory.
root@effe:/media/cdrom0#

```
I do not know why the "dsrc//obj" (note the double slashes) is being used. See if you can access the file as
```
/media/cdrom0/dsrc/obj/ptcsetup
```

---

### Post by doghouse-(ocau) on 2006-09-25
ooooh, so I need a C" Shell, hmmm, the plot thickens.](*,)

---

### Post by Hg80 on 2006-09-25
i have got wildfire 2 to work, but cant remember how

---

### Post by tideline on 2006-09-25
Do you have build-essentials installed?  If not try to install it via Synaptic Package Manager.  Also, install gcc and make.  See if that helps.


Mike

---

### Post by skymt on 2006-09-25
Install tcsh (sudo aptitude install tcsh). That should provide /bin/csh.

---

### Post by fedleo on 2006-09-26
First of all, thanks to all for the help.
I double checked for build-essemtial, make and gcc and all are installed.
I installed tcsh, and tried again. No way, same error. 
There is an error in the path showed and probably for this reason setup can't go on. The correct path for ptcsetup must be /media/cdrom0/dsrc/i486_linux/obj, not /media/cdrom0/dsrc//obj.
SO I think there's an error on getpmt.csh but cant see where:
```
#!/bin/csh -f

###########################################################################
# 02/05/93 James Created - get machine type using file/hinv/uname.
# 02/12/93 James check for sun/solaris.
# 03/01/93 James Fix for nec_risc r4000
# 04/05/93 Pete  added alpha_unix
# 04/17/93 James Removed quotes around hinv_out.
# 06/21/93 jmichaud Allow for IRIX 5.0 sgi and sgi_r4k (ELF 32-bit).
# 08/27/93 James sun4_solaris.
# 11/17/93 James R4000->R4..0
# 11/19/93 James IBM PowerPC fix.
# 12/08/93 $$1 James hitachi.
# 04/26/94 $$2 James handle jap sgi.
# 05/16/95 $$3 Pete  set LANG C at top, all platforms work well with this
# 06/22/95 $$4 true R4..0->R[48]..0 to allow for SGI R8000 systems.
# 11/27/95 $$5 Pete  added sgi_elf2 for 5.3 and beyond
# 02/01/96 $$6 Pete  added R5000 support for sgi (for Tom True)
# 18-Jun-96 Pete   $$7  revised by Joe Michaud and tweaked by me
# 20-Jun-96 Pete   $$8  fixed bug in previous subm comment block
# 05-Dec-96 Pete   $$9  added hp8k
# 30-Dec-96 Jane   $$10 distinguish hp700 and hp8k properly
# 08-Sep-97 JJE    $$11 Just hp8k now for 19
# 27-Mar-98 jmichaud $$12 added sgi_mips4
# 08-Mar-00 MAZ           Get rid of env os_name
# 04-Aug-00 TWH      $$13 Add hpux11_pa32
# 01-Dec-00 TWH      $$14 Add sun4_solaris_64
# 16-May-01 TWH      $$15 Add hpux_pa64
# 10-Aug-01 MAZ      $$16 Introduce FORCE_PMT
# 21-Nov-01 TWH      $$17 Add sgi_elf4
# 01-AUG-02 MTP      $$18 Add i486_linux
# 25-OCT-05 MTP      $$19 Add sun_solaris_x64
###########################################################################

setenv LANG C

set id = "UNKNOWN"

switch (`uname -s`)
    case "IRIX":
    case "IRIX64":
        #
        # There are three different platform types for SGI:
        #   sgi_elf4  - built -64  -mips4
        #   sgi_mips4 - built -n32 -mips4 (older)
        #   sgi_elf2  - built -32  -mips2 (oldest)
        #
        # IRIX OS can handle only 32-bit programs.
        # IRIX64 OS can handle 32-bit and 64-bit programs.
        #
        # Machines with R2000 and R3000 CPUs are obsolete.
        # Machines with R4XXX CPUs can't handle MIPS4 ISA, and so can
        # only deal with sgi_elf2.  Machines with all other CPUs can
        # handle MIPS4 ISA, but only those running IRIX64 OS can handle
        # sgi_elf4.  Others run sgi_mips4.
        #
        set cpu = (`hinv -t cpu`)
        if ("`expr $cpu[3] : 'R[23]*'`" > "1") then
            # Not supported.
        else if ("`expr $cpu[3] : 'R4*'`" > "1") then
            set id = "sgi_elf2"
        else
	    if ("`uname -s`" == "IRIX64") then
                set id = "sgi_elf4"
            else
                set id = "sgi_mips4"
            endif
        endif
    breaksw

    case "OSF1":
        set id = "alpha_unix"
    breaksw

    case "Linux":
        set id = "i486_linux"
    breaksw

    case "HP-UX":
        set rev = `uname -r`
        if ("`expr $rev : '[A-Z].11.*'`" > "1") then
	  if ("`file /stand/vmunix | grep 'ELF-64'`" == "") then
            set id = "hpux11_pa32"
          else
            set id = "hpux_pa64"
          endif
        else
            set id = "hp8k"
        endif
    breaksw

    case "AIX":
        set id = "ibm_rs6000"
    breaksw

    case "SunOS":
        set rev = `isalist |grep sparcv9 | wc -c`
        if ("$rev" > "0") then
	   set id = "sun4_solaris_64"
        else
           set rev = `isalist |grep amd64 | wc -c`
           if ("$rev" > "0") then
              set id = "sun_solaris_x64"
           else
              set id = "sun4_solaris"
           endif
        endif
    breaksw

    case "HI-UX":
        set id = "hitachi"
    breaksw

    case "UNIX_SV":
        set id = "nec_mips"
    breaksw
endsw

if( $?FORCE_PMT ) then
    echo $FORCE_PMT 
else
    echo $id 
endif

```

Ps: On my first post there are some italian words,"Accesso negato". Means Access denied

---

### Post by nikhilk on 2006-09-26
Ok first please confirm that /bin/csh is actually present. If it is you should not get the "/bin/csh: bad interpreter" error. Also could you post the contetnts of the "setup" file?

What happens if you run the setup as a non-root user ("effe" I guess) after you are in the proper directory ("/media/cdrom0" right?)
```
sudo ./setup
```

---

### Post by the_mechanical on 2006-10-21
Hi
I have (or had) the same problem. After fixing the path in the scripts (getmpt.sh and so on) was it able to install the software :) . But i can't run it now because of the same errors. :confused: 

I would also be happy if the solution would be found.

---

### Post by pkorpela on 2006-10-22
I was able to start the isntalla from web tool after installing packages csh and libmotif3. But in the setup program the text is not visible. I guess it is due to a missing font in my system. What could be a solution to that?

-Perttu-

---

### Post by the_mechanical on 2006-10-22
Do you have also installed
libstdc++2.10-glibc2.2 ?
If yes - i don't know, if not - try it.

---

### Post by pkorpela on 2006-10-22
I have that  packet too. I am running dapper on Dell M50 laptop and Nvidia's own drivers. Had some problems to get X running but it seems to OK now. What is funny is that there is no errors in console what so ever. 

I attached a picture of license agreement page from setup.

> **the_mechanical said:**
> Do you have also installed
libstdc++2.10-glibc2.2 ?
If yes - i don't know, if not - try it.

---

### Post by the_mechanical on 2006-10-28
As a (possible) solution for this problem

```
ERROR:  /media/cdrom0/dsrc//obj/ptcsetup - file is missing.
        Check the name of the CD mount directory.
```

copy the CD to the harddisk and try to set the other rights.
For example: chmod -R 777 "Directory"
And then ```
sh setup
``` from the harddisk.

---

### Post by sw_ on 2007-01-27
sorry to bring that up, but at the beginning i had all the problems listed in this thread, followed the single steps and the setup went on further, and it actually entered the setup.

now there's an error that's not listed. the last one. it's probably just another library thing. can someone tell me what lib i'm missing?

```
r@lil:~/Desktop/Pro-E$ ./setup
./setup: 121: /home/r/Desktop/Pro-E/getpmt.csh: not found

Starting PTC.Setup, please wait ...
ERROR:  /home/r/Desktop/Pro-E/dsrc//obj/ptcsetup - file is missing.
        Check the name of the CD mount directory.
r@lil:~/Desktop/Pro-E$ ./setup

Starting PTC.Setup, please wait .../home/r/Desktop/Pro-E/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

r@lil:~/Desktop/Pro-E$ ./setup

Starting PTC.Setup, please wait ...
r@lil:~/Desktop/Pro-E$ /home/r/Desktop/Pro-E/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

```

so what is this linbXm

---

### Post by alfexy on 2007-02-23
> I attached a picture of license agreement page from setup.

You just have to change the screen resolution to 1280x1024 (maybe others work too) if you have a higher one.
then you will see the text in the setup menu.
After starting "setup" you can switch back to your usual resolution (for me 1600x...)

---

### Post by someuser on 2007-03-16
> **pkorpela said:**
> I have that  packet too. I am running dapper on Dell M50 laptop and Nvidia's own drivers. Had some problems to get X running but it seems to OK now. What is funny is that there is no errors in console what so ever. 

I attached a picture of license agreement page from setup.

I have this exact problem.
Did any-one ever figure it out?
Some font or so?

---

### Post by trancepose on 2007-03-25
hello everyone. finally i have found something that might be useful(thx to brothers in china) i have found something that may help for installation

just follow the codes and don't ask me what is told in here. I don't know neither. if anyone is present in this forum who has a couple of words to tell about chinese, i'd appreciatthe efforts for translation. 


fortunately, codes are clear enough, thx to latin alphabet


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


&#22312;&#21407;&#29256;ubuntu 6.10&#23433;&#35013;Wildfire.v3.0.M020.for.Linux

&#19968; &#20934;&#22791;&#24037;&#20316;

1 &#23433;&#35013;csh &#25110; tcsh
sudo apt-get install csh
&#25110;sudo apt-get install tcsh

2 &#23433;&#35013; libmotif3&#12289; libstdc++2.10-glibc2.2
sudo apt-get install libmotif3 libstdc++2.10-glibc2.2

3&#29992;&#26032;&#31435;&#24471;&#23433;&#35013;gkt1.2(&#22914;&#26524;&#31995;&#32479;&#24050;&#32463;&#23433;&#35013;&#30340;&#35805;&#65292;&#24403;&#28982;&#21487;&#20197;&#19981;&#36827;&#34892;&#27492;&#25805;&#20316;)

4 &#23433;&#35013; portmap
sudo apt-get install portmap (&#21542;&#21017;&#65292;&#23433;&#35013;&#21518;&#36816;&#34892;&#26102;&#20250;&#65306;&#26080;&#27861;&#27880;&#20876;&#26381;&#21153;&#65306;RPC&#65306;&#26080;&#27861;&#25509;&#25910;&#65307;errno = &#25298;&#32477;&#36830;&#25509;)

5 &#23433;&#35013;wine(&#29992;&#20110;&#29983;&#25104;lincense&#65289;
sudo apt-get install wine

6 &#22788;&#29702; libXm.so.3
sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.3.0.2
sudo cp /usr/lib/libXm.so.3 /usr/X11R6/lib/libXm.so.3

7 &#25214;&#20986;&#32593;&#21345;&#30828;&#20214;&#22320;&#22336;
&#21551;&#21160;&#23433;&#35013;&#31243;&#24207;,&#22312;&#24038;&#19979;&#26041;&#26377;&#12290;
&#25110;&#32773;&#29992;ifconfig &#21629;&#20196;&#26469;&#26597;&#35810;&#32593;&#21345;&#30340;Mac&#22320;&#22336;&#12290;
&#36825;&#37324;&#20808;&#20551;&#35774;&#20026; "XX-XX-XX-XX-XX-XX"

8 &#25346;&#36733; cdrom
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux1.iso /mnt/cdrom1
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux2.iso /mnt/cdrom2

9 &#23558;/mnt/cdrom1/&#19979;&#30340;crack&#25991;&#20214;&#22841;&#25335;&#36125;&#33267;&#20320;&#30340;&#29992;&#25143;&#30446;&#24405;&#65292;&#22914;/home/yourname/crack/
&#22312;&#35813;&#30446;&#24405;&#19979;&#29992;wine &#36816;&#34892;&#31639;&#21495;&#22120;&#65292;&#36755;&#20837;&#32593;&#21345;&#30340;Mac&#22320;&#22336;&#65292;&#29983;&#25104;lincense&#25991;&#20214;&#65288;&#24403;&#28982;&#65292;&#20063;&#21487;&#20197;&#22312;windowns&#19979;&#36827;&#34892;&#65289;&#12290;

&#20108; &#23433;&#35013; Pro/Engineer
&#36807;&#31243;&#22914;&#19979;&#65306;
cd /mnt/cdrom1/
LANG=EN(&#27492;&#27493;&#19981;&#21487;&#32570;&#23569;&#65289;
sudo ./setup
1 &#36873;&#25321;&#23433;&#35013;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
&#23433;&#35013;&#36807;&#31243;&#20013;&#35810;&#38382;lincese&#26102;&#65292;&#36873;&#25321;&#20320;&#29983;&#25104;&#30340;lincese.dat
&#24403;&#35810;&#38382;&#31532;&#20108;&#24352;&#20809;&#30424;&#30340;&#20301;&#32622;&#26102;&#65292;&#36873;&#25321;/mnt/cdrom2&#21363;&#21487;&#12290;
&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#23433;&#35013;&#23436;&#27605;&#21518;&#65292;&#23558;&#25552;&#31034;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#26410;&#33021;&#21551;&#21160;,&#20851;&#38381;&#25552;&#31034;&#31383;&#21475;,&#36864;&#20986;&#23433;&#35013;&#31243;&#24207;&#12290;

2 &#22788;&#29702;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
sudo cp /usr/local/ptc/flexnet/starup/s99ptcflexlm /etc/init.d/
sudo ln -s /etc/rc2.d/s99ptcflexlm /etc/init.d/s99ptcflexlm
sudo ln -s /etc/rc5.d/s99ptcflexlm /etc/init.d/s99ptcflexlm
3 &#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
sodu /usr/local/ptc/flexnet/bin/ptcstartserver
4 &#23433;&#35013; Pro/Engineer &#20027;&#31243;&#24207;
cd /mnt/cdrom1/
LANG=EN(&#27492;&#27493;&#19981;&#21487;&#32570;&#23569;&#65289;
sudo ./setup
&#36873;&#25321;&#23433;&#35013; Pro/Engineer&#19968;&#36335;next,&#19981;&#20570;&#20219;&#20241;&#36873;&#25321;&#12290;

&#25552;&#31034;&#65306;&#23433;&#35013;&#23436;&#20043;&#21518;&#21487;&#29992; sudo /usr/local/ptc/proeWildfire3.0/bin/ptcsetup &#37325;&#26032;&#37197;&#21046;&#12290;
&#25552;&#31034;&#65306;&#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#30340;&#21629;&#20196;&#65306;/usr/local/ptc/flexnet/bin/ptcstartserve
&#25552;&#31034;&#65306;&#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#30340;&#21629;&#20196;&#65306;/usr/local/ptc/flexnet/bin/ptcshutdown

&#36215;&#21160;proe/Engineer&#21487;&#20197;&#22914;&#27492;&#65306;

1 &#25171;&#24320;&#19968;&#20010;&#32456;&#31471;
2 LANG=EN
3 /usr/local/ptc/proeWildfire3.0/bin/proe1

&#24314;&#35758;&#20320;&#37319;&#29992;&#22914;&#19979;&#30340;&#21150;&#27861;&#36215;&#21160;proe&#65306;
&#22312;/home/yourname/.gnome2/.nautilus-scripts/ &#30446;&#24405;&#19979;&#24314;&#19968;&#20010;shell&#25991;&#20214;&#65288;&#20551;&#35774;&#25991;&#20214;&#21517;&#20026;Wildfire3.0),&#25991;&#20214;&#30340;&#20869;&#23481;&#22914;&#19979;&#65306;
#!/bin/sh
cd /home/username/proe
LANG=en_US
/usr/local/ptc/proeWildfire3.0/bin/proe1

&#32473;&#35813;&#25991;&#20214;&#21152;&#19978;&#21487;&#25191;&#34892;&#23646;&#24615;,&#27599;&#27425;&#36215;&#21160;&#26102;&#65292;&#21482;&#39035;&#22312;&#26700;&#38754;&#21491;&#20987; &#65292;&#36873;scripts->Wildfire3.0 &#21363;&#21487;&#12290;


-----------------------------------------------------------------------------------------------------------------


** *can anyone send me if you have a link or torrent for wf3 with mechanica??? - [email]trancepose@hotmail.co.uk[/email]*

---

### Post by cap_gemo on 2007-04-01
Ok, just to summarize the installation procedure: first do

  sudo apt-get install csh libmotif3 libstdc++2.10-glibc2.2 build-essential

  and then install pro/e.


  I have got another problem with it. There was no problem with the installation (feisty beta), but I can't run pro/e now. If I launch the script proe, I get a message:

  setenv: Too many arguments.

  The command setenv is a couple of times present in that script. Each time it has a syntax like:

  setenv VARIABLE VALUE

  Of course, I don't think, that the ptc-guys made some mistakes, writing this scripts, but the setenv command produces that error message, and my first thought is: Is this the correct syntax for that command? Should I change this script somehow? Or is there something, I've missed?

  Thanks for your help

---

### Post by The_Mag on 2007-04-02
I installed the license-server on Ubuntu 6.10.

1.) installed KDE
2.) created new user "ptcserver"
3.) copied both CDs on HDD
4.) started install-process for the server.          ==> lib missing
5.) installed one missing lib (can't remember which one)
6.) started  install-process for the server again  ==> lib missing
7.) installed one missing lib (can't remember which one)
8.) started install-process for the server again
     (Can't read the EULA - doesn't matter!)
9.) copied the PTC-start-script as shown in last page of install-process (for start at boot)

The license-server is running with 3 windows-clients

---

### Post by bustler on 2007-04-05
hi
since my pc is off m$ i'm looking for wildfire2linux install-cd's (multi-language for the best).
anyone  out there who have it 4me? 
i just want to test it under edgy :-k 

peter

---

### Post by trancepose on 2007-04-11
I've checked it out cap_gemo. i think the startup commands are not allright, try to run from the source or generate yours. i do the first because i don't know how to generate one. but i still have several problems about licensing. at windows, i've used to install flexnet servers with computer name and add a single license server with computer description stuff. if i knew what computer description corresponds to in linux, i'll solve the problem. anyone knows?

---

### Post by cmittle on 2007-11-16
I am a Mechanical Engineering student at South Dakota State University and will be graduating in December.  For a graduation present I was going to have my mom purchase me ProE.  I work with this everyday at Daktronics and would like to use it in planning my own projects from mopeds to bed frames and book shelves.  I contacted PTC help earlier today and was told that they do not support linux platforms with wildfire 3 and they do not sell student versions of wildfire 2 any more.  Does anybody know where I could find Wildfire 2 for my Ubuntu computer?

Thank you,
Cory

---

### Post by cmittle on 2007-11-16
Never mind my last question I was able to get a copy of WF3.  I followed the install instructions found [here]("http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695").  When I run the proe script that was installed I see an error.  It says "Your chosen language "en_US.UTF08" is based on Unicode, which this version of Pro/ENGINEER does not use. Pro/ENGINEER will shut down; please restart with a language that does not contain the string ".utf" or ".UTF"" 

Any ideas what I can do to fix this.  Where this particular file it's talking about is located and how I might be able to make this work?

Thank you,
Cory

---

### Post by cmittle on 2007-11-19
I managed to get this installed and working on my ubuntu 7.10 laptop.  Look [here]("http://http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695") for the initial steps, but scroll down if you have any questions there is a lot of information down there.  The thing that solved my problem with not recognizing the utf-8 was posted by jcvasquezt  on 10/30/2007 about setting the language to english.  Hope this helps somebody later to install this awesome 3d cad package

---

### Post by kurotenshi on 2008-01-28
I used that blog also but I can't get pass that UTF problem. In my case it is pt_PT.UTF-8
I've tried to use```
sudo export LANG=pt_PT
``` but I get a command not found error. Any ideas?

---

### Post by kurotenshi on 2008-01-28
On closer and more cautious look at the blog found this solves the LANG UTF problem 
> 	jcvasquezt writes:	
10/30/2007 #

hi so i got a couple of things.
1. to solve the language issue, Locutus, the lproe.sh script worked fine, but I went a bit further. So this is what i did. I installed the links (shorcuts) for proe, there is one called "proe", so open it with a text editor (you have to be root for this) and after the first line:

#!/bin/csh -f

paste the following lines:

#lines added to change in the environment the LANG from en_US.utf8
#.utf are not supported by proe
set lang="English"
setenv LANG $lang

this way you just have to click on the proe link.

2. I also have the problem with the license and my host id, proe will pick what ever it wants every time I change my internet connection, i don't know if there is a better way of solving this, but i just have different license files for each scenario. Is there a way to fix the host id?

3. Finally, Locotus, i've been unable to fix the graphics issue, the software works a lot faster than in windows, but still i can not get it to show me the part while moving or zooming, i can only see the initial and final state... it would be nice to fix this... anyways proe is amazing (especially under linux).

thanks 

---

### Post by kid-lj on 2008-07-10
> **trancepose said:**
> hello everyone. finally i have found something that might be useful(thx to brothers in china) i have found something that may help for installation

just follow the codes and don't ask me what is told in here. I don't know neither. if anyone is present in this forum who has a couple of words to tell about chinese, i'd appreciatthe efforts for translation. 


fortunately, codes are clear enough, thx to latin alphabet


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


&#22312;&#21407;&#29256;ubuntu 6.10&#23433;&#35013;Wildfire.v3.0.M020.for.Linux

&#19968; &#20934;&#22791;&#24037;&#20316;

1 &#23433;&#35013;csh &#25110; tcsh
sudo apt-get install csh
&#25110;sudo apt-get install tcsh

2 &#23433;&#35013; libmotif3&#12289; libstdc++2.10-glibc2.2
sudo apt-get install libmotif3 libstdc++2.10-glibc2.2

3&#29992;&#26032;&#31435;&#24471;&#23433;&#35013;gkt1.2(&#22914;&#26524;&#31995;&#32479;&#24050;&#32463;&#23433;&#35013;&#30340;&#35805;&#65292;&#24403;&#28982;&#21487;&#20197;&#19981;&#36827;&#34892;&#27492;&#25805;&#20316;)

4 &#23433;&#35013; portmap
sudo apt-get install portmap (&#21542;&#21017;&#65292;&#23433;&#35013;&#21518;&#36816;&#34892;&#26102;&#20250;&#65306;&#26080;&#27861;&#27880;&#20876;&#26381;&#21153;&#65306;RPC&#65306;&#26080;&#27861;&#25509;&#25910;&#65307;errno = &#25298;&#32477;&#36830;&#25509;)

5 &#23433;&#35013;wine(&#29992;&#20110;&#29983;&#25104;lincense&#65289;
sudo apt-get install wine

6 &#22788;&#29702; libXm.so.3
sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.3.0.2
sudo cp /usr/lib/libXm.so.3 /usr/X11R6/lib/libXm.so.3

7 &#25214;&#20986;&#32593;&#21345;&#30828;&#20214;&#22320;&#22336;
&#21551;&#21160;&#23433;&#35013;&#31243;&#24207;,&#22312;&#24038;&#19979;&#26041;&#26377;&#12290;
&#25110;&#32773;&#29992;ifconfig &#21629;&#20196;&#26469;&#26597;&#35810;&#32593;&#21345;&#30340;Mac&#22320;&#22336;&#12290;
&#36825;&#37324;&#20808;&#20551;&#35774;&#20026; "XX-XX-XX-XX-XX-XX"

8 &#25346;&#36733; cdrom
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux1.iso /mnt/cdrom1
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux2.iso /mnt/cdrom2

9 &#23558;/mnt/cdrom1/&#19979;&#30340;crack&#25991;&#20214;&#22841;&#25335;&#36125;&#33267;&#20320;&#30340;&#29992;&#25143;&#30446;&#24405;&#65292;&#22914;/home/yourname/crack/
&#22312;&#35813;&#30446;&#24405;&#19979;&#29992;wine &#36816;&#34892;&#31639;&#21495;&#22120;&#65292;&#36755;&#20837;&#32593;&#21345;&#30340;Mac&#22320;&#22336;&#65292;&#29983;&#25104;lincense&#25991;&#20214;&#65288;&#24403;&#28982;&#65292;&#20063;&#21487;&#20197;&#22312;windowns&#19979;&#36827;&#34892;&#65289;&#12290;

&#20108; &#23433;&#35013; Pro/Engineer
&#36807;&#31243;&#22914;&#19979;&#65306;
cd /mnt/cdrom1/
LANG=EN(&#27492;&#27493;&#19981;&#21487;&#32570;&#23569;&#65289;
sudo ./setup
1 &#36873;&#25321;&#23433;&#35013;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
&#23433;&#35013;&#36807;&#31243;&#20013;&#35810;&#38382;lincese&#26102;&#65292;&#36873;&#25321;&#20320;&#29983;&#25104;&#30340;lincese.dat
&#24403;&#35810;&#38382;&#31532;&#20108;&#24352;&#20809;&#30424;&#30340;&#20301;&#32622;&#26102;&#65292;&#36873;&#25321;/mnt/cdrom2&#21363;&#21487;&#12290;
&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#23433;&#35013;&#23436;&#27605;&#21518;&#65292;&#23558;&#25552;&#31034;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#26410;&#33021;&#21551;&#21160;,&#20851;&#38381;&#25552;&#31034;&#31383;&#21475;,&#36864;&#20986;&#23433;&#35013;&#31243;&#24207;&#12290;

2 &#22788;&#29702;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
sudo cp /usr/local/ptc/flexnet/starup/s99ptcflexlm /etc/init.d/
sudo ln -s /etc/rc2.d/s99ptcflexlm /etc/init.d/s99ptcflexlm
sudo ln -s /etc/rc5.d/s99ptcflexlm /etc/init.d/s99ptcflexlm
3 &#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;
sodu /usr/local/ptc/flexnet/bin/ptcstartserver
4 &#23433;&#35013; Pro/Engineer &#20027;&#31243;&#24207;
cd /mnt/cdrom1/
LANG=EN(&#27492;&#27493;&#19981;&#21487;&#32570;&#23569;&#65289;
sudo ./setup
&#36873;&#25321;&#23433;&#35013; Pro/Engineer&#19968;&#36335;next,&#19981;&#20570;&#20219;&#20241;&#36873;&#25321;&#12290;

&#25552;&#31034;&#65306;&#23433;&#35013;&#23436;&#20043;&#21518;&#21487;&#29992; sudo /usr/local/ptc/proeWildfire3.0/bin/ptcsetup &#37325;&#26032;&#37197;&#21046;&#12290;
&#25552;&#31034;&#65306;&#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#30340;&#21629;&#20196;&#65306;/usr/local/ptc/flexnet/bin/ptcstartserve
&#25552;&#31034;&#65306;&#21551;&#21160;&#35768;&#21487;&#35777;&#31649;&#29702;&#22120;&#30340;&#21629;&#20196;&#65306;/usr/local/ptc/flexnet/bin/ptcshutdown

&#36215;&#21160;proe/Engineer&#21487;&#20197;&#22914;&#27492;&#65306;

1 &#25171;&#24320;&#19968;&#20010;&#32456;&#31471;
2 LANG=EN
3 /usr/local/ptc/proeWildfire3.0/bin/proe1

&#24314;&#35758;&#20320;&#37319;&#29992;&#22914;&#19979;&#30340;&#21150;&#27861;&#36215;&#21160;proe&#65306;
&#22312;/home/yourname/.gnome2/.nautilus-scripts/ &#30446;&#24405;&#19979;&#24314;&#19968;&#20010;shell&#25991;&#20214;&#65288;&#20551;&#35774;&#25991;&#20214;&#21517;&#20026;Wildfire3.0),&#25991;&#20214;&#30340;&#20869;&#23481;&#22914;&#19979;&#65306;
#!/bin/sh
cd /home/username/proe
LANG=en_US
/usr/local/ptc/proeWildfire3.0/bin/proe1

&#32473;&#35813;&#25991;&#20214;&#21152;&#19978;&#21487;&#25191;&#34892;&#23646;&#24615;,&#27599;&#27425;&#36215;&#21160;&#26102;&#65292;&#21482;&#39035;&#22312;&#26700;&#38754;&#21491;&#20987; &#65292;&#36873;scripts->Wildfire3.0 &#21363;&#21487;&#12290;


-----------------------------------------------------------------------------------------------------------------


** *can anyone send me if you have a link or torrent for wf3 with mechanica??? - [email]trancepose@hotmail.co.uk[/email]*


Well, I am a student from China who loves Ubuntu and Open Source.I am 
very glad to translate the installation process written in Chines to 
English,but without the promise that it will be  exactly right and the
method works well.However, I will do my best :)
OK,let's begin:
-----------------------------------------------------------------------
Install Wildfire.v3.0.M020.for.Linux on original ubuntu 6.10

1, Get ready

1) Install csh or tcsh
CMD: sudo apt-get install csh
OR sudo apt-get install tcsh

2) Install libmotif3&#12289; libstdc++2.10-glibc2.2
CMD:sudo apt-get install libmotif3&#12289; libstdc++2.10-glibc2.2

3) Install gkt1.2 via synaptic(of course,if it has exsited,no need)

4) Install portmap
CMD: sudo apt-get install portmap (If not,when running after installation there will be errors: Can't regester service; RPC: Can't
reciev; errno&#65309;connection denied) (not exact translation).

5)Install wine( for generating license)
CMD: sudo apt-get install wine

6)Deal with libXm.so.3
CMD: sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.3.0.2
     sudo cp /usr/lib/libXm.so.3 /usr/X11R6/lib/libXm.so.3

7) Find the "address" of your network card
#one way I don't understand
OR 
Get the MAC address of your network via CMD ifconfig
Here we consume it be "xx-xx-xx-xx-xx-xx"

8) Mount the CD-ROM
CMD:
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux1.iso /mnt/cdrom1
sudo mount -o loop /mnt/win_d/Wildfire.v3.0.M020.Linux2.iso /mnt/cdrom2

9) Copy the file "crack" under /mnt/cdrom1/ to your HOME directory,such as
/home/yourname/crack/,run "code-generating-machine"(anyway) via wine under
this directory and input your MAC address,it will generate a license file
(Of course,you can also do this at Windows).

2 Install Pro/Engineer
Process:

cd /mnt/cdrom1/
LANG=EN(neccessary!)
sudo ./setup

1) Choose to install the license manager
When the installation asks a lecense,choose the license.dat you have got.
when asking where the second CD is,just choose /mnt/cdrom2.
After the installation of the license manager,it will prompt that the license
manager can't launch and close the prompt window, quit the install-setup.

2) Handle the license manager
CMD: 
sudo cp /usr/local/ptc/flexnet/startup/s99ptcflexlm /etc/init.d/
sudo ln -s /etc/rc2.d/s99ptcflexlm /etc/init.d/s99ptcflexlm
sudo ln -s /etc/rc5.d/s99ptcflexlm /etc/init.d/s99ptcflexlm

3) Run the license manager 
CMD: sudo /usr/local/ptc/flexnet/bin/ptcstartserver

4) Install the Pro/Engineer main program
CMD:
cd /mnt/cdrom1
LANG=EN (neccessary!)
sudo ./setup
Then choose to install Pro/Engineer.Then directly click "NEXT" without doult
and choosing.

Tips: You can re-configure after installation by CMD: 
sudo /usr/local/ptc/proeWildfire3.o/bin/ptcsetup 
Tips: The CMD to run license manager:
/usr/local/ptc/flexnet/bin/ptcstartserver
Tips: The CMD to run license manager:
/usr/local/ptc/flexnet/bin/ptcshutdown

You can run Pro/Engineer like this:

1) open a console
2) LANG=EN
3) /usr/local/ptc/proewildfire3.0/bin/proe1

We suggest you run Pro/E following this:
Write a shell script under the directory /home/yourname/.gnome2/.nautilus-scripts/ (We consume it's name as "Wildfire3.0"),and it contains:
#!/bin/sh
cd /home/username/proe
LANG=en_US
/usr/local/ptc/proewildfire3.0/bin/proe1

Then make this script excutable.Every time you want to launch it,you just need to click the right button on the desktop, choose "script"->Wildfire3.0.
----------------------------------------------------------------------------

That'a all.NOT EXACTLY.

---

