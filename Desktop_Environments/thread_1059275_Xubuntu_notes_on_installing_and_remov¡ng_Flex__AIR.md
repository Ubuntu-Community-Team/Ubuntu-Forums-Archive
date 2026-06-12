---
title: "Xubuntu: notes on installing and remov¡ng Flex / AIR"
date: 2009-02-03
forum: Desktop Environments
---

### Post by slumbergod on 2009-02-03
Hi, this is just to help anyone who might be encountering the same problems I did when experimenting with Adobe Flex and Air.

In the end Flex worked fine for me but something just wasn't quite right with AIR so I removed it. That is when I discovered how pathetic Adobe's documentation is for Linux.

I really wanted to learn development for JavaFX but Sun's decision to release the Windows and Mac SDK while making Linux users wait (forever) makes me question the cross platform philosophy they've always pushed. At least Adobe made Flex open source. Though their installation documentation for Linux sux, they did at least give it to everyone so that is reason enough to develop flex. 

Installing FLEX
---------------
1. download the flex zip to your desktop from the Adobe website. It's chunky at over 100Mb.
2. right-click the file and select Extract Here and you'll get a new folder on your desktop. I chose to rename the unzipped folder as "flex" for simplicity.
3. next, move it to where you want it. There is no "installation" as such. I chose /opt using "sudo mv ~/Desktop/flex /opt"
4. make sure you have installed Sun's java SDK. It is in Synaptic (i.e. sun-java6-jre and sun-java6-jdk for the java runtime and development kit respectively). If you have the alternative java sdk installed already you might want to run this command to make the Sun one the default one: sudo update-java-alternatives -s java-6-sun
5. make sure the path for the java development kit is set correctly, something that is almost never done correctly. I set mine by adding in as an environment variable. 
sudo nano /etc/environment
then adding the line:
JAVA_HOME="/usr/lib/jvm/java-6-sun/jre/bin/java"
save it, then reload your environment with:
source /etc/environment
if it worked, the command
echo $JAVA_HOME 
will display a path (if it didn't work you'll get a blank line)
6. next, you need to make sure that your system knows where the flex compiler etc is. I did this in the bashrc file:
nano ~/.bashrc
and added the line:
export PATH=/opt/flex/bin:$PATH
save. I restarted the pc to make sure everything was loaded correctly.
I tested my installation on the command line with a demo mxml file I downloaded off one of the dozens of sites you can find with Google.
I compiled it to get a swf file then dragged it into Firefox to display it.
mxmlc testfile.mxml
Everything worked fine.

Installing AIR
==============
there are two parts - the run time and the sdk.
I won't go into this suffice to say that it didn't work for me. The SDK procedure was more or less the same as installing the flex SDK...i.e. no installation per se. The instructions online were not very good and I never managed to confirm it worked or not.

What I will comment on is the AIR runtime. On the Adobe website I grabbed the AIR runtime installer. Unlike the SDKs, this is a bin file. You download it, make it executable (e.g. sudo chmod +x installer.bin) then execute it from a terminal with:
./installer.bin (or whatever the exact name is).

The installer said it installed correctly in Xubuntu so I grabbed a demo air application off a demo site. Double clicking the air application showed that the .air extension was recognised as an Adobe Air Application but no program was registered to deal with it. Later, I discovered you need to go to the command line, make it executable, and install it that way (or you might find an AIR Application Installer in your AppFinder). After installing there was no desktop launcher but it was listed under AppFinder.

Unfortunately, the application didn't do anything even though it installed properly. I decided to stick with Flex since that was working and ditch AIR. Air seemed too unfriendly at this stage. Uninstalling it was challenging because I couldn't find it listed in Synaptic and the AIR installer didn't trigger an uninstaller routine.

First, uninstall any applications for Air that you might have installed:
dpkg --list | grep -i AirAppName
I got an ugly long name returned which I then removed with:
sudo dpkg -r 'appname.in.quotes'

Then I removed the AIR runtime too:
dpkg --list | grep -i Adobe
returned something like adobeair1.0 which I removed with
sudo dpkg -r 'adobeair1.0'

FINAL THOUGHTS
==============
No doubt experienced linux users will not have the same issues I had. I found installing Flex was easy enough but it was more work than it should have been. If Adobe can distribute the flash runtime as a nice .deb for easy installation then the same should be so for other applications/sdks.

Getting AIR installed was just more effort than it was worth. I am sure at a later stage they will make it easier for users but for now I bet a lot of users will run into problems as I did. The big problem is the lack of detailed installation/removal instructions. Hopefully, if you get stuck you can at least get Flex installed using my tips above.

---

