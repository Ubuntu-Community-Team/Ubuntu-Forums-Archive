---
title: "Help With Verizon USB Modem"
date: 2010-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OlRedHair on 2010-08-18
I just purchased a USB760 Modem from Verizon for my Dell Mini9 Netbook running Ubuntu. It says on the Verizon website that the modem is compatable with Linux. But I can't get it to work.  It works fine on my Vista laptop. Can anyone give me some help?

Thank you so much!
__________________
Nora

---

### Post by ssdt on 2010-08-20
Most of the modems work if you just plug it in and it starts to work fine.

---

### Post by OlRedHair on 2010-08-21
> **ssdt said:**
> Most of the modems work if you just plug it in and it starts to work fine.

That's what I was hoping for.  And it does "plug and play" on Windows.  But not on my Dell Mini9 Netbook operating Ubuntu.  The modem is a Novatel USB760, which Vezizon advertises as being compatable with Linux.  Neither Dell nor Verizon tech support was of any help.

This is a work around posted from another forum.  But I am a novice,and wouldn't have any idea how or where to type in these commands.  All I have ever done on a computer is read email, research, shop, and read forums.

This is the fix that was posted:

(2008 data) hope it helps: 
by GODhack - 8/19/10 6:57 AM In reply to: My New Modem for Mobile Broadband by nbwilcox 
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"

save and close

sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Add this in there:

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match>

save and close

Now plug in your card and make sure it didn't mount anything (Places -> Computer USB Drive shouldn't be mounted)
Now left click the network applet and select 'Auto mobile broadband (CDMA) connection'
It connect. If it doesn't make sure to go into VZAccessManager on a Windows machine and activate your USB760. VerizonWireless that works with Linux but it is on the enterprise section of [www.vzam.net](www.vzam.net) so call up or email VZW and ask to have it moved to the consumer downloads. They say the USB760 supports Linux on their site so be sure they provide the resources!

---

### Post by jstalnak on 2010-10-05
Brilliant! Steps involving the file edits worked perfectly. I only wish the same could be said for the networking issues I have with my HP Pavilion laptop!  Thanks for the posts.

---

