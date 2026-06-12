---
title: "usb pen drive"
date: 2008-12-27
forum: General Help
---

### Post by mosaic2s on 2008-12-27
"you are not privileged to mount this volume"

This message pops up when i insert a usb pen drive.

Am using ubuntu 8.04 fully updated at the moment.

Any advise?

---

### Post by namdung on 2008-12-27
> **mosaic2s said:**
> "you are not privileged to mount this volume"

This message pops up when i insert a usb pen drive.

Am using ubuntu 8.04 fully updated at the moment.

Any advise?

Do u have administrator privileges?

In *System-->Admin-->Users and Groups*, select the *Properties* for your account and ensure that *Access external storage automatically* in *User Privileges* tab is selected.

---

### Post by mosaic2s on 2008-12-27
it is selected.

---

### Post by namdung on 2008-12-27
Seems like a Hardy bug.

Try
```
pmount /dev/sdX
```

U might need to install *pmount* and ensure sdX is wher the USB is.

---

### Post by mosaic2s on 2008-12-28
installed pmount.
ran

pmount /dev/sdb


situation is same as earlier. The 2gb pendrive is detected but no further.

"you are not privileged to mount this volume"

What next?

---

### Post by 5BallJuggler on 2008-12-28
> **mosaic2s said:**
> installed pmount.
ran

pmount /dev/sdb


situation is same as earlier. The 2gb pendrive is detected but no further.

"you are not privileged to mount this volume"

What next?

Do you have another pen drive to try? Do you get the same result?

---

### Post by mosaic2s on 2008-12-28
Yes. tried with 2. both are working ok on other os.
Earlier the usb pen drive worked fine.

---

