---
title: "Ubuntu 810 in a Dell Dimensia..?"
date: 2009-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DonaldJ on 2009-02-27
I've tried 8 installs every way I could think of, after formatting, in W2000, beside W2000, on its own, as the CD... and still no work...
I must be doing something silly wrong..?

So now this 20-gig hd is formating with the W98 CD..  
Then I plan to pull the battery for 10 to 20 minutes...  
Then reinstall the battery...   
Then reboot with the Ubuntu-810(386) Image CD in the slot...

What is the best thing to do now..? I'm gonna get this thing working "come hell or high-ubuntu"...

---

### Post by superprash2003 on 2009-02-27
what is the error message you get?? do you see a busybox window?

---

### Post by muteXe on 2009-02-27
Have you checked the cd's okay?  md5 checksum and that kinda thing?

---

### Post by DonaldJ on 2009-02-27
I can't even get the PC to see the Ubuntu CD...  This Dell is a real Pain...
I've changed the CD ROM, and the hd, and still it doesn't register this Ubuntu CD, which installed in two other towers without incident...

OK..  Attempt one: Boot, and I get "Invalid installation disk"...

Attempt two: Pull Battery a few minutes..  Reinstall Battery.. Reset boot to CD first..

It's started to install...  But when it comes time for reboot, it's gonna get stuck at "sudo command prompt"..  and I've tried all the codes I found in the forum to try to get through this...  Even with 15 spare gigs in the hd I get the message it is out of memory moments after it started the updates from sudo command...  It's installing now...  I'll post any messages that happen...

---

### Post by DonaldJ on 2009-02-27
At command prompt I ran:   

sudo apt-get -f install  

Enter

sudo apt-get update && sudo apt-get dist-upgrade

________________________________

Message:

"Need to get 278 MB of Archives.
After this operation 150 MB of additional disk space will be used
E: You don't have enough disk space in  /var/cache/apt/archives/.

Ubuntu@ubuntu:~$_

________________________________


This is where it always gets stuck, if it even gets this far, which is rare...

This Dell is troublesome trying to install anything into it...

---

### Post by DonaldJ on 2009-02-27
I ran a barrage of troubleshooting checks inside this old Dell tower...  
I found a weak battery.  Can a weak battery cause these installation problems?

---

### Post by DonaldJ on 2009-02-27
> **muteXe said:**
> Have you checked the cd's okay?  md5 checksum and that kinda thing?

The CD is OK... I ran checks in another PC...  It's the same CD I've used to install in other PC's...  The CD ROM is OK..  I tested it in the other PC...

---

### Post by DonaldJ on 2009-02-27
Just a thought off the top..  If I were to bump the BIOS, could that make it better for Ubuntu to install on the Dell..?

___________________________


I did a little surfing on the problem...  It seems this thread comes the closest to solving these Dell problems... And near the end of the thread the wise guys start insulting the OP like happens in a lot of forums when things go beyond the player's comprehension...

[http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=242549&messageID=2349106](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=242549&messageID=2349106)

In that thread there's a little talk about the battery...

I'm gonna try the Dell's Ubuntu install without the battery in...
Then try it with a new battery in...

And later I'll try the iMac's Ubuntu install without the battery in, then a new battery...  Maybe there is something in this "battery thing" causing install problems..?  Maybe that's all it is..?

In that guy's Dell, it sounds like maybe he has the battery adjustment bridge set on the wrong pins.., or maybe it fell off, or got pulled off..?
Maybe Dells are bad for those bridges slipping off..?
I better take a closer look into the tower.. and do a few checks on solder joints too...  This is very likely a common Dell hardware problem...  It's probably posted all over the Net as a problem for windows installs too..?

[http://www.google.ca/search?hl=en&q=Dell+dimension+won%27t+install+an+operating+system&start=10&sa=N](http://www.google.ca/search?hl=en&q=Dell+dimension+won%27t+install+an+operating+system&start=10&sa=N)

I bet the solution is in there somewhere...  It looks like a couple hours effort...  I wonders if I'm closer to getting Ubuntu in this Dell..?

---

### Post by DonaldJ on 2009-02-28
The battery thing didn't help...  Changing hd's did nothing...  installing a preloaded hd didn't do it...  I'm stuck with this one..?

I bet that when the reason comes clear for these Dells being so difficult to install Ubuntu in, it will probably be a little hardware problem that cant be fixed without making a serious modification to the mother board...

Hmm..?  Could it possibly be a setting on the mother board..?  One of those little switches, or a connector..?

Could this possibly be the cure for those hard to install iMacs..?

I'm just stabbing in the dark.. but it's all I've got now, to try to determine the reason for the glitch...  I've tried everything I found in all the forums...  Someone wrote that he tried 50-times before he gave up...

Has anyone tried changing the switches on the mother boards?..  
Who has deep knowledge about what those shunts and switches do in relationship to installing bootable CD's..?

Are there specific BIOS's that Linux's and Ubuntu just won't install on..?

---

### Post by bapoumba on 2009-02-28
Moved to Dell.

---

