---
title: "USAA Bank website doesn't like linux"
date: 2009-05-11
forum: General Help
---

### Post by mauro24 on 2009-05-11
I've been using ubuntu 9.04 for a month, and i'm loving it. I got security, amsn, and the quickness of linux.  The only problem that holds me back from switching to ubuntu fully is my bank. My Bank uses java runtime environment to detect the scanner, scan the check and transfer it directly to them, so I deposit my checks in my account through internet explorer in windows xp.  Well the first time i try it in firefox 3.0.1, it rejected the browser because of its version and because i was using linux. The website states that it only supports Firefox 2.0 for mac and pc, internet explorer 6 and 7. I know, I tried to use the User agent switcher with the internet explorer 7 in vista setting, and it worked to a certain point.  It went through the browser and OS check, the java applet started inside the browser, but it didn't dectect the scanner, and some buttons or tools that say scan, rotate or rescan didn't appear. My scanner works just fine. Any ideas?:(

---

### Post by steveneddy on 2009-05-12
I use USAA and I don't have any issues.

I use Flash 10 from Adobe and Iced Tea for Java.

Works great for me.

---

### Post by mauro24 on 2009-05-12
> **steveneddy said:**
> I use USAA and I don't have any issues.

I use Flash 10 from Adobe and Iced Tea for Java.

Works great for me.

do you still have to use the agent switcher? and how do you get those plugins? Does iced tea replaces java completely?:confused:

---

### Post by lvleph on 2009-05-12
> **steveneddy said:**
> I use USAA and I don't have any issues.

I use Flash 10 from Adobe and Iced Tea for Java.

Works great for me.

Your saying you can get deposit at home working using linux? I doubt that. I even tried using ie in wine to trick it and it didn't work. I complained to USAA and the lady actually tried to fix my issue. I had to laugh and tell her she couldn't fix it, just register my complaint. She also had no idea what linux was.

EDIT: I use VirtualBox. In fact, the only reason I have virtual box is for MS Money, Deposit at Home, and my Garmin Forerunner.

---

### Post by LoneWolfJack on 2009-05-12
> My scanner works just fine.

do I read that as "my scanner ain't broken" or "my scanner works on ubuntu, but not with my banking software"?

---

### Post by ugm6hr on 2009-05-12
Wow.  I'm impressed (and a little concerned) that any bank allows you to deposit an electronic copy of a cheque.

Sorry, can't help with the technical issue.

---

### Post by lvleph on 2009-05-12
There is no difference between a paper copy, electronic copy, and a debit card. They use the account numbers anyway.

EDIT: They do this, because there is only one branch in the world.

---

### Post by mauro24 on 2009-05-12
> **LoneWolfJack said:**
> do I read that as "my scanner ain't broken" or "my scanner works on ubuntu, but not with my banking software"?

well, like I said, my scanner works just fine in ubuntu, but when the page loads, like in internet explorer, the java applet is supposed to detect the scanners on your computer to scan the check, it gives you one or a list of scanners if you have more than one.  I don't know if it's the firefox browser, the linux version of java, or maybe  to do with my scanner.  In, windows I didn't have to do anything with my scanner, as long it was detected by the OS.:confused:

---

### Post by lvleph on 2009-05-12
It is the linux version of java as far as I understand.

---

### Post by mauro24 on 2009-05-12
It looks like steven know the answer, I guess I have to wait for his new reply.:(

---

### Post by jespdj on 2009-05-12
Which version of Java are you using?

Try installing Sun Java 6:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by mauro24 on 2009-05-12
> **jespdj said:**
> Which version of Java are you using?

Try installing Sun Java 6:
```
sudo apt-get install sun-java6-plugin
```

yes, I have the latest in sun java 6, firefox 3.0.1 , and ubuntu 9.04.

---

### Post by lvleph on 2009-05-12
From what I recall the problem occurred when java tried to control the scanner. It couldn't find it or something.

---

### Post by steveneddy on 2009-06-02
> **mauro24 said:**
> It looks like steven know the answer, I guess I have to wait for his new reply.:(

I am on the road constantly lately so I am not able to answer very quickly sometimes. Once I do get online when traveling, UF is usually the last thing on my mind, LOL.

I don't have any problems doing anything I need to do online, including banking.

iced tea is in the repos - just install it for java support.

[COLOR=Red]**you must totally uninstall any other java software that is currently installed BEFORE installing iced tea for iced tea to function properly.**[/COLOR]

I use adobe flash 10 from the Adobe website for any flash software on the web.

I am on Ubuntu 8.04 64 bit, fully updated. 

I use firefox without using a user agent switcher. Although I use the user agent switcher on occasion, it is not necessary on the USAA website.

I don't use the deposit from home feature. Although it should work with no issues. maybe scanning first and creating a .jpg of the check would work well also?

I also use this Linux laptop for two other banking websites and have no issues there.

My checks are direct deposited so no need to scan deposits.

Any other deposits I use a local bank branch for deposit and then transfer the funds to USAA at a later time.

I hope this helps.

---

### Post by munishvit on 2009-06-02
> **steveneddy said:**
> I am on the road constantly lately so I am not able to answer very quickly sometimes. Once I do get online when traveling, UF is usually the last thing on my mind, LOL.

I don't have any problems doing anything I need to do online, including banking.

iced tea is in the repos - just install it for java support.

[COLOR=Red]**you must totally uninstall any other java software that is currently installed BEFORE installing iced tea for iced tea to function properly.**[/COLOR]

I use adobe flash 10 from the Adobe website for any flash software on the web.

I am on Ubuntu 8.04 64 bit, fully updated. 

I use firefox without using a user agent switcher. Although I use the user agent switcher on occasion, it is not necessary on the USAA website.

I don't use the deposit from home feature. Although it should work with no issues. maybe scanning first and creating a .jpg of the check would work well also?

I also use this Linux laptop for two other banking websites and have no issues there.

My checks are direct deposited so no need to scan deposits.

Any other deposits I use a local bank branch for deposit and then transfer the funds to USAA at a later time.

I hope this helps.

..helpful :D

---

### Post by torstenaf on 2009-07-19
Hi, I can submit checks to USAA through Firefox on Linux. Here's how...

**1. Install Plugin**
I tried using IcedTea plugin, but it didn't work (?). So I used the sun java 6 plugin.
```
sudo apt-get install sun-java6-plugin
```

**2. Install User Agent Switcher**
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

**3. Restart Firefox**

**4. Add New User Agent**
user agent icon --> User Agent Switcher --> Options --> New --> New User Agent ...

**5. Enter New User Agent Information**
In the popup dialog box, delete all pre-filled entries and insert the information below.

Description:
```
FireFox 1.5.0.3 (Mac OSX)
```

User Agent:
```
Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.0.3) Gecko/20060426 Firefox/1.5.0.3
```

**6. Restart Firefox**

**7. Change to user agent _Firefox 1.5.0.3 (Mac OSX)_**

**8. Navigate to the USAA deposit at home page:**
[https://www.usaa.com/inet/bank_deposit/BkHomeDeposit?action=INIT&SearchRanking=1&SearchLinkPhrase=deposit[atsn]home](https://www.usaa.com/inet/bank_deposit/BkHomeDeposit?action=INIT&SearchRanking=1&SearchLinkPhrase=deposit[atsn]home)

**9. You should now see**

> Deposit checks from home with your Mac® and scanner &#8212; USAA Deposit@HomeSM is quick and secure.

instead of the usual nonsense

> We're sorry, but you do not meet the minimum system requirements for USAA Deposit@Home.

**10. Click _Get Started_**

**11. You'll see this message:**

> In order for us to accept a check image, please ensure that it is:

A grayscale image with resolution of 200 dots per inch (DPI), and that it is saved as jpg or jpeg. Learn more about changing scanner settings.

1.  Scan the front of your check by placing it (with the front side facing down) at the origin of the scanner. See examples of good and bad images.
2. Save the image in a location where you can easily find it, such as your desktop.
3. Sign the back of your check and mark it "For deposit only to USAA Bank account number [your account number]."
4. Scan the back of your check by placing it at the origin of the scanner. See examples of good and bad images.
5. Save the image in a location where you can easily find it, such as your desktop.


**12. Enter Info**
Click **Next**, select account from dropdown and type in check amount, then click **Next**.

**13. Scan Check**
Scan the check with **xsane** or similar software (see step 11). USAA for the Mac (and us Linux/Ubuntu users) requires the user to pre-scan the check and upload them, rather than the Windows method where the check is directly scanned into the applet.

- greyscale
- 200dpi
- signature on right side
- front & back

**14. Upload Scanned Check Images**
Java will start, asking whether or not you trust the vendor of the software. Say "Run". Above the applet window is a browse button. Load each side of the scanned check, so on and so forth.

---

### Post by lvleph on 2009-07-20
All I am getting a grey box with a cancel button.

---

### Post by torstenaf on 2009-07-20
I got the grey box with the cancel button when I installed and tried to use IcedTea. I had to uninstall IcedTea, and install sun-java6-plugin.

Here's a list of my installed java.

default-jre
default-jre-headless
java-common
libaccess-bridge-gnome
openjdk-6-jre-lib
openjdk-6-jre-lib-headless
openjdk-6-jre
sun-java6-bin
sun-java6-jre
sun-java6-plugin

I couldn't tell you which one is actually being made use of. In firefox, when I type about:plugins it says

> 
Java(TM) Plug-in 1.6.0_14

    File name: libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java™ Plug-in 		Yes
application/x-java-applet 	Java™ Plug-in Applet 		Yes
application/x-java-applet;version=1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.5 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.6 	Java™ Plug-in 		Yes
application/x-java-applet;jpi-version=1.6.0_14 	Java™ Plug-in 		Yes
application/x-java-bean 	Java™ Plug-in JavaBeans 		Yes
application/x-java-bean;version=1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.5 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.6 	Java™ Plug-in 		Yes
application/x-java-bean;jpi-version=1.6.0_14 	Java™ Plug-in 		Yes


---

### Post by lvleph on 2009-07-20
I had to run
```
sudo update-java-alternatives -s java-6-sun
```
and then restarted FF to get it to change to the correct java.

This was very clever to switch it to Mac OSX agent. I didn't know that they have you scan it yourself on Mac. I would have thought of trying it if I did.

---

### Post by jkratze1 on 2009-07-29
This works great!  For those using 64-bit Ubuntu, you need to link the Firefox java plugin libnpjp2.so since libjavaplugin_oji.so is not included with the 64 bit JRE.  USAA needs to allow Linux so we don't need to masquerade as a Mac.

---

### Post by lvleph on 2009-07-29
> **jkratze1 said:**
> This works great!  For those using 64-bit Ubuntu, you need to link the Firefox java plugin libnpjp2.so since libjavaplugin_oji.so is not included with the 64 bit JRE.  USAA needs to allow Linux so we don't need to masquerade as a Mac.

I am not sure if I understand what I need to do. Can you please explain a little more completely.

---

### Post by khermans on 2009-08-23
> **torstenaf said:**
> Hi, I can submit checks to USAA through Firefox on Linux. Here's how...

**1. Install Plugin**
I tried using IcedTea plugin, but it didn't work (?). So I used the sun java 6 plugin.
```
sudo apt-get install sun-java6-plugin
```

**2. Install User Agent Switcher**
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

**3. Restart Firefox**

**4. Add New User Agent**
user agent icon --> User Agent Switcher --> Options --> New --> New User Agent ...

**5. Enter New User Agent Information**
In the popup dialog box, delete all pre-filled entries and insert the information below.

Description:
```
FireFox 1.5.0.3 (Mac OSX)
```

User Agent:
```
Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.0.3) Gecko/20060426 Firefox/1.5.0.3
```

**6. Restart Firefox**

**7. Change to user agent _Firefox 1.5.0.3 (Mac OSX)_**

**8. Navigate to the USAA deposit at home page:**
[https://www.usaa.com/inet/bank_deposit/BkHomeDeposit?action=INIT&SearchRanking=1&SearchLinkPhrase=deposit[atsn]home](https://www.usaa.com/inet/bank_deposit/BkHomeDeposit?action=INIT&SearchRanking=1&SearchLinkPhrase=deposit[atsn]home)

**9. You should now see**



instead of the usual nonsense



**10. Click _Get Started_**

**11. You'll see this message:**



**12. Enter Info**
Click **Next**, select account from dropdown and type in check amount, then click **Next**.

**13. Scan Check**
Scan the check with **xsane** or similar software (see step 11). USAA for the Mac (and us Linux/Ubuntu users) requires the user to pre-scan the check and upload them, rather than the Windows method where the check is directly scanned into the applet.

- greyscale
- 200dpi
- signature on right side
- front & back

**14. Upload Scanned Check Images**
Java will start, asking whether or not you trust the vendor of the software. Say "Run". Above the applet window is a browse button. Load each side of the scanned check, so on and so forth.

Does this still work?  Tried today to no avail :-(  Perhaps USAA updated their website to require more than just a new User Agent now?  Please let me know!!

---

### Post by khermans on 2009-08-23
OK, I figured out why it didnt work.  Something must be getting set in the cookie when you log into the USAA website.  If you change your User Agent post-login and try to access the Deposit@Home feature, you will be rejected.  However, if you Log Off, then set your User Agent to any normal Mac OS X browser (Safari 3.x or Chrome 3.x), it should work!  Yay :-D  Happy dance...

USAA still needs to fix their website.  It is like one line of code to fix this on their end.  I don't see why they want to reject Linux customers :-(

---

### Post by lvleph on 2009-08-23
For some reason when I try it doesn't like my scans. I even did everything at 300dpi.

---

### Post by scouser73 on 2009-08-23
Go to **Synaptic Package Manager**, de-select the Linux versions of Java you have, and then search for **sun-java6-bin**, **sun-java6-jre** & **sun-java-plugin** then click Apply and install it, then check the USAA Banking website. Hopefully this will resolve the problem.

---

### Post by lvleph on 2009-08-23
I have sun-java6 and it is activated.

---

### Post by ricojonah on 2009-08-28
Hi everyone. I've managed to (finally) get deposit@home working with the instructions here (using the user agent switcher).

Please join me in sending a message to USAA to resolve this. This is a significant problem that they can correct with a fairly trivial fix.

If you've got a moment, send them this message by logging into USAA and selecting "Contact Us" at the bottom of the page:

---

SUBJECT: Linux computer not allowed to use Deposit@Home

MESSAGE:
Thank you in advance for your time and consideration.

I am experiencing technical difficulties when accessing the USAA deposit@home service. More specifically, the USAA web site appears to deny USAA members access to the deposit@home service if they are not  using a computer containing the Microsoft Windows or Apple OSX operating systems.

As a USAA member, I am one of many individuals within the USAA community who do not use Microsoft Windows or Apple OSX for online banking with USAA. I use a computer that meets all other requirements for using the deposit@home service. My computer is fully capable of interacting with the deposit@home service without any technical problems, with the exception that USAA specifically denies my system the ability to perform this essential banking activity. 

As an otherwise satisfied USAA member, please consider modifying the deposit@home service to allow USAA members to use the service if they are using a Linux operating system (as opposed to exclusively allowing only Microsoft Windows operating system or Apple devices).

USAA appears to be working towards compatibility with the iPhone, Blackberry devices, and other methods for accessing deposit@home. As opposed to those active (and fantastic) developments, allowing USAA members who use Linux to deposit@home requires only a trivial change to the deposit@home web page (by simply adding Linux as an acceptable "user agent" section, alongside Microsoft Windows and Apple OSX). 

Millions of users having already adopted Linux as their choice for computing platforms. With USAA leading the way with technological innovation and convenience, USAA and its members can tremendously benefit by further expanding deposit@home compatibility to the USAA linux user community.

Again, thank you for your time and attention to this matter. I look forward to seeing this technical issue resolved.

---

### Post by lvleph on 2009-08-28
I sent mine.

---

### Post by ricojonah on 2009-08-29
I just received (as one would expect) a nice little template-style response from USAA via the site's email:

[B]We appreciate your feedback regarding our Deposit@home service,  We continually look for ways to improve our products and services so they are of the highest quality for our members. We will forward your feedback to the appropriate department.  Thank you for taking the time to send your suggestion..

We value your business and the opportunity to serve all your financial needs.

Thank you,
Valerie Lozano
USAA [/B]

Of course! =)

Thanks, lvleph. Normally, I'm not very optimistic about seeing a positive reaction from a large company. But USAA is one of the few financial institutions--let alone as a business of any sort--that I've actually got considerable confidence in for resolving this problem. With as many customer feedback surveys, questionnaires, and other efforts that they're always actively utilizing to give their members a warm&fuzzy, I think having a few members sending this clear message may hold some weight.

Please everyone, let them know that their banking should be penguin-friendly!

---

### Post by lvleph on 2009-08-29
> **ricojonah said:**
> I just received (as one would expect) a nice little template-style response from USAA via the site's email:

[B]We appreciate your feedback regarding our Deposit@home service,  We continually look for ways to improve our products and services so they are of the highest quality for our members. We will forward your feedback to the appropriate department.  Thank you for taking the time to send your suggestion..

We value your business and the opportunity to serve all your financial needs.

Thank you,
Valerie Lozano
USAA [/B]

Of course! =)

Thanks, lvleph. Normally, I'm not very optimistic about seeing a positive reaction from a large company. But USAA is one of the few financial institutions--let alone as a business of any sort--that I've actually got considerable confidence in for resolving this problem. With as many customer feedback surveys, questionnaires, and other efforts that they're always actively utilizing to give their members a warm&fuzzy, I think having a few members sending this clear message may hold some weight.

Please everyone, let them know that their banking should be penguin-friendly!
Well, we do own the company; don't forget that.

---

### Post by williamts99 on 2009-08-30
I sent them a message also.  Though the user agent switch worked for me, it hangs at the last section where it is waiting for the confirmation page.  Anyone else have this issue?

Edit:
My user agent string is:
[PHP]Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; sv-SE; rv:1.9.0.8) Gecko/2009032608 Firefox/3.0.8[/PHP][

---

### Post by lvleph on 2009-08-30
For me it just won't accept the check. I don't think the quality is high enough or something. I will have to try it again some time.

---

### Post by Sgt-Slyde on 2009-09-04
Yep, I'm having the same issue.  I've edited my user agent switcher data using lines I've found here as well as from some other Linux forums but no luck - it works fine until I click the "Submit" button and then hangs until USAA auto-logs me out.

---

### Post by torstenaf on 2009-09-12
I continue to be able to deposit checks, I just did another tonight.
- Ubuntu 9.04 (32-bit)
- Mozilla Firefox 3.0.14
- Java(TM) Plug-in 1.6.0_16

Checks are scanned with xsane. I usually do "Acquire Preview" and crop the check images before scanning.
- 200 dpi
- greyscale
- jpeg

After Java starts on the check deposit page, I click "Browse" and load up each check image. 
- For the back of check, signature is to the right.
- I always print very clearly "For deposit only to USAA FSB account number ########.". I don't know if they try to OCR that part.

Then I click "Submit" and it takes a little while, then a flash popup comes up saying "this may take a minute," and then I get the success page.

I sent a request to support linux with Deposit@Home to USAA a couple of years ago, and got the exact same template message in return. I don't think Linux support is on the USAA radar at the moment, though hopefully with enough requests it will increase in priority.

---

### Post by david.rahrer on 2009-09-28
Perhaps all those emails they got telling them about the user agent string trick prompted them to block it?

---

### Post by torstenaf on 2009-09-29
Continues to work fine for me with the same user agent string. 

I did notice that I have to change the user agent string BEFORE I even load the login page for the website. I tried to change the user agent string after loading the login page but before actually logging in, and deposit at home failed to work. I closed/opened the browser, changed the user agent string, then loaded the USAA login page and all was well.

Best of luck.

---

### Post by sgosnell on 2009-09-29
I installed the UserAgentSwitcher, called it a Mac, and it seems to work.  I get to the dialog where I browse for the check image, at least.  Since I have no actual check at the moment, I can't say that it works for sure, but as far as I can tell, it should work OK, if you have the images available.  I do notice that they don't support network printers, only directly-connected USB, and my HP is connected via my network, not USB.  I have done deposits using Windows and my network printer in the past, though.  Prescanning and uploading the images will do fine for me, though.  That way I know what I'm sending beforehand.

I've also asked USAA to support Linux, with no success.  That's about the only thing I'm not happy about with USAA.  For everything else, it's by far the best there is.  I've been a member since 1970, and have never had a bad experience, other than the lack of Linux support.

---

### Post by lvleph on 2010-03-17
I am having problems, because of java. It appears that the site is not able to control java.

---

### Post by gbear14275 on 2010-03-17
Hey guys,

Here's my exploits documented here (under G): [http://www.cliffordfell.com/joomla/index.php?option=com_content&view=article&id=147:haha-i-fooled-you&catid=46:computers&Itemid=73](http://www.cliffordfell.com/joomla/index.php?option=com_content&view=article&id=147:haha-i-fooled-you&catid=46:computers&Itemid=73)

and now I'm trying to get a push like the previous guy but i'm trying to get the blog posters in on it too.  Help me out if you can, here's my pitch:

Hey guys,

I am writing to actually request your help. I am currently trying to get the USAA web team to lift the linux/other OS restrictions from their website. (as you have seen here)

Everyone who sees this and would like to be able to use their system with USAA please do the following:
1. Open up your USAA account and go to the message center (located at the very top right of the website: Messages).
2. Start a new message with them (right side "Send a new e-mail to USAA).
3. Under topic select "feedback" then "Website" then "suggestion".
4. Subject "Deposit@home unlock OS"
5. Copy this text, "Attn: Anthony Garza

I would like to express my desire to see the USAA Deposit@home website drop its OS restrictions so that I may use an OS of my choice. I understand there are concerns of using various configurations and so would ask that a "Use Unsupported" option be implemented. This offers alternative users the ability to use the site while also keeping costs low for the USAA deposit@home support team. Thank you for your time and consideration.

//Signature//"

I figure a push to a single POC might show them the volume of users that would support this.   Thanks again for helping if you can.

---

### Post by sgosnell on 2010-03-17
Done, FWIW.  I'm not going to hold my breath, though.

---

### Post by wbar2 on 2010-04-03
I recently sent a message to their technical support about supporting Linux. They said that they currently do not have plans to support it for Deposit@Home, but they said basically if they heard from enough people who wanted / needed it they would implement it.

---

### Post by wbar2 on 2010-04-15
I was able to deposit a check through Deposit@Home on Lucid by:

1. Uninstalling Icedtea Firefox plugin and [Installing Java Firefox plugin]("http://sites.google.com/site/easylinuxtipsproject/java")
2. Installing [Xsane]("apt:xsane") (Simple Scan does not have greyscale option)
3. Installing [HeaderControl]("https://addons.mozilla.org/en-US/firefox/addon/11327") Firefox addon and setting the user agent for usaa.com to be:

```
Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.0.3) Gecko/20060426 Firefox/1.5.0.3
```

Then just login to USAA and follow the instructions on the Deposit@Home section. The site will think you are on a Mac everytime you go to it, bypassing the system requirements. You will then scan in your checks with xsane and upload them to USAA. Make sure they are 200 dpi and greyscale.

---

### Post by wbar2 on 2010-04-16
Here's a more detailed tutorial on how to make it work:
[http://ubuntuforums.org/showthread.php?t=1454931](http://ubuntuforums.org/showthread.php?t=1454931)

---

### Post by meckelman on 2011-04-10
Use this for Firefox 4 to modify the Header:  [https://addons.mozilla.org/en-us/firefox/addon/modify-headers/](https://addons.mozilla.org/en-us/firefox/addon/modify-headers/)

Set up like this:
Action = Modify
Name = user-agent
Value = Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.7; en-US; rv:1.9.2.2) Gecko/20100316 Firefox/3.6.2

---

### Post by gbear14275 on 2011-09-26
A change should have been released this weekend that allows for unsupported configurations to use the site without having to do user agent string spoofing.  This should allow linux computer systems and a variety of browsers to use the site in an "unsupported" fashion.  This simply means if it doesn't work you are on your own.

BUT...  At least we don't have to spoof the system anymore.

---

### Post by ubudog on 2011-09-26
Back to sleep thread.

---

