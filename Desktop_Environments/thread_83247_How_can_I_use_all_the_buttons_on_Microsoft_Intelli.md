---
title: "How can I use all the buttons on Microsoft IntelliMouse Explorer v2.0 and keyboard"
date: 2005-10-28
forum: Desktop Environments
---

### Post by itsnotvalid on 2005-10-28
Sorry if I have made the title so long.

I am a new user of ubuntu (after several days of torture in Gentoo :???: ) and seems to be ubuntu is ten times much easier to install and get it run.
It start up without serious problems (except the detection for gurb, but since Gentoo handbook taught me how to fix so no problem), but just the back/forward buttons and 4-Way Scrolling is not working for my mouse (which is Microsoft Wireless IntelliMouse Explorer 2.0). After looking Howtos and Wikipages, I find no information on fixing this problem. It is simply because the HID interface of this particular mouse has custom commands. I searched the forums several times and other forums and found something like [here]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=186975&highlight=tilt"), but I can't understand well how to do that without building the kernel.

---

### Post by Appolusionist on 2005-10-28
[quote=itsnotvalid]
 
After looking Howtos and Wikipages, I find no information on fixing this problem. It is simply because the HID interface of this particular mouse has custom commands. I searched the forums several times and other forums and found something like [here]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=186975&highlight=tilt"), but I can't understand well how to do that without building the kernel.[/quote]
 
I found a few articles on the wiki that should point you in the right direction...
 
[HOWTO: Setup an Intellimouse or Mouseman's Back/Forward Buttons]("https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons")
[Many Buttons Mouse Howto]("https://wiki.ubuntu.com/ManyButtonsMouseHowto")

---

### Post by itsnotvalid on 2005-10-28
Sorry I have tried this two HOWTO already.
As I use xev to detect the mouse buttons, the side buttons has the same id as other buttons, which means the kernel is unable to detect those "custom HID" settings.
So besides building the kernel myself (which may make my system unstable because ubuntu is not totally designed to do so), what could I do?

---

### Post by itsnotvalid on 2005-10-31
Any clues?

---

### Post by Appolusionist on 2005-11-02
[quote=itsnotvalid]Any clues?[/quote]
 
I found this post here in the forums that has a working configuration for their Microsoft Wireless IntelliMouse Explorer 2.0 under Hoary 5.04. Maybe you can apply everything to Breezy.
 
[http://ubuntuforums.org/showpost.php?p=156761&postcount=4]("http://ubuntuforums.org/showpost.php?p=156761&postcount=4")

---

