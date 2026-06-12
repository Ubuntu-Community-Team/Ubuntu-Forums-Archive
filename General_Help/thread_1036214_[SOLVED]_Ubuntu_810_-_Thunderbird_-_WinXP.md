---
title: "[SOLVED] Ubuntu 810 - Thunderbird - WinXP"
date: 2009-01-10
forum: General Help
---

### Post by sandman3838 on 2009-01-10
Hello

Just curious.... 

Of the 4 HD's that I have one is Winxp (NTFS) and a second HD is Ubuntu with it's default format.  In both operating systems I have Thunderbird running for my Email.  

Has anyone out there tried to combine both Email folders and setup a joint Email for both systems?

If it's possible, I was wanting to use one of my extra HD's for the Email folders?

Any ideas or suggested reading would be great.  Thank you one and all!

---

### Post by jesterthejedi on 2009-01-10
Moved off Thunderbird to Evolution. Use it here with Gmail, and I love it. You sure that computer is running okay with 4 drives? That wastes tons of electricity and can generate lots of heat. I would not be surprised if your computer overheated in the future, or something gives out prematurely. My advice, toss the extra drives, get a big roomy one, and partition it for your different OS. There are posts how to sync your linux and windows emails on the same drive, contacts, emails, etc. I would search Google first though.

---

### Post by skern03 on 2009-01-10
> **sandman3838 said:**
> Hello

Just curious.... 

Of the 4 HD's that I have one is Winxp (NTFS) and a second HD is Ubuntu with it's default format.  In both operating systems I have Thunderbird running for my Email.  

Has anyone out there tried to combine both Email folders and setup a joint Email for both systems?

If it's possible, I was wanting to use one of my extra HD's for the Email folders?

Any ideas or suggested reading would be great.  Thank you one and all!

I'm doing it right now, and it's pretty easy. I can boot into either OS, and share the same e-mail folders. I'm not able to share the same address book or settings. For the address book, I do an export into an LDIF (Lightweight Directory Interchange Format) file, and then import it.

So here's how you do it. You'll need to use your installation of Thunderbird on NTFS, because while Linux can read NTFS, Windoze can't read ext3.

Boot into Windows, and locate Settings for the account (you can usually click the Local Folders entry on the left panel of Thunderbird). In the settings dialog box, click Local Folders and make note of the location. It's usually something like this:
> Documents and Settings/<your acct>/Application Data/Thunderbird/Profiles/5xhwbl5c.default/Mail/Local Folders

Now boot into Linux. Make sure the NTFS partition where the mail is stored is mounted. Launch Thunderbird and open Settings. Go to Local Folders, and click the Browse button for the Local Directory field. Find the Local Folders as described above, and you're in business!

---

### Post by jesterthejedi on 2009-01-11
Actually Windows can read and write ext3 drives:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It does both ext2 and ext3, but there is a few steps that need to be checked. 
FAQ:
[http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

---

### Post by sandman3838 on 2009-01-11
Thanks for the help!

A few questions:

Does the
[http://www.fs-driver.org/](http://www.fs-driver.org/)
reformat the drive or do anything that I would need to backup the HD that I want both OS's to read?  I mean does it format or reconfigure the HD or is it just a driver?

I should mention that I already have "NTFS Configuration Tool" installed and running in System Tools.  I read somewhere that it too was needed.

Also, although I'm not planning on going this rout I had to ask this.  Call it a flash back!  In the past to solve this issue some folks have been using FAT32.  Fat32 if I remember correctly had a size limit of 32gb.  However, I'm pretty sure that if you re-partition the HD in Linux or WinXP Admin Disk Manager you can format the entire 200 GB HD?  Is this right or am I thinking of something else?

Thanks for the help!

---

### Post by jesterthejedi on 2009-01-11
No need to do anything to your ext3 drive. Its just a driver, and it gives the Linux drive a drive letter. I usually call it drive U or L. I honestly moved completely off Windows completely thats just the extra computer to store files and my room mate uses it. One down side is while booted in Windows you may have limits on networking the Linux drive.

As for the fat32 question, a separate partition can be formatted or changed to a different type, like NTFS without disturbing the other partitions on that drive. Also fat32 is slower to run on both Linux and Windows systems. One last note, you never want to defrag your ext2/3 or any Linux drive in Windows. This is asking to ruin the drive.

---

### Post by sandman3838 on 2009-01-12
Sounds good!  
Thank you so much for your help.

---

