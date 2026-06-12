---
title: "Install Bruker Topspin software"
date: 2009-01-09
forum: Education &amp; Science
---

### Post by rabbiedoo on 2009-01-09
Would anyone be able to tell me exactly how to install the Bruker Topsin software in Ubuntu. I have the V1.3 disk and a license.  Ubuntu is running on VMWare workstation in XP, but otherwise is normal and I need to use Ubuntu to link the output data to another package. The install disks for Redhat Enterprise v3 failed to install on VMWare so that route is also a no go at present. Help with either problem would be much appreciated.

---

### Post by stefanjhill on 2009-05-06
I have found that I was able to install TopSpin version 2.x with only a little playing around.  The folders for the FlexLM need to be manually made and the license file needs moved.  BUT, TS 1.3 I have been trying to install on Ubuntu (won't even start the install script), Fedora 10 and openSUSE 11.1.  The last two install until you get to the part where you need to type in the NMRSU password, then they crash out.  Again TopSpin 2.x will install fine.  We have DR-series instruments so we need to run TS 1.3, as such I have requested from the software department of Bruker an install script similar to the one that works in later version of TS.  I'll will post here if (hopefully when) I get a reply.

Regards,
   Stefan.

---

### Post by Danchik on 2009-07-21
Could you please specify what exactly has to be made with the flexlm folders and where you licence file is. 
 I am also trying to install 2.xx under Kubuntu hardy. 
 The installation seems to be fine, to i've got problems with the flexlm licencing stuff

---

### Post by inaho on 2010-09-03
Dear all,
I also have the same problem: install topspin on ubuntu.

I manage to make it work on ubuntu hardy, but after I upgraded to lucid lynx I am always getting an error:

> /opt/topspin/topspin: 366: source: not found
CPR : Path to prog : "/opt/topspin/prog"
CPR : Path to exp  : "/opt/topspin/exp"
CPR : Path to conf : "/opt/topspin/conf"
CPR : waiting for FLEXlm license
CPR : FLEXlm license is valid until 2011-04-06
CPR : 2010-09-03 08:54:56.940 +0200 environment variable JAVA not set
Program is exiting ...

Hit ENTER to continue ...

I am trying to understand from where this java problem is coming, it was not there with the older versions of ubuntu...
so far, here's what I did:

-installed the development tools for lynx
-to over come the "su" problem: just type sudo -i
then go to the Tospin folder and launch ./install
(or you can use nautilus with sudo privileges)
-set path on java (not sure this was useful to solve the problem :S) 
to do it I followed this page:
[http://www.adobe.com/devnet/livecycle/articles/blazeds_ubuntu_linux.html](http://www.adobe.com/devnet/livecycle/articles/blazeds_ubuntu_linux.html)

but so far I was unsucessfull...

I guess this java path has to be specified somewhere in a CPR configuration file...?

---

### Post by inaho on 2010-09-06
So, here's my "how to"... 

it works for ubuntu 8.04 and 10.04 

installation:

you need to be root; sudo will not work, so type

> sudo -i

go to the correct folder:

> cd /media/cdrom0 

or 

> cd /media/TOPSPIN_ts21 

now launch the install:

> ./install 

the installation start: follow all the guided procedure until the end. At the very end you will get an error message about not finding /sbin/chkconfig/ directory. Ignore it and reboot.

add the key to the license file:

> sudo gedit /usr/local/flexlm/Bruker/licenses/license.dat

you have to modify the license file with the correct lines provided by Bruker. Your license file should start with a SERVER line, next is you computer id (what it appear in you terminal after the @ symbol), the mac address of you machine and the port (I always get 1700). The second line is the DAEMON line. You should add the FEATURES lines starting from the 3rd line and before the line starting with #. Do not add anything else, no spaces, no / or other characters. Save and close.

You have now to restart the license server, so put on again the dvd and do the same as before:

> sudo -i
cd /media/cdrom0/
./install

select CUSTOM installation and at the next page deselect everything except the flexlm case; proceed until the end and ignore again the /sbin/chkconfig/ missing directory error.

Install BUM:

> sudo apt-get install bum 

Now from system->administration->BootUp Manager select bruker_lmgr and say yes to make start the daemon immediately.

Now if you click on applications->bruker->topspin it should load and tell you somewhere "this licence is valid until...". If you get some errors here, then you messed up something on the license.dat file.

Next it will give an error "JAVA environment variable not set".

Open again a terminal and type in 

> sudo gedit /opt/topspin/topspin

go to line 666 and change it from 

> source "$XWINNMRHOME"/javaenv.sh
to 
> . "$XWINNMRHOME"/javaenv.sh

please, note that there is a space between the . and the "

save it and close it.
Finally, you can launch topspin typing in a terminal 
> topspin
or clicking into applications->bruker->topspin

(thanks to one of my colleagues for the java problem)

---

### Post by acrocephalus on 2011-04-14
Hello!
I am trying the procedure described by Inaho but I get this error when I execute the install file
```
./install: 29: Syntax error: "(" unexpected
```
Could anyone help? Which info do you need?
Cheers!

Dani

---

### Post by Rangua on 2011-10-04
Hi.
first of all, 
Dani: the install script is written with an invalid syntax (how did this happen???).. if you open the install file with a text editor youll see that in every function declaration the syntax you have goes like:

> function FUNCTION_NAME ()
{ 
... function body...
}

just delete the word function in each declaration and the error message should dissapear (an alternative way would be to delete the parenthesis on each declaration (?))

HOWEVER!

after doing that, i still get a message about some unexpected parenthesis in the ./xwinstall.d/swim/lib/lib.sh at line 1119.. 
after checking the file i see that the function in which the error is popping (probably) is called GetRedHatVersion () which makes me go o.O 
neverminding that, i looked for the rogue parenthesis and i found none (why would there be?? ) so i'm really lost now. 
after popping the error message, the installation stops and it reccomends me to remove all that was done in the installation process. after a bit it asks whether to try again or just quit.
what should i do?

---

