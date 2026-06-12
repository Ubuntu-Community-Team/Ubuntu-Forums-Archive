---
title: "Editing Edubuntu's Live CD"
date: 2007-12-06
forum: Education &amp; Science
---

### Post by Haywood on 2007-12-06
Hi,

I work for a school system and was talking to our CIO about the possibilities of using Edubuntu in the classroom.

As it stand now, when one runs the Live CD they have full admin rights and the ability to change system settings, install, manipulate files on the hard drive, etc.  What I would like to do is to create or edit the Live CD so that when the teacher runs it for a student they only have “USER” privileges.  They should not have the ability to change system settings, install or the ability to access external storage devices.  Essentially run the programs that come on a Live CD but do absolutely nothing else.

Is there anyway to set this up?

Thanks in advance,
Bill

---

### Post by ryanVickers on 2007-12-06
Once you install, you can do all this easily of course, much easier than windows and it also actually works :p (I can hack our computers with XP so easy lol), but I see why you'd want the live CD to come like that.  Well, for starters, you'd want 2 disks - a normal one the the computer guys would use to install on the computers with, and the "student" CD - the one with less privileges.  First of all you'd have to decide what privileges exactly you want them to have, and then change the default live CD user to not be root, but just an ordinary user with the abilities and file permissions you pick.  Personally, I think it would be a good idea to switch all the computers to Linux BEFORE making the demo disk just because you need to set up user groups and what they can do, and then make the disc  user fit into that/those...

---

### Post by Haywood on 2007-12-06
Thank you for the quick reply.  However, I feel that I may have not expressed the objective well enough.  I do not want Edubuntu to be installed on any machine.  If it were up to me I would install it on the machins and give the teacher the ability to dual boot.  What I am looking for is that I want to give the CD to the teacher and let them run it straight off of the Live CD without any options... Just run the programs that are on the Live CD.

---

### Post by ryanVickers on 2007-12-06
Well, if it's for the teachers, then the normal CD should be fine, right?  And regardless of who's using it, your going to just run the live CD all the time?  I hope your computers have a decent amount of RAM and no one will ever need to save anything then... :p

---

### Post by Haywood on 2007-12-06
The issue is that the Live CD gives the user too many privileges.  I want to edit the Live CD so that essentially the person running it (student or teacher) has only USER level privileges and can not install Edubuntu.  I am not looking for the user to save anything, just play the educational games that are on the CD.

---

### Post by ryanVickers on 2007-12-06
I see.  Well, by default the "ubuntu" user (at least that's what it is on mine) is basically root, but it also will never ask for a password.  I would say that the best way to go about doing anything would be to simply add a root password requirement and have the time out be "0" so that ANY root task will ALWAYS need the password, (by default, it will allow other root tasks without a password for 5 minutes after a root task)

---

### Post by Blutack on 2007-12-06
Or change the sudoers file to deny all sudo access to user 'ubuntu'

---

### Post by Haywood on 2007-12-10
How would you edit the files for the iso?

---

### Post by edm1 on 2007-12-10
I've never tried this but wouldnt the easiest thing be to boot the live cd, make a new user account with no privilages, log out, then back in with the new user. Oh, you'd also have to System>Admin>Login Window>Security then disable auto and timed logins. Might work.

---

### Post by engla on 2007-12-10
There are structured tools for this, and some howtos too. It's time that the community starts helping out by using the knowledge already out there and linking to it!

Ubuntu help wiki:
[LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")
[LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

[ubuntu customization kit]("http://uck.sourceforge.net/")

And there is more. Actually I coulndn't find the application I was looking for, it was a quite high-profile tool for remixing a livecd, with a quite easy interface.

---

### Post by engla on 2007-12-10
Ah, I found it: [reconstructor]("http://reconstructor.aperantis.com"). However, many of these tools were developed and tested for older versions of ubuntu and have perhaps not been updated for the latest version if there are incompatibilities.

---

### Post by Haywood on 2007-12-18
Thanks to all for your outstanding help.  I will try to work on this over the Christmas holiday.  This is why I love Ubuntu... the community continues to live up to the Ubuntu philosophy.  I would like to wish each of you a Happy Holiday and hope that it finds you and your family (or friends) well and in good sprits.

---

