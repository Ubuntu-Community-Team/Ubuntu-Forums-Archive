---
title: "After Lucid Upgrade -- Account stuck with Turkish Keyboard layout"
date: 2010-05-16
forum: Desktop Environments
---

### Post by T_W on 2010-05-16
Just upgraded my PC to Lucid (from Karmic).

One of the user accounts is now "stuck" with the Turkish keyboard layout.  Every time that account logs in, the keyboard get set to a Turkish keyboard.

I have used the Keyboard control panel to Remove the Turkish layout, but it keeps coming back on relogin.  Any way to permanently switch to US

---

### Post by T_W on 2010-05-17
Found it.  Somehow the keyboard setting had gotten changed in the login screen (after I select the user account from the list of configured users).

Switching this back to US resolved the issue.

---

### Post by psykickuk on 2010-05-19
I too have found it a little frustrating that applying the keyboard setting system-wide did not change the defaults at the login screen.

This caused me to resort to numerous fixes around forums before realising that the log in screen added a keyboard layout to the users' desktop environment if what was selected at login was different to the users' default setting.

It would be nice to have the option to remove previously selected layouts from the log in screen to ensure that when users choose to set a keyboard layout systemwide, they do not accidentally keep logging in with a previous preference.

Does anyone know what files control the login screen and individual users' desktop layouts, so I can have a nose around manually if the desire takes me?

---

