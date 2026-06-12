---
title: "adobe reader not default for pdf in firefox"
date: 2009-02-03
forum: General Help
---

### Post by groundnut on 2009-02-03
For stand alone files/documents I managed to set the default for pdf's to Adobe Reader.

However pdf's within Firefox are still shown with Document Viewer.

How can I set the default for pdf in Firefox to Adobe Reader?

---

### Post by demosthenese on 2009-02-03
In Firefox, select Edit->Preferences->Applications Tab. Scroll down to 'PDF document' and select the action next to 'PDF document'. A drop down list will appear which will allow you to change the default action. Choose 'use other' and browse to your chosen application - usually in /usr/bin.

---

### Post by OrangeCrate on 2009-02-03
Did you install the "mozilla-acroread" plugin from Synaptic?

Description:

> 
Adobe Acrobat(R) Reader plugin for mozilla / konqueror

Adobe Reader is an Adobe Portable Document Format (PDF) files viewer.

This package contains the plugin for a www-browser like
mozilla/firefox/galeon/konqueror.


---

### Post by groundnut on 2009-02-03
Thanks,

Installing the mozilla-acroread plugin was sufficient.

---

