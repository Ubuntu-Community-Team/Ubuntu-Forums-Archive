---
title: "Ubuntu boot error after resize the partition"
date: 2009-01-19
forum: General Help
---

### Post by bio_amateur on 2009-01-19
I have a dual-boot system (XP and Ubuntu Intrepid). Here is my disk configuration.
<XP installation> | <data disk> | <unused partition> | <Linux swap> | <Ext3 - Ubuntu>

So, now I wanted to increase the size of the <Ext3-Ubuntu>. I used Acronis disk director to 
  (1)  move <Linx swap> in front of <unused partition>
  (2)  merge <unused partition> into <Ext3-Ubuntu>
However, after resizing, I cannot boot into Ubuntu Intrepid. There is no error message, only a black screen. Any one can tell me how to fix the problem. I have the live CD.

Thanks

NOTE: I use Acronis OS Selector to manage multi-OS, GRUB is installed in the partition of <Ext3-Ubuntu>.

---

### Post by theWrkncacnter on 2009-01-19
Can you still boot into Windows?
Describe what happens when you boot, starting with when you turn on your computer to where you get the blank screen. With more information we'll be able to tell better where something is going wrong.

---

### Post by dcstar on 2009-01-20
> **bio_amateur said:**
> I have a dual-boot system (XP and Ubuntu Intrepid). Here is my disk configuration.
<XP installation> | <data disk> | <unused partition> | <Linux swap> | <Ext3 - Ubuntu>

So, now I wanted to increase the size of the <Ext3-Ubuntu>. I used Acronis disk director to 
  (1)  move <Linx swap> in front of <unused partition>
  (2)  merge <unused partition> into <Ext3-Ubuntu>
However, after resizing, I cannot boot into Ubuntu Intrepid. There is no error message, only a black screen. Any one can tell me how to fix the problem. I have the live CD.

Thanks

NOTE: I use Acronis OS Selector to manage multi-OS, GRUB is installed in the partition of <Ext3-Ubuntu>.

Changing partition sizes usually changes the UUIDs, do a search for fixing these (especially swap) and you might be able to get some useful info.

---

### Post by bio_amateur on 2009-01-20
> **theWrkncacnter said:**
> Can you still boot into Windows?
Describe what happens when you boot, starting with when you turn on your computer to where you get the blank screen. With more information we'll be able to tell better where something is going wrong.

The Acronis Partition Manager need to restart to make the necessary change to the partitions (resizing, merging) as described. After making the change, it restart the machine. As I use the Acronis OS Selector to manage the multi-OS (not the GRUB), I just choose Ubuntu to boot. Unfortunately, it doesn't work, a dark screen appear. Then, I restart the machine and this time I choose XP. There is a message from Acronis notifying the task had been completed and Windows XP run normally. It means the master boot sector is ok, it is managed by the Acronis OS Selector, not by GRUB. I'm afraid there is some error when I resize the partition where I installed Ubuntu and where the GRUB is installed also.
Any help is greatly appreciated.

---

### Post by caljohnsmith on 2009-01-20
In order to get a clearer picture of your setup and the current state of your partitions, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Ubuntu booting problem might be.

---

