---
title: "external mic"
date: 2009-05-14
forum: General Help
---

### Post by thundaraptor on 2009-05-14
i have a laptop with webcam and external mic.  how do i get linux capturing the external mic?  the webcam seems to work fine but i can't "talk" to me laptop...  i am particularly using this function with skype.  

cheers

jd

---

### Post by tacantara on 2009-05-15
The microphone dilemma is a road that I've traveled a few times.  I started a thread the first time I had this problem, and I received some excellent replies.  Check this out:  [http://ubuntuforums.org/showthread.php?t=1073884](http://ubuntuforums.org/showthread.php?t=1073884).  See if any of the fixes recommended there will do the trick.
 
If the fixes mentioned in the first thread don't do the trick, I ran a second thread for when I had the same problem after installing the KDE desktop package.  The advice I got there worked like a charm, and will also work in the GNOME environment. You can check that out here:  [http://ubuntuforums.org/showthread.php?t=1153117](http://ubuntuforums.org/showthread.php?t=1153117)
 
After applying the fixes, use the Sound Recorder tool to verify that the microphone is functioning and picking up your voice clearly.  If all is well, open Skype and go to the Options menu (Ctrl+o).  Select Sound Devices from the left pane, and set everything to Default Device.  Make sure the "Allow Skype to automatically adjust my mixer levels" box is unchecked.  Once that's done, go ahead and "Make a test sound" and "Make a test call" just for the additional peace of mind that all is well in Skype-world.
 
 
Hopefully one of these solutions gives you the desired result.  Good luck :)

---

### Post by nave.notnilc on 2009-05-15
Hello, I'm running Jaunty on my m1330, and the options in both of your solutions do not exist in kmix or alsamixer.  Any ideas?

---

