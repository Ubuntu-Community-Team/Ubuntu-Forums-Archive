---
title: "How to FAX in Ubuntu"
date: 2009-01-28
forum: General Help
---

### Post by frogotronic on 2009-01-28
Hello,

  If you're like me, figuring out modems and faxing on a laptop/desktop in Ubuntu is a bit frustrating to say the least.  I know there are many ways to do this (as with all things in Linux).  Here's how I got it to work.

Step 1:  Go to [LINUXANT]("http://www.linuxant.com/drivers/modemident.php") (no...I don't work for them) and buy their Linux driver.  Yes, you can work this out by yourself given an infinite amount of time, but, really, for $20 this will save you DAYS of time.  Besides, I don't have a problem with paying a nominal fee for a good product.  Navigate to the modem driver install page and use their automated installer.  Once finished, restart your machine and then purchase a license (they'll provide instructions).  The free driver DOES NOT fax - only 14.4 Kbps data.

Step 2:  Configure your modem via System>Administration>Network.  You'll enter in the dial-up #'s for your service provider, etc.

Step 3:  Add yourself to the users that can send & receive faxes: System>Admin>Users and Groups>select your username>properties>user privileges>tick the send and receive fax

Step 4:  ([taken from this post]("http://ubuntuforums.org/showpost.php?p=2027377&postcount=2"))

   1. Install and configure your modem using the wiki ([https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)).  ***In my example (our case) we've installed the modem via the Linuxant driver***
   2. Use Synaptic to install eFax-gtk.
   3. Go to Administration -> Printing
   4. Double-click New Printer.
   5. Select network printer, HP JetDirect
   6. Type 'localhost' in the Host box.
   7. Set the port to 9900.
   8. Click Forward.
   9. Select 'Raw' as the printer manufacturer.
  10. Click on 'queue' to select it and then click Forward.
  11. Type 'eFax' in for the Name instead of queue.
  12. Click Apply.
  13. Go to Applications -> Office -> eFax-gtk.
  14. Select 'Socket' as the fax entry method, then close eFax.


To send a fax from Open Office, just click File -> Print and select 'eFax' or whatever name you gave the printer you installed above and click 'Print'. EFax will open a little dialog box prompting you for the fax number to which to send the fax.

Step 5:  You should now be able to fax.


For me it was this easy - hope this helps.   :o

---

### Post by Ralph L on 2009-03-06
Thanks for the write up cement_head.  I am trying to get a print-to-fax function going on a Dell Latitude D610 laptop using intrepid.  Hoping that it would work like hardy I tried to follow your instructions.  However, after entering localhost, 9900, and clicking forward a window comes up asking if I want to use a printer or fax.  I tried both of them, but neither allowed me to enter a printer manufacturer.  Rather there was a pull down menu with printer manufacturers listed.  I selected Generic and clicked Forward. A list of models came up including one named Raw Queue.  I selected it and its driver was listed as Generic Raw Queue. I clicked Forward and got window asking for Printer Name, Description (optional) and Location (optional).  I typed in eFax, clicked Apply and got the following error message: "There was and error during the CUPS operation: "client-error-not-possible'". I backed up and tried selecting printer manufacturers like HP, picked a model, and got the same error message.  In fact no matter what option I selected I always ended up with the same error message.

Any help would be appreciated.

Ralph

---

### Post by frogotronic on 2009-03-06
Maybe this post will help?

[http://forum.soft32.com/linux/CUPS-error-client-error-SOLVED-ftopict440720.html](http://forum.soft32.com/linux/CUPS-error-client-error-SOLVED-ftopict440720.html)

Let me know if not and we'll try something else.

- CH

---

### Post by Ralph L on 2009-03-20
cement head

I got efax to work as described in the attachment to this post;  [http://ubuntuforums.org/showthread.php?t=1086059](http://ubuntuforums.org/showthread.php?t=1086059) , the last part on creating a fax-to-printer.

Now I am having a problem using efax with an MCI phone card.  See [http://ubuntuforums.org/showthread.php?t=1101645](http://ubuntuforums.org/showthread.php?t=1101645)

Any further help is greatly appreciated.

Ralph

---

### Post by frogotronic on 2009-03-21
Hi Ralph,

  I think that might be eFAX-gtk specific - you might try their support forums on sourceforge: [http://sourceforge.net/forum/?group_id=109982](http://sourceforge.net/forum/?group_id=109982)

  Let me know if they come up with a solution.

- CH

---

### Post by frogotronic on 2009-06-17
[QUOTE=Jian726]I read your very helpful post on getting faxing to work. I have a Zoom Modem USB external model 3095. I purchased it because it was supposed to work with Linux. When I attempted to install the driver for it, I got an error because my system is 64 bit. The drivers supplied were 32 bit. Will your methodology work for me?[/QUOTE]


Hi, Linuxant drivers will build on the 64 bit systems.  If they don't have a pre-complied binary ( [http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php) ) you'll have to build from source, which isn't a problem at all.

As to ZOOM Modem USB external model 3095, according to their trouble shooting:

[B]If these drivers will not install properly on your system, you can find additional information on
Linuxant&#8217;s website at [http://www.linuxant.com](http://www.linuxant.com). From here go to Drivers, then Conexant Modems,
then DGC (modem) driver.[/B]

Try this link: [http://www.linuxant.com/drivers/dgc/install.php](http://www.linuxant.com/drivers/dgc/install.php) 

Good Luck

---

### Post by arnoldjames on 2009-06-23
Using 8.10, efax-gtk setup:
modem tab - the modem is "ttyACM0" in /dev/ for a USB modem.  The rest works as posted above.  You may need to have a look through /dev/ and see where the system located your modem on plug-in to see where your's might be.

---

### Post by bob brazie on 2009-07-05
Hello, I am running the file cnxtinstall.run in terminal which I downloaded from the driver web site to try to determine what modem is installed on my system to download the correct drivers.

After running it gives me the password number. When it comes time to enter the information on their web site it asks me for a user-name which is the root if I understand correctly. I enter: bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run

The web site will not take this and asks for both again and again.

Could you help with a proper root?

Thanks in advance. (Bob, new to ubuntu)

---

### Post by frogotronic on 2009-07-06
> **bob brazie said:**
> Hello, I am running the file cnxtinstall.run in terminal which I downloaded from the driver web site to try to determine what modem is installed on my system to download the correct drivers.

After running it gives me the password number. When it comes time to enter the information on their web site it asks me for a user-name which is the root if I understand correctly. I enter: bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run

The web site will not take this and asks for both again and again.

Could you help with a proper root?

Thanks in advance. (Bob, new to ubuntu)

Hi Bob,

BEFORE running the script, close firefox (all windows).  When you run the script as root (sudo) it will automagically enter the username & password.  Post back if you have a problem.

- CH

---

### Post by yodawise on 2009-10-13
I was able to configure a Zoom 3095 USB fax modem on Ubuntu 9.04. I installed the driver hsfmodem-7.80.02.03full from the dell website and followed the instructions in the INSTALL file.

After I rebooted, I used Efax-gtk and selected *modem* in the device where */dev/modem* was symlinked to */dev/ttyACM0*.

I was able to send a fax successfully. The 2nd attempt to send a fax failed. I traced the problem down to /dev/ttyACM0 having disappeared.

I reboot the system which resulted in */dev/ttyACM0* to be regenerated. I created the symlink to */dev/modem* and was able to send two test faxes and then */dev/ttyACM0 *disappeared again.

Any ideas what causes */dev/ttyACM0* to disappear?  Thanks in advance.

---

### Post by frogotronic on 2009-10-13
Hi Yodawise,

  Try 

sudo hsfconfig

  And answer the questions.  If that doesn't work, that'd be a question for Linuxant.

- CH

---

### Post by mike555 on 2009-10-13
Why not just use a faxing service , there are a bunch , even free ones ...     [http://faxzero.com/](http://faxzero.com/)

---

### Post by yodawise on 2009-10-13
I will move this post into a new thread titled "Zoom 3095 USB fax mode: Why is /dev/ttyACM0 is removed". 

Regards.

Update1:
Thanks all for you suggestions and time. 

The title of the new thread is: **Zoom 3095 USB fax modem: Why  cdc_acm and /dev/ttyACM0 are removed?   **[http://ubuntuforums.org/showthread.php?t=1290339](http://ubuntuforums.org/showthread.php?t=1290339)

Update2: The final title is:
                                  **[SOLVED] Zoom 3095 USB fax modem/VirtualBox conflict: Why  /dev/ttyACM0 is removed?**             
             
[http://ubuntuforums.org/showthread.php?p=8099066#post8099066](http://ubuntuforums.org/showthread.php?p=8099066#post8099066)

---

### Post by frogotronic on 2009-10-13
> **mike555 said:**
> Why not just use a faxing service , there are a bunch , even free ones ...     [http://faxzero.com/](http://faxzero.com/)

1) Because to fax from a phone modem (in your laptop) doesn't require an internet connection - just a phone jack.

2) Not all of us want to upload sensitive information to a third party's server.

- CH   [-X

---

