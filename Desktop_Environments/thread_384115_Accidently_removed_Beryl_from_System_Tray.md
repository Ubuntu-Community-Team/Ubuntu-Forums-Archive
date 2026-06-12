---
title: "Accidently removed Beryl from System Tray"
date: 2007-03-14
forum: Desktop Environments
---

### Post by jesters8 on 2007-03-14
I installed Beryl and was having it start automatically when I began an Xgl session. When messing with the system tray, I accidently clicked "Remove from Tray" on the Beryl Manager gem icon. Now I cannot replace it. Does anyone know how?

When I reload Xgl Beryl still runs fine, but the system tray icon is gone.

I have tried adding the beryl-manager executable to the system tray, but it doesn't behave the same way as before. I know have to right-click and click "run" to display the menu. Running beryl-manager from the terminal displays the menu where ever the cursor is. I have also tried completely removing and reinstalling all of beryl and emerald with the Synaptic Package Manager, however that didn't work either. I have also searched repeatedly to no avail on the Web. Can anyone help?

---

### Post by adam.tropics on 2007-03-14
In your menu you can run beryl-manager from Applications-->System tools-->Beryl manager.

However, it sounds more likely that you have actually removed the notification area from the panel. Right click on the panel. Add  to panel, then add a notification area.(in the utilities section) If beryl manager is running you should have your diamond back, if not, do the first suggestion again, and it should appear.

---

### Post by jesters8 on 2007-03-14
Yup! I just had to add the notification area. Thank you so much.

---

