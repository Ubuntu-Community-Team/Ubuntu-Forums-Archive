---
title: "[SOLVED] new to linux; ubuntu-dell-reinstall.iso, 8.04, wireless"
date: 2008-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kesstephen on 2008-07-19
I have bought a dell m1330 with ubuntu 7.10 on it and it worked fine out of the box.
Then I thought I would upgrade to 8.04.

I copied the ubuntu-dell-reinstall.iso file to a dvd.  Well I thought I did.  However I seem to have only copied a link to the file as when I double click the file it says 'The Link "ubuntu-dell-reinstall.iso" is Broken.' and the file if 0kb.

I then tried to upgrade to 8.04 through the Upgrade Manager and it got stuck at the point of processing the 'locales' file. (This has been seen on other forums.)
So I went back and reinstalled 7.10 and found the issue with the  ubuntu-dell-reinstall.iso file.
1) how can I get another ubuntu-dell-reinstall.iso file or can I mimic what it does in some other way or do I not need to worry about it?

I then upgraded to 8.04 and this seemed to go through OK.  I got the picture of the heron on the brown background. But I could not find where I could see the current version number of Ubuntu installed.

2) I look in the /etc/apt/sources.list and it still has 'gutsy' instead of the expected 'hardy' on each line.  Do you think the upgrade has worked correctly?

3) The wireless no longer works. The light does not come on, but there is a fix to this on the Dell website. The laptop has a 3495abg card in it. The wireless can see all of the local networks.  I select mine and enter the password but it fails to connect.  This seems to have been mentioned in a number of forums but there does not seem to be a fix to it. 

Thanks in advance

---

### Post by Spooky5 on 2008-07-19
This site has a link to the the dell re-install isos.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")

---

### Post by Cclips on 2008-07-20
You need to update the dell PPA sources to reflect the change to Hardy, check the dell Wiki, it has all the information ya need.

---

### Post by kesstephen on 2008-07-20
thanks to both of you.

I have downloaded the ...reinstall.iso from the dell page which was mentioned and have got the laptop back to the state it was delivered in.  So for now I am going to hold off going up to 8.04 and learn more about ubuntu/linux before another attempt is made.

As far as the ppt issue.  The problem was that after I upgraded to 8.04 all of the other lines in the sources .list file also had 'gutsy' rather than 'hardy' and I felt that something must have gone wrong for this to happen.

thanks again for your help.

---

