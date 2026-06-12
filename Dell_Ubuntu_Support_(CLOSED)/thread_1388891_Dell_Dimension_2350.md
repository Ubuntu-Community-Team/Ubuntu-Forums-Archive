---
title: "Dell Dimension 2350"
date: 2010-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vetigoodson on 2010-01-23
I'm taking a class called Unix concepts.  The proffessor is using Ubuntu for the entire class.  Instead of having to do my labs in the class until ten at night I would like to be able to do them at home.  So far though I haven't been able to get it to work on my old Dell.  My son tried installing it on our old HP and that didn't work either.  I have another computer as well, but after the bad luck I have had and the horror stories of installing it from another student that locked his computer completely up I'm not willing to put it on my good one.
Some information that might help someone help me.  The Dell has an Intel Pentium 4 processor at 2.5 GH speed and one gig of ram.
Things that I have done: 
I tried to install it off the 9.0.4 disk that the prof gave us.  It would let me chose the language, the Ubutunu display screen screen would come up with the yellow dot going back and forth on the red line, it stays their for about a minute, the red line starts to go yellow like it's loading, and then it frezes when the yellow gets right below the first U.  I have left it all night and it stays there.
I have tried installing it within windows off of the Ubuntu site.  That look more promising, as it actually said that it was installed.  It told me to reboot to finish the instalation.  When I did this it seemed as though it was going to work untill the screen went black with the cursor flashing at the top and then froze.
If anyone could help me be able to do my college homework I would apprciate it.  Thank You.

---

### Post by Dennis N on 2010-01-23
You might try changing the boot options and see if that helps. Read over this guide:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

In particular, part 3: "Changing the CD's Default Boot Options" on that page. Use f6 and try one or more of the options acpi=off, napic, and nolapic. 

This worked to get Xubuntu 8.10 working on a Dell 2300 a friend has (It is a Pentium 4 with Intel graphics of some kind). It might work also with Ubuntu, and maybe your 9.04 version? Worth a try.

Try the live CD mode first and see if graphics and sound all work properly.

---

