---
title: "Ubuntu and Windows can share the same home drive"
date: 2009-04-05
forum: General Help
---

### Post by optimistique1 on 2009-04-05
Hi All
I am thinking about dual booing with Windows so that I have access to iTunes.  Unfortunately, using WINE with iTunes is rubbish and using Windows in Virual Box you cannot plug your iPod in.
Anyway, I heard that you can set the system up so that Ubuntu and Windows can share the same home drive and wondered how to do this.
I have looked around and cannot seem to find anything?
I have heard of Samba and wondered if this has anything to do with what I am trying to achieve);)

---

### Post by albinootje on 2009-04-05
> **optimistique1 said:**
> using Windows in Virual Box you cannot plug your iPod in.

The OSE version of VirtualBox doesn't have usb support.
Install the latest PUEL VirtualBox version from [http://www.virtualbox.org](http://www.virtualbox.org) if you want usb support.
Then you should be able to make your ipod work.
> 
Anyway, I heard that you can set the system up so that Ubuntu and Windows can share the same home drive and wondered how to do this.

Perhaps you mean running VirtualBox or VMware with physical disk access ? That's tricky stuff, but there's a howto for that on this forum somewhere.
> 
I have heard of Samba and wondered if this has anything to do with what I am trying to achieve);)
Not really, Samba is for talking via the SMB protocol between computers.

---

### Post by 3Miro on 2009-04-05
> **optimistique1 said:**
> Hi All
I am thinking about dual booing with Windows so that I have access to iTunes.  Unfortunately, using WINE with iTunes is rubbish and using Windows in Virual Box you cannot plug your iPod in.
Anyway, I heard that you can set the system up so that Ubuntu and Windows can share the same home drive and wondered how to do this.
I have looked around and cannot seem to find anything?
I have heard of Samba and wondered if this has anything to do with what I am trying to achieve);)

There is a way to install Ubuntu and Windows under the same partition with wibi. You first install windows and then you install Ubuntu form within windows, however, if Linux is your primary system you don't want to do that. Under the above setting Linux would be installed on the windows NTFS partition and will be slower.

Your best bet is to download the free version of Virtual Box that comes with USB support.

---

