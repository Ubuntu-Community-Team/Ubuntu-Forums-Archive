---
title: "I need some help with the kernel"
date: 2009-06-05
forum: General Help
---

### Post by TheGreatSudoku on 2009-06-05
two kernel related issues I'd appreciate help with/

#1 ... I have a Motorola ROKR that requires a kernel patch to be recognized properly by usb-storage.  The patch I found in a website thread:

[http://osdir.com/ml/linux.usb.general/2008-03/msg00700.html](http://osdir.com/ml/linux.usb.general/2008-03/msg00700.html)

I'm familiar with getting the kernel source and rolling my own kernel.  But I've never patched it before.  Do I just copy and paste the text of the patch in an editor and save it?  If so where do I begin and end copying in the message?  Also once I get the patch what's the syntax to apply the patch?  (after that I feel fairly competent I can find and enable it in menuconfig)


#2.  Every time I go about rolling my own kernel I end up disabling something that cpu frequency scaling needs.  Can anyone tell me what the kernel dependencies of CPU Frequency scaling are?

---

### Post by Locutus_of_Borg on 2009-06-05
to apply the patch, first copy the text of the patch to a text file in your home directory, name it something like ROKR.patch
the file should be:
```

Signed-off-by: Constantin Baranov <const-ahc5v4N+eSY@xxxxxxxxxxxxxxxx>
Signed-off-by: Matthew Dharm
<mdharm-usb-JGfshJpz5UybPZpvUQj5UqxOck334EZe@xxxxxxxxxxxxxxxx>
Signed-off-by: Daniel Drake <dsd-aBrp7R+bbdUdnm+yROfE0A@xxxxxxxxxxxxxxxx>
Cc: stable <stable-DgEjT+Ai2ygdnm+yROfE0A@xxxxxxxxxxxxxxxx>
Signed-off-by: Greg Kroah-Hartman <gregkh-l3A5Bk7waGM@xxxxxxxxxxxxxxxx>
---
drivers/usb/storage/transport.c | 3 ++-
drivers/usb/storage/unusual_devs.h | 11 +++++++++++
include/linux/usb_usual.h | 4 +++-
3 files changed, 16 insertions(+), 2 deletions(-)

diff --git a/drivers/usb/storage/transport.c b/drivers/usb/storage/transport.c
index 5780ed1..bdd4334 100644
--- a/drivers/usb/storage/transport.c
+++ b/drivers/usb/storage/transport.c
@@ -1009,7 +1009,8 @@ int usb_stor_Bulk_transport(struct scsi_cmnd *srb, struct
us_data *us)
US_DEBUGP("Bulk Status S 0x%x T 0x%x R %u Stat 0x%x\n",
le32_to_cpu(bcs->Signature), bcs->Tag,
residue, bcs->Status);
- if (bcs->Tag != us->tag || bcs->Status > US_BULK_STAT_PHASE) {
+ if (!(bcs->Tag == us->tag || (us->flags & US_FL_BULK_IGNORE_TAG)) ||
+ bcs->Status > US_BULK_STAT_PHASE) {
US_DEBUGP("Bulk logical error\n");
return USB_STOR_TRANSPORT_ERROR;
}
diff --git a/drivers/usb/storage/unusual_devs.h
b/drivers/usb/storage/unusual_devs.h
index 99679a8..e5219a5 100644
--- a/drivers/usb/storage/unusual_devs.h
+++ b/drivers/usb/storage/unusual_devs.h
@@ -1589,6 +1589,17 @@ UNUSUAL_DEV( 0x22b8, 0x4810, 0x0001, 0x0001,
US_SC_DEVICE, US_PR_DEVICE, NULL,
US_FL_FIX_CAPACITY),

+/*
+ * Patch by Constantin Baranov <const-ahc5v4N+eSY@xxxxxxxxxxxxxxxx>
+ * Report by Andreas Koenecke.
+ * Motorola ROKR Z6.
+ */
+UNUSUAL_DEV( 0x22b8, 0x6426, 0x0101, 0x0101,
+ "Motorola",
+ "MSnc.",
+ US_SC_DEVICE, US_PR_DEVICE, NULL,
+ US_FL_FIX_INQUIRY | US_FL_FIX_CAPACITY | US_FL_BULK_IGNORE_TAG),
+
/* Reported by Radovan Garabik
<garabik-IzrVb8zMLl5g+5vNovSFJejSgzwOyGl/@public.gmane.org> */
UNUSUAL_DEV( 0x2735, 0x100b, 0x0000, 0x9999,
"MPIO",
diff --git a/include/linux/usb_usual.h b/include/linux/usb_usual.h
index cee0623..0a40dfa 100644
--- a/include/linux/usb_usual.h
+++ b/include/linux/usb_usual.h
@@ -50,7 +50,9 @@
US_FLAG(CAPACITY_HEURISTICS, 0x00001000) \
/* sometimes sizes is too big */ \
US_FLAG(MAX_SECTORS_MIN,0x00002000) \
- /* Sets max_sectors to arch min */
+ /* Sets max_sectors to arch min */ \
+ US_FLAG(BULK_IGNORE_TAG,0x00004000) \
+ /* Ignore tag mismatch in bulk operations */


#define US_FLAG(name, value) US_FL_##name = value ,
-- 
1.5.4.3

```

then open a terminal become root and cd to the kernel source directory
```

sudo -i
cd /usr/src/linux
```

finally apply the patch with the following command
```

cat ~/ROKR.patch | patch -p1

```

as long as the patch is for that kernel version there should be no errors


read here: [http://en.gentoo-wiki.com/wiki/CPU_Frequency_Scaling](http://en.gentoo-wiki.com/wiki/CPU_Frequency_Scaling)
for cpu frequency scaling information

---

