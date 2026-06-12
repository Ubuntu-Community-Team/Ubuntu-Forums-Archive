---
title: "terms of use startup disclaimer"
date: 2009-03-25
forum: General Help
---

### Post by joelswatson on 2009-03-25
hi,

i want to know can i have a terms of use disclaimer at the login screen of ubuntu, i know this sounds silly but a friend of mine wants to run ubuntu at his internet cafe, and wants people to agree to his terms and conditions before it will allow them to login.

i know you can do it in windows, but i have been on google, with no luck.

any help would be great

thanks

---

### Post by lovinglinux on 2009-03-25
I guess you could probably edit a GDM theme for that, but if you want a simple solution, then you could create a script to launch a zenity dialog with the disclaimer like this:

```
cat ~/disclaimer.txt | zenity --text-info --height=768  --width=1024 --title=Disclaimer; 
```

Where  ~/disclaimer.txt  is the file containing the terms of use.

Change the height and width to fill the entire screen.

If you have compiz enabled, you can use the Window Rules plugin to make this dialog fullscreen and above other windows.

You can then add this script to the session. The only problem is that it will be displayed after login.

---

