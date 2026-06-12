---
title: "UGS NX 5 on Ubuntu 7.10 amd64"
date: 2008-01-29
forum: Education &amp; Science
---

### Post by jackocleebrown on 2008-01-29
Hello,

I know that there is some information about how to install NX5 on ubuntu on [this]("http://ubuntuforums.org/showthread.php?t=581762") thread but to avoid confusion I thought it would be more helpful to make a clean description of what I had to do to install the program.

this worked with NX version 5.0.0.225
Replace "joebloggs" with your username.

_Installing NX5_

1) copy the contents of the nx5 install DVD to a temporary location so that we can alter the install script:
```
mkdir /home/joebloggs/Desktop/ugnx
cp /cdrom/ /home/joebloggs/Desktop/ugnx/
chmod a+x -R /home/joebloggs/Desktop/ugnx/
```

2) install some dependencies
```
sudo apt-get install libmotif3 tcsh ksh libstdc++5
```

3) open the install script for some editing
```
gedit /home/joebloggs/Desktop/ugnx/ugnx050/ug_install
```

4) find this section in the file:
> Linux) # Machine type Linux
    PATH=.:/sbin:/usr/sbin:/usr/bin:/bin:/etc ; export PATH # Set the PATH
    UGS_TMP=/tmp/ugs_tmp               # Define a stash area for old files.
    X11_DIR=/usr/lib/X11               # X11 directory for this system.
    PS_CMD="ps -ef"                    # ps command for this system.
    DF_CMD="df -k"                     # df command for this system.
    AWK_CMD=awk                        # awk command for this system.
    RC_DIR=/etc/rc.d                   # Dir for real rc scripts
    RC_LNK_DIR=/etc/rc.d/rc5.d         # Dir for links to rc scripts
    TMP_DIR=/tmp                       # Tmp directory.
    LPATH_VAR_NAME=LD_LIBRARY_PATH     # Library path var name. V160P14
    RC_PATH_VAR=/sbin:/usr/sbin:/usr/bin:/bin:/etc
    alias -x pwd='pwd -L'              # Tweak Linux pwd to give logical pwd.
    alias -x uncompress=gunzip         # On SuSE 10 must use gunzip. NX050P24
and change it to:
> Linux) # Machine type Linux
    PATH=.:/sbin:/usr/sbin:/usr/bin:/bin:/etc ; export PATH # Set the PATH
    UGS_TMP=/tmp/ugs_tmp               # Define a stash area for old files.
    X11_DIR=/etc/X11                   # X11 directory for this system.
    PS_CMD="ps -ef"                    # ps command for this system.
    DF_CMD="df -k"                     # df command for this system.
    AWK_CMD=awk                        # awk command for this system.
    RC_DIR=/etc/init.d                 # Dir for real rc scripts
    RC_LNK_DIR=/etc/rc2.d              # Dir for links to rc scripts
    TMP_DIR=/tmp                       # Tmp directory.
    LPATH_VAR_NAME=LD_LIBRARY_PATH     # Library path var name. V160P14
    RC_PATH_VAR=/sbin:/usr/sbin:/usr/bin:/bin:/etc
    alias -x pwd='pwd -L'              # Tweak Linux pwd to give logical pwd.
    alias -x uncompress=gunzip         # On SuSE 10 must use gunzip. NX050P24

5) the script fails to correctly check if no products have been selected for install. I did not find a way to correct this, I commented out the selection checking part of the code. Change this:
> echo $FSETS | grep "[A-z]" >$NULL || {
             print "${MSG}no products selected." 
             sleep 2  ; continue 2
             [ "$Q_SWT" ] && { print "${ERR}no products selected." ; exit 1 ;}
          } # End empty FSETS ck.
to this:
>   # echo $FSETS | grep "[A-z]" >$NULL || {
          #   print "${MSG}no products selected." 
          #   sleep 2  ; continue 2
          #   [ "$Q_SWT" ] && { print "${ERR}no products selected." ; exit 1 ;}
          #} # End empty FSETS ck.


6) After you have made these changes save the file and the installer should run fine:
```
sudo /home/joebloggs/Desktop/ugnx/ugnx050/ug_install
```

If you wish to subsequently change the licence server you need to adjust the parameters that are set in these two files:
/etc/profile & /etc/csh.login

you can run nx5 using this code:
```
/opt/ugs050/ugii/ugmenu
```

_Installing the licence server_

1) open the licence install script for editing
```
gedit /home/joebloggs/Desktop/ugnx/ugnx050/ugslicensing/ugslicensing_install
```

2) find the section:
> Linux) # Machine type Linux
    alias -x df="df -k"                    # Alias df to df -k, gives K bytes.
    alias -x pwd='pwd -L'                  # Alias pwd to give a logical pwd.
    alias -x echo=print                    # Alias echo to print.
    DEFAULT_MEDIA=/media/dvd               # Default name for the CD/DVD media.
    PATH=.:/sbin:/usr/sbin:/usr/bin:/bin:/etc # Set the PATH
    PS_CMD="ps -ef"                        # ps command for this system.
    PROD_SIZE=3600                         # Hard coded size for this plat.
    RC_DIR=/etc/rc.d                       # Dir for real rc scripts
    RC_LNK_DIR=/etc/rc.d/rc5.d             # Dir for links to rc scripts
    RC_PATH_VAR=/sbin:/usr/sbin:/usr/bin:/bin:/etc # Path used in the rc script.
    RC_SCRIPTNAME=rc.ugs.licensing         # The rc script name.
    RC_LNK_NAME=S91$RC_SCRIPTNAME          # Name for sym link in rc lnk dir.
    RESTART_DELAY=10                       # Daemon Restart delay in seconds.
    TMP_DIR=/tmp                           # Tmp directory for this plat.
    UGS_TMP=/tmp/ugs_tmp                   # Define a stash area for old files.
and change it to:
> Linux) # Machine type Linux
    alias -x df="df -k"                    # Alias df to df -k, gives K bytes.
    alias -x pwd='pwd -L'                  # Alias pwd to give a logical pwd.
    alias -x echo=print                    # Alias echo to print.
    DEFAULT_MEDIA=/media/dvd               # Default name for the CD/DVD media.
    PATH=.:/sbin:/usr/sbin:/usr/bin:/bin:/etc # Set the PATH
    PS_CMD="ps -ef"                        # ps command for this system.
    PROD_SIZE=3600                         # Hard coded size for this plat.
    RC_DIR=/etc/init.d                       # Dir for real rc scripts
    RC_LNK_DIR=/etc/rc2.d            # Dir for links to rc scripts
    RC_PATH_VAR=/sbin:/usr/sbin:/usr/bin:/bin:/etc # Path used in the rc script.
    RC_SCRIPTNAME=rc.ugs.licensing         # The rc script name.
    RC_LNK_NAME=S91$RC_SCRIPTNAME          # Name for sym link in rc lnk dir.
    RESTART_DELAY=10                       # Daemon Restart delay in seconds.
    TMP_DIR=/tmp                           # Tmp directory for this plat.
    UGS_TMP=/tmp/ugs_tmp                   # Define a stash area for old files.

3) Save the file, you can run the install script for the licence server now:

```
sudo /home/joebloggs/Desktop/ugnx/ugslicensing/ugslicensing_install
```

4) The startup script to automatically run the licence server when the machine starts needs some attention:
```
sudo chmod u+x /etc/init.d/rc.ugs.licensing
sudo update-rc.d rc.ugs.licensing defaults 
```

I hope that this is useful for someone - please let me know if you find I have made an error (I only have my notes to hand, not the installed NX) and I will try and keep this post up to date.


Jack.

---

### Post by zvadinov on 2008-05-07
Hello jackocleebrown


Your description is awesome I follow it and every thing work well (only I install it an Ubunut 8.04 amd 64)!

But I get a problem with the License file!

I' ve done all steps to get the License form UG Support

I generate the CID Key add the  Hostname and  send them to UG 

then I receive the License (txt-File)!

Ok right now!

I open the License, end everything seems ok !

But when I try to install the licenseserver and have to enter the full path to the license File 

it gives me an Error :
> 
WARNING: could not find 28000@MYNAME in '/etc/hosts' or NIS or DNS.

WARNING: no useable servers found in license file.

        UGS products will not run with this license file.

I've open the hosts File this is what it contains 

> 127.0.0.1 localhost

127.0.1.1 MYNAME


# The following lines are desirable for IPv6 capable hosts

::1 ip6-localhost ip6-loopback

fe00::0 ip6-localnet

ff00::0 ip6-mcastprefix

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters

ff02::3 ip6-allhosts

~                        

I think everything is all right, or ?

Thank in forward for you help!


Zvadinov

---

### Post by jackocleebrown on 2008-05-10
Hi Zvadinov,

I am really pleased that you found the instructions helpful.

I can remember having some real problems with the licence file too when I was setting this up. I was actually installing it for a friend on his computer so I don't have a working copy now to compare with your settings.

Your hosts file looks ok, I guess that MYNAME is your computer name.
Is this problem occurring when you are installing the licence server or is it later when you try and run NX?

Jack.

---

### Post by jackocleebrown on 2008-05-10
Hi Zvadinov,

I found this instruction on another thread, it might help you solve your problem - does it make any sense to you?

> Step 5: modify license file
Hopefully by now you got your license file from UGS.
Open it with sudo.
Modify 16th line: SERVER hostname COMPOSITE=xxxxxxxxxxxxx portnumber
Replace hostname and portnumber (usually 28000). Hostname is usually the hostname of your computer.
I named the license file ugs.lic.

Thanks, Jack.

---

### Post by zvadinov on 2008-05-12
Hello Jack..

thank you for your replay!
Now I have try it again and I receive the same error I postet above!
Then I change the hostname only to lower case >> instate MYNAME  I use myname
and the Installation of the Licensserver was done!

// I was so happy and jumping around at this moment without trying to start them :)

then I tried to start up the Licenseserver with:

```
./lmgrd -c ugs1.lic 28000@myname

```
this is the output:


```
18:29:31 (lmgrd) -----------------------------------------------

18:29:31 (lmgrd)   Please Note:

18:29:31 (lmgrd) 

18:29:31 (lmgrd)   This log is intended for debug purposes only.

18:29:31 (lmgrd)   In order to capture accurate license

18:29:31 (lmgrd)   usage data into an organized repository,

18:29:31 (lmgrd)   please enable report logging. Use Macrovision's

18:29:31 (lmgrd)   software license administration  solution,

18:29:31 (lmgrd)   FLEXnet Manager, to  readily gain visibility

18:29:31 (lmgrd)   into license usage data and to create

18:29:31 (lmgrd)   insightful reports on critical information like

18:29:31 (lmgrd)   license availability and usage. FLEXnet Manager

18:29:31 (lmgrd)   can be fully automated to run these reports on

18:29:31 (lmgrd)   schedule and can be used to track license

18:29:31 (lmgrd)   servers and usage across a heterogeneous

18:29:31 (lmgrd)   network of servers including Windows NT, Linux

18:29:31 (lmgrd)   and UNIX. Contact Macrovision at

18:29:31 (lmgrd)   www.macrovision.com for more details on how to

18:29:31 (lmgrd)   obtain an evaluation copy of FLEXnet Manager

18:29:31 (lmgrd)   for your enterprise.

18:29:31 (lmgrd) 

18:29:31 (lmgrd) -----------------------------------------------

18:29:31 (lmgrd) 

18:29:31 (lmgrd) 

18:29:31 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)

18:29:31 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)

18:29:31 (lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.6321, errno: 2

boro@myname:/opt/ugslicensing$ 18:29:31 (lmgrd) Failed to open the TCP port number in the license.

18:29:31 (lmgrd) Can't remove statfile /usr/tmp/.flexlm/lmgrdl.6321: errno No such file or directory



```
I try to start NX5 with :

```
./ugii
```

this is the output:

```

 Starting NX ... Traceback note: Failed to find library for fdc76da2213ffe14

====================================================

Failed to handle error condition correctly - exiting

Initialization error - 

NX License Error:  The license server has not been 

started yet, or UGS_LICENSE_SERVER is set to the 

wrong port@host. [ -15 ]



====================================================

Traceback note: Failed to find library for fdc76da2213ffe14

====================

Fatal error detected

====================


```

I think the Error while starting NX5 is ok because the Licenseserver isn't runnig !

Is it possible that the Port is blockt at Ubunutu 8.04 by default ?

Thank you in forward for you help!!

Zvadinov

---

### Post by jackocleebrown on 2008-05-12
Hi Zvadinov,

When I installed NX I fixed the startup scripts so that the server runs when you turn on the computer this was the last part of the original instructions - it might also help you with your problem. Do this first:

> 4) The startup script to automatically run the license server when the machine starts needs some attention:
Code:

```
sudo chmod u+x /etc/init.d/rc.ugs.licensing
sudo update-rc.d rc.ugs.licensing defaults
```



and then try and run the licence server like this:
```
sudo /etc/init.d/rc.ugs.licensing start
```

Then see if you can run ugii.

I also remember that depending on the type of licence you have you might need to run /opt/ugs050/ugii/ugmenu first and then choose the correct bundle for the licence.

I am sure that the ports are not blocked by default - as long as you have not installed a firewall this should be ok.

Good luck, Jack.

---

### Post by zvadinov on 2008-05-12
Hi Jack,

I've test the way you explain but I receive the same error:

>                 Starting NX ... Traceback note: Failed to find library for fbfb02ff2adffe14

====================================================

Failed to handle error condition correctly - exiting

Initialization error - 

NX License Error:  The license server has not been 

started yet, or UGS_LICENSE_SERVER is set to the 

wrong port@host. [ -15 ]



====================================================

Traceback note: Failed to find library for fbfb02ff2adffe14

====================

Fatal error detected

====================


when I open it over ugmenu it shows me all Bundles and when I choose CAD and apply,
it opens a new shell window and show the same error!
I also tried to add the Environment Variables in the /etc/profile like Showan2 explain
but no changes happens to me

I'm not amused about :( because UGS only supports SUSE and REDHAT but I 
will try to contact them!

thank you for your help!

Zvadinov

---

### Post by zvadinov on 2008-05-13
Hi Jack

it is running but when I wont to open or create a new Part I get X Server crash :-(

---

### Post by jackocleebrown on 2008-05-20
Hi Zvadinov,

Is your openGL working? if you type "glxinfo" in the terminal check to see if it says "direct rendering: Yes"

Jack.

---

### Post by nmucci on 2008-05-20
You may have problems running NX while Compiz is running.  Also, if you have an Nvidia graphics card, use the Nvidia driver, *not* whatever the driver is that comes with Ubuntu.  Its the only way to be sure that the program will draw properly.  

-Nick

---

### Post by zvadinov on 2008-07-20
Hello together,

Im sorry about my late reply, I didn't receive a mail that anybody
is writing in this thread!?
Last months I have to much work, so there was no time for testing !
Now I'm back to upgrade my skills in get nx5 working on Ubuntu :-)

A big THNANKS to all and specially to jackocleebrown for the Help ,NX5 is now working fine!

The problem was the new Nvidia Driver!

I hope sometime it will be possible to work with Compiz (I love the Cube) ;-)

btw. Does anybody know if this would be possible(compiz&nx) with the expensive Quadro Cards?

bye
 ZZ

---

### Post by mountanddo on 2008-08-20
Zvadinov:

How did you fix the "failed to find library error"?

I got the same error as yours.

Thanks,

Todd

---

### Post by zvadinov on 2008-08-21
Hi mountanddo.

this error results because you have not select any License bundle.

try to run ./ugmenu   (<nx_base_folder>/ugii/ugmenu)

it should pop up you a small &#8221;blue&#8221; window

in this window go on &#8222;Options>License Options and select the bundle you wont!

After that click on apply... NX should work now!

I hope my information can help you! 
Would be nice to hear from you if you have also the Shortcut-Problem!


ADDITION:
I'm not realy sure, but i have also played around with the /etc/hosts file 
the name of your Computer must have the same latter's as the license file 
the license file is also case sensitive, i think!  
And if you use 

127.0.0.1 localhost.yourname 

try to make 
127.0.0.1 localhost
127.0.1.1 yourname




Bye 
ZZ

---

### Post by astrokylin on 2009-01-06
Hello jackocleebrown


Your description is awesome I follow it and every thing work well (only I install  UGS NX 4 on Debian Lenny amd 64) and the installer  run fine.

But I get a problem when I run nx4!


```

/usr/ugs040/bin/ugmenu

```
Executing ugmenux...


Then, nothing 

Thank in forward for you help!
Astrokylin

---

### Post by firefox66 on 2009-09-07
i don't understand what it mean ?? may be license wrong ?or port 28000 had not opened??

Starting NX ... ====================================================
Failed to handle error condition correctly - exiting

NX License Error: Invalid (inconsistent) license key or signature.
The license key/signature and data for the feature do not match
====================================================
====================
Fatal error detected
====================

Please help ?

---

### Post by vancouverite on 2009-11-29
Hi UGS NX on Ubuntu users.  I have successfully installed NX 6 on Ubuntu 9.10, but have a question about using the software.

When I load up there are a few pallets (windows with different tools) floating around.  I do not have the option to close them and as I work they seem to multiply - to a ridiculous degree!  They are "always on top" and putting them on a different workspace seems to cause problems like dialog boxes that are important showing up on the alternate workspace.

Is there a way to close or dock these things?  They are very annoying - especially since I'm using NX on a laptop!

I have attached a screen shot to that you see what I mean.

-Van

---

### Post by vancouverite on 2009-11-29
Hey all, isn't it always the way: you post, then 10 min later you figure it out.  Here is the solution I found to remove all the annoying pallets floating around on my screen:

Preferences -> User Interface -> Tab:Layout

Change the "Display Resource Bar" to "As Toolbar"

Now the resource tabs at the left (if using defaults) becomes a toolbar and the buttons are boolean: click on "assembly navigator" button and the relevant window appears, click on the button again and the window disappears.  Click two buttons on at the same time and and both windows appear.

A much cleaner interface!

-Van

---

### Post by hustfuxj on 2011-07-26
Hi, i see you succeed install ug on linux. do you have the crack file libjam.so, please email it to me([EMAIL="hustfuxianjun@qq.com"]hustfuxianjun@qq.com[/EMAIL]).

---

### Post by jackocleebrown on 2011-07-27
Hi Hustfuxj,

I did not have to crack this file, what version are you trying to install?

---

### Post by goliveira on 2011-10-31
Hi!

I found this amazing....

I could install NX8 (client) in an Ubuntu Lucid, and i execute it fine, but it show a window telling me this:

```
nx motif resource file ugnx8 could not been found, contact your system administrator
```

Could anyone help me?

I am using nVidia Gforce 8400 gs, and using nVidia private components found in the repositories.

Thanks.

---

### Post by vancouverite on 2011-10-31
Do you have libmotif3 installed?

---

### Post by goliveira on 2011-11-01
Yes, i have libmotif installed in the client (v.2.2.3-4). Could it be problems in license server??? or am i crazy?

Remember, i have instaled NX8 on Ubuntu Lucid 64bits

Thanks!!

---

