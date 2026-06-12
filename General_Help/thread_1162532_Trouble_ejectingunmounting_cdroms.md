---
title: "Trouble ejecting/unmounting cdroms"
date: 2009-05-17
forum: General Help
---

### Post by bowens44 on 2009-05-17
when attempting to eject cdrom (mounted or unmounted) by right clicking and selecting eject from either Nautilus or the volume icon I get one of the following erros:

Cannot unmount volume an application is preventing the volume from being unmounted.

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I can unmount or eject the cdrom from the CLI.

This just started happening. I had lot of cdrom mounts and unmounts prior to this occurring.

I tried a google search but was unable to find out why this is happening or how to resolve the issue.

---

### Post by bowens44 on 2009-05-17
> **bowens44 said:**
> when attempting to eject cdrom (mounted or unmounted) by right clicking and selecting eject from either Nautilus or the volume icon I get one of the following erros:

Cannot unmount volume an application is preventing the volume from being unmounted.

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I can unmount or eject the cdrom from the CLI.

This just started happening. I had lot of cdrom mounts and unmounts prior to this occurring.

I tried a google search but was unable to find out why this is happening or how to resolve the issue.

Ok, I found the solution right after I posted this.

I deleted /media/.hal-mtab now everything is working properly.

---

### Post by emigrant on 2009-10-24
deleting that file didnt work for me,
even from cli i cant eject.
it asks me to switch to another user (less privliege) and then eject.
and it works :(

any idea how to solve?

---

### Post by CloudLover on 2009-10-25
[FONT=Comic Sans MS][SIZE=3][COLOR=Magenta]I found the following post when I was searching for a fix on how to unmound a cell phone icon from my desk top after I failed to unmount before I exited from Ubuntu. I am using my roommate's computer and both of us are newer than newbies when it comes to working on Linux. The post following the one I've copied/pasted below said that it worked but I don't have any idea what they're talking about. Can somebody put the following in plain English for me? I would really appreciate it. Cheers.[/COLOR][/SIZE][/FONT] :confused:


Actually, I discovered it's a known HAL bug in Ubuntu 7.04. I fixed it with this command:

 	Code:
 	sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup 
and now unmounting works like a charm.

---

