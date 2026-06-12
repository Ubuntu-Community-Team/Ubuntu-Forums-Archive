---
title: "Flash"
date: 2009-02-22
forum: General Help
---

### Post by Krawnik on 2009-02-22
I'm pulling my hair out trying to figure out how to make that gray flash screen auto play when visiting certain web pages, I'm getting tired of having to click all the gray boxes to see what is on the page. I'm running Ubuntu 8.04 with the default Firefox browser.

---

### Post by mb_webguy on 2009-02-22
I've never seen that before (and if anyone should have problems with Flash, it's me since I'm using the 64-bit alpha release plugin).

I'm assuming we couldn't access the video in the screencap, considering the title of the page.  Could you post a link to a page where that occurs that we can access so we can test it?

---

### Post by WaffleCode on 2009-02-22
That looks like your using Gnash.

To get Adobe Flash, which is what you probably want, go to:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download the .deb.

---

### Post by Krawnik on 2009-02-22
ive tryed gnash, no change, ive downloading right off the adobe website, no change. ive tryed 4 or 5 deferent flavors of flash, and i get no change and have no alternate selections in my browser options. just a gray box that i have to click in order for it to load.

---

### Post by mb_webguy on 2009-02-22
I think WaffleCode is right, and I don't think you're using the plugin you think you're using.

Uninstall all Flash plugins, then to make sure, open Firefox and type "about:plugins" in the address bar.  If you see *anything* listed for Flash, you need to keep uninstalling.

Once you have everything even resembling a Flash plugin removed from your system, install the Adobe plugin either from the repositories or from the Adobe website.

---

### Post by Krawnik on 2009-02-22
Thank you very much that worked. in the process of removing all the flash players i had installed trying to fix the problem, 1 big problem manifested itself, and probably the cause of the problem, i had TOTEM installed for gnome. it was overriding everything else i was trying to do. 

thanx to Mb_Webguy and WaffleCode


btw how do i mark this thread as solved?

---

### Post by Hr_Birnbaum on 2009-02-22
How do you uninstall Flash plugins?  

> **mb_webguy said:**
> I think WaffleCode is right, and I don't think you're using the plugin you think you're using.

Uninstall all Flash plugins, then to make sure, open Firefox and type "about:plugins" in the address bar.  If you see *anything* listed for Flash, you need to keep uninstalling.

Once you have everything even resembling a Flash plugin removed from your system, install the Adobe plugin either from the repositories or from the Adobe website.

---

### Post by mb_webguy on 2009-02-22
Open System->Administration->Synaptic Package Manager.

In the search box, type "flash plugin".  Look for installed packages, and if it's a flash plugin, click the checkbox and mark it for removal.  You want to install flashplugin-nonfree if it's not already.  Now click the Apply button.

---

### Post by Hr_Birnbaum on 2009-02-23
Thanks!  Two more questions.  Does Ubuntu/Linux need a registry cleaner and defragment program?
If so, where can I find this software?


> **mb_webguy said:**
> Open System->Administration->Synaptic Package Manager.

In the search box, type "flash plugin".  Look for installed packages, and if it's a flash plugin, click the checkbox and mark it for removal.  You want to install flashplugin-nonfree if it's not already.  Now click the Apply button.

---

### Post by mb_webguy on 2009-02-23
Linux doesn't have a registry.  All user configuration settings and preferences are located in the user's home directory in hidden files and folders.  In Nautilus, type Ctrl-H to see them.  If you choose to completely remove an application, then these configuration files will also be removed.  So you have much better control over your settings than you do in Windows.

System-wide config files are usually found in /etc, though this generally only applies to applications that affect the system and must be run as root or with other elevated privileges.

As far as defragmentation, the native Linux filesystems like ext3 are designed to minimize fragmentation.  Basically you won't start to get any fragmentation until your filesystem starts to reach maximum capacity.  Unless you keep your drive more than 90% full for extended periods of time, you shouldn't ever have to worry about defragmentation -- which is good, because no one's seen the need to write a defragmentation application for ext3 as far as I know...

If you have an ntfs drive, however (such as if you're dual-booting and using ntfs for your shared partition) then you might still need to defrag it (from Windows) on occasion.

---

