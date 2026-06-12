---
title: "Ubuntu over Windows? Help!"
date: 2009-06-21
forum: General Help
---

### Post by Spaceman7o on 2009-06-21
Ok so i have ubuntu and windows... and ever since yesterday (when i got sound working on ubuntu) ive been hooked, but generally when i load up my computer the dual boot menu comes up and windows vista is on top of ubuntu. If i wait too long (6 seconds or something) windows loads. Is there any way to get ubuntu option on the dual boot to be over vista? Although this is really small i generally have to reset my computer which in turn leaves me frustrated help!

---

### Post by SteveDee on 2009-06-21
> **Spaceman7o said:**
> Ok so i have ubuntu and windows... and ever since yesterday (when i got sound working on ubuntu) ive been hooked, but generally when i load up my computer the dual boot menu comes up and windows vista is on top of ubuntu. If i wait too long (6 seconds or something) windows loads. Is there any way to get ubuntu option on the dual boot to be over vista? Although this is really small i generally have to reset my computer which in turn leaves me frustrated help!

Install Startup Manager (from Applications > Add/Remove). This will allow you to change bootup settings using a nice friendly GUI rather than having to edit your menu.lst file manually.

To change default OS, System > Administration > Startup Manager > Boot Options > Default Operating System.

---

### Post by paperplate9 on 2009-06-21
/boot/grub/menu.lst

Change your "default" option to be Windows...remember that the first entry is zero.

---

### Post by Spaceman7o on 2009-06-21
i know this is gona sound bad but i dont get what you mean im a fricken nooob at this man.

---

### Post by Spaceman7o on 2009-06-21
Thread closed got it thankyou all who helped :D

---

