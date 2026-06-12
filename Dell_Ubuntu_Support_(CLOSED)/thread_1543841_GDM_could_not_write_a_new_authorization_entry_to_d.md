---
title: "GDM could not write a new authorization entry to disk"
date: 2010-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TonyMCalifornia on 2010-08-01
OMG  
I'm typing on this forum from my desktop, not the laptop that has the issue :)

Recently I tried to download a bunch of "software updates" on my mini 9 laptop that has ubuntu software.

I realize now, that the disk space is 100%, and tried to add/remove (remove) programs but received an error message doing that :

E: dpkg was interrupted, you must manually run 'dpkg--configure-a' to correct the problem. E:_cache-7opn () failed, please report.


So now, when I try to startup the computer, I get the message:

*GDM could not write a new authorization entry to disk. Possibly *out of diskspace. Error : No space left on device.

(btw I don't know how to get to a command line - please let me know how to do that too)

What is going on? I'm not paying Dell Tech Support money to talk with them over the phone. It is hard to understand them and I seriously don't want to spend more money for an "extended warranty" or extra phone support for this simple stuff.

Any ideas?
I have looked at other threads and just don't know if I should be pressing "0" o "2",etc. when rebooting,etc. on the DELL logo screen.
I don't know if this is related to a computer virus either, but I should just start with the basics here of getting the computer to load correctly.

---

### Post by TonyMCalifornia on 2010-08-01
I just did the instructions below and it temporarily? fixed the problem of starting the computer. It now says disk space use is 87%. 

I still have the problem with add/remove removing programs.

But how do I know this isn't going to happen again?
************
Do:

ctl+alt+F2

login at the prompt then type:

sudo apt-get clean

*************
I just tried this after posting this reply to fix the add/remove problem. (THIS FIXED THE PROBLEMS WITH ADD/REMOVE) wow
ctl-alt-F2, login, then typed:
sudo dpkg --configure -a

---

### Post by snowpine on 2010-08-02
> **TonyMCalifornia said:**
> But how do I know this isn't going to happen again?

Let me guess, you have the 4gb SDD, right?

You can install a lighter distro (such as Xubuntu) or [upgrade your storage]("http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand:RunCore:RunCore+PCI+Express+Mini+PCI-e+SSDs:Dell+Inspiron+Mini+9+PCI-e+SSDs").

---

