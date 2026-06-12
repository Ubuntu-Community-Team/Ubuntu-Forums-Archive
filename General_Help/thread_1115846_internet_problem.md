---
title: "internet problem"
date: 2009-04-04
forum: General Help
---

### Post by ciocarlia.pastilata on 2009-04-04
hy all.i've installed ubuntu on the same partition with windows xp.when i'm in ubuntu the internet works fine, but when i open windows the internet is not working.it says"network cabble is unplugged",but the interent is working on ubuntu.so, can you tell me please what i should do to get the internet working on windows and on ubuntu?pls help.thanks.

---

### Post by accooper on 2009-04-04
OK, this happened to me on my own computer, but does not seem to be a problem on any of the lap tops I have installed 8.10 on.

1. Release your ip in XP here is how you do that.

       1. Click the Start button.
              * In Windows Vista:
                   1. In the search bar, type run.
                   2. Press the Enter key.
              * In Windows XP:
                   1. Select Run.
                   2. In the Open text box, type: cmd
                   3. Click OK.
       2. In the prompt window, type: ipconfig /release
       3. Press the Enter key.
       4. Type: ipconfig /renew
       5. Press the Enter key.
       6. Type: exit
       7. Press the Enter key.

Then in the same cmd box type ipconfig this should get you a new ip address.

If this doesn't help your network settings have been corrupted and you will need to reset them.  Only your isp can give you those.

In my case I had corrupted settings.  Hope this helps.

:guitar:

Andrew

---

### Post by ciocarlia.pastilata on 2009-04-04
> **accooper said:**
> OK, this happened to me on my own computer, but does not seem to be a problem on any of the lap tops I have installed 8.10 on.

1. Release your ip in XP here is how you do that.

       1. Click the Start button.
              * In Windows Vista:
                   1. In the search bar, type run.
                   2. Press the Enter key.
              * In Windows XP:
                   1. Select Run.
                   2. In the Open text box, type: cmd
                   3. Click OK.
       2. In the prompt window, type: ipconfig /release
       3. Press the Enter key.
       4. Type: ipconfig /renew
       5. Press the Enter key.
       6. Type: exit
       7. Press the Enter key.

Then in the same cmd box type ipconfig this should get you a new ip address.

If this doesn't help your network settings have been corrupted and you will need to reset them.  Only your isp can give you those.

In my case I had corrupted settings.  Hope this helps.

:guitar:

Andrew

ok man.i'll try this.thanks a lot.cheers.:)

---

