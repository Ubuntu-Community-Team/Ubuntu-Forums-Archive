---
title: "Laptop Keeps Returning to Maximum Brightness Setting on Boot"
date: 2015-09-10
forum: Desktop Environments
---

### Post by oldefoxx on 2015-09-10
HP Envy 17-K073ca laptop
Ubuntu 14.04.2 Install
Classic Gnome Interface.  Using Metacity
Adjusted Brightness & Lock settings under System Tools >> Preferences >> Brightness & Lock to about 83% and No Lock.
Brightness goes back up to 100% on next boot.  Just too bright.
What's the fix?
Short, right?

---

### Post by mc4man on 2015-09-10
See that here in an ubuntu session (unity), brightness setting survives a log out/in but not a reboot. 
Doesn't seem to write a value anywhere in dconf (gsettings) so not sure how it would know what to set on fresh boot.
(if you can find a setting then a startup script could resolve.
Seems like a bug in 14.04
Edit: tried in 15.10 - setting survives a reboot
In 15.10 it work with & because of systemd. upstart will always return screen to max brightness on fresh boot.

---

### Post by oldefoxx on 2015-10-04
I found elsewhere that there is a way to deal with this.  You use ```
sudo apt-get install xbacklight
```

Then to set the brightness as a percentage, from 0 to 100, You do```
xbacklight -set 35
```
as an example.

xbacklight will also respond to -inc and -dec arguments, like```
xbacklight -inc 5
xbacklight -dec 5
```which means if you can tie these to hotkeys. you could refine your screen brightness on the fly.  In fact, if you make the values slightly different between -inc and -dec, like```
xbacklight -inc 5
xbacklight -dec 6
```you could fine-tune your settings by jiggling between the two keys.

I haven't looked into making hotkeys yet, don't know what hotkeys are in use right now, so this is just an idea.

**THE NEXT STEP DOES NOT WORK**  None of the added commands below performed on reboot.  I'm leaving what's described below as something NOT to try doing.

 As super user, edit the /etc/rc.local script file and add these commands before the exit 0 line.  This is what I am adding:```
xbacklight -set 35
apt-get -qq update
apt-get -qq -y dist-upgrade
apt-get -qq -y autoremove
/usr/bin/update-manager
updatedb
``` 
All the added commands are already there, and the xbacklight utility should have been installed.  If you don't have a brightness issue, either comment out the xbacklight line or remove it.  If I con't come back here, assume it worked and I just moved on.

**WHAT DOES WORK TO  DATE**  Use the text editor and copy this into a text file (I named mine "update") and save it to your Desktop, Home Folder, or both.  Change the Permissions on the file to allow executing file as a program.  Go to the upper right corner of your file manager and under its Preferences/Behavior settings, check the Execute box.  Here is the code that works:```
#!/bin/sh
xbacklight -set 30
echo "\n\n\n"
echo "             SOFTWARE UPDATE SCRIPT"
echo "             This will take several minutes to complete."
echo "             To see all the action, remove the '-qq's from script."
printf "             "
sudo apt-get -qq update
sudo apt-get -qq -y dist-upgrade
sudo apt-get -qq -y autoremove
sudo /usr/bin/update-manager
sudo updatedb
```

This is frustrating.  I've followed several links in an effort to find one that would let me run a series of bash commands or a script file as root just one time when there is a system reboot. but none of them work.  This included putting the executable script file in /etc/init.d/ and following up with update-rc.d to create the necessary links, to adding the commands to /etc/rc-local as described above, to adding a @reboot /etc/init.d/update.sh to my crom schedule while logged in as root.  Nothing takes.

So I guess I will leave the job of automating the script running as root during or after a reboot to someone else to resolve and explain.  But with the update, I can get the screen dimming after every reboot by picking Run as my choice rather than Run in Terminal.  In Run, the sudo commands are simply skipped.

---

### Post by oldefoxx on 2015-11-12
The repeat problem of the screen being too bright when I start up or reboot really got to me.  So I wrote my first bash script(s) to deal with the problem by clicking on it or them and having them do their thing.  The next step was to automate the update/upgrade process in another script file or two.  It was one to start with, but I had to split it into two files, update and upgrade, because gimp2 was somehow particular as to what it took to milk consistent results from it.

So now I have three script files that work for me on a daily or more frequent basis.  And what works for me might work for you.  All you need to do is get the file(s), place them on your Desktop or in your Home Folder, and make sure under the File's Properties/Permissions that the Execute box is checked.  That's pretty much it.  The remaining thing is to enable your GUI File Manager to execute a script file from the Desktop, or enter a Terminal and type the following:```
cd Desktop      # if you put them on the Desktop
./light         # if you want to adjust the screen brightness
./update        # to update/upgrade your software
./upgrade       # called by update, but can be run separately to just update and install grub

```
The three script files can be downloaded using the following links:
[https://my.pcloud.com/publink/show?code=XZEhzzZNK2frwjqkHVsU6iBgtShpfbXOTR7](https://my.pcloud.com/publink/show?code=XZEhzzZNK2frwjqkHVsU6iBgtShpfbXOTR7)
[https://my.pcloud.com/publink/show?code=XZAhzzZQkI21jI2Fiyu532jC04ivYJXPklX](https://my.pcloud.com/publink/show?code=XZAhzzZQkI21jI2Fiyu532jC04ivYJXPklX)
[https://my.pcloud.com/publink/show?code=XZGhzzZ5pzEbTnYXrkwsLMCPo8frzuzlPb7](https://my.pcloud.com/publink/show?code=XZGhzzZ5pzEbTnYXrkwsLMCPo8frzuzlPb7)

I intend to add more helpful script files in the future.  There are a number of problems I am in the process of resolving in this manner.  The leading ./ in front of the script name is important, though it's also possible to use ~/ instead.

The script light needs xbacklight installed/  If it isn't, you can install it from a terminal by entering "sudo apt-get install xbacklight", without the quotes.  The scripts don't recognize you either, so enter these two commands in the terminal:```
sudo chown <your userid> light update upgrade
sudo chmod +x light update upgrade
```
Do these from the same folder where these files are found.  If the Desktop, begin with "cd ~/Desktop" on a line of its own.

There are many very useful files and applications available.  I get many of the ones I like with one or two commands in a terminal window.  Here are some suggestions: ```
sudo apt-get install dkms cream leafpad Xfburn gparted dconf-tools gnome-tweak-tool unity-tweak-tool gimp
```.

There are two other common sources for applications.  The first is Ubuntu Sodtware Center, where you can locate them by name or purpose, whatever you type in the small box in the upper right corner.  The other source is the internet, where you search by name or purpose.  You want applications for Debian or Ubuntu, as these come in .deb files.  Click on a ,deb file, and the Ubuntu Software Center will open up and offer you the choice of installing it or upgrading what you already have installed.  It will also remove what is installed if you change your mind later.

The internet brings you more choices, such as alternate web browsers with names like seamonkey, opera, google chrome-stable, and Slimboat and/or Slimjet.  These can be downloaded and installed easily.  Having choice of what to use for what purpose can be very helpful at times.  You can also install wine, or better yet, install a VM Manager like VMware or Oracle's Virtualbox, which make it possible to run an alternate iperating system and its applications, possibly games, while having some version of Linux running as your primary operating system.  The Ubuntu Software Center does offer you a chance to get Chromium. which is very much like Google's Chrome.  The same rules for changing setup options, adding add-ons or plug-ins apply pretty much to Chrome, Chromium, and Slimjet, since they all make use of the Blink webkit and Chromium Project guidelines.

Programming with Linux is a definite option, and you have choice as to what you learn and do in this environment.  I'm learning PureBasic and different approaches to writing scripted processes myself right now.  Others learn and work with C/C++, Python. Ruby, Perl, assembler, and possibly other alternative langages that exist for Linux.  Each of us does our own thing and go at our own pace, but share ideas and insights on various forums.  There isn't much mney in it for most of us, but learning for learning's sake has a way of bringing its own rewards.  Once you get hooked, it's hard to stop.  More satisfying than playing games that really amount to nothing in the end.

---

