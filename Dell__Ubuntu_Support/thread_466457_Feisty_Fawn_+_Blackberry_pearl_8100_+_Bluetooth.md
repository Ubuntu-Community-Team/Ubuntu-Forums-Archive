---
title: "Feisty Fawn + Blackberry pearl 8100 + Bluetooth"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by aerotops on 2007-06-06
Hi all,

I have been trying to get my Fiesty setup to connect to my Pearl via bluetooth. I have a Dell Inspiron E1705 with built in bluetooth.

My phone does recognize my computer but then it asks for a passcode. I tried "0000", no quotes, but that did not work. Can anyone help out with this?

Thanks,
Harsh.

---

### Post by magicfab on 2007-06-07
Does this work in Windows at all ?

---

### Post by aerotops on 2007-06-07
I don't really know. I did not try it. I mean the phone recognizes the computer by name and all (when running Fiesty), but then it asks for a passcode which I don't know about.

---

### Post by TheOtherShoe on 2007-06-15
The passcode for your computer is defined in the file /etc/bluetooth/hcid.conf - though ubuntu calls it a passkey instead of a passcode. I think by default it is "1234", but you can edit the file if you want to set it to something else. You will have to restart the bluetooth service for that change to take effect; or you can just reboot.

---

### Post by flat4 on 2007-06-19
iok that's is thru blue tooth, how about using the usb cable and attaching it to the computer? :?

---

### Post by showe1966 on 2008-03-21
there's another post about that called "blackberry tether success" or something link that

---

