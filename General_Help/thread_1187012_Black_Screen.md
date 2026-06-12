---
title: "Black Screen"
date: 2009-06-14
forum: General Help
---

### Post by ij21 on 2009-06-14
I'm new to Linux. I had an ATI Radeon 9250E graphics card in my Acer T120E desktop. I installed ubuntu 9.04 with the linux swap, but there is no Linux driver for the card. Something didn't look right, so I took the card out. Now, linux cannot detect the change in hardware and the screen is black. What do I do now?

---

### Post by Comzee on 2009-06-14
Put the graphics card back in?

---

### Post by ij21 on 2009-06-14
I took the graphics card out because there isn't a linux driver for it

---

### Post by QIII on 2009-06-14
What did you replace it with?

Could you post the contents of your xorg.conf?

Don't look at it through the terminal, since I don't want you to hit a wrong key and bork something accidentally.  You will have all sorts of opportunities to do that when you have learned a little more about Linux.

Go to Places -> Computer -> Filesystem -> etc -> X11 and double click xorg.conf.  Open it in a text editor, C&P the contents here.

---

### Post by Comzee on 2009-06-14
Well I found this [here]("http://ohioloco.ubuntuforums.org/showthread.php?t=683291&highlight=low+resolution"). If you can at least get into a bash prompt your can reset your graphics. Hope that helps more than my last post.

---

### Post by ij21 on 2009-06-14
There is a graphics chip on the M board. 
 
I do not know what xorg.conf means, as I said I am new to linux - in any case the screen is black and I cannot log in

---

### Post by QIII on 2009-06-14
When you first start up and get past the POST, you should see some text in the upper left corner of your screen.  Those are some choices you have for booting.  Hit "Esc" and use the down arrow to select "Recovery Mode".

You will get a cart load of scrolling tty.  At some point that will all stop and you'll get to a blue screen with a menu in it.  Use the down arrow to get to netroot.  That will put you in a command line.

Type sudo apt-get install hwinfo

Type "y" when prompted.

Let all the tty finish.

Then type sudo hwinfo.  (This is brut force, but at the moment I can't remember the switch for just looking at your video hardware.)

You'll get a lot of stuff happening real fast, but eventually it will all stop.

Scroll back up and you should find the info about your video card.

Let us know the manufacturer and model.

---

### Post by QIII on 2009-06-14
If we are lucky and you have a vanilla video card, the next step will simply be to get rid of the ATI Driver that may have been installed.

That is as simple as going back to the command line and typing the following commands in order (waiting for some scrolling tty and a y/n prompt in the middle):

sudo apt-get remove --purge xorg-driver-fglrx

sudo dpkg-reconfigure -phigh xserver-xorg

That should get you to a state where you can get back into Gnome.  We can get a specific driver installed after that.

It's 2am for me.  I have to bail out.

Someone should be able to pick up on this.

---

### Post by ij21 on 2009-06-14
Thanks for help.
 
Could not scroll to graphics card info - don't know how to.  
 
The graphics card is SiS 661x 
 
There is still a black screen after removing fgrlx and reconfigure to get to Gnome

---

### Post by QIII on 2009-06-14
OK.  Sorry it took so long to respond.  I had some things to do this morning.

We may just have to try to reinstall.


A couple of questions if that is the case:

Is this a dual boot system?  That is, does it have both Windows and Ubuntu installed?

Do you have any files on the machine you want to keep?

If you use the LiveCD in "Try" mode without making changes, can you use Ubuntu?  If in "Try" mode, do your other hardware items like wireless cards work?

---

### Post by ij21 on 2009-06-15
Firstly I was setting this up to learn about Linux having used windows for years. I am, in no way a geek, but I can usually get things to work after a bit of trial and error, reading and asking etc.
 
I have cloned my original drive so that my data is safe and after messing about yesterday I decided to reinstall. When doing this and after a bit of reading, it seems that Ubuntu will not recognise the SiS 616fx graphics that is present in the chipset. I read that this is a common problem.
 
I find it amazing that Ubuntu 9.04 will not work properly with my ATI card or the SiS card on a chipset that must be the world over
 
I had it set up for a dual boot. But whats the point in going on? It just makes me believe that Linux is a long way off.
 
I am a teacher and our teckies at school are trying to convince us that Linux is the way the truth and light, but after three separate difficult experiences I am somewhat disillusioned.

---

### Post by QIII on 2009-06-15
It might be worth giving a different distribution of Linux a try.  I'm not an Ubuntu evangelist by any means.  I like it, I'm happy with it and it works for me.  It may not be everyone's cup of tea.

With regard to your chipset, it may the that Ubuntu does not play well with it, although that would disappoint me.  I have an ATI card and it works quite well.  But the driver is proprietary, so Ubuntu can't do anything in their development to make it better.  

Understand that Ubuntu does not have the massive resources of Redmond or Cupertino and may not be able to test and re-test every possible hardware combination that exists.  Nor do they have the massive weight to bring to bear to twist arms into compliance with compatibility, as Microsoft does.  Ubuntu is largely a community project involving volunteers around the world.  

It is possible that the problem you are running into will be addressed in the next version of Ubuntu, Karmic Koala.

Until then, don't give up on Linux.  Try a different distribution.  Nobody here will fault you.

Another possibility, albiet one that will cost a buck or two, is to buy a different brand (maybe nVidia) of grapics card -- not integrated, set your bios to detect that one first, and try that.  I know that is a bit much to ask, but I don't want you to be disappointed in a great OS because of a hardware incompatibility.

---

### Post by ij21 on 2009-06-16
Thank you for your help and kind words, perhaps you are right and I should aquire a new G card. I'm not giving up. Perhaps a recomendation for a budget priced card?

---

### Post by QIII on 2009-06-16
Hard for me to make a positive recommendation, since I don't know exactly what might be available on the other side of the pond.

I would say to stay AWAY from anything with an Intel chipset for now, since there seem to be regressions in Jaunty.  There are work-arounds, but that is more frustration.

And you know what your experience has been with AMD/ATI.

And anything on the very bleeding edge from anyone might be a gamble.

---

