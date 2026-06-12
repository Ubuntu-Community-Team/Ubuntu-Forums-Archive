---
title: "typo in ufw wiki page ?"
date: 2012-10-21
forum: Forum Feedback &amp; Help
---

### Post by cogset on 2012-10-21
I didn't find a suitable place to post this,so I apologize in advance if this is the wrong section,however I think there may be a typo in this wiki page [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) ,as the highlighted lines don't make much sense as they are,is it possible that the first one should actually read "remove or edit" and the "or" removed form the second line? 


> **Enable PING**

 Note: Security by obscurity may be of very little actual benefit with modern cracker scripts. **By default, UFW allows ping requests**. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems. 
You need to edit **/etc/ufw/before.rules** and [COLOR=Red]remove edit[/COLOR] the following lines: 

# ok icmp codes -A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT -A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT -A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT -A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT -A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

[COLOR=Red]Change the "ACCEPT" to "DROP" or [/COLOR]

# ok icmp codes -A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP -A ufw-before-input -p icmp --icmp-type source-quench -j DROP -A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP -A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP -A ufw-before-input -p icmp --icmp-type echo-request -j DROP

---

### Post by cariboo on 2012-10-21
If you have a launchpad account, you can correct the errors yourself. If you don't have an account, you can create one [here]("https://login.launchpad.net/+new_account")

---

### Post by cogset on 2012-10-22
OK,but how does this work ? I just edit the page and no one supervises it?

---

### Post by cariboo on 2012-10-22
> **cogset said:**
> OK,but how does this work ? I just edit the page and no one supervises it?

The wiki administrators, will be notified of your edits. There is also peer review, if someone finds something that isn't right, or full of the wrong information, it will be noted and corrected.

---

