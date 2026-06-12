---
title: "Window Control Position in Ubuntu Classic (11.04)"
date: 2011-05-02
forum: Desktop Environments
---

### Post by b.miguel11 on 2011-05-02
Hi everyone,

I have installed Ubuntu 11.04 and tried Unity for a bit (though it is still immature, the idea isn't too bad). Using **gconf-edit** I could successfully change the window control buttons from right to left. Now I had to do a fresh install and this time I chose Ubuntu Classic. I did just the same thing but the buttons still figure on the left side of every window. Can anyone please tell me how can I place them in the right side?

Many thanks!

---

### Post by ducuit on 2011-05-20
I have Ubuntu Classic No Effects and for me the gconf-edit**or** worked.

just in case you had used a different path, this is the setting:
/apps/metacity/general/button_layout

i have taken my buttons out altogether (just leave the : in the button_layout field).
for you, the suggestion is to swap the string before the : with the string after it.

let me know if it works out.

---

### Post by NormanFLinux on 2011-05-20
Simpler way is to choose a theme that has buttons on the right. If you like the Radiance button theme, you can customize to the windows controls.

---

