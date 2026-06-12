---
title: "Virtualbox startup"
date: 2010-07-10
forum: Desktop Environments
---

### Post by AJExtreme on 2010-07-10
Is there a way to set-up Virtualbox  to auto-run upon startup.  

I am working on my mothers computer and she has to have Windows for Internet Explorer.  The websites she has to go on for work require IE6+, and there are a couple programs she has to run that only works with windows may work with Wine.  

But she wants something more stable than windows... She has really bad luck when it comes to Windows, so I was talking to her about Ubuntu.  After thinking everything over, If I could get her computer to startup with Virtualbox and run Win XP in it all her problems may be solved.She has 2 computers so I can play with one of them to figure it all out and she can play and learn Ubuntu.

Anyway not to ramble, could someone please give me some advise and help on this.  If you need more info please let me know.

Thanks

Aaron

---

### Post by Steve603z on 2010-07-10
System > Preferences > Startup Applications > Add and under command type: 
```
VBoxManage startvm [VM Name or UUID] --type gui 
```

that will open the VBox Session when your mother logs into ubuntu

---

### Post by AJExtreme on 2010-07-12
Thankyou for the help,

For VM Name or UUID where would I find that or would that be like Windows XP or whatever I setup in Virtualbox?

---

### Post by _Mark_ on 2010-07-12
> **AJExtreme said:**
> Thankyou for the help,

For VM Name or UUID where would I find that or would that be like Windows XP or whatever I setup in Virtualbox?

Yep it will be whatever name you used on setup

---

### Post by John Bean on 2010-07-12
Be aware that the command VBoxManage is used only by PUEL version of VirtualBox; if you install the free version from the Ubuntu repositories the command will be vboxmanage (all lower case) instead.

Same end result though :-)

---

### Post by isecore on 2010-07-12
Nothing personal, but isn't it a bit overkill to solve it the way you're going to do? Plus, if she has trouble with Windows, then why do Ubuntu and then cover it up with a virtualized Windows anyway?

If it was me and she had to use IE6 for various sites, then why not use the ies4linux project instead? Sure, it hasn't been updated in a while and I'm wondering whether that project is still alive, but last time I checked it worked fine.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Seems to me a more elegant solution using a Wine'd IE6 for the websites that require it instead of doing it your way.

(or simply spoofing the user-agent in Firefox. I've done that too and tricked several "IE6-only" sites)

---

### Post by AJExtreme on 2010-07-13
Thanks for all you help with the code to get VB running on startup.  

Getting IE to run on Linux would solve about 85% of her problems, I tried to run it on mine but it keeps telling me I am not running the latest version, which I have the wine ppa in my software sources and got the latest update. I will try it on my mothers computer since her's is a 32 bit computer and OS, where as mine is 64 bit.

I am interested in how to go about spoofing the user-agent in Firefox, if you could please give me more info on how to do this?

Thanks again for all your help with this.

Aaron

---

### Post by theozzlives on 2010-07-13
Of course you understand the the Virtual Windows is still vulnerable to Windows Mal-ware. Your Ubuntu will not be affected, but the Windows Virtual Disk will. I suggest keeping a copy of the "Disk File" handy in case it gets mucked up.

---

### Post by isecore on 2010-07-13
> **AJExtreme said:**
> Thanks for all you help with the code to get VB running on startup.  

Getting IE to run on Linux would solve about 85% of her problems, I tried to run it on mine but it keeps telling me I am not running the latest version, which I have the wine ppa in my software sources and got the latest update. I will try it on my mothers computer since her's is a 32 bit computer and OS, where as mine is 64 bit.

I am interested in how to go about spoofing the user-agent in Firefox, if you could please give me more info on how to do this?

Thanks again for all your help with this.

Aaron

IE6 using the ies4linux installer works fine for me. I'm running 64-bit Ubuntu Lucid, with Wine 1.2. When installing it says that I should update to the newest Wine, but that's a warning I ignore since I already know I'm running the latest.

It gives an error regarding rundll32 but installs fine, and when I run the software it works just fine.

As for spoofing the user-agent, it's easy. I use this extension, which provides a nice little menu: [https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by AJExtreme on 2010-07-13
Ok I figured out the Spoofing agent for Firefox, I think that may work, I will have to give it a try on her computer later today.  If it works for her then I may not have to worry about VB, unless it comes to some programs that she has to run and this dang old 32bit Laser Printer she refuses to get rid of...

Which is kind of funny because she got it running on her 64 bit vista system, and it started messing up her system, so she had to take it off that system.  I will start another post on all that cause I will have to figure that out to, only for Ubuntu.

Thankyou for the advise about Windows Virtual Disk.  I understand how vulnerable Windows is, that is why I have moved completely away from it. Well with the exception of work and military.  I don't understand why companies and military use such a vulnerable OS.

---

### Post by AJExtreme on 2010-07-13
Did you have to do anything special with it, such as getting beta version or did you just do the updates.

---

### Post by AJExtreme on 2010-07-13
I think I got it installed but, I don't think something is correct then.  I have to go to into program files and right click on the Internet Explorer.exe  Then a window comes up with no navigation bar and it takes me to the wine install/update page.  

Do I have to do anything in the configuration for it, such as add libraries and so on.  If so do you know what libraries I would have to add to it?

Or is there any thing I can run in terminal to help trouble shoot this problem?

The browser says Wine Internet Explorer, but I don't have any way to navigate pages, how do I get the navigation bar on it?

---

