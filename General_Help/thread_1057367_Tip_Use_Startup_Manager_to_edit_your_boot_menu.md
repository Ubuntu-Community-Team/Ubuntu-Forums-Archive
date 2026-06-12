---
title: "Tip: Use Startup Manager to edit your boot menu"
date: 2009-02-01
forum: General Help
---

### Post by guriman on 2009-02-01
[IMG]http://www.blogcdn.com/www.downloadsquad.com/media/2008/10/startup-manager.jpg[/IMG]

So you&#8217;ve decided to install Ubuntu on your computer, but you&#8217;re not ready to give up Windows altogether. No problem. During the install process, just take care not to overwrite Windows and you can have a dual boot setup in under an hour. But what&#8217;s this? The GRUB bootloader adds 10 seconds to your startup time if you don&#8217;t hit the key to skip the countdown. And it automatically assumes Ubuntu should be your default operating system.

It&#8217;s relatively simple to tweak your GRUB menu by editing the menu.lst file hanging out in the grub directory of your Ubuntu file system&#8217;s boot folder. You can change the boot order of the operating systems. Or you can adjust the countdown clock. But if you make a mistake, you could also make it quite difficult to load either Ubuntu or Windows.

Startup Manager, or SUM provides an easier way to edit your GRUB menu. You can find SUM in the Synaptic package manager or by typing &#8220;sudo apt-get install startupmanager&#8221; into a terminal window.

Once it&#8217;s installed, you can access Startup Manager from the System -> Administration menu. The utility lets you change the default operating system, adjust the screen resolution of the GRUB menu, and even alter the background and text colors. You can adjust the countdown timer, set a password, or alter a number of other settings. And there&#8217;s fairly little risk of messing up your boot menu beyond all repair.

---

### Post by jpeddicord on 2009-02-03
Moved to General Help for viewing. I don't think this qualifies as Tutorials and Tips content because it is a direct copy of the linked article. Thanks for citing your source, though.

Please throw sharpened objects at me if I am wrong on this policy.

---

