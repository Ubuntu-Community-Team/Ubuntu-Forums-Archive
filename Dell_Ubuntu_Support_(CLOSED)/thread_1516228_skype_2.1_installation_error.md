---
title: "skype 2.1 installation error"
date: 2010-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PeteBeech on 2010-06-23
I have just tried installing Skype 2.1 beta 32-bit on my Dell Mini 9 running Ubuntu 8.04 and got an error from the installer "dependency is not satisfied: libasound2".

I'm a complete novice with Ubuntu and I've no idea what an unsatisfied dependency is or what to do about it.

Advice would be much appreciated.

Peter

---

### Post by snowpine on 2010-06-23
Hi Pete, are you using the speciall "Dell Ubuntu" that comes preinstalled on the Minis? If so, it uses a special "lpia" architecture that is not compatible with most outside software sources. 

Here is a thread on how to install Skype on Dellbuntu lpia: [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

You might consider, at some point, installing "regular" Ubuntu instead of the preinstalled Dellbuntu. This would give you more up-to-date applications and better compatibility with 3rd party software. There are some good how-to's at this site: [http://www.ubuntumini.com](http://www.ubuntumini.com)

---

### Post by PeteBeech on 2010-06-23
Thanks Snowpine.  

Unfortunately things have now got worse.  

Shortly after posting my question about Skype, a message appeared on my Mini telling me updates (408 of them!) were available so I tried to install them, thinking this might fix the missing dependency.  The update failed and when I responded to a message to run the package manager it came back with an error "failed to run /usr/sbin/synaptic as user root - unable to copy the user Xauthorisation file".  After this, things seemed to be woking but every attempt to start Firefox produced a sequence of "checking your add-ons" messages.  When I tried rebooting I found that my wireless connection settings had disappeared.

I've written down the message that appeared when the update failed but it's about half a yard long so I won't include it here unless someone asks me to.

I did phone Dell's Ubuntu support team before posting the question here about Skype, and their response was to offer me a copy of Windows XP Home to install.  Luckily the Mini belongs to my wife, who will probably put up with a few days of messing about before she breaks my skull.

Last time an update failed (which was the only other time one was offered) Dell told me to send the Mini back and they reinstalled the operating system.

Ho hum

Peter

---

### Post by snowpine on 2010-06-23
Hi Peter, honestly I have less than 10 minutes of experience with "Dell Ubuntu;" maybe I'm not the guy to help you with that. ;) It is sad that Dell is not supporting the product they sold you; "install Windows instead" is a really lame answer in my opinion. :(

You may find it is quicker to just install the current Ubuntu release (Ubuntu 10.04 or Ubuntu Netbook Edition 10.04; they are the same except that UNE has a "launcher" interface instead of a standard desktop) than to troubleshoot the issue with your current, outdated 8.04 (which stands for April 2008 ) install. Everything should work out-of-the-box except for wireless, which you can fix following this guide: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Here are a couple of my favorite Dell Mini 9 resources on the Web:
[http://ubuntunmini.com](http://ubuntunmini.com)
[http://mydellmini.com](http://mydellmini.com)

I'd advise you to gather some more information and decide with your wife what is the best solution. Dell Mini 9 is a nice little computer once it's properly configured. :)

---

### Post by PeteBeech on 2010-06-23
I'm now running Netbook version of Ubuntu 10.04 and (a success!) the wireless connection is working too.

Once I've worked out why this version has decided to report that "one or more disks are failing", I'll have another go at installing Skype - or sending the thing back to Dell again.

Thanks for your efforts.

Peter

---

### Post by snowpine on 2010-06-23
Yay! Glad you got it working. :) I've seen the "disks failing" thing mentioned before on these forums, but I honestly can't remember what the outcome was...

---

