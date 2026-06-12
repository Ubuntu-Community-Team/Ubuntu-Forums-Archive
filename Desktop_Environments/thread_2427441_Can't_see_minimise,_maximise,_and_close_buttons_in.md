---
title: "Can't see minimise, maximise, and close buttons in ubuntu."
date: 2019-09-22
forum: Desktop Environments
---

### Post by shakil-ruetb on 2019-09-22
Dear all,

I am very new to ubuntu, and I am using ubuntu 18.04. Unfortunately, I can't see all three buttons - close, maximise, and minimise - simultaneously. I have attached the screenshot for your information. 


 I can only see one button at a time and can move it from left to right and right to left using the following commands:

```
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize, maximize, close'  


gsettings set org.gnome.desktop.wm.preferences button-layout 'minimize, maximize, close' 
```

When the above commands executed, only the first one (minimise in the commands) is displayed. If I type the close first instead of minimise, I can see only the close button. 

Thank you for your suggestions!

---

### Post by Dennis N on 2019-09-22
There should not be spaces after the commas. Then all three buttons will show.
Instead of terminal commands, you can also set this with dconf-editor.

---

### Post by shakil-ruetb on 2019-09-23
Hi Dennis,

Many thanks - removal of spaces after the commas did work perfect!

Thanks again,
Mahmudul

---

