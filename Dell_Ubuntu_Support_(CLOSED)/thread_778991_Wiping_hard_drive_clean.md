---
title: "Wiping hard drive clean"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gecko113 on 2008-05-02
is there a program that is free that can wipe the hard drive clean and write it with all zeros but after this is done i'm leaving it blank no other OS is going on it.

---

### Post by mattyp123 on 2008-05-02
if you're SURE you want to wipe the drive, boot the ubuntu live CD and try a dd if=/dev/random of=/dev/sda or whatever the drive is...

do that a few times and you're good - better than zeros too

---

### Post by barichardson5727 on 2008-05-03
If you would like to make multiple passes on your hard disk I would recommend using the shred command. 

You can specify the number of passes with the -n switch.

```
brad@rasengan:~$ sudo shred -n2 -v /dev/sdb
```

This should be run from a livecd.

---

### Post by niteshifter on 2008-05-03
Hi,

Two good methods of "clearing" your hard drive are already given. But just for the sake of a precise answer:

With a Live CD and in a terminal do this:

```
sudo dd if=/dev/zero of=/dev/XdY
```

where XdY is the drive, i.e. sda, sdb, or hda, hdb, etc.

I mention this as perhaps the OP wants the drive to appear "virgin" ...

---

### Post by dragoon025 on 2009-02-10
i am just trying to figure how to get back to my old os to play my WOW can anyone help just e-mail me the e-mail is [email]crackercs711@yahoo.com[/email]

---

### Post by JK3mp on 2009-02-10
dragoon...wats your old OS? Windows? And did you delete or rewrite over the windows partition or did you compress it to dual with Ubuntu..?

---

### Post by johngreth on 2010-02-16
I always just use dban. My site has info about it: [http://johngreth.com/blog/?p=4](http://johngreth.com/blog/?p=4)

---

### Post by viper250 on 2010-02-16
I agree with johngreth
I use d-ban to wipe drives for forensic purposes 
this program exceeds the requirement of the d.o.d. for a securely wiped drive and It will also perform a brute force test on the drive for errors.
d-ban is also free

---

### Post by manuganji on 2010-12-18
how long does this command ```
sudo dd if=/dev/random of=/dev/sda

``` take to execute ? is there a way to get a feedback of the progress of the process? mine is a 500 GB Toshiba hard drive.

I'm getting this reallocated sector count ( ID:5 ) error in my SMART status. That DELL guy asked me to erase the whole disk and reinstall the OS. Now, how do I erase my disk?

One more thing that dell guy told me was to use only one OS either windows or Ubuntu. not both. he says using two OS' may be corrupting my sectors.how far is this true?

---

### Post by yunone on 2011-01-27
> **manuganji said:**
> how long does this command ```
sudo dd if=/dev/random of=/dev/sda

``` take to execute ? is there a way to get a feedback of the progress of the process? mine is a 500 GB Toshiba hard drive.

I'm getting this reallocated sector count ( ID:5 ) error in my SMART status. That DELL guy asked me to erase the whole disk and reinstall the OS. Now, how do I erase my disk?

One more thing that dell guy told me was to use only one OS either windows or Ubuntu. not both. he says using two OS' may be corrupting my sectors.how far is this true?

i would take that advice with a grain of salt. Running multiple OS'es should not cause sector issues. Sector issues could come from manufacturing defects, excessive jarring, damage to the platters, etc.

I dual boot and have been so for many years with Windows and a Nix distro and wouldnt hesitate to continue to do so. 

this is taken from Wiki
"Typical hard drives attempt to "remap" the data in a physical sector that is going bad to a spare physical sector—hopefully while the errors in that bad sector are still few enough that the ECC can recover the data without loss. The S.M.A.R.T. system counts the total number of errors in the entire hard drive fixed by ECC, and the total number of remappings, in an attempt to predict hard drive failure."


hard drives have a certain number of sectors that are set aside per say to account for sectors going bad and as the drive ages or goes through the rigors of use, sectors will go bad and the SMART technology in HD's will write that data to other sectors preserving your data without you knowing it. 


if your drive is giving you sector warnings it might be time for a replacement and HD's are pretty cheap per GiB now... just some things to consider..hope this helps

---

### Post by phpdev on 2011-06-08
> **niteshifter said:**
> Hi,

Two good methods of "clearing" your hard drive are already given. But just for the sake of a precise answer:

With a Live CD and in a terminal do this:

```
sudo dd if=/dev/zero of=/dev/XdY
```

where XdY is the drive, i.e. sda, sdb, or hda, hdb, etc.

I mention this as perhaps the OP wants the drive to appear "virgin" ...

Excuse my noob-ness, but how do you know what to replace XdY with? I'm trying to wipe my Dell Mini 10's SSD before selling it, and am not good with command line at all. Using this technique, would the Dell/Ubuntu recovery disk still work to reinstall the OS?

---

### Post by T-56 on 2011-08-23
The following command will list all the drives, partitions and their sizes.

sudo sfdisk -l

---

### Post by XT99 on 2011-10-19
I used the old fashioned method of copying a very large file (a video file) over and over again until the drive was filled to the max and then deleted the folder. It may have taken a little time but I was sure the drive was cleared of all previous data. Just my old school way.

[http://www.theharddrivereviewer.com/seagate-goflex-review-2](http://www.theharddrivereviewer.com/seagate-goflex-review-2)

---

