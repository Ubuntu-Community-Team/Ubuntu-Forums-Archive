---
title: "volname results have whitespace problem"
date: 2010-07-07
forum: Desktop Environments
---

### Post by targus on 2010-07-07
How do I get rid of the blank characters that volname outputs?

As an example, for volume name of "FAMILY_GUY_VOLUME_6_DISC_2" then the output is:

vadmin@ubu1004:~$ vol=`volname` 
vadmin@ubu1004:~$ echo "$vol-dvd.iso"
vadmin@ubu1004:~$ FAMILY_GUY_VOLUME_6_DISC_2     -dvd.iso

vadmin@ubu1004:~$ volname |wc
      1       1      33

vadmin@ubu1004:~$ echo "FAMILY_GUY_VOLUME_6_DISC_2" |wc
      1       1      27

EDIT:
Ok, this is even more annoying because I see the extra spaces but when viewed in this post the extra spaces are squeezed out.
FAMILY_GUY_VOLUME_6_DISC_2**[COLOR="Red"]?????[/COLOR]**-dvd.iso
I put the red question marks as place holders to show where the whitespace shows up.  You can see that the wc command actually does see the hidden characters.

---

