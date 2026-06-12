---
title: "How to get apps to appear in the unity system tray."
date: 2012-03-03
forum: Desktop Environments
---

### Post by usalabs on 2012-03-03
At some point using unity, you may find you've installed an app and when run it "should" appear running in the background and shown in the system tray, one such app is cryptkeeper, (there may be others too), this method is to make sure that "ALL" apps that use the system tray are visible.

Using the Ubuntu software center, install 'Dconf Editor'

Then in the Dash Home, search for dconf editor and run it.

On the left side follow this line:-

Desktop->Unity->Panel

Then on the right window on the line that starts with Systray-Whitelist click it, then move along to the end of the line that shows:-

'Update-notifier']

and add , "all" so that the end of the line looks like this:-

'Update-notifier', "all"]

if yours shows anything else at the end of the line, before the square right bracket, just add:-

,"all"

between the last quote and the square bracket, EG:-

"something", "something", "all"]

then press enter to apply it, then close the editor.

This will ensure that 'ANY' program that relies on the system tray for visual representation of it running in the background, does get shown in the system tray, I tried it by running cryptkeeper as an example, and it does work.

---

### Post by kazztan0325 on 2012-03-03
There is an additional information which include the way to do this with the command line here:

"HOW TO RE-ENABLE THE NOTIFICATION AREA (SYSTRAY) IN UBUNTU, FOR ALL APPLICATIONS"
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html")

---

