---
title: "How do you add web mail notification and calendar to Gnome 3?"
date: 2012-04-06
forum: Desktop Environments
---

### Post by Svante65 on 2012-04-06
Is it possible to add web mail notification and calendar to Gnome 3?
What I want is to get notifications from Gnome 3, when I receive a mail in my gmail and maybe also hotmail if possible.
I also would like my Google calender to be connected to the Gnome 3 calendar. Is that possible?

---

### Post by cottfcfan on 2012-04-06
gm-notify is in the repos, install & configure and it integrates with the envelope icon on your panel.
As for your calendar, I think if you install xul-ext-lightning, and configure it with Thunderbird, you should be able to access your google calendar from add-ons.

---

### Post by Svante65 on 2012-04-07
> **cottfcfan said:**
> gm-notify is in the repos, install & configure and it integrates with the envelope icon on your panel.
As for your calendar, I think if you install xul-ext-lightning, and configure it with Thunderbird, you should be able to access your google calendar from add-ons.
Can it be done without including Thunderbird or Evolution? It seems that Gnome 3 is hooked up to Evolution.
I want to total web-enable my Gnome 3 desktop, without using any local installed programs like Thunderbird and Evolution. Maybe it's not possible yet???

---

### Post by cottfcfan on 2012-04-07
> **Svante65 said:**
> Can it be done without including Thunderbird or Evolution? 
I Think so.
Configure gm-notify to use "gmail web interface" instead of email client, then when you click on the envelope & inbox, it should connect you to the web & your gmail account.

---

### Post by Frogs Hair on 2012-04-07
You may want look at this link, it describes a method to integrate Google Calendar in the Gnome Shell without Evolution. [http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html](http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html)

---

### Post by Svante65 on 2012-04-08
> **Frogs Hair said:**
> You may want look at this link, it describes a method to integrate Google Calendar in the Gnome Shell without Evolution. [http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html](http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html)
Works fine !:p Thanks. Hope it's safe....
Gnome should make an integration with Google Calendar as a standard option.
Maybe in the future...

---

### Post by Svante65 on 2012-04-08
> **cottfcfan said:**
> I Think so.
Configure gm-notify to use "gmail web interface" instead of email client, then when you click on the envelope & inbox, it should connect you to the web & your gmail account.
Is there a 'gm-notify' that can include other web-mail accounts like hotmail?

---

### Post by cottfcfan on 2012-04-08
> **Svante65 said:**
> Is there a 'gm-notify' that can include other web-mail accounts like hotmail?

If you search "hotmail" in synaptic, there seem to be 1 or 2 apps.
How well they work i don't know as i don't have a hotmail account.
Just try them!

---

### Post by Svante65 on 2012-04-08
> **cottfcfan said:**
> If you search "hotmail" in synaptic, there seem to be 1 or 2 apps.
How well they work i don't know as i don't have a hotmail account.
Just try them!
I will install synaptic and try that :p

---

