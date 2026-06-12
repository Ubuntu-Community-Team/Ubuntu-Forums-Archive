---
title: "Re-install of Ubuntu does not work on Dell Inspiron 14(3421)"
date: 2013-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nickton on 2013-03-17
Hi,

I have a problem with my Dell system which requires advice!

I have a Dell Inspiron 14(3421) (i5, 1GB NVIDIA graphics, 4gb RAM, etc.) which came pre-installed with Ubuntu 12.04LTS. I suppose that the version was a specially customised version of Ubuntu by Dell for this 3421 system with in-built drivers,etc. So I made a Dell Ubuntu 12.04LTS recovery disk as they prompted to me the first time I powered-ON my system. Then, I formatted the whole drive, wiped out everything, created partition and installed my unused copy of Win-7-Pro-64bit. its working successfully without problems. Now I wanted to load Ubuntu as the secondary dual boot OS to my system with Win-7 being Primary. So i tried the following:

1) I Used the Dell Ubuntu System Recovery Disk to install/load ubuntu 12.04 LTS. In the setup interface I selected "LOAD AND INSTALL ONLY MY UBUNTU PARTITIONS". I Created the ext4/ and swap for the installations,etc. Everything went on OK and files got copied successfully  The system restarted and the next stage of the setup began where I had to type in computer name, username, password,etc. which I did. Evrything seemed ok. but then the progress bar shows CONFIGURING and then setup stops and shows an error message that "Installation has stoped/encounterd a problem/will not continue, Do you want to send error report?" ------------ [B][I]SO IN SHORT THIS OPTION I TRIED OVER AND OVER AGAIN BUT DID'NT WORK. WHY is it happening?Is'nt the recovery medium supposed to work? HOW DO I SOLVE IT?
[/I][/B]
2) Next I downloaded the fresh Ubuntu 12.04LTS 64bit from the Ubuntu website. I loaded it on a PenDrive using the UNIVERSAL USB INSTALLER and tried booting from USB. It booted successfully and shows the 1st option screen Try Ubuntu, Install, Mem Test,etc. But when I select the option Install on Hard Drive/Try Ubuntu the screen goes blank and the same list of options appear again. ------[I][B]WHY is it happening? HOW DO I SOLVE IT?
[/B][/I]
3) I suppose 12.04LTS is always more stable due to the LTS. but will installing the latest 12.10 will help in anyway? Why did'nt the Dell Ubuntu recovery disk work?:(

What do I do? Can anyone help me? all responses will be appreciated as I am new to Linux/Ubuntu!:) plzzzzzzzzzzzz....

---

### Post by Hexxus on 2013-03-18
I know this might sound weird so hear me out:

Did you try to format your USB drive, re-image it with Ubuntu and see if it works again? I've had a few USB Drives for no apparent reason not work, then I re-add the image then they work fine.

Regarding your Dell media, can you go to [www.dell.com/support](www.dell.com/support) - enter in your service tag (After choosing home, SMB, or enterprise) and see if you can re-download it and try again? My best guess
would be to check out the media your installing from first, usually that's solved my problems in the past.

---

### Post by rvergara on 2013-05-18
Hi,

I have the same laptop that came with Ubuntu 12.04, however I only use W7 for signing electronic invoices in my country otherwise I am 100% on Ubuntu, so I generated a VM with W7 and that was it.

I wonder why you wanted W7 as your primary in a dual boot instead of just installing it in a VM

---

### Post by rvergara on 2013-05-18
Hi,

I have the same laptop that came with Ubuntu 12.04, however I only use W7 for signing electronic invoices in my country otherwise I am 100% on Ubuntu, so I generated a VM with W7 and that was it.

I wonder why you wanted W7 as your primary in a dual boot instead of just installing it in a VM

---

