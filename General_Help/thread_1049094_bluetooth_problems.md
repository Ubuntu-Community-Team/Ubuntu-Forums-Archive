---
title: "bluetooth problems"
date: 2009-01-24
forum: General Help
---

### Post by tgpraveen on 2009-01-24
so i recently bought a bluetooth usb adapter made by same small company named ENTER it is popular for cheap stuff like this in India.
it gets detected in ubuntu 8.10 properly. but the problem is that i am not able to transfer files to my cell.
what happens is that my cell see my pc. and my pc sees my cell.
but when i click on setup new device in ubuntu then after it detects my cell and i select it.then i get a pairing failed msg. and nothing happens on the **cell** except that bluetooth symbol shows connection established for a few secs but then that goes off.

the cd that came with the adapter had bluesoliel for windows.

and by the way i have tried transfer with nokia n73,e51, and another motorola phone.

so now my question is

[LIST=1]
[*]How do i fix this file transfer and pairing issue?
[*]now could this be a driver problem? but since all bluetooth devices are being detected i thought no.what do u say??
[*]could it be faulty hardware but again the bluetooth devices are detected so less likely right?
[/LIST]

update1: bluetooth file transfer works correctly in windows using Bluesoleil so hardware is correct.


update2: ok now i am going to list exactly the error messages that i receive.

couldnt pair from pc to cell.
so tried reverse

and i could pair via the phone nokia n73.
so after doing this when i click
on browse files on device and selecting cell
i get error msg
Could not display "obex://[00:19:79:E4:1F:BE]/".Could not display "obex://[00:19:79:E4:1F:BE]/".

on clicking send to in nautilius and then in that bluetooth and clicking send
i get error msg
OBEX Push file transfer unsupported.

---

### Post by tgpraveen on 2009-01-24
ok so now when i use kernel version 2.24 and use ubuntu then it works everything works out of the box perfectly.
it is gr8.

but when i use my default kernel version which is the latest on my system 2.27 then i get the problems mentioned in the previous post. 

is this a known bug.

also i must add that i have not updated my system for about 45 days now.
so if this has been fixed since then then pls tell me so that i can do updates.

i have a internet sacc that costs per mb so dont want to keep doing regular updates.

---

### Post by fragos on 2009-01-24
Right click send to doesn't work any more for me. I have found I can right click the bluetooth icon and select Send Files to Device which does work. Otherwise bluetooth works for me with my TRENDnet dongle. Some phones require you to enable pairing but disable it again after a short delay -- a security measure I assume. On the Ubuntu side enabling pairing leaves it on until you manually turn it off.

---

### Post by tgpraveen on 2009-01-25
u didnt read my 2nd post.

this seems to be a regression which i might have to live with until i can get updates on my sys which is gonna take a long time.
if someone with the latest updates is still facing a similar prob then pls post so that a bugreport may be filed.

---

