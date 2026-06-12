---
title: "No option to hibernate from gdm"
date: 2010-12-02
forum: Desktop Environments
---

### Post by bedege on 2010-12-02
Hi
I'm using Xubuntu 10.10 on a Toshiba laptop. Since I upgraded to Maverick, I noticed that the gdm login screen does no longer offer the option to hibernate my computer :(. The bottom right button can be used to "stop, "restart" or "suspend" but no "hibernate" option.
I looked at the option the [FONT="Courier New"]gconf-editor[/FONT] can toggle for [FONT="Courier New"]simple-greeter[/FONT], but no mention of "hibernate" option anywhere.
Do you have the same issues on your laptop? How to make that "hibernate" option reappear :confused:?
Thanks

---

### Post by bedege on 2010-12-03
Anyone with the same concern?
):P

---

### Post by bedege on 2010-12-04
up

---

### Post by bedege on 2010-12-08
up):P

---

### Post by Graeme.N on 2010-12-29
I've been having a similar problem on an Acer Aspire 3054WXMi laptop, and after finding nothing helpful to this problem, I was about to post about that and other problems I'm having.  I decided to have one last "poke around" before I posted and ... I found ... the answer!!! \\:D/

Go to "Applications" - "Settings" - "Settings Editor".  Choose "xfce4-session" on the left and then open "shutdown" on the right and you'll see 2 settings: "ShowHibernate" and "ShowSuspend", whose values are probably set to "false".  Select the setting you want to change, click the "Edit property" button (looks like a pencil) and tick "Enabled" and click "Save".  Close out of the Settings Editor and you should find that hibernate and/or suspend (depending on your selections) options will now be available to you.

Enjoy! - I know I will! \\:D/

TTFN.,
Graeme

---

### Post by java.artisan on 2011-03-21
Thanks man ! :-)

---

### Post by bedege on 2011-03-24
Hi there
I wanted to test the solution proposed. I checked on two machines (one running Xfce4.6, the other Xfce4.8) but none of them showed "shutdown" on the right, under "sfce4-session".
What Xfce release do you have?

---

