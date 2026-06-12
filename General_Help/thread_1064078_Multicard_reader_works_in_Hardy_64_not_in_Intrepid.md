---
title: "Multicard reader works in Hardy 64 not in Intrepid 64"
date: 2009-02-08
forum: General Help
---

### Post by oubaas on 2009-02-08
Been digging about for a few hours now with no real solution for this,
Have a multi card reader:
ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer
(Internal/External)
That works perfectly on Xubuntu 8.04 AMD64 machine with MSI P6NGM mobo, so I bought another for my new box, and installed Xubuntu 8.10 AMD64 on MSI P7NGM mobo.
On new box all the USB plugs work fine, the SD Card slot works rarely, the CF card slot never.
Controller seems to be nVidia MC79 EHCI USB2.0.
When I insert a Kingston 2GB CF card, nothing happens.
So I do Places->Removable Media->CompactFlash Drive, and after about 30 secs I get 

Unable to scan CompactFlash Drive for media changes
Cannot invoke CheckMedia on HAL:
org.freedesktop.DBus.Error.NoReply.

I have checked that I have permission for messageBus.
The SD card is not a real issue for me, but I would really like to be able to read/write
CF cards. ( I use them a lot @ work)
Thanks

---

