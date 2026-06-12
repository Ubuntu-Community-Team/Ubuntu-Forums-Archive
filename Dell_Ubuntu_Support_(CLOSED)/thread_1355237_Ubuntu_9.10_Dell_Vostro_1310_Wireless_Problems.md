---
title: "Ubuntu 9.10 Dell Vostro 1310 Wireless Problems"
date: 2009-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cmpgm88 on 2009-12-14
Greetings!
 
I recently installed Ubuntu via the Wubi Installer.  There is one slight problem, though.  My wireless card does not work.  I installed the "BCMWL Kernel" package and the "Windows Wireless Card Driver" package, and that helped slightly.  You see, I can detect a wireless network, yet cannot detect an IP address.  When I manually input the IP address, it cannot access anything beyond the gateway IP (192.168.1.1 on my wireless web router).
 
I'm using a Dell Vostro 1310, and using a 1395 wireless card manufactured by Broadcom.
 
What should I do?
-Chris N.

---

### Post by bobcollard on 2009-12-14
> **cmpgm88 said:**
> Greetings!
 
I recently installed Ubuntu via the Wubi Installer.  There is one slight problem, though.  My wireless card does not work.  I installed the "BCMWL Kernel" package and the "Windows Wireless Card Driver" package, and that helped slightly.  You see, I can detect a wireless network, yet cannot detect an IP address.  When I manually input the IP address, it cannot access anything beyond the gateway IP (192.168.1.1 on my wireless web router).
 
I'm using a Dell Vostro 1310, and using a 1395 wireless card manufactured by Broadcom.
 
What should I do?
-Chris N.
Go to the System menu and open Hardware Drivers.  From there you will need a network connection like an Ethernet cable to download the proper driver.  Reboot and it should work if your settings are right in Manage Connections.

---

### Post by cmpgm88 on 2009-12-14
alright..... I pulled up the hardware drivers screen, and this is what I got. (please see the attached screenshot)

---

### Post by loveandequality on 2009-12-14
> **cmpgm88 said:**
> alright..... I pulled up the hardware drivers screen, and this is what I got. (please see the attached screenshot)
It looks like your Wi-fi is not turn on. Check that in OS & computer as in the wireless button.

---

### Post by cmpgm88 on 2009-12-15
> **loveandequality said:**
> It looks like your Wi-fi is not turn on. Check that in OS & computer as in the wireless button.
 
I can assure you that the wirless works in Windows (that's what I'm using now, to type this response) and that the wireless switch located on the side of the laptop is on.
 
This may, or may not be significant, but I've noticed that the process BCMWLTRY.EXE seems to have some sort of impact on the performace of the wireless...

---

### Post by fibercode on 2009-12-15
Can you post the results of this command:

lspci

Broadcom is normally good with Linux driver support. But I could not find a 1395 chipset on their site.

---

### Post by cmpgm88 on 2009-12-15
I figured it out!

I uninstalled the Windows Wireless Drivers I had installed, and it worked perfectly! (most likely due to the BCMWL Kernel)


Thank you for your help!

With Ubuntu Love,
Chris N.

---

### Post by cmpgm88 on 2009-12-15
Oh! and one other thing!

Where are the desktop background files located?

---

### Post by bobcollard on 2009-12-15
> **cmpgm88 said:**
> Oh! and one other thing!

Where are the desktop background files located?
Right click on the desktop and "Change Background"  You can remove all but one picture and add your own.

---

### Post by cmpgm88 on 2009-12-15
I'm sorry... I'm not being clear...

Where are the default image files that you see when you open up the appearance dialog?  (as in a folder location)

---

### Post by fibercode on 2009-12-16
> **cmpgm88 said:**
> 
Where are the default image files that you see when you open up the appearance dialog?  (as in a folder location)


/usr/share/backgrounds

---

### Post by bobcollard on 2009-12-16
> **fibercode said:**
> /usr/share/backgrounds
Thanks Fibercode, mine are the ones I put in and yours are the original set location.

---

### Post by cmpgm88 on 2009-12-16
> **fibercode said:**
> Can you post the results of this command:

lspci

Broadcom is normally good with Linux driver support. But I could not find a 1395 chipset on their site.

The result was piped to a text file, which is attached... let me know if there's a problem.

---

### Post by bobcollard on 2009-12-16
> **cmpgm88 said:**
> The result was piped to a text file, which is attached... let me know if there's a problem.
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
You may install drivers for this controller using: 	 	 	 	 	  *sudo apt-get install b43-fwcutter*

---

### Post by fibercode on 2009-12-17
As Bobcollard pointed out your wireless chipset is Broadcom Corporation BCM4312. 

You might want to make a note of that for a future reference.

If your wireless works now, I would not touch it.

Just in case you ever need it, here is a step by step tutorial how to install the official Broadcom drivers for BCM4312:

[http://dimitar.me/?p=728](http://dimitar.me/?p=728)

---

### Post by cmpgm88 on 2009-12-18
> **fibercode said:**
> As Bobcollard pointed out your wireless chipset is Broadcom Corporation BCM4312. 
 
You might want to make a note of that for a future reference.
 
If your wireless works now, I would not touch it.
 
Just in case you ever need it, here is a step by step tutorial how to install the official Broadcom drivers for BCM4312:
 
[http://dimitar.me/?p=728](http://dimitar.me/?p=728)
 
 
 
To say it works is a bit over-the top... It works after re-booting multiple times, and typing in the correct password about three times the amount of reboots... :(
 
I'll try your method of installation.

---

### Post by cmpgm88 on 2009-12-19
okay..........  I don't understand what I'm doing..... I am not doing this right.... I'm probably going to need something simpler......


I attempted to use bobcollard's method, but it seemed to have no effect, and I can't follow the step-by-step tutorial as listed on the website....



What do I do?

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> okay..........  I don't understand what I'm doing..... I am not doing this right.... I'm probably going to need something simpler......


I attempted to use bobcollard's method, but it seemed to have no effect, and I can't follow the step-by-step tutorial as listed on the website....



What do I do?
After you installed by "My method" All you needed to do was right click on the Internet connection in your task bar,  Edit Connections and go to  Wireless, then (Add) your information.  Sorry if we are not making this clear enough.  We are not aware of your capabilities.  Did it ask you when you used the Terminal if you wanted to install y/n?  I hope you entered (y)

---

### Post by cmpgm88 on 2009-12-19
No, it did not ask me to install it, but it has appeared to have installed the package.  You can see the output in the attached file.

I still have the Windows Wireless Drivers: BCMWL5 and netrtle installed...

Could that be part of the problem?

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> No, it did not ask me to install it, but it has appeared to have installed the package.  You can see the output in the attached file.

I still have the Windows Wireless Drivers: BCMWL5 and netrtle installed...

Could that be part of the problem?
Running windows you will lose your wireless if you  remove them.  They should have no effect on Linux anyway.  There are some systems that will run using the Windows drivers.  I am not sure about Ubuntu, perhaps someone else might know.

---

### Post by cmpgm88 on 2009-12-19
> **bobcollard said:**
> Running windows you will lose your wireless if you  remove them.  They should have no effect on Linux anyway.  There are some systems that will run using the Windows drivers.  I am not sure about Ubuntu, perhaps someone else might know.

I'm sorry, let me be more clear.

I am still have the "Windows Wireless Drivers" installed (ndiswrapper).   And, currently, the driver I have installed is callled "BCMWL15" From /host/drivers/network/R189335

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> I'm sorry, let me be more clear.

I am still have the "Windows Wireless Drivers" installed (ndiswrapper).   And, currently, the driver I have installed is callled "BCMWL15" From /host/drivers/network/R189335
Go to menu/System/Hardware Drivers and see if any of them are Active.  If the ones for Broadcom STA is active you can deactivate all the others.  Otherwise, that is the one you need to be active, it is the one supporting your wireless.

---

### Post by cmpgm88 on 2009-12-19
I see a Broadcom STA Driver, yet I cannot seem to activate it (every time  click activate, it asks me for my password, and then changes nothing)

---

### Post by cmpgm88 on 2009-12-19
I've attached a screen-shot to show you.

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> I see a Broadcom STA Driver, yet I cannot seem to activate it (every time  click activate, it asks me for my password, and then changes nothing)
If you get a download you need to restart your computer to activate it.

---

### Post by cmpgm88 on 2009-12-19
I have restarted many times, with no difference.

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> I have restarted many times, with no difference.
Have you created your wifi account in Edit Connections, if so, check to make sure all entries are correct.  It may be the difference of having Automatic DHCP or Automatic DHCP with Addresses Only in the IPv4 settings.  Or leaving IPv6 Settings with Ignore or Automatic.

---

### Post by cmpgm88 on 2009-12-19
well......... it works right now..... Currently set to "Automatic DHCP" under IPv4, and Ignore under IPv6.

The only problem with it is that I have to type the password repeatedly to make it connect, which can be ignored, but it's VERY annoying.

---

### Post by bobcollard on 2009-12-19
> **cmpgm88 said:**
> well......... it works right now..... Currently set to "Automatic DHCP" under IPv4, and Ignore under IPv6.

The only problem with it is that I have to type the password repeatedly to make it connect, which can be ignored, but it's VERY annoying.
I'm not sure why you would need to type it more than twice if you were running KDE, but you are in gnome.  KDE has a wallet where passwords are kept and you have to run it to use some programs.  I haven't found that in Ubuntu.

---

### Post by cmpgm88 on 2009-12-19
> **bobcollard said:**
> I'm not sure why you would need to type it more than twice if you were running KDE, but you are in gnome.  KDE has a wallet where passwords are kept and you have to run it to use some programs.  I haven't found that in Ubuntu.
Yes, there is a password manager (Applications--> Accessories---> Passwords and Encryption Keys)


It didn't have the Read attribute marked, so that might be the problem.. I'm not going to restart it now, but I will tell you how it goes soon.

---

### Post by cmpgm88 on 2009-12-20
No luck... I still have to type the password in repeatedly in order for it to work!
 
Isn't there some way to simply turn on the laptop, and have it connect to the (wireless) internet automatically?

---

### Post by bobcollard on 2009-12-20
> **cmpgm88 said:**
> No luck... I still have to type the password in repeatedly in order for it to work!
 
Isn't there some way to simply turn on the laptop, and have it connect to the (wireless) internet automatically?
It depends upon the Distribution.  I'm currently using Linux Mint 8 Helena x64,   It is based on  Debian and Ubuntu with a few extras like a nice menu and well supported.  I am using the Gnome version and it does everything at startup.  Another two distributions I have on my computer are Kubuntu 9.10 and Fedora 12, both KDE x86_64 and they require logins for everything from network wifi to e-mail browsers and even the music player.  That's KDE for you.  But you get nice features that do other things.  It's a trade off.  BTW (by the way) all of these distributions have to have the drivers added, you cannot get away from that.  If you consider this solved please Edit the Subject of your first entry and add [Solved]  this is so others may benefit from our solution or skip over it if they wish to.

---

### Post by cmpgm88 on 2009-12-20
So you're saying that there's no atumated way to sign into a wireless network under Ubuntu 9.10?

Is the reason I have to enter my password numerous times (sometimes having to re-connect) just to access the internet also an effect of Ubuntu?

---

### Post by bobcollard on 2009-12-20
> **cmpgm88 said:**
> So you're saying that there's no atumated way to sign into a wireless network under Ubuntu 9.10?

Is the reason I have to enter my password numerous times (sometimes having to re-connect) just to access the internet also an effect of Ubuntu?
I believe so.  I'm not a programer nor a representative of the forum, just a user like you.  If you are willing to experiment, I'd recommend Linux Mint.  It is no harder to download and burn to a cd than Ubuntu and far easier to use.  This is only my opinion.   Choose 32 bit or 64 bit depending upon the condition of your computer.   If you want to continue this discussion off forum here is my address : [EMAIL="bobcollard@sbcglobal.net"]bobcollard@sbcglobal.net[/EMAIL]

---

### Post by fibercode on 2009-12-22
> **cmpgm88 said:**
> So you're saying that there's no atumated way to sign into a wireless network under Ubuntu 9.10?

Is the reason I have to enter my password numerous times (sometimes having to re-connect) just to access the internet also an effect of Ubuntu?

Ubuntu 9.10 (or any Ubuntu I have used since 7.04) can connect to a wireless access point automatically on boot.

Your driver does not work properly! That is why you are experiencing this.

I gave you a link with a tutorial how to install the native Linux Broadcom driver. This will fix all your issues.

Is there a problem following it?

---

### Post by cmpgm88 on 2009-12-25
YAY!!!!!!!!!!! It worked!

The only thing is that you understand what you're doing while you're doing it, and not just blindly following the steps.

For example, when an echo command didn't pipe to the proper file, I used the command "sudo gedit (insert file name)" and added whatever was "echoed" to the end of the file.

Thanks a bunch!

---

