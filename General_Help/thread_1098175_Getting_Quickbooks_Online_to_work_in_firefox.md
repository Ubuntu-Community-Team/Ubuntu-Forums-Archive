---
title: "Getting Quickbooks Online to work in firefox"
date: 2009-03-16
forum: General Help
---

### Post by yochaigal on 2009-03-16
in linux or mac, install the user agent switcher from here:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

then go to tools > user agent switcher > options > options

then do add:

Description : Firefox 3 (Windows XP)

User Agent: Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6

App Name: Mozilla Firefox

App Version:  5.0 (Windows; en-US)

Platform:  Win32


Then switch to it from tools, and go!

You won't be able to print pdfs (actually you will, but not the way quickbooks would like you to) until you install adobe pdf reader.

here's how:
Make sure the medibuntu repositories are enabled.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

then

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install acroread acroread-plugins mozilla-acroread

Then open firefox again, and you should be able to print documents or whatever.

---

### Post by yochaigal on 2009-04-21
Here is the useragent xml file...
[http://ryanboyd.com/stuff/Firefox3-WindowsXP.xml](http://ryanboyd.com/stuff/Firefox3-WindowsXP.xml)

---

### Post by steelbp on 2009-07-14
I am using quickbooks online with linux and firefox 3.  I installed user agent and used one of the pre-made agents for MS IE.  
The reports would not work until i made and used the custom agent that [COLOR=Black][yochaigal]("http://ubuntuforums.org/member.php?u=240755")[/COLOR] put in the first post.

I hope this helps other impatient users.

---

### Post by yochaigal on 2009-07-14
I discovered today that the new version of User Agent switcher doesn't accept the .xml import file, so if all else fails, create a new one with these properties:

Description : Firefox 3 (Windows XP)

User Agent: Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6

App Name: Mozilla Firefox

App Version:  5.0 (Windows; en-US)

Platform:  Win32

---

### Post by topdownjimmy on 2010-01-19
Wow!  I'm stunned that this works.  I'd been trying a user agent that specified Firefox 3.5.x, which never worked, but this works like a charm.  Thanks so much!

Edit: It appears that the essential element is having "5.0 (Windows; en-US)" in the "App Version" field.  Without this, the user agent does not work -- hence why the user agents provided at [http://chrispederick.com/forums/viewtopic.php?id=1772](http://chrispederick.com/forums/viewtopic.php?id=1772) don't work, because they don't specify anything in these extra fields.

---

### Post by motionmind on 2010-01-21
I can use QB Online just fine now, except the PDF issue is still not resolved for me. I've installed the packages listed but once I get ti this step:

"sudo apt-get install acroread acroread-plugins mozilla-acroread"

This is the response:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate"

I need to get the PDF printing/preview function working or this push to switch the office ovewr to Ubuntu is dead in the water. Any suggestions?

---

### Post by yochaigal on 2010-01-21
I had the same problem in Karmic. It is because the package acroread is not available in the karmic repository.  My solution would be to install it from here:

[http://www.adobe.com/products/acrobat/readstep2_allversions_nojs1.html](http://www.adobe.com/products/acrobat/readstep2_allversions_nojs1.html)

---

### Post by jmilne on 2011-01-22
I too have been looking for a QUICKBOOKS ONLINE solution in Australia for Ubuntu/Linux for over 5 years. 
Allot of the alternate options for linux were too basic and not able to do what QB would do. So a few things that hindered me moving to linux over the years were;

1. Iphone / mobile device sync with music
2. Accounting package
3. Outlook solution syncing with mobile device. 
4. Sharing with windows users over internet with shared documents.

MY GOAL WAS "NO WINE" AND NO "VM PLayer". (FULL NATIVE LINUX)

Yeah VM was OK, but it bugged me that i was dependent on Microsoft!

THEN I FOUND THE SOLUTIONS FOR ALL ABOVE.

1. Iphone  / Mobile (Ubuntu 10.10)
- Works great and all my itunes music now running and syncing out of RYTHYMBOX. To watch movies on my iphone and ipad, I use "Air Video" in ubuntu (This uses wine, but works easy)

2. Accounting software
CLOUD Saas software in browser solution: [www.xero.com](www.xero.com)
Not only did it work on any platform and browser, it reconciles better than any software i have seen and did more than quickbooks being easier to use, cheaper for multiuser and faster with no complications!!!
There are some great bookkeepers working out of Melbourne that can help data entry for chart of accounts.
FULLY TAX Compliant for BAS.

Moving from quickbooks to this package was easy. A little data entry in "Chart of accounts" but was so worth it. After the change I reaslised that windows/linux did not matter. this package was better regardless.

Qb and MYOB future direction research:
Quickbooks online and MYOB live will both use .net (Microsoft) technology form what I could find out.
It will not be a true Linux Saas provision requiring emulated wine or VM machines to run in Linux. 

3. Google apps (Outlook alternate)
Email Contacts and Calender for mobile sync and linux desktop.
The web browser works great and it all works with my Phones no worries via internet sync, but for people that really need an outlook solution in linux "Thunderbird" with plug ins giving contacts calender sync with google works a treat.

4.DROPBOX:(Sharing files with windows users)
File sharing accross Windows machines via internet
Dropbox.com Could not work better.

I hope this helps you as it has for me. GO UBUNTU!!! LINUX. :-) I LOVE IT.

JOSH

---

