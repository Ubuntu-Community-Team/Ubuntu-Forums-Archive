---
title: "StarOffice 8"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Sopranosmainman on 2006-01-08
Ok i extracted the sh file, and when i go to setup... i get the following error....

Running installer
InvocationTargetException in ArchiveReader constructornull
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Sou
rce)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does n                                           ot exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        ... 7 more
Target Exception Trace:
java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Sou                                           rce)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
0022


What is wrong.. i have java installed.... so i cant make any sense of this error message. Someone can dicifer this? Any help is much appreciated. THanks

---

### Post by zachariah on 2006-01-17
Hello

I have just spent the best part of a day trying to get this damn piece of **** to install. I nearly gave up hope. I wept bitter tears of frustration.

But not now! Tears of joy streak my cheeks! StarOffice is installed and I have learned yet again why Linux is great for us geeky types who enjoy the thrill of overcoming difficulties, but is hopelessly behind Microsoft when it comes to providing a simple computing experience for general users.

So! Here's how you do it:

Your first task is to ensure the latest version of Java is installed. The forums here are a great help, this is the link which worked flawlessly:

[JDK Install How-to]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=jdk+install")
(One thing this How-to does not tell you is that for apt-get to recognise this package, you have to add in some non-default repositories, ones that aren't even listed by Synaptic. These are:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Both of these should be added to Synaptic or manually added to the /etc/apt/sources.list file before trying to get either java or alien. I had already downloaded the java .bin file from Sun)

Now you download and install the 200MB StarOffice package from Sun. They give it away free, don'tcha know. You now have a huge great .sh file somewhere.

Navigate to this file and run it (annoyingly for new Linux users, there is no hint from the Sun site on how to run a .sh file. New Ubuntu users like myself would have been greatful to hear that the command you are looking for is 'sudo ./(filename)' (once you are in the directory containing the file).

Hopefully your new Java files will allow StarOffice to correctly unpack itself. The default folder it unpacks itself to is /var/tmp/unpack_staroffice. Navigate to this folder. Possible problems at this stage can also be caused if you dont already have a folder called /opt or /var/opt or possibly /bin/rpm (I don't think that last one is necessary, I just checked the one I made and it is empty). You can make all these folders with the 'sudo mkdir (full folder path)' command.

And now you have a directory called /var/tmp/unpack_staroffice, full of various things. None of them at all useful for Ubuntu, so we have to change them from wicked RPMs to lovely DEBs.

'sudo apt-get install alien' should install the alien program, which allows you to convert an rpm into something Ubuntu can install. As you will read in the read_me file inside the StarOffice directory, the command is 'alien -i -k RPMS/*.i586.deb'. I ran this while logged in as root but I don't think this matters, a sudo command should also work. 

The Konsole will sit there for several minutes, unless your PC is unfeasibly fast. Do not panic.

Eventually the bash prompt will return as if nothing happened (there is probably a -v verbose switch to add to alien to show what is going on, you may want to try this). That is essentially it. Check synaptic and you will see StarOffice is installed.

Except of course there are no desktop shortcuts...no shortcuts in any menus...no clue whatsoever as to how to start the damn program. Restrain your urge to throw expensive equipment as far as your puny muscles allow.

The main startup script is called 'soffice', and can be found in the new directory /opt/staroffice8/program. Either make a desktop link to it or, if you are feeling adventurous, a bash alias, or make a link to go inside your Office Applications menu.

Then sit back and enjoy the amazing office suite that is etc etc.

---

### Post by mips on 2006-01-17
What are the advantages of staroffice over openoffice ?

---

### Post by zachariah on 2006-01-17
No idea. Possibly none. I only went through all this palaver because it was for work. It looks ever-so-slightly nicer than OpenOffice, but that's a matter of opinion.

---

### Post by limit223 on 2006-01-17
[QUOTE=zachariah]Hello


'sudo apt-get install alien' should install the alien program, which allows you to convert an rpm into something Ubuntu can install. As you will read in the read_me file inside the StarOffice directory, the command is 'alien -i -k RPMS/*.i586.deb'. I ran this while logged in as root but I don't think this matters, a sudo command should also work. 

The Konsole will sit there for several minutes, unless your PC is unfeasibly fast. Do not panic.

Eventually the bash prompt will return as if nothing happened (there is probably a -v verbose switch to add to alien to show what is going on, you may want to try this). That is essentially it. Check synaptic and you will see StarOffice is installed.

Except of course there are no desktop shortcuts...no shortcuts in any menus...no clue whatsoever as to how to start the damn program. Restrain your urge to throw expensive equipment as far as your puny muscles allow.

[/QUOTE]

 Yeah...I installed this software too, and I had this problem at first installation finding any link or shortcut in kmenu but then I found that doing

sudo alien -i -k RPMS/*.i586.deb 

it is ommited one of the rpm from the whole package named: staroffice-desktop-integration_8.0.0-124.noarch.rpm (due to the noarch suffix)
which install all those links and set of staroffice icons in the system

To avoid that don't forget to alien and install that package as well..

---

### Post by sayantandas on 2008-05-27
thank you for the detailed instructions.
u r a lifesaver.. i have star office installed now.
By the way i would also like to add that at the beginning of the installation, when it asks for the installation directory, its better if a new folder to desktop is added manually. In that way , its easier to find the directory.
Thanks again.

---

