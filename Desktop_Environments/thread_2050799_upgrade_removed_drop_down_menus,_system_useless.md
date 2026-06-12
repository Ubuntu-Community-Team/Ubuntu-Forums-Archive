---
title: "upgrade removed drop down menus, system useless"
date: 2012-08-31
forum: Desktop Environments
---

### Post by zeelog on 2012-08-31
Upgraded from 10.1 to 11.04 and lost my drop down menus. I can't
start anything or do most anything. Will I have to expunge Ubuntu ?
Or is there a fix ?

---

### Post by JRV on 2012-08-31
This works in 12.04.
```

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

```
Log out and back in, the menus are on the Ubuntu icon in the upper right.

---

### Post by zeelog on 2012-09-01
sudo add-apt-repository ppa:diesh/testing
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~diesh/+archive/testing](https://launchpad.net/api/1.0/~diesh/+archive/testing)
ed@ed-System-Product-Name:~$ 
  Well, it looked too good to work anyway. 
  I tried it in root to and I got the same error.
  Any idea what this error means and what do they want ?
  I will never ever do another Ubuntu "upgrade".

---

### Post by cortman on 2012-09-01
> **zeelog said:**
> sudo add-apt-repository ppa:diesh/testing
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~diesh/+archive/testing]("https://launchpad.net/api/1.0/%7Ediesh/+archive/testing")
ed@ed-System-Product-Name:~$ 
  Well, it looked too good to work anyway. 
  I tried it in root to and I got the same error.
  Any idea what this error means and what do they want ?
  I will never ever do another Ubuntu "upgrade".

By "drop down menus" I assume you mean the Applications/Places menus from Gnome 2?

---

### Post by zeelog on 2012-09-01
Yes Cortman. I don't know how to get them back. The upgrade has
 either hidden them or they are zapped. Either way, Ubuntu is
  rather useless now.
 Got any ideas ?

---

### Post by jerome1232 on 2012-09-01
> **zeelog said:**
> Yes Cortman. I don't know how to get them back. The upgrade has
 either hidden them or they are zapped. Either way, Ubuntu is
  rather useless now.
 Got any ideas ?

Do you have a launcher bar on the left-hand side of your screen? Or are you missing panels entirely.

What session are you logging into?

---

### Post by brolin_1911a1 on 2012-09-01
Zeelog, I'm going to make a guess as it's been a year since I "upgraded" to 11.04 and discovered the same problem you're having.  I corrected it then by logging out (not a total shutdown) to the user login screen.  

I believe you'll see a "gear" icon in the extreme upper right corner of your screen.  Clicking on that should give you the option to shutdown/logout/restart.  Choose log out.  When you log back in, before hitting <return> look down at the lower right corner.  In quite small type there should be a checkbox next the words "classic login" or words to that effect.  Check that box.  Then finish logging in.  From now on, you should be logged in with the classic Gnome desktop interface.

Warning: Once you've done that, DON'T upgrade to 11.10 or 12.04 because that option has been completely removed from those versions.  I made that mistake on one computer and the only "fix" I've found so far has been to install Linux Mint 13 Cinnamon as a third boot option.  I am, at this very moment, trying to find a way to "upgrade" Ubuntu 12.04 to Kubuntu 12.04 to get rid of that Gottverdamt Unity interface.  I heard that Gnome will be once again offered for a version of 12.10; If so, I'll definitely be upgrading to that.

---

### Post by jerome1232 on 2012-09-01
> **brolin_1911a1 said:**
> Zeelog, I'm going to make a guess as it's been a year since I "upgraded" to 11.04 and discovered the same problem you're having.  I corrected it then by logging out (not a total shutdown) to the user login screen.  When you log back in off that screen, before hitting <return> look down at the lower right corner.  In quite small type there should be a checkbox next the words "classic login" or words to that effect.  Check that box.  Then finish logging in.  From now on, you should be logged in with the classic Gnome desktop interface.

Warning: Once you've done that, DON'T upgrade to 11.10 or 12.04 because that option has been completely removed from those versions.  I made that mistake on one computer and the only "fix" I've found so far has been to install Linux Mint 13 Cinnamon as a third boot option.  I am, at this very moment, trying to find a way to "upgrade" Ubuntu 12.04 to Kubuntu 12.04 to get rid of that Gottverdamt Unity interface.  I heard that Gnome will be once again offered for a version of 12.10; If so, I'll definitely be upgrading to that.

This is in all respects, wrong. Under 12.04 you can use Unity, Gnome-Shell, Gnome-Classic and any other DE you want to use. You just need to click the Ubuntu Icon near your name at the login screen and select the session you want to log into.

---

### Post by brolin_1911a1 on 2012-09-01
> **jerome1232 said:**
> This is in all respects, wrong. Under 12.04 you can use Unity, Gnome-Shell, Gnome-Classic and any other DE you want to use. You just need to click the Ubuntu Icon near your name at the login screen and select the session you want to log into.

Sir!  I disagree.  My post was not wrong in all respects!  Just in several respects. <sheepish grin>

The procedure I offered for Zeelog to get back his Classic Gnome desktop was valid, worked for me, and should work for him in Nasty Narwhal v11.04.  It did not, however, work for me when I installed Obstreperous Octopus (v11.10) or Precocious Porpoise (12.04.)  In fact, my inability to get rid of that "Unity" DE was what led me to install Linux Mint 13 on my computer and look into removing Ubuntu entirely.  But....

Immediately after I posted my reply to Zeelog and probably while you were in the process of replying to me, I discovered this post/thread: [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370).  I followed the directions given there and am happy to report that for the first time since I installed Precise Pangolem in May, I now have nice, familiar, Gnome DE again.  I am a happy camper and feel certain that if Zeelog visits that thread it will solve his problems also.  I'm most happy to say that I was wrong, you are correct, and Gnome can be enabled on 12.04.

---

### Post by jerome1232 on 2012-09-01
> **brolin_1911a1 said:**
> Sir!  I disagree.  My post was not wrong in all respects!  Just in several respects. <sheepish grin>

:lolflag: touche good sir, touche. 

I just wanted to point out your, by far, not hedge pinned into using unity if it doesn't float your boat.

---

### Post by 1script on 2012-09-01
Just went through this ordeal yesterday : [http://ubuntuforums.org/showthread.php?t=2050760](http://ubuntuforums.org/showthread.php?t=2050760)  Classic Menu Indicator did the trick for me. It even picked up all the customised menus just the way I left them in 10.10. Install it the way JRV says in the earlier reply above.  Take a bit to get used to since the menu is on the right and all the sub-menus open up as mirror images of what it was on the old system, but at least they are all there.

---

### Post by brolin_1911a1 on 2012-09-01
> **jerome1232 said:**
> :lolflag: touche good sir, touche. 

I just wanted to point out your, by far, not hedge pinned into using unity if it doesn't float your boat.

You were quite correct in doing so and I do appreciate it.  When I first upgraded from 10.09 to 11.04, I spent nearly a week searching the 'net for a way to escape that fondle-slab interface that had been imposed on my laptop with no warning. Logging out and then back in using that all but unnoticeable classic option proved the answer. But... when I then upgraded another machine from 11.04 to 11.10 and then 12.04 in a (so far) fruitless attempt to get a wireless adapter recognized, that trick didn't work.  I found myself stuck with Unity and the amount of resultant frustration is hard to express.  I really was happy, nay sir, overjoyed to find that thread posted above and to find that it worked.  I expect that by the end of this weekend I'll have upgraded both my old Celeron machine and my ACER Athlon II laptop from 11.04 to 12.04 as a result of that newfound knowledge.

---

### Post by cortman on 2012-09-01
> **zeelog said:**
> Yes Cortman. I don't know how to get them back. The upgrade has
 either hidden them or they are zapped. Either way, Ubuntu is
  rather useless now.
 Got any ideas ?

I'm putting the finishing touches on kansasnoob's (of this forum) thread on the Gnome Classic environment. See [here]("https://help.ubuntu.com/community/GnomeClassicTweaks")- it should explain how to install it and how to tweak it to fit your fancy. :)

Good luck!

---

### Post by zeelog on 2012-09-02
I do not have any gear icon of any kind any where.
 All I have are a few icons that I had before, like
 Firefox, my email client, and two Xterms. Thank goodness
 for the Xterms. I use them to log out with the reboot
  or shutdown -h now command. 
 If you can tell me how to choose a "classic" gui and
 get back my drop-down menus by using the command line
 I could do that in Xterm. Otherwise, there is nothing
 to click on except Firefox and my email client.
    I was hoping there would be an apt-get install <filename>
 kind of solution since something is obviously missing.
 Why would Ubuntu run faulty upgrades ?  I'm rather upset.
     Thank you for your help. It is appreciated.

---

### Post by cortman on 2012-09-02
> **zeelog said:**
> I do not have any gear icon of any kind any where.
 All I have are a few icons that I had before, like
 Firefox, my email client, and two Xterms. Thank goodness
 for the Xterms. I use them to log out with the reboot
  or shutdown -h now command. 
 If you can tell me how to choose a "classic" gui and
 get back my drop-down menus by using the command line
 I could do that in Xterm. Otherwise, there is nothing
 to click on except Firefox and my email client.
    I was hoping there would be an apt-get install <filename>
 kind of solution since something is obviously missing.
 Why would Ubuntu run faulty upgrades ?  I'm rather upset.
     Thank you for your help. It is appreciated.

You're not paying enough attention. The gear icon is **when you log in**, not after you've logged in.
It's not a faulty upgrade. The desktop you're using is called Unity. It's different from Gnome. If you like it, great. If you don't, follow the instructions I gave in that link to get Gnome classic back. Since it's an upgrade, you probably don't need to install anything. Just choose which desktop environment to use **when you log in** (when you give your username and password).

---

### Post by zeelog on 2012-09-04
Thank you Cortman !  I've got the Classic gui going and ALL IS GREAT !
  And it was so EASY to do ! One little click and that was it.
  BAD BAD Unity !  Good Good Classic !  I'm very happy.
  Thank you Very much !

---

### Post by cortman on 2012-09-04
> **zeelog said:**
> Thank you Cortman !  I've got the Classic gui going and ALL IS GREAT !
  And it was so EASY to do ! One little click and that was it.
  BAD BAD Unity !  Good Good Classic !  I'm very happy.
  Thank you Very much !

No problem. :) Glad you got it working.

---

