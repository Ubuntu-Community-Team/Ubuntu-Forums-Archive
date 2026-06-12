---
title: "storing CUPS print options"
date: 2005-12-12
forum: General Help
---

### Post by Brando569 on 2005-12-12
is there a way that i can store the printer options that i have to set everytime i go to print something through CUPS? the option that i want set is to reverse the printing order. its slightly annoying when i print a 20+ page document and have to organzine it. thanks

---

### Post by asimon on 2005-12-13
Try this:
1. Start "System Settings" from the K-Menue
2. Choose "Printers" under "Hardware"
3. Make sure you have CUPS selected under "Print System currently in use" on the lower right
4. Choose your printer from the list
5. Choose the "Instances" tab
6. There choose "Default"
7. "Settings"
8. Change your default Settings
9. Press the "Save" button in the settings dialog

Edit: Actually it should be easier than this. Doesn't it work if you just press the "Save" button after changing the properties in the print dialog?

---

### Post by Brando569 on 2005-12-13
thanks for the response but that didnt work, theres no "reverse print order" in the config, also there isnt a save button on the print dialog in Kword or openoffice :-/

---

### Post by asimon on 2005-12-13
Ah sorry, I confused some things. If you press "properties" in KDE's print dialog you get a new window were you can set some settings. There is a save button in this properties dialog but not on the general printing dialog. But these properties have no reverse printing order option (I read something about reverse in the dialog but it wasn't the printing order).

You can set the reverse order in KDE's printing dialog if you press options and in the copies tab choose "reverse" and "collate" under Output Settings. But I looks indeed like that those settings can not be saved and made default.

Because openoffice doesn't use KDE's printing facility the settings you make/save in KDE's printing dialog have no effect on openoffice.

But it seems there is a way to make cups print per default in reverse order: [How do I print pages always in reverse order?](http://www.linuxprinting.org/cups-faq.html#q_1_7). Sadly the instructions are not very verbose. It looks like you have to edit the ppd file with some editor.  The ppd for your configured printer should be found under /etc/cups/ppd/ . Probably you have to restart cupsd after making changes to that file via 'sudo /etc/init.d/cupsys restart'. Maybe someone with more cups knowledge can comment on that.

---

### Post by Brando569 on 2005-12-13
cool thanks ill try that out :)

---

### Post by arphe_el on 2005-12-14
how can i add printing options such as 

printout mode 
resolution, quality, ink type, media type

at the properties > device 

when printing documents?

my printer is HP 695c :)

---

### Post by Zurd on 2008-06-02
Though this post is 2 years old, I found it on google, so if someone else if also searching for my problem, here's the solution I found for "Reverse page order".

In Ubuntu with Gnome : 
System / Administration / Printing, click on your printer, then the Job Options tab, at the end for Other Options (Advanced), add outputorder and for his value, add reverse, click Apply and enjoy, I know I did after I printed a 77 pages PDF document, no need to reorganize it afterwards ^_^

---

### Post by Perfect Storm on 2008-06-03
Closed due to necromancing.

---

