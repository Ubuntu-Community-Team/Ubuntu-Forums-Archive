---
title: "1720 suspend/hibernate issues"
date: 2008-10-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by number3 on 2008-10-03
I've got a inspiron 1720 and I'm currently on Ubuntu 8.04 and I'm having trouble with suspend and hibernate.

I'm able to go into a suspend and hibernate state without any issues, however coming out of either state is where I run into trouble.

When coming out from a suspend, all I see is a black screen, but with no keyboard input or hard drive activity; and I have to manually shut down and boot up to get back to Ubuntu.

When it comes to hibernate, all I end up seeing is black background and a stretched Ubuntu logo.  I do have keyboard input however the only thing that seems to do anything is ctrl-alt-del; and the function keys to dim my lcd work.  Other than that, my laptop will sit on that screen for any length of time.

I've searched on the forums and have come across a couple of posts of people, with the same laptop, who have had success with suspend and hibernate.  One such post had something to do with updating video card drivers.

I have a Geforce 8600M GT, but don't know what version of drivers is being used.  Tried searching for nvidia-glx-new and I'm unable to find it when I use Synaptic Package Manager and if I go to System - Administration - Hardware Drivers I see nothing in the list.

Anyone have any suggestions as to what I can try of fiddle around with?

Thanks,

---

### Post by number3 on 2008-10-14
Does anyone have this problem?  Or is it just me?

---

### Post by dizcrypt on 2008-10-14
Try to set DOUBLE_CONSOLE_SWITCH parameter of /etc/default/acpi-support file to true. For me it works perfectly.

---

### Post by PinkFloyd102489 on 2008-10-14
I have the same problem on my 1720. I'll try what dizcrypt suggested.

---

### Post by Cavalierski on 2008-10-15
Hi, I'm using the same graphicboard but even without the setting it works fine.
System - Administration - Hardware , I can see the driver. This is my 3rd time installation but I've never encountered this kind of issue.

Have you ugraded from the lower version? If so there might be some mis-interoperability between the version.

---

### Post by number3 on 2008-10-15
> **dizcrypt said:**
> Try to set DOUBLE_CONSOLE_SWITCH parameter of /etc/default/acpi-support file to true. For me it works perfectly.

Hey dizcrypt.  I uncommented that line in the file you mentioned.  Unfortunately that didn't do the trick.

Again I was able to get my laptop to suspend, but coming out of a suspend only showed a black screen.  In fact when I initially get out of suspend I can see my num-lock light come on.  Tried putting caps lock but nothing happens.

However I'm able to press ctrl alt del and my laptop did reboot.

Cavalierski, in response to your question, how have you upgraded your video drivers from a lower version?  Because when I go to System - Administration - Hardware I see nothing in the list.

Thanks for the replies, I'm hopeful for getting this working because some people already have theirs working.

---

### Post by parajuito on 2008-10-15
i thought this was fixed with the new .21 kernel :S

---

### Post by dizcrypt on 2008-10-16
I had similar symptoms before the fix. Sometimes it was possible to recover througth pressing ctrl-alt-f1 (switch to console) and then alt-f7 (back to X), sometimes not.

Regarding the driver. After the installation, there was a message, whether to install proprietary driver or not.

Do you have proposed updates enabled on your system? It enabled on mine and AFAIR there were some fixes for suspend / hibernate.

---

### Post by number3 on 2008-10-16
> **dizcrypt said:**
> I had similar symptoms before the fix. Sometimes it was possible to recover througth pressing ctrl-alt-f1 (switch to console) and then alt-f7 (back to X), sometimes not.

Regarding the driver. After the installation, there was a message, whether to install proprietary driver or not.

Do you have proposed updates enabled on your system? It enabled on mine and AFAIR there were some fixes for suspend / hibernate.

Hey dizcrypt,

Which update are you referring to by the way?  I'm on release 8.04 (Hardy), kernel 2.6.24-19.

My Hal gui keeps crashing (tried to re-install it to no avail) so I'm unable to find out specifically what video drivers I'm on.

If it's possible would you be able to forward to me the link where you obtained the drivers for your video card?  Or if there is a certain repo I should enabled, could you please let me know?

---

### Post by dizcrypt on 2008-10-16
Hi number3,

I have hardy-proposed updates enabled (Software Sources - Updates), so my kernel is 2.6.24-21.

Do you have a checkbox "Proprietary drivers for devices (restricted)" enabled in Software Sources - Ubuntu Software?

---

### Post by number3 on 2008-10-17
> **dizcrypt said:**
> Hi number3,

I have hardy-proposed updates enabled (Software Sources - Updates), so my kernel is 2.6.24-21.

Do you have a checkbox "Proprietary drivers for devices (restricted)" enabled in Software Sources - Ubuntu Software?

Fantastic, hibernate and suspend work!

The trick for me was to check the checkbox you mentioned dizcrypt.  I than ran update manager and the nvidia drivers were installed.

Thanks for all your help.

Regards,

---

