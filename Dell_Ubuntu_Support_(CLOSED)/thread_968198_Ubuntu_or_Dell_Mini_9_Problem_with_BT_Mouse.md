---
title: "Ubuntu or Dell Mini 9 Problem with BT Mouse?"
date: 2008-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jazz1 on 2008-11-02
Okay, I finally got the Mini 9 on Friday, and got the Dell BT mouse working with no sweat. Day two and the mouse stops working. Going into the BT preferences I try to re-pair the device, and it says it is already paired. I can't figure out how to delete the Dell BT Mouse and start again. Can anyone help? 

Under "services" I see serial device and network box is unchecked. Should the be checked along with Audio and Input services?

I did a search but did not find anything that could help me. Sorry if this is obvious.

---

### Post by ArKay on 2008-11-03
> **jazz1 said:**
> Okay, I finally got the Mini 9 on Friday, and got the Dell BT mouse working with no sweat. Day two and the mouse stops working. Going into the BT preferences I try to re-pair the device, and it says it is already paired. I can't figure out how to delete the Dell BT Mouse and start again. Can anyone help? 

Under "services" I see serial device and network box is unchecked. Should the be checked along with Audio and Input services?

I did a search but did not find anything that could help me. Sorry if this is obvious.
As I look at my preferences box with my Apple BT mouse active the network service & serial service boxes are unchecked and they are both listed as stopped as well - so that isn't your problem.

On the General pane do you have 'select class of device' checked ?

On the Mode of operation (on the xxx-x) pane do you have the BT adapter discoverable and connectable ?

If you go to first pane (xxxx-x) of your preferences you should see a list of bonded devices at the bottom. If you click on the device name you should then get the 'Delete' and 'Remove Trust' buttons to become available. From there you can either attempt to kill it and retry - or just makein untrusted and go through the pairing again.

   
Sadly that's all I can come up with - Hope it works for you.

---

### Post by jazz1 on 2008-11-06
> **ArKay said:**
> As I look at my preferences box with my Apple BT mouse active the network service & serial service boxes are unchecked and they are both listed as stopped as well - so that isn't your problem.

On the General pane do you have 'select class of device' checked ?

On the Mode of operation (on the xxx-x) pane do you have the BT adapter discoverable and connectable ?

If you go to first pane (xxxx-x) of your preferences you should see a list of bonded devices at the bottom. If you click on the device name you should then get the 'Delete' and 'Remove Trust' buttons to become available. From there you can either attempt to kill it and retry - or just makein untrusted and go through the pairing again.

   
Sadly that's all I can come up with - Hope it works for you.

That did it thank you so very much! There are so many options it makes it hard to know where to start. Again, thanks!

---

