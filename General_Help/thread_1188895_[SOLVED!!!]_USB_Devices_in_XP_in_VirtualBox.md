---
title: "[SOLVED!!!] USB Devices in XP in VirtualBox"
date: 2009-06-16
forum: General Help
---

### Post by sookoon on 2009-06-16
I searched the forums over the last several days, to get my USB devices to work again in XP in VirtualBox, and none of the seven forum posts that I found were able to help.  

Then I located ARSGEEK's solution, and it worked, the first time (I'm on Intrepid). 

This solution has been posted before on this forum, but it merits repeating, to help people walk past the non-working approaches.

I have pasted it below, because the link to the page works only sometimes. 

[http://www.arsgeek.com/2007/10/24/get-usb-devices-mounted-on-your-virtualbox-xp-machine-in-gutsy-ubuntu-710/](http://www.arsgeek.com/2007/10/24/get-usb-devices-mounted-on-your-virtualbox-xp-machine-in-gutsy-ubuntu-710/)

Additionally, I have made edits, marked [sookoon] that indicate what I had to add, to make it work.

----------------------------------------

vbox.pngThere’s nothing more frustrating than not being able to mount your USB devices in your virtual machines. Well, maybe there are lots of things that are more frustrating but this morning my inability to do something that should be simple, easy and fun was driving me nuts.

So I figured out how to do it. It’s not terribly pretty but here’s what you need to do.

First, Gutsy got rid of the previous versions of Ubuntu’s way of handling USB mounts by not using USBFS anymore. Doh. That’s an issue for Virtualbox and your virtual XP installs. So you’ll need to download and install the latest Vbox release, 1.5.2. Click on that link to download the .deb file. Save it on your desktop and then double click on it to install it.

For a quick and easy tutorial on using Virtualbox and installing a virtual XP instance, see UbuntuGeek.

Once you have your virtual XP machine running on your Gutsy host, it’s time to do a wee bit of hacking. Turn of your XP instance and let’s roll up our sleeves and get to work.


First, open a terminal session (Applications-> Accessories-> Terminal) and type in the following to edit a script file:

    gksudo gedit /etc/init.d/mountdevsubfs.sh

Once you’ve got that open in Gedit, type CTRL-F to search for a string. Search for ‘magic’ (sans quotes).

That should bring you to this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount –rbind /dev/bus/usb /proc/bus/usb

All those pound signs are comments. Remove them from the last four lines so you end up with this:

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount –rbind /dev/bus/usb /proc/bus/usb

[sookoon] if you don't see this list of commands at all, no problem, just copy and paste into the body.

Save the file and exit Gedit. Round one goes to the user!

Now we’re going to create a group called usbusers. Go to System-> Administration-> Users and Groups. Type in your password and then click the Manage Groups button. From there click the Add Group button and name it usbusers. Check off your username below. Exit these windows and round two goes to us.

Now we’ve got to change a file in udev. So, let’s gedit it and gedit over with. I’ll apologize for the bad jokes in a later post.

    gksu gedit /etc/udev/rules.d/40-permissions.rules

Again, CTRL-F to bring up the search dialog and search for ‘usbfs replacement’ (again, sans quotes). Once you find it, you should be looking at this:

    USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, MODE=”0664&#8243;

You’ll want to change it to this:

    # USB devices (usbfs replacement)
    SUBSYSTEM==”usb_device”, GROUP=”usbusers”, MODE=”0664&#8243;

[sookoon] if you don't see this list of commands at all, no problem, just copy and paste into the body.

Save your file and exit out of Gedit.

Now, the last bit of hackery which may or may not be required for you. It was for me. We’re going to add a mount to /etc/fstab for usb devices using usbfs.

    gksudo gedit /etc/fstab

At the bottom, add the following line:

    none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Save the file and exit Gedit. Phew! Now, the easiest way to get all of these changes working on your system is to restart it. So go ahead and do that and then I’ll see you back here in a few.

Back? Great. Time to plug in your USB device, whether it’s a thumb drive, an iPod or something else, plug it in and let Ubuntu detect it.

Now, we’re going to open up Virtualbox and make some changes to your XP machine BEFORE you start it up. So go to Applications-> System Tools-> Virtualbox and get it started up.

Highlight your XP machine (if it’s not the only instance of a virtual machine) and click the Settings button at the top of Virtualbox. You should now have a USB option on the left hand side of your settings. Click the add icon on the right hand side (see the pic below) and select the device from the list. In my example, it’s a 512MB memory key. Now click the Okay button.

Start up your virtual XP machine and you will see a notice pop up courtesy of Ubuntu about unsafe device removal. Nod your head sagely and let’s continue on. Once XP is up and running, it should automatically detect the new USB device, and do it’s best to install it. With my memory key, it was as simple as turning the virtual XP machine on and letting XP take care of it.

You may have to go to the Devices menu on your virtual machine (once it starts up) select USB Devices and then uncheck whatever it is you’re trying to mount.  Repeat the process, this time checking it off and it should mount if it didn’t automatically.

---

### Post by nolliecrooked on 2009-06-16
or you can just tick your username in the vbox section of Users and Groups.

---

### Post by meeples on 2009-06-16
opening virtualbox as root worked for me. :)

---

