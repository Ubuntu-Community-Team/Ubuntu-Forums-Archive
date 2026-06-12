---
title: "Ubuntu Newbie Needs Help With Dual Monitors and Slow Kb/Mouse Response"
date: 2009-02-14
forum: General Help
---

### Post by alunparry on 2009-02-14
Hi

Sorry to post two issues in one but I tihnk they both belong in this section about Desktop Effects.

I can only get a usable kb/mouse response if I switch off all visual effects. Even then its more sluggish than I'd like albeit a few split seconds.

If I put it on normal visual effects its dreadfully sluggish.

Any ideas how I can fix it?

The only other thing I need to do is sort my dual monitors out as only one is working so far.

I have 2 graphics cards. They are

a) ATI Technologies Inc RV370 5B60 [Radeon X300(PCIE)]
b) ATI Technologies Inc Radeon RV100 QY [Radeon 700/VE]

Can anybody help at all?

Much gratitude in advance.

Al 8-)

---

### Post by khelben1979 on 2009-02-14
First off you shold make a backup of this file: /etc/xorg.conf

This is how to do it:
```
sudo cp /etc/X11/xorg.conf /etc/xorg-old.conf
```

When you have done this, go to the ATi website and download appropiate drivers for your graphics card ( [http://www.ati.com](http://www.ati.com) )

Install the driver and make sure to follow all of the instructions. [The ATi Catalyst]("http://en.wikipedia.org/wiki/ATI_Catalyst") will allow you to easy configure your 2 monitors.

---

### Post by alunparry on 2009-02-14
thanks.

i found that file in /etc/X11 rather than just /etc

is that the same one?

i have copied it for safekeeping anyhow.

i've downloaded the driver which is a .run file but when i double click it to run it, it doesn't run. it asks me what application to open it in.

i know its probably a really stupid question, but what do application do i choose?

thanks

al

---

### Post by khelben1979 on 2009-02-14
Yes, it's the right file you have found (I will correct myself on that line).

Okay, do this with the file and make sure you have super user priviliges:
```
sudo chmod 777 ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
```

This should work. And if it doesn't, then it might be due to the fact that they don't have 32bit driver for this specific ATi driver, at least not directly from the ATi website. Do you know if you're on a 32bit och 64bit computer over there?

---

### Post by alunparry on 2009-02-14
thanks.

ok i'm almost there.

upon install the final install screen says that the driver is now configured in basic mode .

For advanced i should either

a) run aticonfig from the console (tried that but looked incomprehensible to a newbie like me)

or 

b) AMD CCC:LE from Desktop Manager Menu (sounds like it'll be nicer to use but I can't find the Desktop Manager Menu anywhere).

Also, it didn't ask me to reboot to but this new set up in place but am wondering if that is actually necessary after all.

ta again

al

---

### Post by alunparry on 2009-02-14
aha! well i found the ATI Catalyst Control Centre (which I guess is what CCC stood for) in the Applications menu (top left of the screen).

However.....

when I click it I get an error message as follows:

-----------

There was a problem initialising Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed or the ATI driver is not functioning properly.

Please install the ATI driver appropriate to your ATI hardware, or configure using aticonfig.

-----------

hopefully i'm 90% there but that message might mean I'm back to being just 10% there.

any more ideas? really grateful for your help so far,

al 8-)

---

### Post by khelben1979 on 2009-02-14
Try to reboot to see if it changes anything.

---

### Post by alunparry on 2009-02-14
ok wish me luck....

hopefully will report back in a few ticks...

ta again

al

---

### Post by alunparry on 2009-02-14
nightmare. am typing this from my netbook.

when i rebooted it gave the initial ubuntu splash screen and followed it with a black screen

not even a terminal

i can do aanything

can you help

ta

al

---

### Post by khelben1979 on 2009-02-14
Since you created a backup file of your xorg.conf. Replace your existing xorg.conf with the backup file and rename the current file according to this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg-bad.conf
sudo mv /etc/X11/xorg-old.conf /etc/X11/xorg.conf
```

You must do this from a text console. Pressing ```
ctrl + alt + f1
``` will take you there. Also, if this does not work (nightmare scenario), you still have possibility to use the ssh command to login to your computer from another computer if they are attached in a network. I'm not sure how to do this myself, since I've never done it myself, but if it's critical you can always do some search on google or this Ubuntu forum on how to do this.

---

### Post by alunparry on 2009-02-14
i got a terminal on reboot at least but it says kinit: No resume image, doing normal boot

---

### Post by khelben1979 on 2009-02-14
Are you able to login to an account?

---

### Post by alunparry on 2009-02-14
yes i can do that. but i cant escape the cli into the gui

---

### Post by khelben1979 on 2009-02-14
If you have renamed the file which I mentioned earlier, everything should be back to the way it was before. Although, I suspect you need to reboot afterwards.

Have you done this?

---

### Post by alunparry on 2009-02-14
yep

thats why i no longer get the black screen and no longer have to  do ctrl alt f1 to get my cli

i get the cli straight away but it doesn't bring up the gui at all

it says instead kinit: No resume image, doing normal boot.....

then within the cli it asks for my username

so i log on but i cant get into the gui from here at all

---

### Post by emshains on 2009-02-14
> **alunparry said:**
> yep

thats why i no longer get the black screen and no longer have to  do ctrl alt f1 to get my cli

i get the cli straight away but it doesn't bring up the gui at all

it says instead kinit: No resume image, doing normal boot.....

then within the cli it asks for my username

so i log on but i cant get into the gui from here at all

Try typing "startx". See what happens and report.

---

### Post by alunparry on 2009-02-14
fatal server error: no screens found

---

### Post by emshains on 2009-02-14
> **alunparry said:**
> fatal server error: no screens found

You've screwed the driver/xorg.conf. Try fixing X through the recovery mode. You can get there by rebooting and choosing the recovery mode from grub ( to enter grub, press [esc] repeatedly after the bios screen) or you can run ```
sudo shutdown now
```.

After that, I suggest you install the video drivers from the restricted driver manager, and then make X use them. After that, you can continue researching your primary problem.

---

### Post by alunparry on 2009-02-14
whats the restricted driver manager

also i did actually try the fix x before and it didn't work

---

### Post by alunparry on 2009-02-14
tried it again and it diidnt work

---

### Post by emshains on 2009-02-14
Well, then, my friend, you should try your X.org config file backup, and running apt to get your drivers. But, since I am no expert at ATI drivers, I can't help you at the moment. I am really sorry for that, and I hope you will get ubuntu up and running in no time.

---

