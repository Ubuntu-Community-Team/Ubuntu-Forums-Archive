---
title: "Sync palm treo 680 via bluetooth"
date: 2009-02-12
forum: Desktop Environments
---

### Post by drozzy on 2009-02-12
Sorry to repost this question, but I still get the 0x030B error on my palm Treo 680 when connecting to ubuntu 8.10. Could someone help me?
The original post is [here]("http://ubuntuforums.org/showthread.php?t=328880"), and here is the problem:

>  Sync palm treo 680 via bluetooth, Network error 0x030B on Treo.
Thanks to this forum i am able now to send and receive files (photos) from amd to my Treo.
I would also like to sync via bluetooth. To achieve this there is an excellent HOWTO at [http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html)
Setting it all up goes well untill The last item under the header 'Create a new network'.
I get ther error: 'Error:Serial: (0x030B)'

Can someone give me a hint on how to proceed?

---

### Post by drizad on 2009-05-06
yeah... I am stuck with 'Error:Serial: (0x030B)'...
please help...

---

### Post by grico on 2009-05-21
I also followed the same instructions, managed to pair my Treo 680 with my laptop but got the same message when testing the connection.

However, I tested sending a file from the PC to my Treo and this worked painlessly.

I then tried running a hotsync. This didn't work, and I got the following error message:

"Unable to initiate HotSync operation because the port is in use by another application."

I'm guessing this may be the meaning of the error code 0x030B that all three of us got?

Finally, I tried sending a file from my Treo to my laptop. That didn't work.

Can anyone offer any more help based on this information?

---

### Post by grico on 2009-05-21
Well, well... Problem solved, or at least partially.

I backtraced my steps through the guide at [http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html).

I deleted all the changes to scripts and restarted.

First I rebooted my laptop. Next I paired the device with the laptop through bluetooth. I then made sure I had the PalmSync applet running, and checked that both this and the device were set up to sync through bluetooth.

Next, I made sure I had the sync settings I wanted in Evolution. I did not bother to check the network settings. I just pressed HotSync, and everything apparentlyg worked just fine!

Going back to the network settings I still got the same error message when attempting to connect from the Treo, but HotSync seems to work.

HotSync backs up databases on the Treo, but it turns out the calendar in Evolution does not sync properly. It looks like it does, but when I check after the sync completes, nothing has been copied either from the device to the laptop or the other way... AAargh!

---

