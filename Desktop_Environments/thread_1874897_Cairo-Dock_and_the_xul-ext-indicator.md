---
title: "Cairo-Dock and the xul-ext-indicator"
date: 2011-11-04
forum: Desktop Environments
---

### Post by johnathanamber on 2011-11-04
Hey everyone,

I am running Xubuntu 11.04 with Cairo-Dock 2.4.0-2.

I am also running Thunderbird 7.0.1.

I am trying to get an indicator working that will display at least the number of incoming messages.

I've already installed xul-ext-indicator via the ruben-verweij/thunderbird-indicator PPA.

I can't seem to get it working with the Messaging Menu.

Any ideas would be grateful.

Thank you and God bless,
Johnathan

---

### Post by LewisTM on 2011-11-04
If you want to see the number of incoming messages in a tray icon, the only tool I know of is the Firetray Thunderbird Addon.
It will show up in the notification area however, not as an indicator. That may not be best for Cairo-Dock but sits well in a XFCE panel.

Otherwise the messaging menu applet in Cairo — which is a clone of the messaging indicator — works well for me and turns blue when new mail arrives. 
In my experience there is no need for the xul-ext-indicator in 11.10, I removed that PPA entry.

---

### Post by johnathanamber on 2011-11-04
Thanks for your help, your suggestions of Firetray lead me to a solution.

Gnome Integration 0.4.3 works well with a popup for each new message.

You can search it via Extensions in Firefox.

Thanks again for your help.

God bless,
Johnathan

---

### Post by Bobhuber on 2011-11-04
> **johnathanamber said:**
> Hey everyone,

I am running Xubuntu 11.04 with Cairo-Dock 2.4.0-2.

I am also running Thunderbird 7.0.1.

I am trying to get an indicator working that will display at least the number of incoming messages.

I've already installed xul-ext-indicator via the ruben-verweij/thunderbird-indicator PPA.

I can't seem to get it working with the Messaging Menu.

Any ideas would be grateful.

Thank you and God bless,
Johnathan
I'm not running Xubutu and am running the daily-build of Cairo-Dock.I use the mail app that comes with the dock which does exactly what you are trying to do.

---

### Post by johnathanamber on 2011-11-17
> **Bobhuber said:**
> I'm not running Xubutu and am running the daily-build of Cairo-Dock.I use the mail app that comes with the dock which does exactly what you are trying to do.

Hey Bobhuber,

I couldn't get it configured right to work with Thunderbird and check the accounts that Thunderbird has.

What did you do to configure that Mail applet in Cairo-dock?

---

### Post by Bobhuber on 2011-11-18
> **johnathanamber said:**
> Hey Bobhuber,

I couldn't get it configured right to work with Thunderbird and check the accounts that Thunderbird has.

What did you do to configure that Mail applet in Cairo-dock?
Your not giving me enough info to tell you exactly but I'll give you the procedure for a standard POP3 mail server.
I've seen problems in SUSE but none in any of the Ubuntu releases with the app.
You can add multiple accounts with it if needed. Open the CD mail configuration screen. Mail application - Add a mail account  - Action on new mail (add your preferences)-Mail application-Preferred App - thunderbird - account type - POP3 - click add.
This will create a thunderbird title on top of the screen- click on that-enter your pop3 mail server  address (this will normally be pop-server.<something> and MUST be correct)-you shouldn't have to enter a port number unless you ISP uses something funcky for incoming,the default is 110- enter user name and password- click apply.

---

