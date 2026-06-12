---
title: "Help: Possible to run Windows as a desktop?"
date: 2009-02-12
forum: General Help
---

### Post by janthonywj on 2009-02-12
Howdy,

I'm pretty new to Linux, so this question might insult some of you. I'm wondering if it is possible to run Windows and have it take the place of one of my Linux desktops. 

If not, what is the best way to use both operating systems? I love the switch to Kubuntu, and I'm learning quickly, but I'm not so experienced with Wine, and I'm doubting it would handle some apps like Blackberry manager. I need to use Blackberry Manager to update leaked software to my Storm for instance. Games. etc. 

If so, what can I expect in terms of resource requirements? 

Thanks,
Anthony.

---

### Post by thegreenblob on 2009-02-12
So you want to replace linux with windows? If so all you have to do is pop in the windows install disc and install it like normal.

If you're asking to dual boot with linux installed first, I believe it's possible but I'm not sure how.

---

### Post by ajmctaggart on 2009-02-12
Okay, the ? is pretty insulting :) Just kidding...

Here's the deal...
If you want to run Windows XP or Vista WITHIN Kubuntu you need to install a Virtual Machine...It is a "XP Installation" that runs within Linux...Sometimes an app works, sometimes it doesn't...trial and error will be the only way to know (I'm sure someone has tried and succeeded or failed already at Blackberry Desktop Manager on a Virtual Machine, so you wont ACTUALLY have to do it before knowing whether or not it'll work, just google..."

Right Now, the ones I know of for Ubuntu are VMWare and Virtual Box...Virtual Box is pretty popular right now for OpenSource and for Individual users...

If you want to Dual Boot Windows with Linux, the suggestion would be to partition AT LEAST 2 partitions, One for Linux and one for Windows, and install Windows FIRST THEN KUBUNTU...

If you've already got Kubuntu right where you want it and install Windows, it may take a little work to get Grub going again...(You'll need to pop in a live-cd and "re-calibrate," Grub.  This is because your MBR Master Boot Record which is currently being controlled by Grub, will get overwritten with Windows own idea of what it should be, which will usually close of access to your Linux drive till you fix Grub...

Sorry if this sounds confusing, but Google and these forums can get you through it no problem...

Good Luck...

---

