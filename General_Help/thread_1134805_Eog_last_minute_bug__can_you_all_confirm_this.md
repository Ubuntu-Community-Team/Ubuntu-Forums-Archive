---
title: "Eog last minute bug  can you all confirm this?"
date: 2009-04-23
forum: General Help
---

### Post by mickbuntu on 2009-04-23
I found a bug in last minute jaunty or at least think I do. See if you are able to reproduce my bug which I have reported at: [https://bugs.launchpad.net/ubuntu/+source/eog/+bug/365334](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/365334)


> 


Think was able to pinpoint how to trigger it (but not sure yet see if you try this it wakes the bug up). Perform the following steps:

1. Go to a folder with lots of pictures
2. Inside of eog enable "image collection" from the file --> view menu. in the image collection select few pictures by clicking on them individually with mouse. Now stop. 
3. Close eog
4. click on any single picture in the picture folder or try to call eog from the terminal.

Results:

   You should get eog lag of at least 1.5 ..... 1 1/2 minutes.  Eog empty or with a picture will still open but very late. You'll think it did nothing.   followed by the error if you started from the command line:

** (eog: random x): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.






If you can confirm this please get into my bug report thanks.

---

