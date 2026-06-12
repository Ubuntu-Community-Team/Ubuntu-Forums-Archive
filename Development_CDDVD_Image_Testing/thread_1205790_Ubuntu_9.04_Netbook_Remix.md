---
title: "Ubuntu 9.04 Netbook Remix"
date: 2009-07-06
forum: Development CD/DVD Image Testing
---

### Post by Yumpin_Yimminie on 2009-07-06
I decided to give Ubuntu another try on my Acer Aspire. It's been about 7 months since I looked at Linux or this computer.

Not having much luck with "**Ubuntu 9.04 Netbook Remix**" package. I've downloaded from a couple of sites (Purdue & MIT). When I check the hash with **winMD5Sum** it checks out just fine.

However after using **Win32DiskImager** to IMG file to flashcard I am having problem. I can check the directory on the flashcard and have no problems seeing it. But when I put the flashcard in the aspire and boot from the flashcard. I then choose the "Check file for errors" option. I consistently get a report of error in one file. I've tried this numerous times with downloads from either of the above mentioned sites.

So I decided to go the DVD route. I've used a couple of different packages for burning the ISO. The one's I've used are "**InfraRecorder**" and "**IsoBurner**." Haven't had any success with this route. After finishing the burn with either package. I attempted to read the directory using Windows XP Windows Explorer. All four of the times the system has been unable to read the directories. I've tried connecting the external DVD writer/reader to the Acer Aspire and boot from it. It gives me the boot menu option of loading from the DVD but then ends up loading the old Ubuntu version that was currently on the computer.

I'm looking for suggestions. From what I've read the file '**Ubuntu 9.04 Netbook Remix**' is supposed to have taken care of a lot of issues that I was having with the previous Ubuntu. But after so many failures, I'm beginning to wonder if the file has been changed and is non-operable now.

Help would be greatly appreciated.

Thank you.

Have a Great Day,
Jim

---

### Post by snowpine on 2009-07-06
Hi Y.Y., burning a CD/DVD will not work, as you have an .img file, not an .iso. These instructions should work ok: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Try just booting from your flash device, instead of choosing the "check for errors" option.

Also, if you already have a working Ubuntu install on the computer, have you considered simply using the Update Manager to upgrade to 9.04?

---

### Post by gwenn on 2009-07-06
I suggest you to find a linux user and prepare the netbook remix on a linux system where there are some good programs.It's the easiest way.9.04 has some tools that are very simple to make a stick with ubuntu.An example should be imagewriter.

---

