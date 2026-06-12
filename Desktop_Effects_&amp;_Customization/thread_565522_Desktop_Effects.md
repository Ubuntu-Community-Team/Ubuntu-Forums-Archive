---
title: "Desktop Effects"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by evolushun on 2007-10-02
When trying to access my Desktop Effects, I get this:

"The Cosmposite extension is not available."

How do I get this to work?

---

### Post by HokeyFry on 2007-10-02
what video card to you have

---

### Post by pluviosity on 2007-10-02
Did you enable the restricted driver for your card?  I'm going on a limb here and guessing you have an ATI card because that happened to me when I tried to enable desktop effects after enabling the restricted driver.

ANYhow, if that is the case, you need to get XGL.  [http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by evolushun on 2007-10-02
Yes...I have an ATi onboard graphics card.

---

### Post by Rupertronco on 2007-10-02
Then you need to be in an XGL session to use compositing.

---

### Post by evolushun on 2007-10-02
I ran that tutorial to the T and it doesn't seem to work.  Is there something I can post here to show you if I did it right?  Or if my system is working?

---

### Post by Rupertronco on 2007-10-04
Yeah post your X11/xorg.conf file and the model number of your card. Also you should explain how and if you installed the xserver-xgl package, as well as how you configured it.

---

