---
title: "Upgrade to lucid kills WEP [solved]"
date: 2010-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by twowheeler on 2010-05-01
In case anyone else encounters the same problem, here is what I did to get wifi working with lucid.

On my dell latitude C640, karmic ran very smoothly.  The upgrade to lucid caused the wireless to disappear.  Wicd would return "bad password".  Dmesg reported numerous lines like "Lucent/Agere firmware doesn't support manual roaming".  The orinoco_cs module loaded successfully as usual, but after login the network password dialog box would pop up every few minutes, even though the password was saved.  

I tried numerous fixes suggested in the forums, to no avail.  Finally I changed the wireless router settings from 64-bit WEP to WPA1, and voila, it syncs right up.  WPA is better security, but I could never get WPA to work on this laptop using ubuntu before so I was forced to use WEP.  So now I can (actually, have to) use WPA. 

I don't understand it, but it works.

---

### Post by Michl on 2010-05-01
I have the same problem on a Dell C610.  But I need to keep the
router on WEP because some devices connected to it are not
WPA capable.  Really, lucid should work with WEP, too.  SO
this does not seem like a solution but a workaround.

---

