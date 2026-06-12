---
title: "Language selection not working properly"
date: 2009-05-07
forum: Desktop Environments
---

### Post by Koen De Voegt on 2009-05-07
I'm running kubuntu 9.04 KDE is set to use Dutch, and most applications are in Dutch, but some major ones that I know have good translations are running in English. Firefox, Thunderbird, Pidgin, OpenOffice, ... So mostly or maybe all non KDE applications. I've had this problem since 8.10. I Have tried to look for more translations in the packet manager but didn't find anything. Anybody an idea on how to fix this?

---

### Post by Screwdriver0815 on 2009-05-07
> Anybody an idea on how to fix this?
a simple but maybe rude suggestion would be: contribute to the project(s) and help the translators. Normally when there is no language package for an application, then it is not translated.

In our translation team (for Ubuntu) we have loads of work and when the new version is finished we always still have packages untranslated because we do it in our spare-time and don't work fulltime on the translations.

---

### Post by Poborskiii on 2009-05-08
For complete Dutch localisation you need:
language-pack-nl
language-pack-gnome-nl
language-pack-kde-nl
language-support-nl

For Dutch translations of Gnome aplications you need package language-pack-gnome-nl, for Thunderbird and Openoffice package language-support-nl, for others (Fifefox, etc.) language-pack-nl

---

### Post by Koen De Voegt on 2009-06-07
Thank you both for your reply. 
   
  @Screwdriver0815: Language support has always been one of the places where Linux outperformed Windows & MacOS. So for someone running the stable version all major software is normally translated right away. 
  
  @Poborskiii: From that list I was only missing language-pack-gnome-nl and I'm still not sure I need it.
  
There seems to be an inconsistency in Kubuntu. In System Settings > Regional & Language KDE and it's apps follow the settings in this window, while FF, TB, OOo and others follow the System Language setting. This last setting seems to remain English even when installing Kubuntu in Dutch. This is what had me confused. Is this something I should report as a bug? Where and How?

---

