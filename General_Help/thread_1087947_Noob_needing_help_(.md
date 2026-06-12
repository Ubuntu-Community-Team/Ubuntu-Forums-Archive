---
title: "Noob needing help :("
date: 2009-03-05
forum: General Help
---

### Post by Katashi on 2009-03-05
So I am new to Ubuntu. I love the idea and concept of Linux. But being as I have grown up on and learned Windows so much, Linux is like looking at Japanese instructions. I have two basic problems that are keeping me from furthering my adventure into the Linux world. First off, I only have a wireless Linksys WP110 PCI card. I have found the driver for it but for the life of me I cannot get the driver installed. Secondly, I can't install the driver for my graphics card. Again I've found the driver but have no idea how to install it. It tells me that it has to be run from the root, when I go to the root it says it cannot be opened. I haven't successfully done anything in the command prompt besides changing directories. I've read about the package called ndiswrapper, but again I can't get it installed. It doesn't show up in my application loader. I've also read about Beryl packages, and again.....yeah.... Any help is much appreciated. Thanks in advance. 

NIC- Linksys WP110
Video Card- Nvidia Geforce 6200
Ndiswrapper- 1.54
Beryl- 0.2.1

---

### Post by jcbeas on 2009-03-05
try this link it should help you
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by cb951303 on 2009-03-05
Go to Menu > System > Admin > Hardware Drivers
to install Nvidia graphic drivers :popcorn:

---

### Post by Katashi on 2009-03-05
> **cb951303 said:**
> Go to Menu > System > Admin > Hardware Drivers
to install Nvidia graphic drivers :popcorn:

I tried that, but it doesn't list the driver I downloaded and the two drivers it does list won't install correctly. I didn't see an option to import a file to use either.

---

### Post by cb951303 on 2009-03-05
> **Katashi said:**
> I tried that, but it doesn't list the driver I downloaded and the two drivers it does list won't install correctly. I didn't see an option to import a file to use either.
you don't need to download drivers yourself. Hardware Drivers will do it for you. The list should work. What does it say as error?

---

### Post by Katashi on 2009-03-05
> **cb951303 said:**
> you don't need to download drivers yourself. Hardware Drivers will do it for you. The list should work. What does it say as error?

I don't have my internet working, first thing I tried to do was update my package list. But it can't without the internet. I got the ndis package to install somehow. I'm not sure why it didn't work before. But I don't know where to go from here either to enable and connect my card. As for the video card driver, it doesn't give me an error through the Hardware Drivers. It just says it is loading and then disappears, when I try to turn on the graphics option for higher graphics on the desktop it says they cannot be turned on.

---

### Post by cb951303 on 2009-03-05
> **Katashi said:**
> I don't have my internet working, first thing I tried to do was update my package list. But it can't without the internet. I got the ndis package to install somehow. I'm not sure why it didn't work before. But I don't know where to go from here either to enable and connect my card. As for the video card driver, it doesn't give me an error through the Hardware Drivers. It just says it is loading and then disappears, when I try to turn on the graphics option for higher graphics on the desktop it says they cannot be turned on.

ah that's why you can't install video drivers. it needs internet.

---

### Post by Therion on 2009-03-05
Any possibility of connecting to the Internet with a cable so you can at least download your updates?  That might help get your wireless working.

---

### Post by Katashi on 2009-03-05
> **Therion said:**
> Any possibility of connecting to the Internet with a cable so you can at least download your updates?  That might help get your wireless working.

I wish there was, the only hard lines are in the room across the apt in my roomates room. I can't exactly bring my entire desktop over there lol.

---

### Post by Katashi on 2009-03-05
Even though I installed the Ndiswrapper packages, it's not in the Synaptic manager. I don't see it in my home directory either so I'm at a loss here. I tried running the install cd for the NIC after I installed Ndiswrapper with no luck. *sigh*

---

### Post by Therion on 2009-03-05
> **Katashi said:**
> 

I wish there was, the only hard lines are in the room across the apt in my roomates room. I can't exactly bring my entire desktop over there lol.
Step 1.  Get a looong ethernet cable, they're cheap.

Step 2.  Observe Roomie.  Wait till he goes to sleep or, (my preferred methodology): Crack him over the noggin with the lamp off the coffee table.

Step 3.  Connect cable and download updates.

Joy!

---

### Post by boof1988 on 2009-03-05
> **Katashi said:**
> Even though I installed the Ndiswrapper packages, it's not in the Synaptic manager. I don't see it in my home directory either so I'm at a loss here. I tried running the install cd for the NIC after I installed Ndiswrapper with no luck. *sigh*

I just wanted to mention (for reference) that there is a GUI available for ndiswrapper.

[ndisgtk](http://linuxappfinder.com/package/ndisgtk)

IIRC it can be started either from a menu option or

in terminal...
```
gksu ndisgtk
```

Then the user inputs the non-native drivers and ndisgtk does the configurations...  Pretty sweet... If you ask me...

Someone please correct this if I'm wrong.

---

### Post by Katashi on 2009-03-05
> **boof1988 said:**
> I just wanted to mention (for reference) that there is a GUI available for ndiswrapper.

[ndisgtk](http://linuxappfinder.com/package/ndisgtk)

IIRC it can be started either from a menu option or

in terminal...
```
ndisgtk
```

Then the user inputs the non-native drivers and ndisgtk does the configurations...  Pretty sweet... If you ask me...

Someone please correct this if I'm wrong.

I can try that. I installed that also but didn't see it while I was looking over things. What are the non-native drivers and how do I input them? Is it syntax? or is it a GUI?

*Update* I went into the terminal and entered ndisgtk and it said Root or Sudo privileges required

---

### Post by uvmedraco on 2009-03-05
Katashi it looks like youll have to move ur pc easiest way unless you have a silly pc with too many pieces, u shudda installed on a laptop a lot easier lol

---

### Post by Katashi on 2009-03-05
Ok, so reading on another site I found that sudo -i let you run on the root. I got ndisgtk to work now but the .inf files on my driver don't work.

---

### Post by boof1988 on 2009-03-05
> **Katashi said:**
> I can try that. I installed that also but didn't see it while I was looking over things. What are the non-native drivers and how do I input them? Is it syntax? or is it a GUI?

From what I understand, ndiswrapper is used to install (wrap?) the Windows drivers for use in linux.  So if there are no linux drivers available (or they are not wanted), then ndiswrapper may provide a way to work around this.

ndisgtk is a graphical interface to do the "dirty" work (the commands that would normally be input in the terminal).

Attached are a couple screen shots of ndisgtk.  One shows the window without the driver installed.  The other one shows the driver installed (I think the language is in german, but you get the idea of how it looks).  

> **Katashi said:**
> *Update* I went into the terminal and entered ndisgtk and it said Root or Sudo privileges required

Yeah... sorry... I forgot to include the part of the command to execute the ndisgtk with proper privileges (use gksu or whichever applies for you os):

```
gksu ndisgtk
```

Hope this helps some.

---

### Post by boof1988 on 2009-03-05
> **Katashi said:**
> Ok, so reading on another site I found that sudo -i let you run on the root. I got ndisgtk to work now but the .inf files on my driver don't work.

I'm sorry I don't know how to proceed further form here.  Hopefully someone else will join in that has the requisite knowledge.

---

### Post by Katashi on 2009-03-05
Success! I found the linux driver I needed and installed it just fine. But the hardware isn't being detected...

---

### Post by boof1988 on 2009-03-05
> **Katashi said:**
> Success! I found the linux driver I needed and installed it just fine. But the hardware isn't being detected...

Which hardware (video card or network card)?

---

### Post by Katashi on 2009-03-05
> **boof1988 said:**
> Which hardware (video card or network card)?

The NIC card. I haven't messed with the video card anymore till I get the internet working and I can update the system.

---

### Post by Katashi on 2009-03-05
Making baby steps. I have the NIC driver installed, but it says the hardware isn't on. I checked the lspci and it's listed in there. So now it at least knows it's there.

---

### Post by Katashi on 2009-03-06
So I still haven't been able to get any kind of connection going. I've looked into some things like the Network Manager and Wifi-radar. I've had no luck so far. I can't even get the Network Manager to start. It's installed already since I'm using the 8.10 system, but when I tried to start it with "sudo nm-applet" it says it cannot aquire the NetworkManagerUserSettings service because it is already taken. I went into the Services and there's nothing listed there as Network Manager. It's supposed to start on boot up. But it's not there.

Error Message...eric@eric-desktop:~$ sudo nm-applet
[sudo] password for eric: 

** (nm-applet:6038): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6038): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Katashi on 2009-03-07
*sigh* really nobody can help?

---

