---
title: "Citrix ICA client on Dapper with Firefox plugin?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Schalken on 2006-06-05
The HOWTO is in the posts below this one.

My old message:
> It appears that I should be able to login to my school computers using the Citrix ICA client!

Has anyone successfully installed and run the Citrix ICA client on Dapper? I have only found tutorials for Breezy and so far the Firefox plugin hasn't worked. :(

The tutorial I followed was: [http://www.zwhlug.nl/content/citrix_ica_client_how_to_install_the_citrix_ica_client_on_ubuntu_and_debian_gnu_linux](http://www.zwhlug.nl/content/citrix_ica_client_how_to_install_the_citrix_ica_client_on_ubuntu_and_debian_gnu_linux)

---

### Post by thebone on 2006-06-05
Install the latest citrix 9.0 client.  It will say that it is setup for Netscape when it is done installing.  I then had to go into the 
Edit->Preferences->Downloads->View and Edit Actions area in Firefox.  From there, highlight the IC extension for Citrix apps and hit Change Action.  From there, click the Open with this application radio button and browse to wfica located in username/ICAClient/linuxx86.

It will then work, or at least it did for me.

thebone

---

### Post by Schalken on 2006-06-05
OMG it worked! Thank you so much!

Note: another way to change Firefox's action when it hits an ICA file is to select Open With... when it asks you what to do then select 'other' in the dropdown menu, browse to '/usr/lib/ICAClient' (thats where it should be unless you installed the client as a user (not root)(in which case it might be in username/ICAClient/linuxx86 as thebone said above) or specifically specified another location) and select the wfcia file (the executable with the diamond icon) in that dircetory. Then make sure the 'Do for all files like this from now on' checkbox is ticked. Worked for me!

Note: the Citrix ICA client for linux (x86) can be downloaded from: [http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186](http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186)

---

### Post by paul74 on 2006-06-06
Hello there, unfortunately I still have problems, I can't get it work.
Would you please provide some more help for this exact topic...

Here's my point:
- I istalled citrix ica client 9.0 as root. ok
- Firefox doesn't open the launch.ica file provided from the metaframe web server
- if I type ./wfcmgr I get the "libXm.so.3" not found error. Can't even make a sym link because I only got the libXm.so.2 on my system
- if I manually launch ./wfica /home/user/launch.ica I get the two warnings:
"missing charsets in string to fontset conversione"
"unable to load any usable fontset"
then the Citrix connection window opens but nothing happens.

Thanks to all.

Ubuntu 6.06 TLS desktop.

---

### Post by techstop on 2006-06-06
OK, I managed to get the Citrix ICA client working with Firefox 1.5 (Swiftfox actually) by doing the following;

-download the tar.gz from citrix (link above) and unpack to a temporary folder and change to that directory

```
sudo ./setupwfc
```

Follow the prompt, let it install to the default location

Once you are finished the client install, change to your firefox plugin folder, mine was;
(change your folder to match your actual firefox plugin path)

```
cd /opt/swiftfox/plugins
```

Make a symlink from the citrix plugin to the firefox plugin folder;

```
ln -s /usr/lib/ICAClient/npica.so npica.so
```

Then you can login with your citrix client. If it complains about not trusting certificates, you can download one here;

[http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm](http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm)

And save it to the following folder;
```

/usr/lib/ICAClient/keystore/cacerts
```

I cobbled this together with the help of the following;

[http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml](http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml)
[http://www2.slac.stanford.edu/computing/windows/services/citrix/faq_xp.htm](http://www2.slac.stanford.edu/computing/windows/services/citrix/faq_xp.htm)

Hope this helps, works great for me. And you don't need to specify the plugin from within firefox, it just "knows". Cheers. :-D

---

### Post by paul74 on 2006-06-06
[QUOTE=techstop]Hope this helps, works great for me. And you don't need to specify the plugin from within firefox, it just "knows". Cheers. :-D[/QUOTE]

sorry that didn't help, Firefox still doesnt understand .ica files...and still remains the libXm.so.3 problem.
anyway I discovered that usig ICA client from Ubuntu (from any linux/osx distro actually) makes the metaframe server rebooting...:-k :confused: 
so the administrator told me to stop it until they move on the new servers/citrix versions

so probably someway it works (at least from terminal) but it just make the server reboot so I actually cannot understand if the ica client fully works :-\" 
oh well....:roll:

---

### Post by techstop on 2006-06-06
Did you uninstall the ICA client and then reinstall with my instructions? I had to uninstall when I was trying to get it working.

EDIT: Just had a look at that other HOWTO, seems very complicated. I don't know what the libXm.so.3 does, but this post;

[http://www.ubuntuforums.org/showthread.php?t=65879&highlight=libXm.so.3](http://www.ubuntuforums.org/showthread.php?t=65879&highlight=libXm.so.3)

shows you how to install it. It was entirely unnecessary for me with my instructions. HTH.

Also, how do you connect to your Citrix session? I didn't set up the client at all, I just navigate to the remote web site by;

remote.domain.com

and login, and the run the desktop shortcut.

---

### Post by paul74 on 2006-06-06
> **techstop]Did you uninstall the ICA client and then reinstall with my instructions? I had to uninstall when I was trying to get it working.[/quote]

I already installed it that way (also reinstalled).

> 
EDIT: Just had a look at that other HOWTO, seems very complicated. I don't know what the libXm.so.3 does, but this post said:**
> http://www.ubuntuforums.org/showthread.php?t=65879&highlight=libXm.so.3[/url]


I'll try to do "sudo apt-get install libxp6" but I think I've already done that...I kind of lost the count on the things I've installed to fix it...

[quote]
Also, how do you connect to your Citrix session? I didn't set up the client at all, I just navigate to the remote web site by;

remote.domain.com

and login, and the run the desktop shortcut.

yes that's just how I do it. just log to a web site, get the "desktop" icon and click on it. I don't setup the metaframe program neighborhood or what is called.
anyway as already said I can't try anymore because the remote server will reboot upon my connecting request (isn't it weird :( ) so if I don't want to be killed by the administrator I'd better be quiet for a while...:-\" 

btw I remember I've installed ICA on a SUSE 9.x and not having any kind of problems...](*,)

---

### Post by techstop on 2006-06-06
OK, I'm almost out of ideas. It "just works" for me with my instructions. Maybe you introduced some unneeded dependency with that libxm stuff? Maybe try;

```
sudo apt-get remove libmotif3 libmotif-dev libxaw6
```

to remove the packages installed from the first step of the other HOWTO? Then uninstall citrix ica, and restart with my instructions. The reason I suggest this is that I don't even have this file on my system;

/usr/X11R6/lib/libXm.so.3 

Failing that, I really am all out of ideas... :-k

---

### Post by paul74 on 2006-06-06
> **techstop]OK, I'm almost out of ideas. It "just works" for me with my instructions. Maybe you introduced some unneeded dependency with that libxm stuff? Maybe try said:**
> 

ok

[quote]
to remove the packages installed from the first step of the other HOWTO? Then uninstall citrix ica, and restart with my instructions. The reason I suggest this is that I don't even have this file on my system;

/usr/X11R6/lib/libXm.so.3 


yeah me to...

thanks very much for you support, I'll take my time to solve the problem.

---

### Post by techstop on 2006-06-06
good luck!

---

### Post by kitchens on 2006-06-06
I am attempting to setup citrix client 9. When I run setupwfc this is what I get:
```
$:~/linuxx86/linuxx86.cor$ sudo ./setupwfc
cat: /home/user/linuxx86/linuxx86.cor/./pkginf/V*: No such file or directory

This installation is not the correct type for a Linux (x86) workstation.

```
Any suggestions? I downloaded the linux tar from [here.]("http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186")

---

### Post by techstop on 2006-06-06
I think it may be because you're running the installation script from the wrong location. You have run it from the linux86.cor folder, it needs to be run from the root of the folder you extracted it to. 

eg.

```
~/linuxx86/linuxx86.cor$ sudo ./setupwfc
```

Should be 

```
$ sudo ./setupwfc
```

EDIT: Error in 2nd path...

---

### Post by kitchens on 2006-06-06
[QUOTE=techstop]I think it may be because you're running the installation script from the wrong location. You have run it from the linux86.cor folder, it needs to be run from the root of the folder you extracted it to. 

eg.

```
~/linuxx86/linuxx86.cor$ sudo ./setupwfc
```

Should be 

```
~/linuxx86/$ sudo ./setupwfc
```[/QUOTE]

Well I ran it where it extracted it. But I did what you suggested and I get the same error.

---

### Post by techstop on 2006-06-06
OK, I have just looked at how the archive is structured. You will have the following in the folder you extracted to;

```
-rw-r--r-- 1 barney barney 20329 2005-04-09 03:52 eula.txt
-r--r--r-- 1 barney barney  1983 2005-04-09 03:52 install.txt
drwxr-xr-x 3 barney barney  4096 2006-06-06 21:08 linuxx86
-r--r--r-- 1 barney barney   878 2005-04-09 03:52 PkgId
-r-xr-xr-x 1 barney barney 14860 2005-04-09 03:52 setupwfc
```

From the terminal output you posted, it looks like you have run setupwfc from the following folder;

/linuxx86/linuxx86.cor/

instead of the root of where you extracted.

Can you post the output of the following commands to confirm? Run them from the same folder that you were running setupwfc from...
```

ls -l
```

```
pwd
```

---

### Post by techstop on 2006-06-08
I noticed that I gave the wrong path a couple of post up. I have now edited that post. Have you got it working yet?

---

### Post by jgcamp99 on 2006-06-09
After re-eanbling root to login on gnome, I used the synaptic package manager application installer to get and update/install Open Motif 2.2.3, then ran the downlaoded installer for Citrix ICA Client 9 and it worked without a hitch.

Basically version 9 needs Open Motif 2.2.3, synaptic package manager, under system, administration while logged in as root gets that done out of the box for Ubuntu. After that, you copy the tarball to /usr/lib and a folder of your own naming convention. Double click and install the setupwfc and tell it to run in the terminal as the first item to your left indicates, you can install and even use this to uninstall it later. Follow the instructions very slowly and carefully to put it into the default directory. There is a EULA, initially it opens to a less than 100% level, you have to go line by line until it hits 100% and then option 1 accepts 2 rejects, but go slowly, because you do have to Accept with a "1" and enter, then follow thru with the rest of the prompts.

At the end, you'll have a directory under:

/usr/lib/ICAClient

in that folder is your wfcmgr that opens your Citrix connection expert. It's the purple diamond shaped icon. Double click that and it opens up to setup your configuration. From there you can add it to menu's or wherever you want as a program applet. The icons are even there in the same directory structure, a folder called icons. It automatically puts menu items in the Applications menu at the top left of your screen.

---

### Post by techstop on 2006-06-09
The Citrix download page says you need OpenMotif, but I don't appear to have it on my system :confused:  What's the name of the package you installed in Synaptic? There is one called motif-clients which I don't have installed....

---

### Post by jgcamp99 on 2006-06-09
Unfortunately I'm @ work, will get back to you on the exact item to install. I figured it was installed and Citrix failed everytime and then I tracked down that Open Motif dependency and installed it. Citrix went on and I was able to set up the defaults and profiles very easily after that. Even added a quick launch icon to the menu/start bar.

---

### Post by techstop on 2006-06-09
Oh, Citrix is working fine for me, I'm just curious that you had to install Open Motif (and Citrix say it's required). I also don't have libxm or libmotif listed in the other HOWTO. Strange.

---

### Post by jgcamp99 on 2006-06-09
yep, the clients 2.2.3 version, that's it I think, it's been about a week, but that sounds like the selection I made. I would run it before and there would be some weird messages that appeared in the terminal thatr told me that it didn't go on very cleanly. After getting the Open Motif version installed, the installation went on, no terminal window error messages.

---

### Post by diafebus on 2006-06-14
Just intall the client as it is explained at the begining of the thread.
Once installed, connect to the server.
When firefox says it can't open the file with ica extension, choose the option 'open with...' and click on Browser. Choose the file /usr/lib/ICAClient/wfica (the one without the capital W and without the .sh extension)
Then, check the option below and click OK.

There's no need of any additional package or software.

---

### Post by AklBlue on 2006-06-15
I found this to work for me in Dapper:

1. Install the Motif-Clients package, which installs libmotif3, and the files to allow the ICA session to display on your desktop.
2. Install the ICA client from Citrix.  Untar to your home directory, and run the "setupfwc" as root (or sudo) .. follow the onscreen directions.
3. In firefox, when you first open an *.ica file, choose the option 'open with...' and click on Browser. Choose the file /usr/lib/ICAClient/wfica

Thats it.

---

### Post by syounkim on 2006-06-19
I installed citrix on dapper. But have two problems;

1. 

'/usr/lib/ICAClient/wfcmgr' says it can't find libXm.3.so. However, I found that /usr/lib/libXm.3.so is symlinked to /usr/lib/libXm.3.0.2.

Any idea?

2. 

'/usr/lib/ICAClient/wfica' works. However, when I run applications like MS Word , it could not even read dirs and files on my computer, giving an error 'restrictions in effect on this computer'. By the way, I found from a how to that users should belong to ICA ? user NDS group, which I have no idea about.  

Any help?

Thanks in advance.

---

### Post by usererror on 2006-06-21
[QUOTE=AklBlue]I found this to work for me in Dapper:

1. Install the Motif-Clients package, which installs libmotif3, and the files to allow the ICA session to display on your desktop.
2. Install the ICA client from Citrix.  Untar to your home directory, and run the "setupfwc" as root (or sudo) .. follow the onscreen directions.
3. In firefox, when you first open an *.ica file, choose the option 'open with...' and click on Browser. Choose the file /usr/lib/ICAClient/wfica

Thats it.[/QUOTE]

For what it's worth, this is also how I got it to work for me as well.  I had one working by creating the symlink to the plugin in /usr/lib/ICAClient/ on a different Ubuntu box but now that method doesn't seem to work anymore.

---

### Post by Jeff_From_VA on 2006-06-21
I did not read the whole thread, I don't know if this will be of use but I wanted to share... I found these instructions and this is how I set mine up and it works great for me.

[http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml](http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml)

---

