---
title: "Remmina bug defaults to minimal quality settings"
date: 2014-08-23
forum: Desktop Environments
---

### Post by jcllings on 2014-08-23
This is a known issue but I'm searching for a work-around. Link to the bug is noted below but in a nutshell, the GUI doesn't change the quality so you get stuck with something I can barely stand to look at. 

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1345602](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1345602)

I note the last few lines of :  ~/.remmina/remmina.pref
are: 
...
vte_allow_bold_text=false
vte_lines=512
rdp_use_client_keymap=1
rdp_quality_0=0
rdp_quality_1=7
rdp_quality_2=0
rdp_quality_9=80

So, in theory if you knew what to set the quality settings above to, you could get a higher quality than the minimal setting. 
Ideas anyone? Trial-and-Error hasn't been providing much in the way of predictable results.

---

### Post by jcllings on 2014-08-23
I've found the answer although it wasn't what I was looking for.  
The bug is on the global setting but there's also a similar setting in each connection. 

Open the main window and edit the connection. Select the Advanced tab and you will see a drop-down for Quality.

---

