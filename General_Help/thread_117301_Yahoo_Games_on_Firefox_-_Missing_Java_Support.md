---
title: "Yahoo Games on Firefox - Missing Java Support"
date: 2006-01-14
forum: General Help
---

### Post by Optiker on 2006-01-14
I'm trying to play games on Yahoo Games using Firefox. When I try, I get the message that I am missing the Java plugin. I checked with Adept and that shows that it is installed. If I elect to download it, it kicks me to the Sun DL page for the runtime environment, but the options there are an RPM and a self extracting (non-RPM?) file, and then a pari of the same for AMD64.

I tried to DL the self-extracting file, but while tthe DL manager saaid it was DLing to the desktop, I don't find it.

1.  if it's already installed as part of the Kubuntu installation, why is Yahoo not seeing it?

2. where is the new DL from Sun and canI install it, and if so, how. I see that Sun doesn't list Debian as on of the supported distros.

Suggestions?

Thanks!
Optiker

---

### Post by 23meg on 2006-01-15
Did you follow [these instructions]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") to install Java?

---

### Post by gordon33 on 2006-01-25
[QUOTE=23meg]Did you follow [these instructions]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") to install Java?[/QUOTE]


Good day to all
I have also been trying to down load Java in order to play Yahoo games.  In black and blue are the instructions as given.  My comments are in RED.  I thought it easiest to write comments and questions in the instructions where I had problems. 
Getting Java
Blackdown Java
For Ubuntu 5.10 (breezy), the easiest method is to use the Blackdown Java 1.4 installer from Multiverse. To install Java with the installer, just do: 
sudo apt-get install j2re1.4

Is Blackdown Java 1.4 installer from Multiverse something that can be down loaded from the web? How do I get to the installer? 

And what is the next sentence all about.  Is Ubuntu ppc or amd64 referring to my operating system?
Ubuntu PPC, please see: JavaPPC. Ubuntu AMD64, please see: JavaAMD64. 
Not doing well With the above method I moved on to the alternative method getting the latest version from Sun.  
Sun Java
The alternative method it to get the latest version from Sun. This version of Java works better for most applications. Sun's implementation of Java and Java plugin for browsers however is non-free. Free Java is in active development and will be the preferred choice once it is released. 
Go to  [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and click on â€œDownload JRE 5.0 Update 6â€. Ensure you do not choose one of the JDK or J2EE versions. 
You must first accept the licence, then click on â€œLinux self-extracting fileâ€ (jre-1_5_0_06-linux-i586.bin). Save this file to your hard drive. 
I thought things were going better.  I was not sure if saving the above to my desk top was the same as saving to the hard drive.  But I have an icon on my desk top labled “jre-1_5_0_06-linux-i586.bin”.  If I need to save “jre-1_5_0_06-linux-i586.bin” to my hard drive what steps need to be taken?
In spite of the questionable success, I though I would move on to the next step.  The next step stopped me. “Make the downloaded file executable.”  I assumed that could be done at the command line, by changing to the directory where you downloaded the file.  
What “command line” where would you find it?  Is by asumtion corect the t the desk top is the directory where I down loaded “jre-1_5_0_06-linux-i586.bin”
Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type 
Because of the problems mentioned above I never got to type the next command.  Would typing the “chmod +x jre-1_5_0_06-linux-i586.bin”  Make the downloaded file executable?

chmod +x jre-1_5_0_06-linux-i586.bin

So I ran in to a wall again.  I trust that my lack of basic knowledge show.  If you can help with the above and questions listed below in red I would appreciate the instruction.
Install the java-package and java-common, as well as fakeroot (which allows a non-root user to create the package derived from Sun's bin file): 
Where would the following command be typed?
sudo apt-get install fakeroot java-package java-common
If you get an error when installing java-package, you need to enable the multiverse repository (see AddingRepositoriesHowto). 
To install the JRE, type the lines below: 
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
(Note: in above example, i386 might have to be i586.) 
If you get an error similar to this: 
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Try 
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_03-linux-i586.bin
or similar command if you are not using i386 architecture. (Note: in above example, 1_5_0_03 might have to be 1_5_0_06.) 
make-jpkg translates Sun's bin file into a debian package. Then dpkg installs that package. 
Sun Java SDK (Software Development Kit)
The same procedure can also be used to install Sun's Java SDK instead of just the runtime environment (JRE). Just choose "Download JDK 5.0 Update 6" when downloading the package from Sun, and replace the file name with jdk-1_5_0_06-linux-i586.bin 
Selecting the default Java version
In Breezy, if you want to use Sun Java instead of the open source GIJ you need to set it as default. Run: 
sudo update-alternatives --config java
and select your preference from the list. 
Java on Mozilla Firefox
Installing Java without following the previous steps does not alert Firefox to its presence. If you simply executed the .bin file you downloaded, you will need to tell Firefox or Mozilla where to find the plugin library: 
If you do not have a .mozilla/plugins directory in your home directory, create one. 
mkdir -p /home/username/.mozilla/plugins
Then 
cd /home/username/.mozilla/plugins
ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
You can skip these steps if you used the make-jpkg command. 
If you have downloaded more than one, you need to modify the command to be more specific. 
Java on amd64 computers
Unfortunately, Sun's Java for 64-bit PC's does't work very well yet, but the Blackdown version of Java works and is available in the Ubuntu 5.10 (Breezy Badger) multiverse repository. 
sudo apt-get install j2re1.4 j2re1.4-mozilla-plugin
Afterwards restart Firefox and you should have a working Java plugin. 
CategoryDocumentation CategoryCleanup 
last edited 2006-01-13 04:51:45 by Michael10
© 2005 Canonical Ltd. Ubuntu, Kubuntu, Edubuntu and Canonical are registered trademarks of Canonical Ltd.

---

### Post by ftmichael on 2008-03-01
In case this is still an issue for you, or someone else:

Your coloured text didn't show up at all, so I'm trying to make sense of your post, but here.

What version of Ubuntu are you using?  Are you still using Breezy?  I recommend updating to something a little more recent, if so.

> Is Blackdown Java 1.4 installer from Multiverse something that can be down loaded from the web? How do I get to the installer?
You have the installer.  It's called apt-get.  Just do what it tells you to do: open up a terminal and type **sudo apt-get install j2re1.4** .  If you don't know whether the Multiverse repository is enabled, check.  See [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) for help in managing your repositories.  Once Multiverse is enabled, open up a terminal and type **sudo apt-get install j2re1.4** .  It'll ask you for your password; type it in (it won't appear on the screen, but it's there) and hit Enter.  It'll install Blackdown Java 1.4.

Be sure first that Blackdown Java 1.4 is really the best thing for you.  Check the current version of [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) .

Michael

---

