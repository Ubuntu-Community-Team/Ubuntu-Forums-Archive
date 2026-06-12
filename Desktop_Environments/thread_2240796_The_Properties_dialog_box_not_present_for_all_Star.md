---
title: "The Properties dialog box not present for all Start Menu Programs Lubuntu 14.04"
date: 2014-08-22
forum: Desktop Environments
---

### Post by roler2 on 2014-08-22
I posted quite a while ago about this issue, actually when Lubuntu 14.04 first came out. A couple of weeks after I first posted the issue was fixed. Actually I believe the Properties dialog was present for all Start Menu Programs but did not work when clicked on, don't exactly remember. Now the issue has returned and now there is no option to click on for Properties. I was suprised being that 14.04.1 was supposed to include several bug fixes and improvements. The only option present is "Add to Desktop". Was the Properties option completely removed? Is there a way to retrieve the Properties dialog via any type of configuration file?

Any assistance would be greatly appreciated. Thank you.

---

### Post by Rex Bouwense on 2014-08-22
Hi roler2.  I just checked about a dozen of my start menu programs in Lubuntu 14.04 and the properties dialog box is there and is functional in all of them.  Could you provide some additional information as to which programs are missing the dialog box and/or which are non-functional.

---

### Post by roler2 on 2014-08-22
Hello Rex!

ALL of the Start Menu Programs do not have the Properties dialog box. It is missing from every Start Menu Program. The only option is "Add to Desktop". Is there a corrupt update that could be causing the issue? Is there a way to figure out which update it might be and reinstall the update with an earlier working version?

---

### Post by roler2 on 2014-08-23
I completely reinstalled Lubuntu. The Properties dialog box now appears for all Start Menu Programs but does not work when you right-click. This is similiar to what happened when Lubuntu 14.04 first came out. Then the bug was fixed and the Properties dialog box worked when you right-clicked. Now the issue appears to have returned. From what I have read, and I could be wrong and probably am, it looks like the lxshortcut is faulty. I noticed that it was upgraded. I believe the lxshortcut is what was fixed the last time this happened. Is there a way to figure out how to fix it via a configuration file? Or does the upgrade contain the issue? Is there a way to download and install the lxshortcut that was working correctly?

---

### Post by vasa1 on 2014-08-23
> **roler2 said:**
> I completely reinstalled Lubuntu. The Properties dialog box now appears for all Start Menu Programs **but does not work when you right-click**. This is similiar to what happened when Lubuntu 14.04 first came out. Then the bug was fixed and the Properties dialog box worked when you right-clicked. Now the issue appears to have returned. **From what I have read**, and I could be wrong and probably am, it looks like the lxshortcut is faulty. I noticed that it was upgraded. I believe the lxshortcut is what was fixed the last time this happened. Is there a way to figure out how to fix it via a configuration file? Or does the upgrade contain the issue? Is there a way to download and install the lxshortcut that was working correctly?
1. When you say it "does not work when you right-click", what doesn't work?
2. Could you please post a link to what you have read about lxshortcut being faulty?

---

### Post by roler2 on 2014-08-23
When you right-click on the Properties tab, another box should pop up that gives information about the specific Start Menu Program, such as the executable information, etc. In my case, nothing pops up. Just like in Windows, when you click on the Properties tab of any Start Menu Program it gives you information about that Program. In Lubuntu 14.04 when it was first released nothing popped up when you right-clicked on the Properties tab. Then a fix was issued and I noted it was with the LXShortcut. I noticed that the LXShortcut was also upgraded with Lubuntu 14.04.1 and now when you right-click on the Properties tab once gain nothing pops up. I also found out that when you uninstall LXShortcut the Properties tab also disappears from all Start Menu Programs. Re-installing LXSession brings the Properties tab back but no box pops up when you right-click. So I would like to restore functionality to the Properties tab.

When you right-click on your Properties tab on any Start Menu Program does another box pop-up? Maybe it is a problem with my configuration.

---

### Post by roler2 on 2014-08-23
In regards to your second question, I referred to my notes I took a while back and although I did not find anything about LXShortcut being faulty I did find this definition of LXShortcut:

[B][COLOR=#555555][FONT=Arial]LXDE ships with a .desktop file editor called LXShortcut[/FONT][/COLOR][COLOR=#555555][FONT=Arial]. It&#8217;s the application that is launched when you right click on a menu entry and choose the &#8220;Properties&#8221; option.

[/FONT][/COLOR][/B][COLOR=#555555][FONT=Arial]So it appears to me that since when you right-click on the Properties dialog box and nothing happens that the issue may have to do with a faulty LXShortcut as no application is launched when you right-click and choose the Properties option. Well, at least for me it doesn't.[/FONT][/COLOR]

---

### Post by vasa1 on 2014-08-24
Hi, thanks for clarifying. I'll get back a few hours later with an image of what I see.

---

### Post by vasa1 on 2014-08-24
Hi, here are three images, one after right-clicking on the desktop item and choosing "Properties", the other two for each tab seen in the "File Properties" window. This works in both the Lubuntu session as well as in an Openbox session in which LXSession has no part.

So things seem to be working for me although that's a feature of Lubuntu I don't use and didn't explore until seeing your thread.

What I did notice is that the first dropdown seen when clicking on the menu doesn't go away easily and that's an old bug :(

My Lubuntu is fully updated:
```
[01:31 PM] ~ $ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
[01:31 PM] ~ $ 

```

---

### Post by roler2 on 2014-08-24
Hello and thank you for the information. However I believe you are right-clicking on a Desktop shortcut and not any Start Menu Program Properties tab. If you go to the Start Menu and choose any Start Menu Program, pick any one it doesn't matter, such as Firefox, and then right-click on the Properties tab which is right below the "Add To Desktop" option, then please let me know if another box pops up with the "File Properties" Window. In my case it does not. The Desktop shortuts work just fine as you have posted. It is the Start Menu Program Properties tab that does not.

---

### Post by roler2 on 2014-08-28
It appears that this issue has been fixed. At least for me when I now right-click on the Properties tab for any Start Menu Program the "File Properties" box pops-up. Well. . .at least it did today. I hope it stays that way!

I very much appreciate the assistance in resolving this issue. Thank you!

---

