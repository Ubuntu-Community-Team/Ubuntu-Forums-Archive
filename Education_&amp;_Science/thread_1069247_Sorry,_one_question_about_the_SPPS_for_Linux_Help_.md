---
title: "Sorry, one question about the SPPS for Linux Help Thread"
date: 2009-02-13
forum: Education &amp; Science
---

### Post by shateredsoul on 2009-02-13
I found this.  I got as far as trying to install.. but it fails.  I'm not sure where to enter the first code (do I enter that in the terminal?) and also, in the following directions for the second code confuse me a little 

"you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:" 

Do I have to edit the code for the .bin file? How do I do this? So my basic question is... where do I enter the first code? and where do I enter the second code (what is it asking me to edit, and how do i do this)?  

I'm as newb as newb can get.. I would appreciate any help.  Even if you are not familar with spss maybe you can help me figure out what these directions are telling me to do. 

Thank you! ( i posted the directions from the post as well)


SPSS 16 for Linux + Hardy... it works
I just wanted to let anyone interested know that SPSS 16 for linux does work. At first impression everything works fine though the processing of analyses seems somewhat slower than on windows (same machine).

There were a few quirks I had to deal with to get it all going.

The installer is Java based and there currently is a bug that appears to cause a lot of Java based stuff to fail on Hardy. To be able to run the Java based installer run the following command:

Code:

export LIBXCB_ALLOW_SLOPPY_LOCK=true

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this... you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

Code:

export AWT_TOOLKIT="MToolkit"

Don't ask me what that does I didn't come up with it myself.

You can then create a launcher that will launch SPSS by using the command to \SPSS16\bin\spss rather than "SPSS" (in caps which is the regular launcher).

There you have it. I didnt come up with any of this myself but I pieced it together from random searches. (i.e. this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272](http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272))

To: Mods... is this the right forum section for this?

Hope this helps a few of you.

As far as I know there are no Java based problems in 7.10

---

