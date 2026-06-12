---
title: "update manager broken w/new CD's"
date: 2006-09-07
forum: Desktop Environments
---

### Post by ng0g on 2006-09-07
After reinstalling 3 times with 3 of the 5 CD's that came in the mail from 
Ubuntu a couple of days ago. I have more closely defined the problem.

During the install a message comes up implying that the install program cannot 
get to "security updates".  After the install you cannot update or add new 
programs using any of the built in techniques.  

Update manager says that there are 116 updates that need to be installed. 
(which I find odd considering that these are the latest and greatest and just 
came in the mail).  When you tell it to go ahead and download and install the 
updates, the download fails with the message that the connection to 
146.137.96.7 fails.  I can ping that IP with no problems, I can use firefox 
to go there with no problems.  I have used this computer with several 
previous releases of Ubuntu and never had a problem.  I am starting to 
believe that there is something wrong with the update software or the server.

I even reinstalled the previous version and used update manager with it.  It 
works fine.  But Drapper Drake 6.06 is not able to update.  Everything else 
appears to work fine.

Any thoughts or help will be greatly appreciated.  I have gone through the forums and tried everything I found.](*,)

---

### Post by orb9220 on 2006-09-07
You do not have the latest greatest which has the integrated 119 upgrades integrated in 6.0.6.1 here 
[http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)
which was released after the 6.0.6 were made.

And it should not matter I have installed without internet connect for updates and still had the basic system installed then did the updates fine.

---

### Post by ng0g on 2006-09-08
I am very surprised that they would send out CDs that were this broken. Update does not work at all, in any fashion, so you cannot fix them.  The only solution is to discard them.  Then download the new "fixed" release and install it.  They wasted money sending these out as they are not very usable.  You can install Ubuntu but you cannot ever update it.  I will discard them and download the new release.:confused:

---

### Post by ng0g on 2006-09-08
I downloaded 6.06.1 and installed it.  I still have the same problem.  I tried to add ethereal so that I could watch what was happening, but it won't even do that.  I get the same kind of failure message.  My internet connection is fine as I can ping the ip's that update manager gets the failure to connect message about.  And I can go there with Firfox with no problems.](*,)

---

### Post by ng0g on 2006-09-08
There is one difference now that I have 6.06.1, and that is that update manager says that there is only 1 package that needs updating.

---

### Post by ng0g on 2006-09-10
I completely reinstalled Breezy Badger and update manager works perfectly.  Back to Drapper Drake and it failed everytime.  At the moment I am back to Breezy Badger and getting very tired of beating my head against the wall over this one.  I am astounded at nobody else seems to be reporting similar problems.  My harware all works fine.  I have no problems with update manager under Breezy Badger, but it won't work at all under Drapper Drake.  This is making me nuts.:confused: :frown: ](*,)

---

### Post by ng0g on 2006-09-11
I reinstalled Breezy Badger and used it to update to Dapper Drake.  Update manager now works under Dapper Drake.  Installing from the CD's, it is broken.  Something is wrong with the CD's  I hope that someone from Ubuntu see's this and can get it fixed.  I will try to submit a bug report.

---

